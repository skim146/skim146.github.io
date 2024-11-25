---
layout: posts
title: Vector Spaces
comments: false
author_profile: true
classes: wide
permalink: /vector/
---

## Referencing Linear Algebra Done Wrong - Treil

This lecture series will detail linear algebra for beginners. It is aimed at students who are first learning pure math and are struggling with basic proofs/mathematical reasoning.

- **8 axioms of a vector space $V$**
    1. Commutativity 
        1. $v+w=w+v\ \forall v,w \in V$.
    2. Associativity
        1. $(u+v)+w=u+(v+w)\ \forall u,v,w \in V$.
    3. Zero Vector
        1. There exists a unique vector denoted $0$ such that $v+0=v$.
    4. Additive Inverse
        1. $\forall v\in V, \exists w\in V: v+w=0.$ $w$ is usually denoted $-v$.  
    5. Multiplicative Identity
        1. $1v=v\ \forall v \in V$.
    6. Multiplicative Associativity
        1. $(\alpha \beta )v= \alpha(\beta v)\ \forall v \in V$ and scalars all $\alpha, \beta$.
    7. Distributivity
        1. $\alpha (u+v)=\alpha u+\alpha v \ \forall u,v \in V$ and all scalars $\alpha$.
    8. Distributivity
        1. $(\alpha +\beta) v= \alpha v+\beta v \ \forall v \in V$ and all scalars $\alpha,\beta$.
    
- If the scalars are real values, then $V$ is a real vector space, while if they are complex, $V$ is a complex vector space.
    - More generally, we say $V$ is a vector space over a field $\mathbb{F}$ when the scalars are elements of an arbitrary field $\mathbb{F}$.
    - Proof that the zero vector is unique:
        
        Statement: *For all vectors $v \in V$, there exists a **unique** vector denoted $0$ such that $v+0=v$.*
        
        *Proof.*
        
        Let $V$ be an arbitrary vector space. Suppose $0_1$ and $0_2$ are zero vectors of $V$ such that $v+0_1=v$ and $v+0_2=v$ for all $v\in V$. These equations imply that
        
        $0_2+0_1=0_2$, and by commutativity, $0_1+0_2=0_2$, which implies $0_1=0_2$. Thus, we have shown that the zero vector is unique. $\blacksquare$
        
    - Proof that the additive inverse vector is unique:
        
        Statement: *For all vectors $v \in V$, there exists a **unique** vector $w$ such that $v+w=0$.*
        
        *Proof.*
        
        Let $V$ be an arbitrary vector space. Suppose there exists an arbitrary vector $v\in V$, and also suppose $w_1$ and $w_2$ are the additive inverses of $v$. This means that $v+w_1=0$ and $v+w_2=0$. Since the zero vector is unique, these equations imply that           $v+w_1=v+w_2$, and adding $w_1$ to both sides and commutativity and associativity, we see that$(v+w_1)+w_1=(v+w_1)+w_2 \implies 0+w_1=0+w_2$. By commutativity and the zero vector axiom of vector spaces, $w_1+0=w_1=w_2+0=w_2$. Hence, the additive inverse vector is unique. $\blacksquare$
        
    - Proof that $0v=0$ for any vector $v \in V$:
        
        Statement: *For any vector $v\in V$, $0v=0.$*
        
        *Proof.*
        
        Let $V$ be an arbitrary vector space, and suppose there is an arbitrary vector $v\in V$. Since every vector has an additive inverse, $0v-0v=0$. We also have that $0v=(0+0)v=0v+0v$ by distributivity, and using the first equation, we see that      $0=0v-0v=(0v+0v)-0v=0v+(0v-0v)=0v+0=0v$. Hence, for any vector $v\in V$, $0v=0$. $\blacksquare$
        

**Examples:**

- $\mathbb{R}, \mathbb{R}^n, \mathbb{C}^n, \mathbb{F}^n$.
- The space $M_{m \times n}$ of all $m\times n$ matrices.
- The space $\mathbb{P}_n$ of polynomials of the form $p(t)=\sum_{i=0}^na_it^i$ with degree at most $n$.

### **Matrix Transpose:**

- For a matrix $A$, the transpose of $A$ is defined to be

$$
⁍
$$

- Means that $A^T$ is the matrix which contains the entries of $A$’s rows and columns swapped.
- If $A$ is an $n\times m$ matrix, $A^T$is an $m \times n$ matrix.
- A column vector $v \in\mathbb{F}^n$ can be represented as $(x_1,x_2,...,x_n)^T$. (To save space)

### **Linear Combinations:**

- Let $V$ be a vector space, and let $v_1,v_2,...,v_p \in V$ be a collection of vectors. A **linear combination** of these vectors is a sum of the form

$$
\alpha_1 v_1+\alpha_2 v_2 +...+ \alpha_p v_p=\sum_{i=1}^p \alpha_i v_i.
$$

- A system of vectors is a basis of $V$ if any vector in $V$  can be **uniquely** represented as a linear combination.

$$
\vec{v}=\alpha_1 v_1+\alpha_2 v_2 +...+ \alpha_p v_p=\sum_{i=1}^p \alpha_i v_i.
$$

