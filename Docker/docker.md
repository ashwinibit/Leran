Architecture of Docker





Concepts

    Registry: where all reop are stored eg hub.docker.com
    Reposetry: collection of all released tags
    Tags: version image

1. Instalation

    docs.docker.com

    $ docker --version

2. Commands

    $ docker --version

    1. Deploy 1 application

        $ docker run -d -p 5000:5000 in28min/hello-world-python:0.0.1 RELEASE

            -d: detaiched mode it hides log
            
            if need logs run 
                $ docker logs
                $ docker logs <few uniqe words of output logs>
                $ docker -f logs : follow the logs

        $ docker run -p 5000:5000 in28min/hello-world-python:0.0.1 RELEASE
            
            it downlodas docker image from registry and runs it as container

            in28min/hello-world-python : path of docker image on docker hub 

            0.0.1: specific verison

            -p: --publish 
            
            5000(host port):5000(container port)


    2. Deoploy multiple application 
        simply change host port and run in different tabs
    

    3. $ docker images
        gives detal about Repository

    4. $ docker container ls
        detail of containers whih are running

    5. $ docker container ls -a
        detail of all containers
    
    6. $ docker container stop <name of container>

    7. 


















Rsources:
    https://github.com/in28minutes/devops-master-class/tree/master/docker#commands