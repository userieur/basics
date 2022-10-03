## Docker

*REQUIREMENT: Cloned Git-Repository which includes a DockerFile and Dockercompose (.yml) file*

* Setting up the environment
* Using the environment
* Closing the environment
* Common errors & solutions

### Setting the environment
1) Using a terminal, navigate to the folder which contains the Dockerfile (it should be the main folder of the repository)
2) Build the Dockerfile with the below code snippet.

*The Dockerfile should be a plaintext file called "Dockerfile"*

```
sudo docker build -t [name]:[version]            #e.g. canopus:1.0
```
3) Using the same terminal, use the below code snippet to initialize all the containers through a docker-compose (.yml) file.

*The Dockercompose file can be named however you like, but should use the .yml extension.*
```
sudo docker-compose -f docker-compose.yml up     #-f flags allows for monitoring all containers in terminal
```
### Using the environment
1) Open a new terminal and enter the following commands:

*These commands are made for a container running 3.10-slim (Linux)*
```
sudo docker exec -it [container name] /bin/bash #e.g. sudo docker exec -it canopus /bin/bash
```
2) In the same terminal (which is now a terminal within the container) navigate to the desired folder and run a file/program.
```
cd path/path & program file.ext                 #e.g. cd app & python3 main.py
```
### Closing the environment
1) Using the terminal which is running the docker-compose, enter `CTRL+C`. This terminates all running containers.
2) Enter the following command:
```
sudo docker-compose down                        #add --remove-orphans if you want to clean everything
```
3) Next time when starting the environment, you only have to do the `docker-compose up` from setting up the environment step 3

### Common errors & solutions
* Ports used in dockercompose file are already occupied

#### Ports used in dockercompose file are already occupied
1) Open a new terminal
2) Identify program that is using the port
```
sudo lsof -i:[port]                             #e.g. sudo lsof -i:2181
```
This should return something like this:
```
COMMAND PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
java    854 kafka  122u  IPv6  31313      0t0  TCP *:2181 (LISTEN)
```
3) Terminate program that is using the port (decide at own discretion)
```
sudo kill [PID]                                 #e.g. sudo kill 854
```
4) Close terminal
***