- The scalar coefficients $\alpha_i$ are the **coordinates** of vector $v$.
- Example:
    - We call the vectors $e_1, e_2,...,e_n$ of a the vector space $\mathbb{F}^n$ the **standard basis** of $\mathbb{F}^n$ if they are the vectors
    
    $$
    e_1=\begin{pmatrix} 1\\ 0\\0 \\ \vdots \\ 0\end{pmatrix},\ e_2=\begin{pmatrix} 0\\ 1\\0 \\ \vdots \\ 0\end{pmatrix},\ ...\ , e_n=\begin{pmatrix} 0\\ 0\\0 \\ \vdots \\ 1\end{pmatrix}
    $$
    
    - since they can represent any vector $v$ with the linear combination
    
    $$
    v=\sum_{i=0}^n x_ie_i.
    $$
    
- The sum of two vectors $v$ and $u$ can be represented through this notation:
    
    $$
    v+u=\sum_{i=1}^n\alpha_iv_i+\sum_{i=1}^n \beta_iv_i=\sum_{i=1}^n(\alpha_i+\beta_i)v_i
    $$
    

### **Generating and Linearly Independent Systems:**

- A system of vectors $v_1,v_2,...,v_p \in V$ is a generating **system/spanning system/complete system** in $V$ if any vector  $v\in V$ can be represented as a linear combination of such vectors.
    - **Not** unique (while a basis is).
    - Any **basis** is a generating system.
    - If one adds a number of vectors $v_{n+1},...\ ,v_p$ to a basis $v_1,v_2,...\ , v_n$, then this new system of vectors will be a generating system. (Since we can just ignore these new vectors by setting their coefficients to 0).
- A linear combination $\sum_{i=1}^n \alpha_iv_i$ is **trivial** if $\alpha_i = 0 \ \forall i$.
    - This linear combination always equals the zero vector $0$.
- A system of vectors is **linearly independent** if the zero vector can only be represented by the trivial linear combination.
- A system of vectors is called **linearly dependent** if the zero vector $0$ can be represented with a non-trivial linear combination.
    
    $$
    \exists k: a_k\neq0 \wedge0=\sum_{k=1}^n\alpha_kv_k 
    $$
    
    - This can be written as $\sum_{k=1}^n |\alpha_k| \neq 0$.
    - Proposition: *A system of vectors $v_1,v_2,...\ ,v_p \in V$  is linearly dependent iff*
    
    $$
    ⁍
    $$
    
    - *Proof.*
        
        Suppose the system $v_1,v_2,... \ , v_p \in V$ is linearly dependent. Then, 
        
        $$
        \exists j: \sum_{j=1}^p |\alpha_j| \neq 0\  \wedge \sum_{j=1}^p \alpha_jv_j =0 .
        $$
        
        Let $k$ be the index where $a_k\neq 0$. In the equation above, we subtract all the terms except $a_kv_k$ to the other side, and get
        
        $$
        a_kv_k=-\sum_{j=1,j\neq k}^p \alpha_jv_j.
        $$
        
        Let $\beta_j=-\frac{\alpha_j}{a_k}$ and divide both sides by $a_k$, and we get 
        
        $$
        v_k=\sum_{j=1,j\neq k}^p \beta_jv_j
        $$
        
        as desired. The right side of the equation is the additive inverse of $v_k$, and thus 
        
        $$
        v_k-\sum_{j=1,j \neq k}^p \beta_jv_j=0,
        $$
        
        giving us the nontrivial linear combination for $0$. $\blacksquare$
        
    - Proposition: *A system of vectors $v_1,v_2, ... \ , v_n \in V$ is a basis iff it is linearly independent and generating.*
    - *Proof.*
        
        Suppose a system $v_1, v_2, ... \ , v_n$  is linearly independent and generating. Suppose there is an arbitrary vector $v \in V$. Since the system of vectors is generating, we can write $v$  as a linear combination
        
        $$
        v=\sum_{k=1}^n\alpha_kv_k.
        $$
        
        We must show that this linear combination is unique for the system to be a basis. Suppose there is another linear combination for $v$:
        
        $$
        v= \sum_{k=1}^n \beta_kv_k.
        $$
        
        We subtract the second equation from the first, and obtain
        
        $$
        \sum_{k=1}^n \alpha_kv_k - \sum_{k=1}^n \beta_kv_k =\sum_{k=1}^n(\alpha_k-\beta_k)v_k = v-v=0
        $$
        
        Since the system is linearly independent, $\alpha_k-\beta_k=0 \ \forall k$, and thus $v=\sum_{k=1}^n\alpha_kv_k$ is unique. $\blacksquare$
        
    - Proposition: *Any finite generating system contains a basis.*
    - *Proof.*
        
        Suppose $v_1,v_2,... \ ,v_p \in V$ is a generating set of vectors. If it is linearly independent, it is a basis and we are done. Suppose the system is not linearly independent. Then, there exists a vector $v_k$ that can be represented by a linear combination of vectors $v_j, j \neq k$. This implies any linear combination of vectors $v_1, v_2, ... \ , v_p$ can be represented as a linear combination of the vectors $v_j, 1 \leq j \leq p, j\neq k.$ Therefore, if $v_k$ is deleted, the new system is still a generating one. One can continue this process finitely many times until the system is linearly independent. $\blacksquare$
        
    - Exercises
        
        ![Screen Shot 2022-03-28 at 10.43.03 PM.png](Vector%20Spaces%2075017d01ddce48a5ac078bb8bb1d099e/Screen_Shot_2022-03-28_at_10.43.03_PM.png)
        
        *Proof.*
        
        Take a vector $v_{r+1}$ that cannot be represented by a linear combination of the system of vectors $v_1,v_2,\ldots,v_r$. Suppose that the system $v_1,v_2,\ldots,v_r,v_{r+1}$is linearly dependent. This means that 
        
        $$
        \sum_{k=1}^{r+1}|\alpha_k|\neq 0 \ \wedge \sum_{k=1}^{r+1}\alpha_k v_k=0.
        $$
        
        If $\alpha_{r+1}=0$, then $\sum_{k=1}^r|\alpha_k|\neq0$, contradicting how the system $v_1,v_2,\ldots,v_r$ is linearly independent, implying $\alpha_{r+1}\neq0$. Then, $\alpha_{r+1}$ can be represented as 
        
        $$
        v_{r+1}=-\frac{1}{\alpha_{r+1}}\sum_{k=1}^r\alpha_kv_k.
        $$
        
        This contradicts how $v_{r+1}$  cannot be represented as a linear combination of vectors $v_1,v_2,\ldots,v_r$, and thus the system $v_1,v_2,\ldots,v_r,v_{r+1}$ is linearly independent. $\blacksquare$
        

