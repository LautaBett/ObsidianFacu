¡Excelente! Vamos a resolver estos ejercicios utilizando los conceptos que hemos repasado.

**Ejercicio 1: Determinar cuáles de las siguientes aplicaciones son transformaciones lineales:**

Para que una aplicación $f: V \rightarrow W$ sea una transformación lineal (TL), debe cumplir dos condiciones para todos los vectores $u, v \in V$ y todo escalar $\alpha \in \mathbb{R}$:
1.  $f(u+v) = f(u) + f(v)$ (Aditividad)
2.  $f(\alpha u) = \alpha f(u)$ (Homogeneidad)

a) $f: \mathbb{R}^3 \rightarrow \mathbb{R}^2$ definida por $f(x, y, z) = (y, x)$
   Sean $u = (x_1, y_1, z_1)$ y $v = (x_2, y_2, z_2)$.
   1. Aditividad:
      $f(u+v) = f(x_1+x_2, y_1+y_2, z_1+z_2) = (y_1+y_2, x_1+x_2)$
      $f(u) + f(v) = (y_1, x_1) + (y_2, x_2) = (y_1+y_2, x_1+x_2)$
      Se cumple $f(u+v) = f(u) + f(v)$.
   2. Homogeneidad:
      Sea $\alpha \in \mathbb{R}$.
      $f(\alpha u) = f(\alpha x_1, \alpha y_1, \alpha z_1) = (\alpha y_1, \alpha x_1)$
      $\alpha f(u) = \alpha (y_1, x_1) = (\alpha y_1, \alpha x_1)$
      Se cumple $f(\alpha u) = \alpha f(u)$.
   **Conclusión:** $f(x, y, z) = (y, x)$ **es una transformación lineal.**

b) $f: \mathbb{R}^2 \rightarrow \mathbb{R}^3$ definida por $f(x, y) = (x, y, 0) + (-1,0,0) = (x-1, y, 0)$
   Una propiedad necesaria para que una transformación sea lineal es que $f(\vec{0}) = \vec{0}$.
   $f(0,0) = (0-1, 0, 0) = (-1, 0, 0) \neq (0,0,0)$.
   **Conclusión:** $f(x, y) = (x-1, y, 0)$ **no es una transformación lineal.** (La suma de un vector constante no nulo generalmente rompe la linealidad).

c) $f: \mathbb{R}^2 \rightarrow \mathbb{R}$ definida por $f(x, y) = xy$
   Sean $u = (x_1, y_1)$ y $v = (x_2, y_2)$.
   1. Aditividad:
      $f(u+v) = f(x_1+x_2, y_1+y_2) = (x_1+x_2)(y_1+y_2) = x_1y_1 + x_1y_2 + x_2y_1 + x_2y_2$
      $f(u) + f(v) = x_1y_1 + x_2y_2$
      En general, $x_1y_1 + x_1y_2 + x_2y_1 + x_2y_2 \neq x_1y_1 + x_2y_2$. Por ejemplo, si $u=(1,1)$ y $v=(1,1)$, $f(u+v)=f(2,2)=4$, pero $f(u)+f(v)=1+1=2$.
      No se cumple la aditividad.
   **Conclusión:** $f(x, y) = xy$ **no es una transformación lineal.**

d) $f: \mathbb{R}^2 \rightarrow \mathbb{R}^2$ definida por $f(x, y) = (2x - y, x)$
   Sean $u = (x_1, y_1)$ y $v = (x_2, y_2)$.
   1. Aditividad:
      $f(u+v) = f(x_1+x_2, y_1+y_2) = (2(x_1+x_2) - (y_1+y_2), x_1+x_2) = (2x_1+2x_2 - y_1-y_2, x_1+x_2)$
      $f(u) + f(v) = (2x_1-y_1, x_1) + (2x_2-y_2, x_2) = (2x_1-y_1+2x_2-y_2, x_1+x_2) = (2x_1+2x_2-y_1-y_2, x_1+x_2)$
      Se cumple $f(u+v) = f(u) + f(v)$.
   2. Homogeneidad:
      Sea $\alpha \in \mathbb{R}$.
      $f(\alpha u) = f(\alpha x_1, \alpha y_1) = (2(\alpha x_1) - (\alpha y_1), \alpha x_1) = (\alpha(2x_1-y_1), \alpha x_1)$
      $\alpha f(u) = \alpha (2x_1-y_1, x_1) = (\alpha(2x_1-y_1), \alpha x_1)$
      Se cumple $f(\alpha u) = \alpha f(u)$.
   **Conclusión:** $f(x, y) = (2x - y, x)$ **es una transformación lineal.**

