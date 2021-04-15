This project shows you how to map configmap and secrets as environment values 
and also as files that can be mounted as volumes types

The MongoDb-config yaml file contain the configmap as environment values
the mongodb-secret yaml file contain the username and password as key value pair
the mongodb-express file is the yaml that creates the pod and uses the values from the configmap and secrets file


The config-file contains the name of the file that is going to be created along with the contents of the file that it will contain
the secret-file will contain the file name along with the random secret info that is passed into it
the mosquitto-novolume file will create a pod without any volume , you will see after the pod is created if you enter the container
using the /bin/sh option and cd into the mosquito folder there is a mosquitto.conf file with default config info inside

Now if you create a pod using the mosquito-withvolume file , this mosquito.config file will be overwritten with your mounted volumes
first create your configmap and secrets using the yaml files
then create the mosquittowithvolumes pod (this file has a volumes section that uses the configmap file and a secrets file
Now you have to mount these into the container here you will list everything you want to mount from inside the pod, so in this case 
I want to mount the configmap and secrets and make sure it is readonly so it cannot be written over . this will also contain the mountpath
Now after the pod is created you can enter the container and check the path to find the values/files placed here 