### **Linear Transformations:**

- Let $V,W$ be vector spaces over the same field $\mathbb{F}$. A linear transformation $T:V\to W$ is one which follows the properties:
    1. $T(v+u)=T(v)+T(u)\ \forall v,u \in V$.
    2. $T(\alpha v) = \alpha T(v) \ \forall v\in v$ and all scalars $\alpha \in \mathbb{F}$.
    - These properties combine into one property called linearity.
    
    $$
    T(\alpha v+\beta u)=\alpha T(v)+\beta T(u) \ \forall v,u \in V \ \wedge \forall\alpha, \beta \in \mathbb{F}
    $$
    
    - Examples:
        - Differentiation
            
            ![Screen Shot 2022-03-29 at 9.30.30 AM.png](Vector%20Spaces%2075017d01ddce48a5ac078bb8bb1d099e/Screen_Shot_2022-03-29_at_9.30.30_AM.png)
            
        - Rotation and Reflection
            
            ![Screen Shot 2022-03-29 at 9.31.28 AM.png](Vector%20Spaces%2075017d01ddce48a5ac078bb8bb1d099e/Screen_Shot_2022-03-29_at_9.31.28_AM.png)
            
            Any linear transformation $T: \mathbb{R} \to \mathbb{R}$ is just a multiplication by a constant.
            