---
**Ejercicio 2: Si $A = \begin{pmatrix} 4 & 0 & -1 \\ -2 & 1 & 3 \end{pmatrix}$, hallar $f_A(x) = Ax$ para $x = (1, -1, 2)^t$ y $x = (0, 5, -1)^t$**

Para $x = \begin{pmatrix} 1 \\ -1 \\ 2 \end{pmatrix}$:
$f_A(x) = Ax = \begin{pmatrix} 4 & 0 & -1 \\ -2 & 1 & 3 \end{pmatrix} \begin{pmatrix} 1 \\ -1 \\ 2 \end{pmatrix} = \begin{pmatrix} 4(1) + 0(-1) + (-1)(2) \\ -2(1) + 1(-1) + 3(2) \end{pmatrix} = \begin{pmatrix} 4 - 0 - 2 \\ -2 - 1 + 6 \end{pmatrix} = \begin{pmatrix} 2 \\ 3 \end{pmatrix}$

Para $x = \begin{pmatrix} 0 \\ 5 \\ -1 \end{pmatrix}$:
$f_A(x) = Ax = \begin{pmatrix} 4 & 0 & -1 \\ -2 & 1 & 3 \end{pmatrix} \begin{pmatrix} 0 \\ 5 \\ -1 \end{pmatrix} = \begin{pmatrix} 4(0) + 0(5) + (-1)(-1) \\ -2(0) + 1(5) + 3(-1) \end{pmatrix} = \begin{pmatrix} 0 + 0 + 1 \\ 0 + 5 - 3 \end{pmatrix} = \begin{pmatrix} 1 \\ 2 \end{pmatrix}$

---
**Ejercicio 3: Mostrar que las siguientes aplicaciones son TL, verificando las propiedades y hallando luego la matriz $A$ que permita realizar $t$ mediante un producto matricial $t(x) = Ax$**

a) $t(x, y) = (x + y, x - y)$
   Dominio $\mathbb{R}^2$, Codominio $\mathbb{R}^2$.
   Verificación de TL (similar al Ejercicio 1d, las componentes son lineales):
   Sean $u=(x_1,y_1), v=(x_2,y_2)$.
   $t(u+v) = t(x_1+x_2, y_1+y_2) = ((x_1+x_2)+(y_1+y_2), (x_1+x_2)-(y_1+y_2)) = (x_1+y_1+x_2+y_2, x_1-y_1+x_2-y_2)$
   $t(u)+t(v) = (x_1+y_1, x_1-y_1) + (x_2+y_2, x_2-y_2) = (x_1+y_1+x_2+y_2, x_1-y_1+x_2-y_2)$. Cumple aditividad.
   $t(\alpha u) = t(\alpha x_1, \alpha y_1) = (\alpha x_1 + \alpha y_1, \alpha x_1 - \alpha y_1) = \alpha(x_1+y_1, x_1-y_1) = \alpha t(u)$. Cumple homogeneidad.
   Es TL.
   Matriz $A$:
   $t(1,0) = (1+0, 1-0) = (1,1)$
   $t(0,1) = (0+1, 0-1) = (1,-1)$
   $A = \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$

b) $t(x, y) = (-x, 2x + y, x + 3y)$
   Dominio $\mathbb{R}^2$, Codominio $\mathbb{R}^3$. Es TL (componentes lineales).
   Matriz $A$:
   $t(1,0) = (-1, 2(1)+0, 1+3(0)) = (-1, 2, 1)$
   $t(0,1) = (-0, 2(0)+1, 0+3(1)) = (0, 1, 3)$
   $A = \begin{pmatrix} -1 & 0 \\ 2 & 1 \\ 1 & 3 \end{pmatrix}$

c) $t(x, y, z) = (x - y + z, x + 2y - 3z)$
   Dominio $\mathbb{R}^3$, Codominio $\mathbb{R}^2$. Es TL (componentes lineales).
   Matriz $A$:
   $t(1,0,0) = (1-0+0, 1+2(0)-3(0)) = (1,1)$
   $t(0,1,0) = (0-1+0, 0+2(1)-3(0)) = (-1,2)$
   $t(0,0,1) = (0-0+1, 0+2(0)-3(1)) = (1,-3)$
   $A = \begin{pmatrix} 1 & -1 & 1 \\ 1 & 2 & -3 \end{pmatrix}$

