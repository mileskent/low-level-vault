[[OpenGL]] Mathematics Library
* A header only [[C++]] mathematics library for [[Computer Graphics]] software
* Mirrors naming conventions of [[GLSL]]
* [Site](https://glm.g-truc.net/0.9.9/index.html)
	* [Manual](https://github.com/g-truc/glm/blob/0.9.9.2/doc/manual.pdf)
	* [Docs](https://glm.g-truc.net/0.9.9/api/modules.html)
* [Repo](https://github.com/g-truc/glm)

# Tensors
* vec<L, T, Q>
	* Template
		* L = length
		* T = typename
		* Q = qualifier
		* e.g. vec3 = vec<3, float, defaultp>
		* e.g. ivec2 = vec<2, int, defaultp>
	* length(vec)
	* normalize(vec)
	* dot(vec, vec)
	* cross(vec, vec)
* mat<C, R, T, Q>
	* Template
		* C = # columns
		* R = # rows
		* T = typename
		* Q = qualifier
		* e.g. mat4 = mat<4, 4, float, defaultp>
		* e.g. mat2x3 = mat<2, 3, float, defaultp>
# Functions
* Trig
	* cos, sin, tan
	* cosh, sinh, tanh
	* acos, asin, atan
	* acosh, asinh, atanh

# Transformations
$$
\begin{gathered}
\text{Model Matrix}\\
\text{Model} = (S \cdot R \cdot T)
\end{gathered}
$$
$$
\begin{gathered}
\text{Scaling Matrix}\\
\text{scale}\ :\ (\mathbb{R}^{m \times n},\ \mathbb{R}^n) \rightarrow \mathbb{R}^{m \times n}\\
\text{scale}(M, v) = M
\begin{bmatrix}
I\cdot\vec{v} & \vec{0}\\
\vec{0} & 1
\end{bmatrix} = MS\\
\end{gathered}
$$
$$
\begin{gathered}
\text{Translation Matrix}\\
\text{translate}\ :\ (\mathbb{R}^{4 \times 4},\ \mathbb{R}^3) \rightarrow \mathbb{R}^{4 \times 4}\\
\text{translate}(M, v) = M
\begin{bmatrix} 
I_{3} & v \\
\vec{0} & 1
\end{bmatrix} = MT\\
\end{gathered}
$$
$$
\begin{gathered}
\text{Rotation Matrix}\\
\text{rotate}\ :\ (\mathbb{R}^{4 \times 4},\ \mathbb{R},\ \mathbb{R}^3) \rightarrow \mathbb{R}^{4 \times 4}\\
\text{rotate}(M, \theta, \mathbf{u}) = M
\begin{bmatrix}
u_x^2 \left(1-\cos \theta\right) + \cos \theta & u_x u_y \left(1-\cos \theta\right) - u_z \sin \theta & u_x u_z \left(1-\cos \theta\right) + u_y \sin \theta & 0\\ 
u_x u_y \left(1-\cos \theta\right) + u_z \sin \theta & u_y^2\left(1-\cos \theta\right) + \cos \theta & u_y u_z \left(1-\cos \theta\right) - u_x \sin \theta & 0\\ 
u_x u_z \left(1-\cos \theta\right) - u_y \sin \theta & u_y u_z \left(1-\cos \theta\right) + u_x \sin \theta & u_z^2\left(1-\cos \theta\right) + \cos \theta & 0 \\
0& 0& 0& 1
\end{bmatrix}\\
\text{where } \theta \text{ is radians}\\
\text{where } \lvert u \rvert = 1\\
\end{gathered} = MR
$$

