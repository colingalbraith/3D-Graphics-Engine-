# 3D Graphics Engine

## Introduction
This 3D Graphics Engine, developed in Python, demonstrates the principles of 3D graphics, including object parsing, transformations, camera operations, and projections. The engine reads OBJ files, processes 3D transformations, and projects them onto a 2D screen with realistic effects such as perspective projection.

## Project Structure
The project is structured into several modules, each responsible for a different part of the graphics rendering pipeline:

- **`main.py`**
- **`camera.py`**
- **`object_3d.py`**
- **`matrix_functions.py`**
- **`projection.py`**

## How the Engine Works

### Object Parsing (`object_3d.py`)
The OBJ file format is a simple text-based file format that contains 3D geometry data. The `object_3d.py` module reads these files line by line:
- **Vertices (`v`)**: Define the points in 3D space.
- **Texture Coordinates (`vt`)**: Represent the 2D coordinates of the texture mapping.
- **Normals (`vn`)**: Define the direction perpendicular to the surface for lighting calculations.
- **Faces (`f`)**: Combine vertices into polygons, typically triangles or quads.

Once parsed, these components are stored in Python data structures for later use in the rendering pipeline.

### Transformations (`matrix_functions.py`)
In 3D graphics, transformations are used to move, rotate, and scale objects within the scene. The `matrix_functions.py` module provides the necessary functions to create transformation matrices:
- **Translation**: Moves objects around in the scene.
- **Rotation**: Rotates objects about an axis (x, y, or z).
- **Scaling**: Changes the size of objects.

These transformations are applied to the object's vertices by multiplying the transformation matrix with the vertex coordinates. Multiple transformations can be combined into a single matrix through matrix multiplication.

### Camera Operations (`camera.py`)
The camera module simulates a virtual camera within the scene. It computes the **view matrix**, which transforms the scene from world space to camera space (i.e., how objects are positioned relative to the camera). You can control the camera's position, orientation, and zoom level to navigate the scene.

### Projection (`projection.py`)
The `projection.py` module performs perspective projection. This involves transforming 3D coordinates into 2D coordinates for display on a flat screen while preserving the appearance of depth. Objects further from the camera appear smaller, and objects closer appear larger. This mimics the way human eyes perceive depth, providing a sense of realism in the rendered scene.

### Rendering Process
1. **Initialization**: The engine starts by setting up the camera, initializing the projection matrix, and parsing OBJ files to load the 3D objects.
2. **Transformation**: The loaded objects are transformed using translation, rotation, and scaling matrices.
3. **View and Projection**: The camera's view matrix is applied to adjust how the objects are seen, followed by perspective projection, which converts the 3D coordinates to 2D screen coordinates.
4. **Rendering**: Finally, the objects are rendered on the screen using the 2D coordinates. This process repeats for every frame in the rendering loop.


https://github.com/colingalbraith/3D-Graphics-Engine-/assets/146497900/09bf04c8-88d9-48ac-8ae9-0d7721ee1eec



https://github.com/colingalbraith/3D-Graphics-Engine-/assets/146497900/fc2832de-5427-4f92-b676-fe8acfe96b9a


## Future Development: 

### Texture Mapping 
One of the major future directions for this project is adding texture mapping. Texture mapping allows the application of images (textures) to 3D surfaces, adding detail without increasing the polygon count. This feature will give the 3D objects a more realistic and intricate appearance by mapping 2D images onto the 3D models.

### Potential Approaches

- **UV Mapping**: 
   UV mapping is a technique that wraps a 2D image (the texture) around a 3D object by associating each vertex of the object with coordinates in the 2D texture image. For implementation:
   - **Texture Coordinates**: The `object_3d.py` module already reads texture coordinates (`vt` in the OBJ file). The next step would be to use these coordinates to map pixels from the image onto the surfaces of the 3D model.
   - **Texture Interpolation**: Linear interpolation between texture coordinates will ensure smooth application of textures across faces of varying shapes.
   - **Mapping Algorithm**: A bilinear filtering algorithm will be implemented to sample pixels from the texture image and apply them to the polygons during rendering.

### Other Improvements  

- **Mipmap Generation**: 
   For better performance and quality during rendering, mipmap generation will be implemented. Mipmaps are pre-calculated, optimized sequences of textures that reduce in size to allow smoother transitions when objects are scaled in the scene. This prevents texture distortion and blurring.
   - **Implementation**: The engine will generate mipmaps by recursively halving the resolution of the original texture until reaching a base resolution, applying an appropriate averaging algorithm.

- **Normal Mapping**: 
   In addition to texture mapping, normal mapping will be explored. This method perturbs the surface normals of objects to give the illusion of complex surface details (such as bumps and grooves) without increasing the polygon count. The normals will be modified at each pixel using a special texture called a "normal map."
   - **Implementation**: The shading and lighting calculations in the engine will be adapted to incorporate the modified normals provided by the normal map, adding realism to the rendered models.


## Installation
To get this project running on your machine, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/colingalbraith/3D-Graphics-Engine-.git

## Contributing
Contributions to the 3D Graphics Engine are welcomed! If you have ideas for improving performance, adding features, or fixing bugs, feel free to fork the repository, create a new branch, and submit a pull request.