d) $t(x, y, z) = (x + z, y + z, x + y)$
   Dominio $\mathbb{R}^3$, Codominio $\mathbb{R}^3$. Es TL (componentes lineales).
   Matriz $A$:
   $t(1,0,0) = (1+0, 0+0, 1+0) = (1,0,1)$
   $t(0,1,0) = (0+0, 1+0, 0+1) = (0,1,1)$
   $t(0,0,1) = (0+1, 0+1, 0+0) = (1,1,0)$
   $A = \begin{pmatrix} 1 & 0 & 1 \\ 0 & 1 & 1 \\ 1 & 1 & 0 \end{pmatrix}$

---
**Ejercicio 4: Hallar la matriz asociada a la transformación pedida en cada caso:**

a) La transformación $t \circ s$ donde
   $t: \mathbb{R}^2 \rightarrow \mathbb{R}^2$ donde $t(x, y) = (2x + 3y, x - 5y)$
   $s: \mathbb{R}^3 \rightarrow \mathbb{R}^2$ donde $s(x, y, z) = (4x + 3y + 6z, x - 2y + 3z)$
   Matriz de $t$, $[T]$:
   $t(1,0) = (2,1)$
   $t(0,1) = (3,-5)$
   $[T] = \begin{pmatrix} 2 & 3 \\ 1 & -5 \end{pmatrix}$
   Matriz de $s$, $[S]$:
   $s(1,0,0) = (4,1)$
   $s(0,1,0) = (3,-2)$
   $s(0,0,1) = (6,3)$
   $[S] = \begin{pmatrix} 4 & 3 & 6 \\ 1 & -2 & 3 \end{pmatrix}$
   Matriz de $t \circ s$ es $[T][S]$:
   $[T \circ S] = \begin{pmatrix} 2 & 3 \\ 1 & -5 \end{pmatrix} \begin{pmatrix} 4 & 3 & 6 \\ 1 & -2 & 3 \end{pmatrix} = \begin{pmatrix} 2(4)+3(1) & 2(3)+3(-2) & 2(6)+3(3) \\ 1(4)+(-5)(1) & 1(3)+(-5)(-2) & 1(6)+(-5)(3) \end{pmatrix}$
   $= \begin{pmatrix} 8+3 & 6-6 & 12+9 \\ 4-5 & 3+10 & 6-15 \end{pmatrix} = \begin{pmatrix} 11 & 0 & 21 \\ -1 & 13 & -9 \end{pmatrix}$

b) La transformación $t + s$ donde
   $t: \mathbb{R}^3 \rightarrow \mathbb{R}^2$ donde $t(x, y, z) = (2x + y + z, x - y - 2z)$
   $s: \mathbb{R}^3 \rightarrow \mathbb{R}^2$ donde $s(x, y, z) = (x + 3y + z, x - 2y + z)$ (corregido de $t(x,y,z)$ a $s(x,y,z)$)
   Matriz de $t$, $[T]$:
   $t(1,0,0) = (2,1)$
   $t(0,1,0) = (1,-1)$
   $t(0,0,1) = (1,-2)$
   $[T] = \begin{pmatrix} 2 & 1 & 1 \\ 1 & -1 & -2 \end{pmatrix}$
   Matriz de $s$, $[S]$:
   $s(1,0,0) = (1,1)$
   $s(0,1,0) = (3,-2)$
   $s(0,0,1) = (1,1)$
   $[S] = \begin{pmatrix} 1 & 3 & 1 \\ 1 & -2 & 1 \end{pmatrix}$
   Matriz de $t+s$ es $[T]+[S]$:
   $[T+S] = \begin{pmatrix} 2 & 1 & 1 \\ 1 & -1 & -2 \end{pmatrix} + \begin{pmatrix} 1 & 3 & 1 \\ 1 & -2 & 1 \end{pmatrix} = \begin{pmatrix} 2+1 & 1+3 & 1+1 \\ 1+1 & -1-2 & -2+1 \end{pmatrix} = \begin{pmatrix} 3 & 4 & 2 \\ 2 & -3 & -1 \end{pmatrix}$

