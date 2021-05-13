# debian_container
Debian remote desktop container

version: "3.6"
services:
 debian:
   image: dgarridouma/debian_xrdp_vscode_java_cosmos_docker_iotcore
   ports:
     - "4389:3389"
   volumes: 
     - ${MYFOLDER}:/home/alumno/data # shared folder
     - .xsessionrc:/home/alumno/.xsessionrc # env variables
     - /var/run/docker.sock:/var/run/docker.sock # docker in docker
     - type: tmpfs
       target: /dev/shm # firefox requirement
     - ./cosmos-examples:/home/alumno/src/cosmos-examples # Note: This container has an own cosmos-examples directory
                                                          # that is "hidden" by this volume 
   networks:
      default:

networks:
  default:
    name: iot

