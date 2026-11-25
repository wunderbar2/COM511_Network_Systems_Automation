[Main Menu](../../../sessions/README.md) |[session6](../../session6/) | [Session 6 Notes](../docs/sessionNotes.md)

# Session 6 Notes - Docker orchestration with docker compose

In session 5, we saw how to install and run docker containers using the docker command line interface.
In most situations, however, we need to install several components and have them work together to delver a production application.

[Docker Compose](https://docs.docker.com/compose/) has proven to be a widely used solution for specifying how containers are to be run in a common application. 
In many scenarios, `Docker Compose` is all that is needed to spin up a local lab or run a system in production. 

In larger cloud based systems, [Kubernetes](https://kubernetes.io/) is often the preferred choice but this can be overkill for most smaller apps.

In fact until recently, you were encouraged by the cloud providers to deploy smaller container applications directly using docker compose files and this is still possible.

`Docker Compose` has now unfortunately been deprecated in the cloud in favour of `Kubernetes` or proprietary cloud container services but `Docker Compose` remains a strong contender for developing and testing applications locally and can also act as an orchestrator in small production environments.

I have provided some details below of cloud container services for interest - but this is more complicated than we need and beyond the scope of this module.

Amazon Elastic Container Service (ECS)
* [Migrate from Docker Compose to ECS](https://oneuptime.com/blog/post/2026-02-12-migrate-docker-compose-ecs-task-definitions/view)
* [How to Use Docker Compose with ECS](https://oneuptime.com/blog/post/2026-02-12-docker-compose-with-ecs/view#when-to-use-compose-vs-native-ecs)

Azure (Microsoft) 
* [Deployment of multiple Containers in Azure as Container Instance using Docker Compose](https://www.patrickkoch.dev/posts/post_20/)

In summary, `Docker Compose` remains a very good way to spin up containerised applications locally in development and in small production environments.
It can also act as a stepping stone into more complex container orchestration frameworks in the cloud.
We are going to use it to help us learn more about containers in a lab environment.

---
**Exercise 6.1**

Go through the exercises in  [docker-compose-examples](../docker-compose-examples).
Make sure you can explain 
* Using docker compose to build an image
* Using a pre-built image
* Injecting external files and folders from the guest into an image
* Using environment variables to inject values into a `docker-compose.yml` file
* Building more complex examples using multiple containers and networks

 => [internal] load local bake definitions                                                                               0.0s
 => => reading from stdin 746B                                                                                           0.0s
 => [internal] load build definition from Dockerfile                                                                     0.1s
 => => transferring dockerfile: 344B                                                                                     0.0s
 => [internal] load metadata for docker.io/library/ubuntu:22.04                                                          0.1s
 => [internal] load .dockerignore                                                                                        0.0s
 => => transferring context: 2B                                                                                          0.0s
 => [1/2] FROM docker.io/library/ubuntu:22.04@sha256:e0f80c829509ef4df9e76bd8944eb7b8ec25cbb379b112a7f9448b2c77a77c9b    1.5s
 => => resolve docker.io/library/ubuntu:22.04@sha256:e0f80c829509ef4df9e76bd8944eb7b8ec25cbb379b112a7f9448b2c77a77c9b    0.0s
 => => extracting sha256:0626d3cc316c9fea3d4891e2ec19b8f371fe22ffb915622f6072a2ee2ca9017f                                1.4s
 => [2/2] RUN apt-get update && apt-get install -y apache2                                                              17.9s
 => exporting to image                                                                                                   9.2s
 => => exporting layers                                                                                                  7.0s
 => => exporting manifest sha256:8c0a0ad53f1593dd23a833de7619b8950194ad0405823613c7be985892d90621                        0.0s
 => => exporting config sha256:3e8aa3120cb2c77c047aa826d2d68bd25b279ede325b5b3b29f09063388e96db                          0.0s
 => => exporting attestation manifest sha256:ed9b5d7ee9c7921b6e683eb361d939ad75498f4138e218742316f5d309affb3c            0.0s
 => => exporting manifest list sha256:2809aada70d03410be9012abc04b5cea549f600d9991262d726465f3c851a83a                   0.0s
 => => naming to docker.io/library/my-apache2:latest                                                                     0.0s
 => => unpacking to docker.io/library/my-apache2:latest                                                                  2.1s
 => resolving provenance for metadata file                                                                               0.0s
[+] build 1/1

 docker compose up -d
[+] up 3/3
 ✔ Network example6-1_default Created                                                                                     0.1s
 ✔ Container apache-2         Started                                                                                     1.5s
 ✔ Container apache-1         Started 
 compose ps
NAME       IMAGE        COMMAND                  SERVICE    CREATED          STATUS          PORTS
apache-1   my-apache2   "apachectl -D FOREGR…"   apache-1   39 seconds ago   Up 38 seconds   0.0.0.0:8081->80/tcp, [::]:8081->80/tcp
apache-2   my-apache2   "apachectl -D FOREGR…"   apache-2   39 seconds ago   Up 38 seconds   0.0.0.0:8082->80/tcp, [::]:8082->
apache-1  | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.2. Set the 'ServerName' directive globally to suppress this message

PS C:\devel\github\COM511_Network_Systems_Automation\myPracticeCourseWork\session6\docker-compose-examples\example6-1> docker compose logs -f apache-2
apache-2  | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.3. Set the 'ServerName' directive globally to suppress this message
---

---
**Exercise 6.2**

There are many example docker compose projects on github and a number of tutorials.
See if you can run some of the examples in docker's own repository [awesome-compose](https://github.com/docker/awesome-compose)
Pick one or two examples from this repository and try and run them locally.

Make sure you can explain 
* What each example does
* How each example works
* How you might use it if you think it is useful
---



