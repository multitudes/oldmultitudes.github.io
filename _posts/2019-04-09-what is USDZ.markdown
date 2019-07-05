---
layout: post
title:  "Working with usd"
date:   2019-06-23
categories: iOS, developer
comments: true
published: true
---

This is an extract of the Apple Developer Keynote's talk [Working with usd](https://developer.apple.com/videos/play/wwdc2019/602/)
for my own enjoyment and learning 

# usdz  

In 2018 Apple introduced AR QuickLook on iOS. It is the easiest and quickest way of displaying 3D content in your space and environment. Underneath these AR experiences is a file format called usdz which is deeply integrated into Apple apps and ios frameworks. It is possible to share 3D AR models with Messages, Mail, Notes, Safari, in the Finder with QuickLook and of course in 3rd Party applications. The technology behind usdz is usd which stands for Universal Scene Description.   
It is a file Format developed by Pixar and has a C++ library with python bindings for authoring and deploy 3d content. The library can read and write usd files and contains a powerful composition engine and much more. The focus is on speed, scalability and collaboration.
There are three file extensions associated with usd:
- usda plain text version designed to be easy to understand
- usdc, a binary version which is efficient as possible to read and write 
- and usd,  which can be either plain text or binary.

![image](/assets/img/USD/1.png)

usdz is the distribution format for usd. it contains all the data of a 3D scene packed in a single file.  
Optimized for sharing. supported on macOS and TVOS as well.   
The anatomy: It is an uncompressed Zip archive where all the contained files are aligned to 64 Bytes boundaries for most efficient memory mapping.  
there are two types of files in the archive, the scene description files in usda, usdc usd or even usdz for nested archives and a set of texture currently in png or jpeg format.  

current file formats:   
the most basic is obj, essentially a single 3d model, with limited material support and no animation.
Then there is a large group of more modern file formats like .gltf, .fbx, .abc that can support multiple models that can be laid out in a scene graph and support of material description and animation.

usd support all of this and additionally is designated to be scalable and support collaboration.  

usdz as archive package inherits most of these features.  

![image](/assets/img/USD/2.png)

## Workflows  

To convert obj gltf fbx or abc into usdz Apple introduced in 2019 a new command line tool. it also performs asset validation. Python based and platform independent.

