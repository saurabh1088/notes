#  Augmented Reality

## What is an Augmented Reality experience?

Augmented Reality is a technology which belnds digital pieces which could be 2D or
3D with the real world environment.
Augmented Reality tries to seamlessly blend and marry a digital piece with a real
environment, this enhances user's perception and experience which has wide range
of use cases in apps and games.

Modern devices are equipped with cameras and sensors which capture the real world
environment surrounding them and using that are capable to place digital pieces.

While in a Virtual Reality (VR) the technology takes user and immerses user into
an experience which essentially replaces everything user sees in physical world.
Augmented Reality (AR) on the other hand keeps the world around the user same but
adds virtual objects to it.

## ARKit

ARKit is a framework provided by Apple which helps to integrate device's hardware
sensing features within the app thereby producing augmented reality apps and games.

ARKit provides AR (Augmented Reality) experience by combining :
- Device motion tracking
- World tracking
- Scene understanding

### ARSession

ARSession object will manage several major tasks associated with an AR experience.
These taks for an AR experience can include :

- Reading data from device's motion sensor hardware
- Controlling device's camera
- Image analysis

ARSession is kind of a correspondence between real world space and the digital pieces
created and integrated to this real space creating AR experience.

For an app to use ARKit, it needs access to camera, hence it will need user's permission
to grant app permission for camera access. ARKit automatically handles asking of this
permission from user.

Every AR experience requires an ARSession. ARKit provides few out of the box renderers
like ARView, ARSCNView, ARSKView. When these renderers are used, these already take
care of creating ARSession object

## How's ARKit different from SceneKit?

SceneKit is also a framework provided by Apple, though it's primary usage is to
create 3D interactive scenes and animations. SceneKit is used for games and simulations.

Both ARKit and SceneKit frameworks however can be used together to provide an 
immersive experience.



### SCNBox

SCNBox here defines a box as name suggests, more precisely, it defines a six sided 
polyhedron as mentioned in Apple documentation. width, height and length are self explanatory. 

chamferRadius 
- chamferRadius provides rounded "edges and corners" to the box. 
- Maximum corner radius is half the box’s smallest dimension. This is reason, 
below value is in range of 0.0s. If this value is more than half of box's smallest 
dimension messes up the shape and it appears more like a sphere/cylinder etc.


``` swift

let box = SCNBox(width: 0.1, height: 0.1, length: 0.1, chamferRadius: 0)
let boxNode = SCNNode()
boxNode.geometry = box
boxNode.position = SCNVector3(0, 0, -0.2)
```
        
