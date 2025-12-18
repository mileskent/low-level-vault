---
aliases:
  - Element Buffer Object
  - IBO
  - EBO
---
An [[OpenGL]] buffer that holds the order in which indices of a [[Vertex Buffer Object|VBO]] should be visited in order to create all the triangles of the [[Mesh]] while adhering to proper [[Winding Order]]. 
* Basically, instead of having duplicate vertices in the VBO to express triangles with shared vertices, we just only store the set of vertices in the VBO, and then the IBO handles order of visiting. If we were rendering a [[Quad]], there are 2 duplicate vertices. Using an IBO avoids storing those duplicates.
* Bound to the `GL_ELEMENT_ARRAY_BUFFER` enum