- A linear transformation $T:\mathbb{F}^n \to \mathbb{F}^m$ can be represented as multiplication by a matrix (not a scalar), and is completely defined by how it acts on the standard basis of $\mathbb{F}^n$.
    - Consider the basis $e_1,e_2,\ldots, e_n$ of $\mathbb{F}^n$. Applying the transformation $T$, we see we have $n$ vectors $a_1:=T(e_1),a_2:=T(e_2),\ldots,a_n:=T(e_n)$ in $\mathbb{F}^m$.
        
        Let $\vec x=\begin{pmatrix} x_1 \ x_2 \cdots x_n \end{pmatrix}^T$(some arbitrary vector such that $x\in \mathbb{F}^n$). Then $\vec x$ can be represented by some linear combination $\vec x=\sum_{k=1}^nx_ke_k,$ and 
        
        $$
        T(\vec x)=T(\sum_{k=1}^nx_ke_k)=\sum_{k=1}^nT(x_ke_k)=\sum_{k=1}^nx_kT(e_k)=\sum_{k=1}^nx_ka_k.
        $$
        
        We can now join all the vectors $a_1,a_2,\ldots,a_n$ into a matrix $A=[a_1,a_2,\ldots,a_n]$ where $a_k$ is the $k$th column of $A$. Thus, we can represent a linear transformation $T:\mathbb{F}^n \to \mathbb{F}^m$ through matrix multiplication. 
        
        $$
        T(\vec x)=A\vec x = \sum_{k=1}^nx_ka_k\\=x_1 \begin{pmatrix} a_{1,1} \\ a_{2,1} \\ \vdots \\ a_{m,1} \end{pmatrix} +x_2 \begin{pmatrix} a_{1,2} \\ a_{2,2} \\ \vdots \\ a_{m,2} \end{pmatrix} +\ldots +x_n \begin{pmatrix} a_{1,n} \\ a_{2,n} \\ \vdots \\ a_{m,n} \end{pmatrix} \\ = \sum_{k=1}^na_{j,k}x_k,\ j=1,2,\ldots,n.
        $$
        
    - One does not need to only consider the standard basis, they can consider any basis or even any generating set.
        - A linear transformation $T:V \to W$ is completely defined by its values on a generating set of $V$.
        - If $v_1,v_2,\ldots,v_n$ is a generating set in $V$, and $T$  and $T_1$ are linear transformations $T,T_1:V\to W$ such that $T(v_k)=T_1(v_k)$, $k=1,2,\ldots,n$, then $T=T_1$.
        - *Proof.*
            
            Suppose there are two linear transformations $T,T_1:V\to W$ that act on a generating set $v_1,v_2,\ldots,v_n$ in $V$, and also suppose $T(v_k)=T_1(v_k),\ k=1,2,\ldots,n$. Consider an arbitrary vector $\vec u \in V$ . Then $\vec u$ can be represented by a linear combination $\vec u = \sum_{k=1}^n\alpha_kv_k$ for any scalar $\alpha_k$ since the system is generating. Then,
            
            $$
            T(\vec u)=T(\sum_{k=1}^n\alpha_kv_k)=\sum_{k=1}^n\alpha_kT(v_k)=\sum_{k=1}^n\alpha_kT_1(v_k)=T_1(\sum_{k=1}^n\alpha_kv_k)=T_1(\vec u)\ \forall \vec u\in V.
            $$
            
            Hence, $T=T_1$ and the proof is complete. $\blacksquare$
            
    - The matrix of a linear transformation $T:\mathbb{F}^n \to \mathbb{F}^m$ is found by joining the column vectors $a_k=T(e_k)$, where $e_1,e_2,\ldots,e_n$ is the standard basis of $\mathbb{F}^n$.
    - The linear transformation of a vector $x$ is given by $T(x)=Ax$, where $A$ is the matrix of the linear transformation. We usually do not distinguish between the two when there is no confusion, and $Tx$ can be written instead of $T(x)$, omitting the parentheses.
    - A vector in $\mathbb{F}^n$ can only be multiplied with an $m \times n$ matrix, since there is going to be 1 column for each vector in the standard basis, which has the size $n$.
    - Exercises:
        
        ![Screen Shot 2022-03-30 at 11.32.19 AM.png](Vector%20Spaces%2075017d01ddce48a5ac078bb8bb1d099e/Screen_Shot_2022-03-30_at_11.32.19_AM.png)
        
        Let $T:\mathbb{R}^2 \to \mathbb{R}^2$ be a linear transformation, such that $T(x_1,x_2)^T=(x_2,x_1)^T$. Then, we can find the matrix representing this transformation by a linear combination of $\mathbb{R}^2$’s standard basis.
        
        $$
        e_1=\begin{pmatrix} 1 \\ 0\end{pmatrix}, e_2=\begin{pmatrix} 0 \\ 1\end{pmatrix} \implies T(x_1,x_2)^T=\begin{pmatrix} x_2 \\ x_1 \end{pmatrix}\\ = \sum_{k=1}^2x_kTe_k=\begin{pmatrix} 0\ \  1 \\ 1\ \  0 \end{pmatrix}.
        $$
        
        **Find the matrix of $T$:**
        
        ![Screen Shot 2022-03-30 at 11.49.47 AM.png](Vector%20Spaces%2075017d01ddce48a5ac078bb8bb1d099e/Screen_Shot_2022-03-30_at_11.49.47_AM.png)
        
        Consider the standard basis of $\mathbb{P}^n$: $1,t,t^2,\ldots,t^n$, and let $e_k=t^k\begin{pmatrix}0 \\ 0 \\ \vdots \\ 1 \\ \vdots \\ 0 \end{pmatrix}$, with the 1 at the $k$th entry. Then, 
        
        $$
        Tf(t)=f'(t)=\sum_{k=0}^nTe_k=\sum_{k=0}^nkt^{k-1}e_k\\=1\begin{pmatrix} 0 \\ 1 \\0 \\\vdots \\ 0 \end{pmatrix}+t\begin{pmatrix} 0 \\ 0\\2 \\ \vdots \\ 0 \end{pmatrix} +\ldots+t^{n-2}\begin{pmatrix} 0 \\ 0 \\ \vdots \\ n-1\\0 \end{pmatrix}+t^{n-1} \begin{pmatrix} 0 \\ 0 \\ 0 \\ \vdots \\ n \end{pmatrix}+t^n\begin{pmatrix} 0 \\ 0 \\ \vdots \\ 0 \\0 \end{pmatrix}\\
        $$
        
        ![Screen Shot 2022-03-30 at 12.31.49 PM.png](Vector%20Spaces%2075017d01ddce48a5ac078bb8bb1d099e/Screen_Shot_2022-03-30_at_12.31.49_PM.png)
        
        **c)**
        
        ![Screen Shot 2022-03-30 at 12.32.58 PM.png](Vector%20Spaces%2075017d01ddce48a5ac078bb8bb1d099e/Screen_Shot_2022-03-30_at_12.32.58_PM.png)
        
        Let $T:\mathbb{R}^3 \to \mathbb{R}^3$  be a linear transformation such that if $\vec x=(x_1,x_2,x_3)^T$ is a vector,  $T\vec x$ rotates $\vec x$ 30 degrees about the origin in the $xy$ plane. We notice that through a geometric argument the standard basis vectors in $\mathbb{R}^3$ are mapped as follows:
        
        $$
        \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix} \mapsto \begin{pmatrix} \frac{\sqrt 3}{2} \\ \frac{1}{2} \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix} \mapsto \begin{pmatrix} \frac{1}{2} \\ \frac{\sqrt 3}{2} \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix} \mapsto \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}.
        $$
        
        Combining these vectors $Te_k,\  k=1,2,3$ into a matrix, we get
        
        $$
        A=\begin{pmatrix} \frac{\sqrt 3}{2} \ \ \frac{1}{2} \ \ 0 \\ \           \frac{1}{2} \ \frac{\sqrt 3}{2} \  0 \\ \  0\ \ \ 0\ \ \ 1 \end{pmatrix}.
        $$
        
        ![Screen Shot 2022-03-30 at 4.58.32 PM.png](Vector%20Spaces%2075017d01ddce48a5ac078bb8bb1d099e/Screen_Shot_2022-03-30_at_4.58.32_PM.png)
        
        *Proof.*
        
        Suppose $A:\mathbb{F}\to \mathbb{F}$ is a linear transformation. Since $z$ is the center of the closed interval $[x,y]$, this means that $z=\frac{x+y}{2}$. We must show that $Az= \frac{Ax+Ay}{2}$. By the properties of a linear transformation,
        
        $$
        Az=A(\frac{x+y}{2})=\frac{1}{2}A(x+y)=\frac{1}{2}(Ax+Ay)=\frac{Ax+Ay}{2}.
        $$
        
        Hence, $Az$ is the center of the interval of $[Ax,Ay]$ and the proof is complete. $\blacksquare$
        

