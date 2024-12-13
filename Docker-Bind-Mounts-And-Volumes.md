1) Containers are LIGHT-IN-WEIGHT,by default it doesn't have any volumes or filesystem for storage
2) For suppose, if containers are deleted ,the appliaction which is producing some logfiles are also deleted-->This is one Problem.
3) 2nd Problem--> will be front-end,back-end application are running in containers and backend container is creating some files,if BE is destroed then it is crased as it doesnt have
   have persistent(permanent storage)
4)3rd problem-->if their is an application container  and it wants to fetech files from host OS which is geeting files from Cron JOB,this container can't able to fetch files from
   specific host path.

1)BIND MOUNTS:
--------------
It will binds the **directory** that is present in **Container** to **HOST Directory**, if the container1 fails, then if container2 came into exiatence then it can map to HOSR DIRECTORY.

2)VOLUMES:
----------
It will offers same solution but with a lifecycle, 
Using Docker CLI--> you can create Volume(Which created **logical isloation** in your host)-->You can create/destroy volume or move from C1 to C2.
It is similar to Bind mount but iin this we need to mention path of host/directory where as in volumes noneed of mentioning entire path.
Whereas in Bindmount you need to **mount container dir to Host dir** where as with VOLUMES you can mount to **external resources** such as s3,ec2...
We caneasily take Back-up in-case volumes and can mount to any external resources.

Docker -v
docker --mount 
both are same in -v <source dir:dest dir:permissions> whereas in --mount more specific (verbose mode) need to mention sorce,destinationa nd permissions.

**DOCKER CMDS:**
docker volume ls
docker  volume create volume-name
docker volume inspect volume-name -->to inspect where it is created in which logical volume
docker volume rm volume-name-->to delete voulmes

after creating docker image you need to mount the voulme to a container
docker run -d --mount source=volume-name,target=/app image-name:latest
docker ps-->to see all running containers
docker inspect container-name/id

-->If you want to delete a volume first you need to stop&remove an container and then you can delete volume.
