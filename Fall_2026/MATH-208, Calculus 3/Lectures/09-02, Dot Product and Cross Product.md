![[1.3-student.pdf]]

![[Pasted image 20260902093504.png]]

![[Pasted image 20260902093515.png]]

If you've got a force problem, $W=F\cdot v$ for the work done. When they say <mark style="background: #BBFABBA6;">component, they really mean vector in component form</mark>. So, the component of F that is parallel to v is the projection of F onto V, and the component of F that is perpendicular to v is F minus the parallel component (so projection).

If they want you to find the <mark style="background: #ADCCFFA6;">scalar projection of v onto u</mark>, you do a slightly changed version of projections and do $\frac{u\cdot v}{|u|}$. You can then get the projection/parallel component from this by squaring the denominator term and multiplying the vector being projected onto by it, so in this case u. Then, the orthogonal component is just v minus this parallel component.

### Summarized Orthogonal Projection Steps
1. You need two points that the line goes through. This can be given through a graph or explicitly in the question. Use the two points to compute:
$$\overrightarrow{d}=\begin{bmatrix}
x_{2}-x_{1} \\
y_{2}-y_{1}
\end{bmatrix}$$
2. You will be given a starting vector (or the points to find the vector). Take that vector (v used as a placeholder) and the direction vector from step 2 and compute the projection:
$$proj_{\overrightarrow{d}}\overrightarrow{v}=\frac{\overrightarrow{v}\cdot\overrightarrow{d}}{\overrightarrow{d}\cdot\overrightarrow{d}}\overrightarrow{d}$$
NOTE: Once you compute the fraction, it will become a scalar value, so you just do scalar multiplication with the standalone d
NOTE: You can also find a d by finding the unit vector of v

Sometimes this is all the question wants, sometimes it also wants distance to a point. Stop here if all the question wants is the projection (which will be in matrix form). Continue if you need distance to a point

3. Take the original given vector v and the projection calculated previously and subtract them (with regular matrix subtraction)
$$\overrightarrow{v}_{\perp}=\overrightarrow{v}-\overrightarrow{v}_{||}$$
Note: sometimes instead of $v_{\perp}$ it's just called d for distance

4. Finally, compute the distance/magnitude normally on $\overrightarrow{v}_{\perp}$
$$\|v_{\perp}\|=\sqrt{v_1^2+v_2^2+...+v^2_n}$$
This is the distance from vector v to the line L

---

![[1.4-student 1.pdf]]