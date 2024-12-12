By using this MUlti-stage-builds--> you can reduce the size of the docker image
BUilding and running is different.
for building java application-->pom.xml,jar
for running java based application--> you need war,ear,jar files
As from base-image you will be getting heavy loads and resulted image will also be in the heavy size.

IN ORDER TO SOLVE THIS DOCKER HAVE IMPLEMENTED MULTI-STAGE-BUILDS:
----------------------------------------------------------------
1) We can divide our DOCKERFILE into 2 parts
2) In first part :(Stage-1)
   From ubuntu as build
   Run apt packages....
   (Instead of exceting CMD/ENTRYPOINT here)--from this first part I will be taking the Binary files and using them in the second part.
3)Stage-2:
   From python(Minimal image/DISTROLESS IMAGES)[If it is from UBUNTU image it will have all like curl,yum but in this case we dont need all we need only python,so we are using only python]
   Copy --from build
   CMD[/app.ear]
   (By using this you have reduced image size, getting the image from build and then executing it)
4) Base image will be very rich like ubuntu which has all dependencies
   