c) La transformación $t \circ s$ donde
   $t: \mathbb{R}^3 \rightarrow \mathbb{R}^4$ donde $t(x, y, z) = (2x - 5y, -x + 3y - 4z, 6x - 8y - 7z, -3x + 9z)$
   $s: \mathbb{R}^2 \rightarrow \mathbb{R}^3$ donde $s(x, y) = (4x - 6y, 7x + y, 3x + 2y)$ (corregido $s(x,y,z)$ a $s(x,y)$)
   Matriz de $t$, $[T]$:
   $t(1,0,0) = (2,-1,6,-3)$
   $t(0,1,0) = (-5,3,-8,0)$
   $t(0,0,1) = (0,-4,-7,9)$
   $[T] = \begin{pmatrix} 2 & -5 & 0 \\ -1 & 3 & -4 \\ 6 & -8 & -7 \\ -3 & 0 & 9 \end{pmatrix}$
   Matriz de $s$, $[S]$:
   $s(1,0) = (4,7,3)$
   $s(0,1) = (-6,1,2)$
   $[S] = \begin{pmatrix} 4 & -6 \\ 7 & 1 \\ 3 & 2 \end{pmatrix}$
   Matriz de $t \circ s$ es $[T][S]$:
   $[T \circ S] = \begin{pmatrix} 2 & -5 & 0 \\ -1 & 3 & -4 \\ 6 & -8 & -7 \\ -3 & 0 & 9 \end{pmatrix} \begin{pmatrix} 4 & -6 \\ 7 & 1 \\ 3 & 2 \end{pmatrix}$
   $= \begin{pmatrix} 2(4)-5(7)+0(3) & 2(-6)-5(1)+0(2) \\ -1(4)+3(7)-4(3) & -1(-6)+3(1)-4(2) \\ 6(4)-8(7)-7(3) & 6(-6)-8(1)-7(2) \\ -3(4)+0(7)+9(3) & -3(-6)+0(1)+9(2) \end{pmatrix}$
   $= \begin{pmatrix} 8-35 & -12-5 \\ -4+21-12 & 6+3-8 \\ 24-56-21 & -36-8-14 \\ -12+27 & 18+18 \end{pmatrix} = \begin{pmatrix} -27 & -17 \\ 5 & 1 \\ -53 & -58 \\ 15 & 36 \end{pmatrix}$

d) La composición $t + s$ donde (asumo que es suma, no composición)
   $t: \mathbb{R}^3 \rightarrow \mathbb{R}^4$ donde $t(x, y, z) = (2x + y, 2x + z, y + z, y - z)$
   $s: \mathbb{R}^3 \rightarrow \mathbb{R}^4$ donde $s(x, y, z) = (-x + y, -y + z, -z + x, 0)$ (corregido de $t(x,y,z)$ a $s(x,y,z)$)
   Matriz de $t$, $[T]$:
   $t(1,0,0) = (2,2,0,0)$
   $t(0,1,0) = (1,0,1,1)$
   $t(0,0,1) = (0,1,1,-1)$
   $[T] = \begin{pmatrix} 2 & 1 & 0 \\ 2 & 0 & 1 \\ 0 & 1 & 1 \\ 0 & 1 & -1 \end{pmatrix}$
   Matriz de $s$, $[S]$:
   $s(1,0,0) = (-1,0,1,0)$
   $s(0,1,0) = (1,-1,0,0)$
   $s(0,0,1) = (0,1,-1,0)$
   $[S] = \begin{pmatrix} -1 & 1 & 0 \\ 0 & -1 & 1 \\ 1 & 0 & -1 \\ 0 & 0 & 0 \end{pmatrix}$
   Matriz de $t+s$ es $[T]+[S]$:
   $[T+S] = \begin{pmatrix} 2 & 1 & 0 \\ 2 & 0 & 1 \\ 0 & 1 & 1 \\ 0 & 1 & -1 \end{pmatrix} + \begin{pmatrix} -1 & 1 & 0 \\ 0 & -1 & 1 \\ 1 & 0 & -1 \\ 0 & 0 & 0 \end{pmatrix} = \begin{pmatrix} 1 & 2 & 0 \\ 2 & -1 & 2 \\ 1 & 1 & 0 \\ 0 & 1 & -1 \end{pmatrix}$

---
**Ejercicio 5: Para cada transformación lineal, hallar la matriz estándar asociada, las imágenes y preimágenes de los conjuntos indicados en cada caso.**

a) Sea $T: \mathbb{R}^3 \rightarrow \mathbb{R}^2$ definida por $T(x, y, z) = (x - y + z, x + 2y - 3z)$, hallar $T(S)$ donde $S = \langle(1,2,1)\rangle$. (Asumo que el $^2$ es un error).
   Matriz estándar $[T]$: (Ya calculada en Ej 3c)
   $[T] = \begin{pmatrix} 1 & -1 & 1 \\ 1 & 2 & -3 \end{pmatrix}$
   Para hallar $T(S)$:
   $T(S) = \langle T(1,2,1) \rangle$
   $T(1,2,1) = (1 - 2 + 1, 1 + 2(2) - 3(1)) = (0, 1 + 4 - 3) = (0, 2)$
   $T(S) = \langle (0,2) \rangle = \{ \alpha(0,2) : \alpha \in \mathbb{R} \}$