usdzconvert:
[Download usdz tools](https://developer.apple.com/go/?id=python-usd-library)


``` python

% usdzconvert esprit.gltf
usdzconvert: converting file: esprit.gltf
usdzconvert: converted usdz file: esprit.usdz
usdARKitChecker: [Pass] esprit.usdz
 % usdzconvert -h
 [...]
% usdzconvert esprit.obj -diffuseColor d.png -normal n.png -metallic m.png -roughness r.png
[...]

 
% usdzconvert esprit.gltf
 usdzconvert: converting file: esprit.gltf
 usdzconvert: converted usdz file: esprit.usdz
 usdARKitChecker: [Pass] esprit.usdz
 % usdzconvert -h
 [...]
% usdzconvert esprit.obj -diffuseColor d.png -normal n.png -metallic m.png -roughness r.png
[...]

% usdzconvert esprit.gltf
usdzconvert: converting file: esprit.gltf
usdzconvert: converted usdz file: esprit.usdz
usdARKitChecker: [Pass] esprit.usdz
 
 % usdzconvert -h
 [...]
% usdzconvert esprit.obj -diffuseColor d.png -normal n.png -metallic m.png -roughness r.png
[...]

```


You can provide rich material description directly from the command line.  
usdzconvert is a part of a broader package which includes the precompiled binaries for macos and other things like he usd command line tool. usdcat, usdtree to see the structure of the usd file and usdchecker


## Content creation

A growing number of content creation applications supports usdz file export. For instance Substance Painter by Adobe which supports usd and usdz export. Maya supports usd and usdz export with a plug in directly supported by Pixar.  

Because of the Python bindings you can build your own pipeline in Python as well.

## Exporting usdz from SceneKit

It is super easy. Create your SCNScene as before and you use the API. 

``` swift 
let scene = SCNScene(...)
...
scene.write(to: baseURL.appendingPathComponent("file.usdz"), delegate: nil)
```
The usdz export is integrated in Xcode scene editor and can be exported via the user interface as well.

## usd features

usd has a very large feature set. Some of them are:

![image](/assets/img/USD/3.png)

### File structure
The usd format is transparent and readable. Lets see an excerpt of an usda file. It features nested containers. In usd they are called `prims`

![image](/assets/img/USD/4.png)

These prims contain properties that store actual data and there is a set of metadata attached to file level, prim level or property level. because of the nested tructure any object can be acceessed through an object path.
Properties have the dot notation.

![image](/assets/img/USD/5.png)

### Scene Graph
How to store scene data. A scene graph defines the object hierarchy. Transforms on a parent also affect its children.
Scene graph is easy to store with the usd nested structure. Some prims like materials dont belong to the scene graph.

![image](/assets/img/USD/sceneGraph.png)

### Mesh data

![image](/assets/img/USD/6.png)

Mesh Data can be grouped in mesh attributes such as position normals and texture coordinates.
and mesh connectivity such the number of vertices per face or vertex indices.
lets see an example of the mesh file for a dodecahedron

``` python
def Mesh "Tetrahedron"
{
point3f[] points = [(-1,-1,1), (-1,1,-1), (1,-1,-1), (1,1,1)]
int[] faceVertexCounts = [3, 3, 3, 3]
int[] faceVertexIndices = [1,2,0, 3,2,1, 3,0,2, 3,1,0]
normal3f[] normals = [(-0.58,-0.58,-0.58), (0.58,0.58,-0.58),
(0.58,-0.58,0.58), (-0.58,0.58,0.58)] (
interpolation = "uniform"
)
float2[] primvars:st = [(0.75,0.43),(0.5,0.87),(0.25,0.43),
)
interpolation = "faceVarying"
(1,0.87),(0,0.87),(0.5,0)] (
int[] primvars:st:indices = [0,1,2, 3,1,0, 4,2,1, 5,0,2]
 uniform token subdivisionScheme = "none"
```
 

### Materials

![image](/assets/img/USD/7.png)

usd material definition is very rich and meant for movie quality output.  
For realistic real time rendering there is smaller subset called usdpreview surface. It is a phisically based material description and supports metallic roughness and specular roughness.  

Metallic roughness.  
example: We start with this model and we start assigning a constant white color. Next we will set normal and occlusion maps to bring out the fine details.
Then we add the metallic level to make it really shiny and add a roughness map to dull out parts of the object. Lastly we set diffuse color and metallic textures. So with these 5 textures we get the final photorealistic look of this mesh.   

Let's see how this is described in usd. usd uses a Shader Node Graph that has separate shader nodes connected to each other.

![image](/assets/img/USD/shader.png)

There are four node types.
The main node is defining the PBR attributes.
The texture sampler is telling us which texture to use, like a mesh attribute reader for example for the texture coordinates.
and the UV transform node scales or rotates the coordinates.

## Scalability and subdivision surfaces

![image](/assets/img/USD/9.png)

Subdivision surfaces are efficient representation of curved surfaces. In contrast polygonal surface description are an approximation of the real curved surface. This approximation depends of how close are you gonna be to the object.
Subdivision surfaces describe true surfaces. You can do dynamic tassellation based on the distance to the camera to find a good enough approximation with small polygons. Also great for animated contents.

![image](/assets/img/USD/10.png)

Example of animoji or memoji, on the it is left rendered as polygonal surface, fairly coarse and great for memory footprint. On the right showing the final subdivided surface.

The industry standard for subdivision surfaces is OpenSubdiv developed by pixar.
usd and OpenSubdiv work beautifully together.


## Composition engine

Powerful authoring tool enabling cooperation between artists. Instead to store duplicate data, usd stores them as reference and creates virtual object in the structure. Each object has its own object path so that you can go in and override some of its properties. You can remove subtrees and usd stores all those edits.
This allows to decouple the workflows from each one allowing for collaborative editing and creation

![image](/assets/img/USD/11.png)


### sources  

[WWDC Talk - Working with usd](https://developer.apple.com/videos/play/wwdc2019/602/)  

[https://developer.apple.com/augmented-reality/quick-look/](https://developer.apple.com/augmented-reality/quick-look/)  

[Download usdz tools](https://developer.apple.com/go/?id=python-usd-library)  

