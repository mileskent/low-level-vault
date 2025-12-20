![[Pasted image 20251220093633.png|200]]
* A way of respresenting the orientation of a 3 dimension body in space, using a 4D object
* A 4-dimensional extension of the complex numbers
	* $\implies \mathbb{R} \subset \mathbb{H}$
	* $\implies \mathbb{C} \subset \mathbb{H}$
* The quaternion describes the orientation of the object's local reference frame relative to the global reference frame
* A harder to visualize and more abstract, but easier to use alternative to [[Euler Angles]]; not suspectible to the bugs and edge cases of euler angles, e.g. Gimbal Lock.
* Used heavily in (3D) [[Computer Graphics]]

# Definition
$$
\begin{gathered}
\mathbf{q} = a + bi + cj + dk = a + V\\
\text{where }a, b, c, d \in \mathbb{R}\\
\text{where }i, j, k \text{ are imaginary basis vectors}\\
\text{where } V = bi + cj + dk
\end{gathered}
$$
$$
\mathbb{H} = \left\{a + b \mathbf{i} + c \mathbf{j} + d \mathbf{k}\ |\ a, b, c, d \in \mathbb{R}\right\}
$$
$i$ is precisely the $i$ used in complex numbers. $j$ and $k$ function the same as $i$, but are along different axes.
$$
i^2 = j^2 = k^2 = ijk = -1
$$
$$
ij =-ji = k\quad
jk = -kj = i\quad
ki = -ik = j
$$
# Operations
## Addition
$$\mathbf{q}_{1} + \mathbf{q}_{2}$$
## Multiplication
$$\mathbf{q}_{1}\mathbf{q}_{2}$$
$$
\mathbf{q}_{1}\mathbf{q}_{2} \neq \mathbf{q}_{2}\mathbf{q}_{1}
$$
$$k\mathbf{q}_{2}$$
$$k\mathbf{q}_{2} =\mathbf{q}_{2} k $$
## Norm
$$\lVert\mathbf{q}\rVert$$
$$\lVert\mathbf{q}\rVert = \sqrt{ a^2 + b^2 + c^2 + d^2 }$$
## Conjugation
$$\mathbf{q}^* = \bar{\mathbf{q}}$$
$$
(a + bi + cj + dk)^* = 
(a - bi - cj - dk)
$$
# Usage
Let $\mathbf{v} \in \mathbb{H} = 0 + xi + yj + zk$, correspond to a vector in $\mathbb{R}^3$. This is the vector that we want to rotate.

Let $\mathbf{q} \in \mathbb{H} = a + bi + cj + dk$, be the quaternion that we will use to manipulate $\mathbf{v}$

* Left multiplying by $\mathbf{q}$ rotates, and translates negative to the axis of rotation
* Right multiplying by $\mathbf{q}^*$ rotates the same amount, and translates positive to the axis of rotation
* Therefore $\mathbf{q} \mathbf{v} \mathbf{q}^*$ results in that rotation, twice, with the translation cancelled out. This is the form of quaternion rotation.
![[Pasted image 20251220104045.png|300]]
![[Pasted image 20251220103938.png|300]]

Let $\hat{V} = \frac{V}{\lvert V \rvert}$

The following is a quaternion that rotates about $V$ by $\theta$ degrees
$$
\mathbf{q} = \cos \frac{1}{2}\theta + \hat{V} \sin \frac{1}{2}\theta
$$