b) Sea $T: \mathbb{R}^3 \rightarrow \mathbb{R}^2$ definida por $T(x, y, z) = (x - 2y + z, y + z)$, hallar $T(S)$ y $T^{-1}(H)$, donde $S = \langle(1, -3,2)\rangle$ y $H = \{(x, y) \in \mathbb{R}^2 : 2x - y = 0\}$.
   Matriz estándar $[T]$:
   $T(1,0,0) = (1,0)$
   $T(0,1,0) = (-2,1)$
   $T(0,0,1) = (1,1)$
   $[T] = \begin{pmatrix} 1 & -2 & 1 \\ 0 & 1 & 1 \end{pmatrix}$
   $T(S) = \langle T(1,-3,2) \rangle$:
   $T(1,-3,2) = (1 - 2(-3) + 2, -3 + 2) = (1 + 6 + 2, -1) = (9, -1)$
   $T(S) = \langle (9,-1) \rangle$
   $T^{-1}(H)$: Buscamos $(a,b,c) \in \mathbb{R}^3$ tal que $T(a,b,c) \in H$.
   $T(a,b,c) = (a - 2b + c, b + c)$.
   Para que este vector esté en $H$, debe cumplir $2x - y = 0$.
   $2(a - 2b + c) - (b + c) = 0$
   $2a - 4b + 2c - b - c = 0$
   $2a - 5b + c = 0$
   $T^{-1}(H) = \{ (a,b,c) \in \mathbb{R}^3 : 2a - 5b + c = 0 \}$
   Este es un plano en $\mathbb{R}^3$. Podemos hallar sus generadores: $c = -2a+5b$.
   $(a,b, -2a+5b) = a(1,0,-2) + b(0,1,5)$.
   $T^{-1}(H) = \langle (1,0,-2), (0,1,5) \rangle$.

c) Sea $T: \mathbb{R}^2 \rightarrow \mathbb{R}^2$ definida por $T_A(x, y) = A(x, y)^t$, con $A = \begin{pmatrix} 0 & -1 \\ -1 & 0 \end{pmatrix}$. Hallar $T_A((1, -2))$; $T_A^{-1}((1,1))$; $T_A^{-1}((0,0))$; $T(S)$; $T^{-1}(H)$ donde $S = \{(x, y) \in \mathbb{R}^2 : x + 3y = 0\}$ y $H = \{(x, y) \in \mathbb{R}^2 : (x, y) = \alpha(2, -3)\}$.
   La matriz estándar es $A = \begin{pmatrix} 0 & -1 \\ -1 & 0 \end{pmatrix}$.
   $T_A((1,-2)) = \begin{pmatrix} 0 & -1 \\ -1 & 0 \end{pmatrix} \begin{pmatrix} 1 \\ -2 \end{pmatrix} = \begin{pmatrix} 0(1) -1(-2) \\ -1(1) + 0(-2) \end{pmatrix} = \begin{pmatrix} 2 \\ -1 \end{pmatrix}$.
   $T_A^{-1}((1,1))$: Resolvemos $A \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$
   $\begin{pmatrix} 0 & -1 \\ -1 & 0 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} -y \\ -x \end{pmatrix} = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$.
   $-y=1 \Rightarrow y=-1$. $-x=1 \Rightarrow x=-1$.
   $T_A^{-1}((1,1)) = \{(-1,-1)\}$.
   $T_A^{-1}((0,0))$: Resolvemos $A \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$
   $\begin{pmatrix} -y \\ -x \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix} \Rightarrow y=0, x=0$.
   $T_A^{-1}((0,0)) = \{(0,0)\}$. (El núcleo es solo el vector cero).
   $T(S)$ donde $S = \{(x, y) \in \mathbb{R}^2 : x + 3y = 0\}$.
   Un generador de $S$ es $v = (-3,1)$ (ya que $x=-3y$).
   $T(S) = \langle T_A(-3,1) \rangle$.
   $T_A(-3,1) = \begin{pmatrix} 0 & -1 \\ -1 & 0 \end{pmatrix} \begin{pmatrix} -3 \\ 1 \end{pmatrix} = \begin{pmatrix} -1 \\ 3 \end{pmatrix}$.
   $T(S) = \langle (-1,3) \rangle$.
   $T^{-1}(H)$ donde $H = \langle (2,-3) \rangle$.
   Buscamos $(a,b)$ tal que $T_A(a,b) \in H$.
   $T_A(a,b) = (-b, -a)$.
   Queremos que $(-b, -a) = \alpha(2,-3)$ para algún $\alpha$.
   $-b = 2\alpha \Rightarrow b = -2\alpha$
   $-a = -3\alpha \Rightarrow a = 3\alpha$
   Así, los vectores $(a,b)$ de la preimagen son de la forma $(3\alpha, -2\alpha) = \alpha(3,-2)$.
   $T^{-1}(H) = \langle (3,-2) \rangle$.

