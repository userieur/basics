## Docker

*REQUIREMENT: Cloned Git-Repository which includes a DockerFile and Dockercompose (.yml) file*

* Setting up the DockerFile
* Initializing Dockercompose file
* First-time setup
* Common errors & solutions

#### Setting the environment
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