### Linear Transformations as Vector Spaces:

- The sum of two linear transformations is also a linear transformation.
- Let $\mathcal{L}(V,W)$ denote the collection of linear transformations $T:V\to W$.
    - We can define two operations: multiplication by a scalar and addition on $\mathcal{L}(V,W)$, it can be seen that $\mathcal{L}(V,W)$ satisfies the axioms of a vector space.
    - Consider a linear transformation $T:\mathbb{F}^n \to \mathbb{F}^m$. Since any linear operation on $T$ corresponds to the same operation on its corresponding matrix, and a set of $m \times n$ matrices is a vector space, $\mathcal{L}(V,W)$ is also a vector space.

### Matrix Multiplication:

- Let $A, B$ be matrices. Then $AB$ is the product of the two matrices and can be computed by

$$
(AB)_{j,k}=(\text{row}\ \#j\ \text{of}\ A) \cdot(\text{column} \ \#k \ \text{of}\ B)\\= \sum_la_{j,l}b_{l,k}.
$$

- This product is only defined if $A$  is an $m\times n$ matrix and $B$ is an $n \times r$ matrix. $AB$ will be a $m \times r$ matrix.
    - This follows naturally by considering the composition of two linear transformations. Suppose $T_1:\mathbb{F}^n \to \mathbb{F}^m$ and $T_2:\mathbb{F}^r \to \mathbb{F}^n$ are two linear transformations, and        $T=T_1 \circ T_2$. Then, one can easily see that $T=T_1(T_2(x)) \ \forall x \in \mathbb{F}^r$ will be a mapping $T:\mathbb{F}^r \to \mathbb{F}^m$. We can also write $T_1T_2$ instead of $T_1 \circ T_2$.
- Matrix multiplication properties:
    1. Associativity: $(AB)C=A(BC)$ provided that either the left or right side is well defined.
    2. Distributivity: $A(B+C)=AB+AC$, $(A+B)C=AB+BC$ provided that either the left or right side is well defined.
    3. Scalar Multiples: $A(\alpha B)=(\alpha A)B=\alpha (AB)=\alpha AB$.
    4. Matrix multiplication is not commutative.

### Matrix Transposition:

- The matrix transpose is defined as follows: for a matrix $A,$

$$
[A^T]_{j,k}=[A]_{k,j}\ \text{or}\ A^T\ \text{is just A with the rows and columns swapped around}.
$$

- $(AB)^T=B^TA^T$.

### Trace:

- For an $n\times n$ square matrix $A=(a_{j,k})$, its trace is defined by:

$$
\text{trace}\ A=\sum_{k=1}^na_{k,k}.
$$

- For two matrices $A$  and $B$ of size $m\times n$ and $n \times m$ respectively,                     $\text{trace}  (AB)= \text{trace} (BA)$.

- *Proof.*
    
    Consider the product of $AB$ first. According to the row by column rule for matrices, this is equivalent to:
    
    $$
    [AB]_{jk}=\sum_{l=1}^ma_{jl}b_{lk} \implies \text{trace} (AB)=\text{trace}(\sum_{l=1}^ma_{jl}b_{lk})\\=\sum_{p=1}^m(\sum_{l=1}^ma_{jl}b_{lk})=\sum_{p=1}^m(\sum_{l=1}^ma_{jl}b_{lk})_{p,p}=\sum_{p=1}^m\sum_{l=1}^ma_{pl}b_{lp}\\=\sum_{l=1}^m\sum_{p=1}^ma_{pl}b_{lp}.\ \text{Renaming the dummy variables,} \ \\=\sum_{p=1}^m\sum_{l=1}^ma_{lp}b_{pl}=\sum_{p=1}^m\sum_{l=1}^mb_{pl}a_{lp}
    $$
    
    Now consider the product $BA$.
    
    $$
    [BA]_{jk}=\sum_{l=1}^mb_{jl}a_{lk} \implies \text{trace}(BA)=\text{trace}(\sum_{l=1}^mb_{jl}a_{lk})\\=\sum_{p=1}^m(\sum_{l=1}^mb_{jl}a_{lk})_{p,p}=\sum_{p=1}^m\sum_{l=1}^mb_{pl}a_{lp}=\text{trace}(AB)
    $$
    
    Thus, $Tr(AB)=Tr(BA)$ and the proof is complete. $\blacksquare$
    

### Invertibility and Isomorphisms:

- We define the identity transformation (matrix) $I=I_V:V \to V$ such that $Ix=x \ \forall x \in V$.
    - This matrix is always an $n \times n$ square matrix with entries $1$ along the main diagonal and $0$ everywhere else.
    - For any arbitrary linear transformation $A$, $AI=A \wedge IA=A$, whenever the product is defined.
- Let $T:V \to W$ be a linear transformation. $T$ is called left invertible if $\exists A:W \to V$ such that $AT=I , I=I_V$.
    - Similarly, $T$ is right invertible if $\exists B:W \to V$ such that $TB=I, I=I_W$. $A$  is the left inverse of $T$ and $B$ is called the right inverse of $T$. The left/right inverses here are not necessarily unique.
    - A linear transformation $T:V \to W$ is called invertible if it has both a left and right inverse.
    - A linear transformation $A:V \to W$ is invertible if its left and right inverses $B$ and $C$ are unique and coincide.
    - *Proof.*
        
        Let $BA=I$ and $AC=I$. Then $BAC=B(AC)=BI=B$, and $(BA)C=IC=C$, so $B=C$. Suppose there is another linear transformation $B_1: B_1A=I$. Using the same reasoning, $B_1=C$, and $B$ is unique. Also suppose that there is a linear transformation $C_1:AC_1=I$. Then $C_1=B$ and thus $C_1$ is unique, and the proof is complete. $\blacksquare$
        
    - **Corollary.** A transformation $A:V\to W$ is invertible if and only if there exists a unique linear transformation (denoted $A^{-1}$), $A^{-1}:W\to V$  such that $AA^{-1}=I_V \wedge A^{-1}A=I_W$.
- A matrix is invertible if its corresponding linear transformation is invertible.
    - An invertible matrix must be square.
    - If linear transformations $A$ and $B$ are invertible, then $AB$ is invertible and
    $(AB)^{-1}=B^{-1}A^{-1}$.
    - *Proof.*
        
        The products $(AB)(B^{-1}A^{-1})=I$ and $(B^{-1}A^{-1})(AB)=I$ shows that $AB$ is invertible and the inverse is $(AB)^{-1}=B^{-1}A^{-1}$. $\blacksquare$
        
    - The invertibility of a product of two matrices does not necessarily imply invertibility of the two matrices, since they are not required to be square matrices.
        - If one of matrices is invertible however, then the other is also invertible.
- If a matrix $A$ is invertible, then $A^T$ is also invertible and $(A^T)^{-1}=(A^{-1})^T$.
    - *Proof.*
        
        Using $(AB)^T=B^TA^T$, we see that 
        
        $$
        A^T(A^{-1})^T=(A^{-1}A)^T=I^T=I\\ (A^{-1})^TA^T=(AA^{-1})^T=I^T=I.
        $$
        
        Thus, $A^T$ is invertible and the proof is complete. $\blacksquare$
        
- If $A$ is invertible, then $A^{-1}$  is also invertible and $(A^{-1})^{-1}=A$.
- An invertible linear transformation $T:V \to W$ is called an **isomorphism**.
    - Two vector spaces $V,W$ are called isomorphic ($V \cong W$) if there is an isomorphism $A:V\to W$.
    - Two isomorphic spaces are essentially the same, with all properties involving vector space operations being preserved under isomorphism.
    - Let $A:V\to W$ be an isomorphism, and let $\{v_1,v_2,\ldots,v_n\}$ be a basis in $V$. Then $\{Av_1,Av_2,\ldots,Av_n\}$ is a basis in $W$. The converse also holds. This statement also holds if one replaces the “basis” with “linearly independent”, “generating”, or “linearly independent”.
    - *Proof.*
        
        Consider the basis $\{v_1,v_2,\ldots,v_n\}$ in $V$. Then this set of vectors is generating and linearly independent. We will first show that $\{Av_1,Av_2,\ldots,Av_n\}$ is generating in $W$. Notice that since $\{v_1,v_2,\ldots,v_n\}$ is generating, any vector $\vec v \in V$ can be expressed as a linear combination of them. Consider an arbitrary vector $\vec u\in W$. Then
        
        $$
        \vec v=\sum_{k=1}^n \alpha_kv_k \implies A\vec v=\vec u=A(\sum_{k=1}^n \alpha_kv_k)=\sum_{k=1}^n\alpha_kAv_k,\forall \vec u \in W.
        $$
        
        Thus, $\{Av_1,Av_2,\ldots,Av_n\}$ is generating in $W$. Now we will prove that it is also linearly independent. We must show that $\sum_{j=1}^n\beta_jAv_j=0 \implies \sum_{j=1}^n|\beta_j|=0$. Suppose $\sum_{j=1}^n\beta_jAv_j=0$. Then,
        
        $$
        \sum_{j=1}^n\beta_jAv_j=A(\sum_{j=1}^n\beta_jv_j)=A(0)=0 \\ \implies (A^{-1}A)(\sum_{j=1}^n\beta_jv_j)=A^{-1}0=0 \\ \implies \sum_{j=1}^n \beta_jv_j=0 \implies \sum_{j=1}^n|\beta_j|=0,
        $$
        
        since $\{v_1,v_2,\ldots,v_n\}$ is linearly independent in $V$ and $A$ is invertible. Thus, $\{Av_1,Av_2,\ldots,Av_n\}$ is a basis in $W$ and the proof is complete.
        
    - If $A :V \to W$ is an isomorphism, then $A^{-1}:W \to V$ is also an isomorphism.
    - Let $A:V\to W$ be a linear map, and let $\{v_1,v_2,\ldots,v_n\}$ and $\{w_1,w_2,\ldots,w_n\}$ be bases in $V$ and $W$ respectively. If $Av_k=w_k,k=1,2,\ldots,n$ then $A$ is an isomorphism.
- Let $A:X\to Y$ be a linear transformation. Then $A$  is invertible iff for any $b \in Y$, the equation $Ax=b$ has a unique solution $x \in X$.
- *Proof.*
    
    Suppose $A$  is invertible. Then $x=A^{-1}b$ solves $Ax=b$. Suppose there is another vector $x_1\in X$ such that $Ax_1=b$. Then $x_1=A^{-1}b=x$ and thus this solution is unique. Now, we must show that $A$ is invertible if $Ax=b$ has a unique solution $x\in X, \forall b \in Y$. Suppose the equation $Ax=y$ (denoting $b$ as $y$) has a unique solution $x \in X$, which we will call $B(y)$. Then $B(y)$ is defined for all $y \in Y$, so $B$ is a transformation $B:Y\to X$.
    
    ![Screen Shot 2022-04-02 at 6.33.05 PM.png](Vector%20Spaces%2075017d01ddce48a5ac078bb8bb1d099e/Screen_Shot_2022-04-02_at_6.33.05_PM.png)
    
    Consider an arbitrary $x\in X$, and let $y=Ax$. By the definition of $B$, we have $x=By$. Then,
    
    $$
    BAx=By=x, \text{so}\ BA=I.
    $$
    
    Similarly, 
    
    $$
    ABy=Ax=y, \text{so} \ AB=I
    $$
    
    and thus $B$ is the inverse of $A$. $\blacksquare$ 
    
- An $m\times n$ matrix (of a linear transformation $T:\mathbb{F}^n \to \mathbb{F}^m$) is invertible iff its columns form a basis in $\mathbb{F}^m$.
- Let $A$ be an $n \times n$ matrix. If $A^2=0$, then $A$ is not invertible.
- *Proof.*
    
    Suppose the $n \times n$ matrix $A$   is invertible. Then, there exists a matrix $A^{-1}$ such that $AA^{-1}=I$. Then,
    
    $$
    A(AA^{-1})=AI=A\\ \text{and} \\ (AA)A^{-1}=A^2A^{-1} =0A^{-1}=0\\ \implies A=0.
    $$
    
    However, the $0$ matrix is not invertible since there is no way to multiply it by another matrix to result in the identity matrix $I$, contradicting the assumption that $A$ is invertible. Thus, $A$ must not be invertible if $A^2=0$.
    

### Subspaces:

- A subspace of a vector space $V$ is a nonempty subset $V_0 \sub V$, which is closed under vector addition and multiplication by scalars. In other words,
    1. If $v\in V_0$, then $\alpha v \in V_0$ for all scalars $\alpha$.
    2. If $v,w \in V_0,$ then $(v+w) \in V_0$.
    - Or, one could write $\alpha u + \beta v \in V_0, \forall u,v \in V_0$  and all scalars $\alpha, \beta$.
- A subspace of $V$ equipped with the operations from $V$ is also a vector space.
    - The trivial subspaces, which are $V$ itself and $\{0\}$.
    - For a linear transformation $A:V \to W$, there are two different special subspaces
        - The null space or kernel of $A$, denoted $\ker A$ contains all the vectors $v \in V$ such that $Av=0$.
        - The column space denoted $\text{Col} \ A$ is defined to be the set of all vectors $w \in W$ that can be represented as $w=Av$ for some $v \in V$. In other words, it is the space of all vectors that can be represented as some linear combination of the columns of matrix $A$.
        - Given a system of vectors $v_1,v_2,\ldots,v_r \in V$ its linear span $\mathcal{L}\{v_1,v_2,\ldots v_r\}$ is the collection of all vectors $\vec v \in V$ that can be represented as a linear combination $\vec v = \sum_{k=1}^r \alpha _k v_k$. The notation $\text{span} \{v_1,v_2,\ldots,v_r\}$ is also used instead of $\mathcal{L}\{v_1,v_2,\ldots,v_r\}$.
- Exercises:
    
    Suppose $X$ and $Y$ are subspaces of a vector space $V$. Then, $X \cap Y$ is also a subspace of $V$.
    
    *Proof.*
    
    Since $X$ and $Y$ are subspaces of $V$, $\alpha u + \beta v \in X, \forall u,v \in X$ and all scalars $\alpha, \beta$, and $\alpha_0 u_0 + \beta_0 v_0 \in Y, \forall u_0,v_0 \in Y$ and all scalars $\alpha_0, \beta_0$. Consider an arbitrary vector $w \in X$ and another vector $\sigma \in Y$. Then, $w+\sigma \in X \cap Y$ since the definition of intersection implies that $w \in X,Y \wedge \sigma \in X,Y$ and since $X$  and $Y$ are subspaces of themselves, $w+\sigma \in X \cap Y$. Furthermore, $cw \in X \cap Y$ for an arbitrary constant $c$ since $w \in X,Y$ and since both $X$ and $Y$ are subspaces of themselves, $cw \in X \cap Y$. Thus, $X \cap Y$ is also a subspace of $V$. $\blacksquare$
    
    ![Screen Shot 2022-04-05 at 10.44.34 AM.png](Vector%20Spaces%2075017d01ddce48a5ac078bb8bb1d099e/Screen_Shot_2022-04-05_at_10.44.34_AM.png)
    
    *Proof.*
    
    Consider a subspace $X$ of a vector space $V$. Then $X$ is closed under addition and multiplication. Consider a vector $v\in V, v \notin X$, and another vector $x \in X$. Assume that $x+v \in X$. Since any subspace of $V$ is also a vector space, any vector in $X$ has an additive inverse. Then, $(x+v)+(-x) \in X$, since $X$ is closed under addition. Simplifying, we obtain $v \in X$, contradicting the fact that $v \notin X$. Hence, $x +v \notin X$ and the proof is complete. $\blacksquare$
    

### Kronecker Delta:

- The Kronecker Delta is a function of two variables defined as:

$$
\delta_{ij}=\begin{cases} 0 & \text{if $ i \neq j$} \\ 1 & \text{if $i=j$} \end{cases}.
$$

- It satisfies the following properties:
    - $I_{ij}=\delta_{ij},$ the entries of the identity matrix are equal to the kronecker delta.
    - $\sum_j\delta_{ij}a_j=a_i$.
    - $\sum_ia_i\delta_{ij}=a_j$.
    - $\sum_k\delta_{ik}\delta_{kj}=\delta_{ij}.$

### Linear Functionals and Dual Spaces:

- Let $V$ be a vector space over a scalar field $\mathbb F$. Any linear transformation $T:V \to \mathbb F$ is called a linear functional on $V$.
    - The trace operator is a linear functional on the matrix space $F^{n \times n}$
    - The integral is also a linear functional on $C([a,b])$, the set of continuous functions on the closed interval $[a,b]$.
- The set of all linear functionals on $V$ denoted $V^*=\mathcal{L}(V, \mathbb{F})$ is a vector space. This is known as the dual space of $V
.$
    - Let $\beta :=\{\alpha_1,\ldots,\alpha_n\}$ be a basis in $V$. Then, there exists a unique linear functional $f_i$ such that $f_i(\alpha_j)=\delta_{ij}, \forall i \in \mathbb{N}:1\le i \le n$. Thus, we have $n$ distinct linear functionals $f_1,\ldots, f_n$.
        - These functionals are linearly independent. Consider the linear combination
        
        $$
        f=\sum_{i=1}^nc_if_i.
        $$
        
        Then, we can see that 
        
        $$
        f(a_j)=\sum_{i=1}^nc_if_i(a_j) = \sum_{i=1}^nc_i\delta_{ij}=c_j.
        $$
        
        If we assume that $f$ is the $0$ functional, we know that $f(a_j)=0, \forall j \in \mathbb{N}: 1 \le j \le n$, we have that every scalar $c_j$ for all $j$ is equal to $0$, and hence $f_1,\ldots,f_n$ is linearly independent.
        
        - These functionals are generating and form a basis in $V^*$. We denote this set by $\beta^*:=\{f_1,\ldots,f_n\}$, and we call it the dual basis of $\beta$.