d) Sea $T: \mathbb{R}^2 \rightarrow \mathbb{R}^3$ definida por $T_A(x, y) = A(x, y)^t$, con $A = \begin{pmatrix} 1 & 2 \\ -2 & 4 \\ -2 & 2 \end{pmatrix}$. Hallar $T_A((2,4))$; $T_A^{-1}((-1,2,2))$. Explicar por qué el vector $(1,1,1)$ no tiene preimagen bajo esta transformación.
   La matriz estándar es $A$.
   $T_A((2,4)) = \begin{pmatrix} 1 & 2 \\ -2 & 4 \\ -2 & 2 \end{pmatrix} \begin{pmatrix} 2 \\ 4 \end{pmatrix} = \begin{pmatrix} 1(2)+2(4) \\ -2(2)+4(4) \\ -2(2)+2(4) \end{pmatrix} = \begin{pmatrix} 2+8 \\ -4+16 \\ -4+8 \end{pmatrix} = \begin{pmatrix} 10 \\ 12 \\ 4 \end{pmatrix}$.
   $T_A^{-1}((-1,2,2))$: Resolvemos $A \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} -1 \\ 2 \\ 2 \end{pmatrix}$.
   $\begin{pmatrix} 1 & 2 \\ -2 & 4 \\ -2 & 2 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} x+2y \\ -2x+4y \\ -2x+2y \end{pmatrix} = \begin{pmatrix} -1 \\ 2 \\ 2 \end{pmatrix}$.
   Sistema de ecuaciones:
   1) $x + 2y = -1$
   2) $-2x + 4y = 2 \Rightarrow -x + 2y = 1$
   3) $-2x + 2y = 2 \Rightarrow -x + y = 1$
   De (3): $y = x+1$.
   Sustituyendo en (1): $x + 2(x+1) = -1 \Rightarrow x + 2x + 2 = -1 \Rightarrow 3x = -3 \Rightarrow x = -1$.
   Entonces $y = -1+1 = 0$.
   Verificamos en (2): $-(-1) + 2(0) = 1$. $1 = 1$. Se cumple.
   $T_A^{-1}((-1,2,2)) = \{(-1,0)\}$.
   Explicar por qué $(1,1,1)$ no tiene preimagen:
   Intentamos resolver $A \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} 1 \\ 1 \\ 1 \end{pmatrix}$.
   4) $x + 2y = 1$
   5) $-2x + 4y = 1$
   6) $-2x + 2y = 1$
   De (3): $2y = 2x+1 \Rightarrow y = x + 1/2$.
   Sustituyendo en (1): $x + 2(x+1/2) = 1 \Rightarrow x + 2x + 1 = 1 \Rightarrow 3x = 0 \Rightarrow x = 0$.
   Entonces $y = 0 + 1/2 = 1/2$.
   Verificamos en (2): $-2(0) + 4(1/2) = 0 + 2 = 2$. Pero debe ser $1$.
   $2 \neq 1$. El sistema es incompatible.
   Por lo tanto, $(1,1,1)$ no tiene preimagen.

---
**Ejercicio 6: Analizar la existencia y unicidad de una transformación lineal $T$ que cumpla las condiciones indicadas. En los casos posibles determinar la expresión cartesiana de la transformación y la matriz estándar.**

