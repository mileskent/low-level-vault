* A [[GPU]] [[Pipeline]] for [[Rendering]] [[Graphics]], a [[Rendering Pipeline]] (specifically for [[OpenGL]], see [here](https://wikis.khronos.org/opengl/Rendering_Pipeline_Overview)
* A vertex's journey from 3D space in a world to the 2D space of the screen
![[Pasted image 20251214213250.png|150]]
> Rendering Pipeline FlowchartDiagram of the Rendering Pipeline. The blue boxes are programmable [[Shader]] stages.

# Vertex Specification
Where we setup the geometry on the CPU
* Location on vertex in 3D space
* Texture Data
* Normal Information
# Vertex Shader
A [[Shader]] stage. Execute on each vertex, positioning that vertex
See [[Vertex Shader]].
# Tesellation
An optional [[Shader]] stage. Dynamically subdivides polygons into finer triangles, allowing for more the *appearance* of detailed surfaces, existing in GPUland
# Geometry Shader
An optional [[Shader]] stage. Generate more geometry in GPUland, e.g. particle system.
# Vertex Post-Processing
Do post-processing on vertices.
# Primitive Assembly
Assembling the final geometry using primitives, perform [[Culling]], etc.
# Rasterization
Determinign which pixels get filled in in the 2D screen based on the vertices in the pipeline. 
# Fragment Shader
A [[Shader]] stage. Executing once on each fragment (kind of like a pixel), determine the final color per rasterized fragment.
See [[Fragment Shader]]
# Per-Sample Operations
Process the output of the fragment shader
* [[Scissor Test]]
* [[Stencil Test]]
* [[Depth Test]]
* [[Blending]]