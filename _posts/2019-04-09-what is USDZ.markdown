---
layout: post
title:  "Working with USD"
date:   2010-05-23
categories: iOS, developer
comments: true
published: true
---
# this is a draft

This is an extract of the Apple Developer Keynote's Talk [Working with USD](https://developer.apple.com/videos/play/wwdc2019/602/)


# USDZ
In 2018 Apple introduced AR QuickLook on iOS. It is the easiest and quickest way for displaying 3D content in your space and environment. Underneath these AR experiences is a file format called USDZ which is deeply integrated into Apple apps and ios frameworks. It is possible to share 3D AR models with Messages, Mail, Notes, Safari , in the Finder with QuickLook and of course in 3rd Party applications. The technology behind USDZ is USD which stands for Universal Scene Description.   
It is a file Format developed by Pixar and has a C++ library with python bindings for authoring and deploy 3d content. The library can read and write USD files and contains a powerful composition engine and much more. The focus is on speed, scalability and collaboration.
there are three file extension associated with USD:
- USDA a plain text version designed to be easy to understand
- A binary version USDC wich is efficient as possible to read and write 
- and USD which can be either plain text or binary.

- USDZ is the distribution format for usd. it contains all the data of a 3D scene packed in a single file.
Optimized for sharing. supported on macOS and TVOS as well. 
The anatomy: It is an uncompressed Zip archive where all the contained files are aligned to 64 Bytes boundaries for most efficient memory mapping.
there are two types of files in the archive, the scene description files in USDA,USDC usd or even usdz for nested archives and a set of texture currently in png or jpeg format.

current file formats: 
the most basic is obj essentially a single 3d model, with limited material support and no animation
then there is a large group of more modern file formats like .gltf, .fbx, .abc that can support multiple models that can be laid out in a scene graph and support of material description and animation.

USD support all of this and additionally is designated to be scalable and support collaboration.

usdz as archive package inherits most of these features.

## Workflows 
converting and creating new ones.

To convert obj gltf fbx or abc into usdz Apple introduced in 2019 a new command line tool. it also performs asset validation. Pythn based and plattform independent.

USDZConvert 
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



// picture

you can provide rich material description directly from the command line


USDZConvert is a part of a broader package which includes the precompiled binaries for macos and other things like he usd command line tool. usdcat, usdtree to see the structure of the usd file. usdchecher

demo USDZConvert

## Content creation

A growing number of content creation applications supports USDZ file export. For instance Substance Painter by Adobe which supports USD and USDZ export. Maya supports USD and USDZ export with a plug in directly supported by Pixar.  

Because of the Python bindings you can build your own pipeline in Python as well.

## Exporting USDZ from SceneKit

It is super easy. Create your SCNScene as before and you use the API. 
The USDZ export is integrated in Xcode scene editor and can be exported via the user interface as well

## USD features

USD has a very large feature set. Some of them are:

### File structure
The USD format is transparent and readable. Lets see an excerpt of an USDA file. It features nested containers. In USD they are called `prims`
picture

these prims contain properties that store actual data and there is a set of metadata attached to file level, prim level or property level. because of the nested tructure any object can be acceessed through an object path.
Propreties have the dot notation.

### Scene Graph
How to store scene data. A scene graph defines the object hierarchy. transforms on a parent also affect its children.
Scene graph is easy to store with the usd nested structure. Some prims like materials dont belong to the scene graph.
picture
### Mesh data
can be grouped in mesh attributes such as position normals and texture coordinates.
and mesh connectivity such the number of vertices per face or vertex indices.
lets see an example 
pic

### materials
USD material definition is very rich and meant for movie quality output.
For realistic real time rendering there is smaller subset called usdpreview surface. It is a phisically based material descripition and supports metallic roughness and specular roughness

Metallic roughness
example. We start with this model and we start assigning a constant white color. next we will set normal and occlusion maps to bring out the fine details.
next the metallic level to make it really shiny and then add a roughness map to dull out parts of the object. Lastly we set diffuse color and metallic textures. so with these 5 textures we get the final photorealistic look of this mesh.
pic
lets see how this is described in uSD. USD uses a Shader Node  Graph that has separate shader nodes connected to each other.
pic

4 node types.
The main node definining the PBR attributes.
The texture sampler to tell us which texture to use
a mesh attribute reader for ex for the texture coordinates
and a UV transform node to scale or rotate the coordinates

!pic

## advantages of usd.
scalability for complex scenes and live composition and collaboration.

### scalability and subdivision surfaces

Subdivision surfaces are efficient representation of curved surfaces. In contrast polygonal surface description are an approximation of the real curved surface. This approximation depends of how close are you gonna be to the object.

subdivision surfaces describes true surfaces. You can do dynamic tassellation based on the distance to the camera to find a good enough approx with small polygons. Also great for animated contents

!pic animoji memoji
on the left rendered as polygonal surface. fairly coarse great for memory footprint. on the right the final subdivided surface.

industry standard for subdivision surfaces is OpenSubdiv developed by pixar.
subdivision surfaces in SceneKit.

USD and OpenSubdiv work beautifully together.

## composition engine
Powerful authoring tool enabling cooperation between artists.Instead to store duplicate data instead USD stores them as reference and creates virtual object in the structure and each has its own object path so that you can go in and override some of its properties
You can remove subtrees and usd stores all those edits
!pic

lets see an example with macos quicklook rendering in finder a scene usd file

This allows to decouple the workflows from another



### sources
[WWDC Talk - Working with USD](https://developer.apple.com/videos/play/wwdc2019/602/)
[https://developer.apple.com/augmented-reality/quick-look/](https://developer.apple.com/augmented-reality/quick-look/)
[Download usdz tools](https://developer.apple.com/go/?id=python-usd-library)
