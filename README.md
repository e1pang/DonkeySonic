MAE 198: FALL 2017 
Professors: Jack Silberman, Maurício de Oliveira
Team Members: Parker Brown, Layton Hu, Dylan Steiner, Eric Pang (me ^_^)

For reference in case the master donkeycar has changed too much, I forked the version of donkeycar that we used into here: 
https://github.com/e1pang/donkey

### Relevant Links:
* [Get Ultrasonic Sensor here](https://github.com/ptbrown35/MAE198)
* [Forked Donkey (version that we used)](https://github.com/e1pang/donkey)
* [Master Donkey Github](https://github.com/wroscoe/donkey)
* [Class Website](https://guitar.ucsd.edu/mae198/index.php/Introduction_to_Autonomous_Vehicles)


#### First, some explaining to do:
Instead of writing a seperate mode for the sonic sensors by themselves and then the sonic+camera together, I didn't have the foresight that I would have to go back, so I did the lazy thing. In the folders 'Sonic' and 'Sonic+Camera' are the files for 'manage.py' and 'keras.py' for that version. 

To differentiate my comments from those that pre-existed, mine will begin with '##@@##'


# First: Modify tub.py to accept 'listfloat'

tub.py can be found in donkey/donkeycar/management/tub.py
