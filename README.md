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

                
               