a) $\begin{cases} T(1,1,1) = (1,0,0) \\ T(0, -1,1) = (-1,2,1) \\ T(1,0,1) = (1,1,0) \end{cases}$
   Los vectores de entrada son $v_1=(1,1,1), v_2=(0,-1,1), v_3=(1,0,1)$.
   Verificamos si forman una base de $\mathbb{R}^3$:
   $\det \begin{pmatrix} 1 & 0 & 1 \\ 1 & -1 & 0 \\ 1 & 1 & 1 \end{pmatrix} = 1(-1-0) - 0(1-0) + 1(1-(-1)) = -1 + 2 = 1 \neq 0$.
   Son linealmente independientes, forman una base. Por el Teorema de Existencia y Unicidad, existe una única TL.
   Expresión cartesiana $T(x,y,z)$:
   $(x,y,z) = \alpha_1(1,1,1) + \alpha_2(0,-1,1) + \alpha_3(1,0,1)$
   $x = \alpha_1 + \alpha_3$
   $y = \alpha_1 - \alpha_2$
   $z = \alpha_1 + \alpha_2 + \alpha_3$
   De $x = \alpha_1 + \alpha_3 \Rightarrow \alpha_3 = x - \alpha_1$.
   $y = \alpha_1 - \alpha_2 \Rightarrow \alpha_2 = \alpha_1 - y$.
   $z = \alpha_1 + (\alpha_1 - y) + (x - \alpha_1) = \alpha_1 - y + x \Rightarrow \alpha_1 = z - x + y$.
   $\alpha_2 = (z-x+y) - y = z-x$.
   $\alpha_3 = x - (z-x+y) = x - z + x - y = 2x - y - z$.
   $T(x,y,z) = \alpha_1 T(v_1) + \alpha_2 T(v_2) + \alpha_3 T(v_3)$
   $T(x,y,z) = (z-x+y)(1,0,0) + (z-x)(-1,2,1) + (2x-y-z)(1,1,0)$
   $T(x,y,z) = (z-x+y - (z-x) + (2x-y-z), (z-x)(2) + (2x-y-z), (z-x)(1))$
   $T(x,y,z) = (z-x+y-z+x+2x-y-z, 2z-2x+2x-y-z, z-x)$
   $T(x,y,z) = (2x-z, z-y, z-x)$.
   Matriz estándar $[T]$:
   $T(1,0,0) = (2(1)-0, 0-0, 0-1) = (2,0,-1)$
   $T(0,1,0) = (2(0)-0, 0-1, 0-0) = (0,-1,0)$
   $T(0,0,1) = (2(0)-1, 1-0, 1-0) = (-1,1,1)$
   $[T] = \begin{pmatrix} 2 & 0 & -1 \\ 0 & -1 & 0 \\ -1 & 0 & 1 \end{pmatrix}$
   $T(0,3,-1) = (2(0)-(-1), -1-3, -1-0) = (1, -4, -1)$.
   $T(2,-1,0) = (2(2)-0, 0-(-1), 0-2) = (4, 1, -2)$.

b) $T: \mathbb{R}^3 \rightarrow \mathbb{R}^3$ tal que $T(v_1) = (1,1,1), T(v_2) = (0, -1,3)$ y $T(v_3) = (2,5, -7)$
   i. $v_1 = (1,1,1); v_2 = (0,1,0); v_3 = (2, -1,2)$
      $\det \begin{pmatrix} 1 & 0 & 2 \\ 1 & 1 & -1 \\ 1 & 0 & 2 \end{pmatrix} = 1(2-0) - 0 + 2(0-1) = 2-2 = 0$.
      Los vectores $v_1, v_2, v_3$ son linealmente dependientes.
      $v_3 = a v_1 + b v_2 \Rightarrow (2,-1,2) = a(1,1,1) + b(0,1,0) = (a, a+b, a)$.
      $a=2$. $a+b=-1 \Rightarrow 2+b=-1 \Rightarrow b=-3$.
      $v_3 = 2v_1 - 3v_2$.
      Para que exista $T$, debe cumplirse $T(v_3) = 2T(v_1) - 3T(v_2)$.
      $T(v_3) = (2,5,-7)$.
      $2T(v_1) - 3T(v_2) = 2(1,1,1) - 3(0,-1,3) = (2,2,2) - (0,-3,9) = (2, 2+3, 2-9) = (2,5,-7)$.
      La condición se cumple. Existe la transformación lineal, pero **no es única** porque $v_1, v_2, v_3$ no forman una base. La información dada solo define $T$ sobre el subespacio generado por $v_1, v_2$. Para definir $T$ de forma única en $\mathbb{R}^3$, necesitaríamos la imagen de un tercer vector linealmente independiente de $v_1, v_2$.

   ii. $v_1 = (1,1,1); v_2 = (0,1,0); v_3 = (1,0,1)$
       $\det \begin{pmatrix} 1 & 0 & 1 \\ 1 & 1 & 0 \\ 1 & 0 & 1 \end{pmatrix} = 1(1-0) - 0 + 1(0-1) = 1-1 = 0$.
       Los vectores $v_1, v_2, v_3$ son linealmente dependientes.
       $v_3 = a v_1 + b v_2 \Rightarrow (1,0,1) = a(1,1,1) + b(0,1,0) = (a, a+b, a)$.
       $a=1$. $a+b=0 \Rightarrow 1+b=0 \Rightarrow b=-1$.
       $v_3 = v_1 - v_2$.
       Para que exista $T$, debe cumplirse $T(v_3) = T(v_1) - T(v_2)$.
       $T(v_3) = (2,5,-7)$.
       $T(v_1) - T(v_2) = (1,1,1) - (0,-1,3) = (1, 1-(-1), 1-3) = (1,2,-2)$.
       $(2,5,-7) \neq (1,2,-2)$.
       La condición no se cumple. **No existe** tal transformación lineal.

