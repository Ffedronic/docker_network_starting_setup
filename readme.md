Networks / Requests  
==

# Communicate with mongodb container 
* Create a network:
**docker network (example: favorites-net)**, 
* Create a mongodb container:  
 **docker run**,
    **-d** \ detached monde,  
        **--name mongodb** \ assign the name to the container,  
            **--network favorites-net** \ assign a network to the container  
                **mongo** \ name of the image
* build the image of your app and create a container like this:  
**docker run**,  
**-d** \ detached mode,
 **-p 3000:3000** \ publish the container on the port 3000,  
  **--network favorites-net** \ assign the same network that the mongodb container,  
   **--rm** \ remove directly the container after its shutdown,  
     **node** \ the name of the image.  
>Don't forget to link the app with the name of the mongodb container inside the url connection !<br>
``js
mongoose.connect(
  "mongodb://mongodb:27017/swfavorites",
  { useNewUrlParser: true },
  (err) => {
    if (err) {
      console.log(err);
    } else {
      app.listen(3000);
    }
  }
);
``