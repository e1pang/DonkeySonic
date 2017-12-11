MAE 198: FALL 2017 

Professors: Jack Silberman, Maurício de Oliveira

Team Members: Parker Brown, Layton Hu, Dylan Steiner, Eric Pang

#### Relevant Links:
* [Get Ultrasonic Sensor here](https://github.com/ptbrown35/MAE198)
* [Forked Donkey (version that we used)](https://github.com/e1pang/donkey)
* [Master Donkey Github](https://github.com/wroscoe/donkey)
* [Class Website](https://guitar.ucsd.edu/mae198/index.php/Introduction_to_Autonomous_Vehicles)

#### Some explaining to do:
Instead of writing a seperate mode for the sonic sensors by themselves and then the sonic+camera together, I didn't have the foresight that I would have to go back, so I did the lazy thing. In the folders 'Sonic' and 'Sonic+Camera' are the files for 'manage.py' and 'keras.py' for that version. 

To differentiate my comments from those that pre-existed, mine will begin with '##@@##'

To use those files, you will need to make the following change in 'datastore.py'

### How to modify 'datastore.py' to accept the data type you want to add
'datastore.py' is found in donkey/donkeycar/parts/datastore.py

If you add a new part and you want to save the output to the tub, you need to make sure that type is supported. 

The part you need to modify is in line 310 (under the the put_record(self, data) function) in the forked version:
```python
if typ in ['str', 'float', 'int', 'boolean']:
                json_data[key] = val
```
For example, say you want to add 'listfloat' which is what we needed for our ultrasonic sensors (it returned a list of 3 numbers, like [1,2,3]). You would change it to:
                
```python
if typ in ['str', 'float', 'int', 'boolean','listfloat']:
                json_data[key] = val
```
### Extra: Playing with 'camera.py'
Under donkey/donkeycar/parts/camera.py
##### 1) Change what the camera sees- for example look down, up, side, in the middle, etc.
Do you want to change what your camera sees but you don't want to print/attach a new mount? Then this if for you!

[It's as simple as this, the 'zoom' function](http://picamera.readthedocs.io/en/release-1.13/api_camera.html#picamera.PiCamera.zoom)
Insert this in the camera's initialize function.

##### 2) Change what the camera returns or do things to the image- for example, image segmentation or filtering
The code saves the image in an array called 'frame.' If you want to do anything to the image, you can do it on the array before it is returned.

On line 34 of camera.py, the original:
```python
   def run(self):
        f = next(self.stream)
        frame = f.array
        self.rawCapture.truncate(0)
        return frame
```
Say you want to segment a 120x160 image 1/3 from the top. Then, you want throw out the rightmost 50 pixels on the top piece and keep everything on the bottom piece. It might looks something like:
```python
   def run(self):
        f = next(self.stream)
        frame = f.array
        self.rawCapture.truncate(0)
        return [frame[0:40,0:110], frame[40:120] #disclaimer: just an example, it is not debugged
```
                
               