---
**Ejercicio 7: Consideremos una función $T: \mathbb{R}^3 \rightarrow \mathbb{R}^4$ tal que**
$T(1,1,1) = (0,0,2,1)$
$T(k, 0,1) = (1,0,0,0)$
$T(-2, k, -1) = (0, -2,0,0)$

a) Hallar $k \in \mathbb{R}$ tal que $T$ defina una única transformación lineal (para cada $k$)
   Para que $T$ defina una única TL, los vectores $v_1=(1,1,1), v_2=(k,0,1), v_3=(-2,k,-1)$ deben formar una base de $\mathbb{R}^3$. Esto ocurre si son linealmente independientes, es decir, el determinante de la matriz formada por ellos es no nulo.
   $\det \begin{pmatrix} 1 & k & -2 \\ 1 & 0 & k \\ 1 & 1 & -1 \end{pmatrix} = 1(0 \cdot (-1) - k \cdot 1) - k(1 \cdot (-1) - k \cdot 1) + (-2)(1 \cdot 1 - 0 \cdot 1)$
   $= 1(-k) - k(-1-k) - 2(1)$
   $= -k + k + k^2 - 2 = k^2 - 2$.
   Para que sea única, $k^2 - 2 \neq 0 \Rightarrow k^2 \neq 2 \Rightarrow k \neq \sqrt{2}$ y $k \neq -\sqrt{2}$.

b) Para el caso particular $k = -1$ hallar la expresión cartesiana y la matriz estándar de $T$.
   Si $k=-1$, $k^2-2 = (-1)^2-2 = 1-2 = -1 \neq 0$. Existe una única TL.
   $v_1=(1,1,1) \Rightarrow T(v_1)=(0,0,2,1)$
   $v_2=(-1,0,1) \Rightarrow T(v_2)=(1,0,0,0)$
   $v_3=(-2,-1,-1) \Rightarrow T(v_3)=(0,-2,0,0)$
   $(x,y,z) = \alpha_1 v_1 + \alpha_2 v_2 + \alpha_3 v_3$
   $x = \alpha_1 - \alpha_2 - 2\alpha_3$  (1)
   $y = \alpha_1 - \alpha_3$          (2)
   $z = \alpha_1 + \alpha_2 - \alpha_3$  (3)
   De (2), $\alpha_3 = \alpha_1 - y$.
   Sustituyendo $\alpha_3$ en (1): $x = \alpha_1 - \alpha_2 - 2(\alpha_1 - y) = \alpha_1 - \alpha_2 - 2\alpha_1 + 2y = -\alpha_1 - \alpha_2 + 2y$.
   $x - 2y = -\alpha_1 - \alpha_2$. (1')
   Sustituyendo $\alpha_3$ en (3): $z = \alpha_1 + \alpha_2 - (\alpha_1 - y) = \alpha_1 + \alpha_2 - \alpha_1 + y = \alpha_2 + y$.
   $\alpha_2 = z - y$.
   Sustituyendo $\alpha_2$ en (1'): $x - 2y = -\alpha_1 - (z-y) = -\alpha_1 - z + y$.
   $\alpha_1 = -x + 2y - z + y = -x + 3y - z$.
   Ahora $\alpha_3 = \alpha_1 - y = (-x+3y-z) - y = -x+2y-z$.
   Verificamos:
   $\alpha_1 = -x+3y-z$
   $\alpha_2 = z-y$
   $\alpha_3 = -x+2y-z$
   $T(x,y,z) = \alpha_1 T(v_1) + \alpha_2 T(v_2) + \alpha_3 T(v_3)$
   $T(x,y,z) = (-x+3y-z)(0,0,2,1) + (z-y)(1,0,0,0) + (-x+2y-z)(0,-2,0,0)$
   $T(x,y,z) = ( (z-y)(1), (-x+2y-z)(-2), (-x+3y-z)(2), (-x+3y-z)(1) )$
   $T(x,y,z) = (z-y, 2x-4y+2z, -2x+6y-2z, -x+3y-z)$.
   Matriz estándar $[T]$:
   $T(1,0,0) = (0-0, 2(1)-0+0, -2(1)+0-0, -1+0-0) = (0,2,-2,-1)$
   $T(0,1,0) = (0-1, 0-4(1)+0, 0+6(1)-0, 0+3(1)-0) = (-1,-4,6,3)$
   $T(0,0,1) = (1-0, 0-0+2(1), 0+0-2(1), 0+0-1) = (1,2,-2,-1)$
   $[T] = \begin{pmatrix} 0 & -1 & 1 \\ 2 & -4 & 2 \\ -2 & 6 & -2 \\ -1 & 3 & -1 \end{pmatrix}$