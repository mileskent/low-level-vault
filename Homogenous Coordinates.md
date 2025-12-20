In [[Computer Graphics]], under [[Perspective Projection]] use a 4D vector to represent 3D points.

The point of using homogenous coordinates is so that a single transformation can be represented by a single matrix multiplication.

[Video explanation](https://youtu.be/o-xwmTODTUI?si=fYFx-SqnfdLeXDMT).

Homogenous coordinates are not [[Quaternion]]s, even though both are 4D objects.

[[OpenGL]] and [[Vulkan]] force you to use homogenous coordinates.

If we were to use 3D vectors, rotation and scaling would use matrix multiplication, but translation use matrix addition. By adding a fourth coordinate, w, all transformations can be done exclusively with matrix multiplication. [[GPU]]s excel at matrix multiplication and [[Rendering Pipeline|Graphics Pipeline]]s with *fewer* steps. Therefore, to have a single *Model Matrix* to represent a single transformation is ideal.

The coordinate system is called "Homogenous" precisely because it enables all compositions transformations to be described in a single model matrix.

$f\ :$ Homogenous $\rightarrow$ 3D
$$
f(x, y, z, w) : \mathbb{R}^4 \rightarrow \mathbb{R}^3=
\left( \frac{x}{w}, \frac{y}{w}, \frac{z}{w} \right)
$$

Converting a regular 3D transformation matrix to homogenous:
$$
\begin{bmatrix}
x_{00} & x_{01} & x_{02}\\
x_{10} & x_{11} & x_{12}\\
x_{20} & x_{21} & x_{22}\\
\end{bmatrix}
\rightarrow
\begin{bmatrix}
x_{00} & x_{01} & x_{02} & 0\\
x_{10} & x_{11} & x_{12} & 0\\
x_{20} & x_{21} & x_{22} & 0\\
0 & 0 & 0 & w
\end{bmatrix}
$$

A homogenous shift matrix in 2D
$$
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}
\vec{v}
+
\begin{bmatrix}
d_{x} \\
d_{y}
\end{bmatrix}
\rightarrow
\begin{bmatrix}
a & b & d_{x} \\
c & d & d_{y} \\
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
v_{x}\\
v_{y}\\
w
\end{bmatrix}
$$

A homogenous shift matrix in 3D
$$
\begin{bmatrix}
a & b & c\\
d & e & f \\
g & h & i
\end{bmatrix}
\vec{v}
+
\begin{bmatrix}
d_{x} \\
d_{y} \\
d_{z}
\end{bmatrix}
\rightarrow
\begin{bmatrix}
a & b & c & d_{x}\\
d & e & f & d_{y}\\
g & h & i & d_{z}\\
0 & 0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
v_{x}\\
v_{y}\\
v_{z}\\
w
\end{bmatrix}
$$

* If $w < 0$, do not render ([[Clip]])
* Let $w\geq 0$
* When $w = 1$, translations are possible. 
* When $w = 0$, translations are not possible.
* Else, scale all coordinates such that $w = 1$ again
	* [[Perspective Projection]] uses distance from an object to the camera plane for $w$

