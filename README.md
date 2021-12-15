# CS-GY 9053 I2 – Introduction to Java - Fall 2021

# Final Project: Chat software

## Description

This program allows multiple users to create an account in the group and chat privately with each other.

## How to use

### Server: 

* Download the entire file and open the config.perperties.
  * url is where the database located, to create the database you could use e.g. Navicat to import the database
  ![create database](/screenshot/1.gif)
  * username and pwd is the username and password for your mySQL useraccount, and you may need to change it to your own mySQL user.
  * mykey is used to encode the passwords of our users
* launch serverConn.java in the server folder
* Error may occur when connecting to the database. If that happens, you could try to reconfigure the mySQL authentication method to Legacy authentication method (retain MySQL 5.x compatibility)

### Client: 
* Download the entire file and open the configConnection, and change HOST to your server's IP address.
* launch loginInterface.java in the server folder

## Login

You could login with some default username and password already stored in the database. 
Username: Frank, Password frank;
Username: Lucy, Password lucy;

## Registration

Click the create an account button, then you could create an account with your own username and password.

## Chat
Double click the friend name label to open a chat.
If both of clients open the chat, they can send messages to each other by clicking the send button.(Enter does not work here.)
If A is trying to send a message to B that is offline, the server will notify A that your target B is offline.
If both of clients are online, but B has not opened that chat window, B's friendname will turn into blue to notify her that she has a new message from A.



## Mandatory Tasks

For each task below, add at least one image in the readme demonstrating the results. The code that you used for all tasks should be provided.


## Shadow Mapping

Starting with the interactive application you have implemented in the previous assignment, add shadows to the scene to increase its realism. You will still need to be able to add, select and move, and delete 3D meshes to the scene (they can be added in randomly at any position in the scene; otherwise, the center of the scene).

The scene should always contain one light source (you can add more light sources if you want, but that will require multiple depth maps). The light source should be placed on top of the scene and move around the scene's objects in a circular path (imagine you are in the center of a room, and the light source moves around you at the top of your head).

New objects can be added to the scene in three ways:

* The key '1' will add a unit cube in the origin

* The key '2' will import a new copy of the mesh 'bumpy_cube.off', scale it to fit into a unit cube and center it on the origin

* The key '3' will import a new copy the mesh 'bunny.off', scale it to fit into a unit cube and center it on the origin

Note that you can have multiple copies of the same object in the scene, and each copy can have its position, scale, and rotation. All objects (besides the reflective ones) must be shaded using the Phong Shading (per-fragment shading) and Phong's lighting model.

The shadow's color must interchangeably change colors from back to red and vice-versa when the user hits the key 's' (see figures below).  In order to easily visualize the shadows, you must render a plane below the objects in the scene (see figure below).

| ![shadow-black](shadow-black.png) |
|:--:|
| <b>The picture shows the mesh objects and plane rendered using per-fragment shading and the shadow mapping algorithm.</b> |


| ![shadow-red](shadow-red.png) |
|:--:|
| <b>The picture shows the mesh objects and plane rendered using per-fragment shading and the shadow mapping algorithm. In this version, the shadows are displayed using the red color.</b> |

Don't forget to consult the class textbook and the optional and recommended text. The OpenGL Programming Guide has a full section on shadow mapping. It is explained in detail how to set up the depth buffer for using a shadow mapping algorithm and the matrices transformations needed.

## Environment Mapping

In this task, you must implement the environment mapping technique discussed in class.
Using the cube map textures provided in the data folder into the assignment directory in GitHub, you must create the cube skybox and correctly load the textures in OpenGL (remember the axis directions). 

You can convert the images to an image format you already can handle (PPM) (for instance, using GIMP) or use any other image library to load the data from the disk. In the case you use an external library, you must provide the code for the library, the changes in the CMake configurations, and be sure it compiles on Linux with no issues.

The easiest way to accomplish this task is to start adding the skybox cube, validating that you correctly loaded the cube map textures, and then write the vertex and fragment shaders to handle the reflection direction calculation and texture sampling.

When an object is selected, it should be possible to translate it, rotate it around its barycenter, and rescale it without changing its barycenter. All these actions should be associated to keyboard keys (and the choice of keys should be detailed in the readme).

Each object also has a rendering setting associated with it, which can be one of the following two options:

* Phong Shading: the normals are specified on the vertices of the mesh and interpolated in the interior. The lighting equation should be evaluated for each fragment.

* Mirror (chrome) appearance: the object is rendered using the environment mapping technique discussed in class. In this item, you don't need to update the cube map texture at each iteration.


| ![env-mapping](env-mapping.png) |
|:--:|
| <b>Skybox (cube with textures) and reflective objects rendered using the environment mapping technique.</b> |


| ![env-mapping2](env-mapping2.png) |
|:--:|
| <b>Multiple objects can be rendered as reflective ones.</b> |

## Camera Control

Add the possibility to translate the position of the camera (similarly to the previous assignment). The camera should always point to the origin. It should be possible to move it around, but the camera should always face the origin.

Implement only the perspective camera. The cameras should take into account the size of the window, properly adapting the aspect ratio to not distort the image whenever the window is resized. All functionalities should work after resizing the window, including object selection and editing of the scene.

## Optional Tasks

These tasks are optional.

## Refraction

This task is optional and worth 1% of the final grade.
The calculation of the reflection vector can be easily changed to the calculation of the refraction vector. 
Add to your system the refractive material property for the objects. Once it is implemented, you will be able to render transparent objects.

## Dynamically Generated Cube Map Textures

This task is optional and worth 3% of the final grade.

As discussed in class, the cube map textures can be generated on the fly. This technique allows us to render objects with time-dependent reflections, i.e., all objects in the scene will be displayed in the cube map textures. As a result, the 
