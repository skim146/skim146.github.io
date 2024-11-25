---
layout: posts
title: Systems of Linear Equations
comments: false
author_profile: true
classes: wide
permalink: /system/
---

### Solving Systems of Linear Equations:

- Gauss-Jordan Elimination
    1. Row exchange: interchange two rows of the matrix.
    2. Scaling: multiply a row by a non-zero scalar a.
    3. Row replacement: replace a row $$\#k$$ by its sum with a constant multiple of a row $$\#j$$; all other rows remain intact.
    - Does not affect the solutions of the system; each row operation can be written as a special invertible matrix $$E$$:
    
    $$
    Ax=b\\ EAx = Eb \\E^{-1}EAx=E^{-1}Eb
    $$
    
    - From this, it is easy to see that any solution to the equation $$Ax=b$$ is also a solution to $$EAx=Eb$$, and that equation’s solutions are also contained in the set of elements that satisfy $$Ax=b$$. Thus, row replacement does not have any effect on the solutions of a system.
- To solve a system using an augmented matrix;
    1. Find the leftmost non-zero column of the matrix.
    2. Make sure, by applying row operations of type 1 (row exchange), if necessary, that the first (the upper) entry of this column is non-zero. This entry will be called the pivot entry or simply the pivot.
    3. Make all non-zero entries zero below the pivot by adding an appropriate multiple of the first row from the rows number $$2,3,\ldots,m$$.
- Pivot entries are the leftmost nonzero entry in a row.
- A matrix is said to be in echelon form if it satisfies the following:
    1. All zero rows are below all non-zero entries.
    2. For any non-zero row its pivot entry is strictly to the right of the pivot entry in the previous row.
- A matrix is in reduced echelon form if it is in echelon form and also satisfies the following:
    1. All pivot entries are equal 1.
    2. All entries above the pivots are 0.

### Pivots (In Detail):

- A system is inconsistent iff it has a pivot in the last column of the augmented matrix.
    - i.e. $$(0 \ 0 \ 0 \cdots 0\ |\ b), \ b\neq 0$$.
    - If we have a $$0$$ row in the echelon form of the coefficient matrix $$A$$ (which we will denote $$A_e$$, then we can always choose a $$b$$ such that $$A_ex=b$$ does not have a solution.
    - *Proof.*
        
        $$A_e$$ is just the product of two matrices $$A$$ and $$E$$ such that $$A_e=EA$$, where $$E$$ is just a product of the elementary row operation matrices, which are invertible (implying $$E$$ is also invertible). Since $$A_e$$ has a $$0$$ row, the last row of $$A_e$$ will also be a $$0$$ row. Choosing $$b_e=(0, \cdots ,0,1)^T$$, we can see that $$A_ex=EAx=b_e$$  is inconsistent. Then,
        
        $$
        E^{-1}EAx=E^{-1}b_e \\ Ax=E^{-1}b_e,
        $$
        
        and thus the equation $$Ax=E^{-1}b_e$$ also does not have any solutions. $$\blacksquare$$
        
- A solution of a system is unique (if it exists) iff there are no free variables in the coefficient matrix. In other words, the coefficient matrix in echelon form has a pivot in each column.
- An equation $$Ax=b$$ is consistent (has at least one solution) for all right sides $$b$$ iff the echelon form of the coefficient matrix has a pivot in every row.
    - If theres a pivot in each row of the coefficient matrix, there is no room for there to be a pivot in any row in the augmented matrix, which is the only way for the system to be inconsistent. Hence, this implies that at least one solution exists. $$\blacksquare$$
- An equation $$Ax=b$$ has a unique solution for any right side $$b$$ iff the echelon form of the coefficient matrix $$A$$ has a pivot in every column and row.
    - Since $$A$$ has a pivot in each row of the coefficient matrix, $$A$$ is consistent. Furthermore, $$A$$ has no free variables since it has a pivot in each column, and so $$A$$ has a unique solution. $$\blacksquare$$
- In echelon any row and column have no more than 1 pivot.
    - However, it can have 0 pivots.
- Let us have a system of vectors $$v_1, v_2, \ldots, v_m \in \mathbb{F}^n$$, and let $$A=[v_1 \ v_2 \ \cdots \ v_m]$$ be an $$n \times m$$ matrix with columns $$v_1, v_2, \ldots, v_m$$. Then
    1. The system $$v_1, v_2, \ldots, v_m$$ is linearly independent iff the echelon form of $$A$$ has a pivot in every column.
        - *Proof.*
            
            Since the matrix $$A$$ has a pivot in every column, the equation $$x_1v_1+x_2v_2+\cdots+x_mv_m=b,\ b \in \mathbb{F}^n$$ has a unique solution for each $$b$$. Setting $$b:=0$$, we see that the linear combination $$\sum_{i=1}^mx_i v_i, \ x_1=x_2=\cdots=x_m=0$$ will be the only linear combination that equals zero. Hence, the system of vectors is linearly independent. $$\blacksquare$$ 
            
    2. The system $$v_1, v_2, \ldots, v_m$$ is generating in $$\mathbb{F}^n$$ iff the echelon form of $$A$$ has a pivot in every row.
        - *Proof.*
            
            Since $$A$$ has a pivot in each row, the equation $$Ax=b, \ b \in \mathbb{F}^n$$ is consistent for any $$b \in \mathbb{F}^n$$. Thus the system is generating since any element in $$\mathbb{F}^n$$ can be represented as a linear combination of the system. $$\blacksquare$$
            
    3. The system $$v_1, v_2, \ldots, v_m$$ is a basis in $$\mathbb{F}^n$$ iff echelon form of $$A$$ has a pivot in every column and in every row.
        - The proof is trivial to see from (1.) and (2.).
- Corollaries about linearly independency and bases:
    - Any linearly independent system in $$\mathbb{F}^n$$ cannot have more than $$n$$ vectors.
        - *Proof.*
            
            Suppose a system of vectors $$v_1, v_2, \ldots, v_m \in \mathbb{F}^n$$ is linearly independent. Let $$A=[v_1 \ v_2 \ \cdots\ v_m]$$ be an $$n \times m$$ matrix with columns $$v_1, v_2, \ldots, v_m$$. Suppose $$m>n$$. Then, $$A$$ cannot have a pivot in each column since the number of columns (vectors in the system) is greater than the number of pivots, since the number of pivots cannot be greater than the number of rows of the matrix. $$\blacksquare$$
            
    - Any two bases in a vector space $$V$$ have the same number of vectors in them.
        - *Proof.*
            
            Let $$v_1, v_2, \ldots, v_n$$ and $$w_1,w_2, \ldots,w_m$$ be two different bases in a vector space $$V$$. Assume that $$n\leq m$$. Consider an isomorphism $$A:\mathbb{F}^n \to V$$ defined by $$Ae_k=v_k, \ k=1,2,\ldots,n$$, where $$e_k$$ is the standard basis in $$\mathbb{F}^n$$. Since $$A^{-1}:V \to \mathbb{F}^n$$ is also an isomorphism, the system $$A^{-1}w_1,A^{-1}w_2,\ldots , A^{-1}w_m$$ is a basis in $$\mathbb{F}^n$$. Therefore, the system is linearly independent and since any linearly independent system in $$\mathbb{F}^n$$ cannot have more than $$n$$ vectors, $$m\leq n$$. Since we assumed $$n\leq m$$, $$m$$ must be equal to $$n$$. $$\blacksquare$$
            
    - Any basis in $$\mathbb{F}^n$$  has exactly $$n$$ vectors in it.
        - *Proof.*
            
            Consider the standard basis $$e_k, \ k=1,2,\ldots,n$$ in $$\mathbb{F}^n$$. Since every basis in an a specific vector space has the same number of vectors in them, each basis in $$\mathbb{F}^n$$ has exactly $$n$$ vectors in it. $$\blacksquare$$
            
    - Any generating set in $$\mathbb{F}^n$$ has at least $$n$$ vectors.
        - *Proof.*
            
            Let $$v_1, v_2, \ldots, v_m$$ be a generating system in $$\mathbb{F}^n$$. Consider the $$n \times m$$ matrix $$A= [v_1 \ v_2 \ \cdots\ v_m]$$ with columns $$v_1, v_2, \ldots, v_m$$. Then the echelon form $$A$$ can only have a pivot in every row when $$n \le m$$. Thus, a system can only be generating in $$\mathbb{F}^n$$ if it has at least $$n$$ vectors. $$\blacksquare$$
            
- Corollaries about matrix invertibility:
    - A matrix $$A$$ is invertible iff its echelon form has a pivot in each column and row.
        - (Corollary) An invertible matrix $$A$$ must be square.
        - *Proof.*
            
            Suppose that $$A$$ has a pivot in each column and row. Then there will always be a unique solution to the equation $$Ax=b, \ \forall b$$, and thus $$A$$ is invertible. This proof works both ways. $$\blacksquare$$
            
    - To check the invertibility of an $$n \times n$$  matrix, it is sufficient to check the existence of either the right or left inverse.
        - *Proof.*
            
            Suppose $$A$$  is an $$n \times n$$  square matrix. A matrix $$A$$ is only invertible iff $$Ax=b$$ has a unique solution for any $$b$$, which can only happen if the echelon form of $$A$$ has a pivot in every row and column. Suppose the matrix $$A$$ is left invertible, and $$B$$ is its left inverse. Then, $$Ax=0 \implies BAx=B0 \implies x=0$$, and so the solution is unique, implying that there is a pivot in each column. Since the matrix is square ($$n\times n$$), the echelon form also has pivots in each row, since there are $$n$$ pivots and each row cannot have more than 1 pivot. Now suppose that the matrix is right invertible, and $$C$$ is its right inverse. Suppose $$x=Cb, \ b\in \mathbb{F}^n$$. Then, $$Ax=ACb=Ib=b$$, and so for every $$b$$, $$Ax=b$$ has a solution $$x=Cb$$, implying that the echelon form of $$A$$ has a pivot in each row. Using the same logic as before, $$A$$ has a pivot in each column and row, implying that it is invertible. $$\blacksquare$$
            

### Finding $$A^{-1}$$ by Row Reduction:

- Any invertible $$n\times n$$ matrix $$A$$ is row equivalent to the $$n\times n$$ identity matrix $$I$$.
- To find $$A^{-1}$$, create an augmented $$n\times 2n$$ matrix $$[A\ | \ I]$$, and perform row operations on the matrix until $$A$$ is in rref ($$I$$). The $$I$$ matrix will automatically be transformed into $$A^{-1}$$.
    - If $$A$$ cannot be transformed into $$I$$ through row operations, it is not invertible.
    - Why does this work?
        - Suppose $$A$$ is invertible. Then, we know that there is some product of row operations $$E=E_nE_{n-1}\cdots E_1$$ such that $$EA=I$$, where $$E_1,E_2,\ldots,E_n$$ are elementary matrices. Thus, $$E=A^{-1}$$, and $$[A \ | \ I] \implies [EA \ | \ E ] =[ I  \ | \ E]= [ I \ |  \ A^{-1}]$$.
- Any invertible matrix can be represented as a product of elementary matrices.
    - *Proof.*
        
        Since $$A^{-1}=E=E_nE_{n-1}\cdots E_1$$, then $$A=(A^{-1})^{-1}=E_1^{-1}E_{2}^{-1}\cdots E_n^{-1}.$$ (Using the formula $$(AB)^{-1}=B^{-1}A^{-1} \implies (ABC)^{-1} = C^{-1}B^{-1}A^{-1} \ldots$$).
        

### Dimension:

- The dimension of a vector space $$V$$, denoted $$\dim V$$, is the number of vectors in a basis.
    - A vector space consisting of only the zero vector $$0$$, we say $$\dim V=0$$.
    - If the vector space does not have a finite basis, we say $$\dim V = \infty$$.
    - If $$\dim V$$ is finite, we call $$V$$ a finite-dimensional vector space. We call $$V$$ an infinite-dimensional vector space otherwise.
- A vector space $$V$$ is finite-dimensional iff it has a finite generating system.
    - Any linearly independent system in a finite-dimensional vector space $$V$$ cannot have more than $$\dim V$$ vectors in it.
        - *Proof.*
            
            Let $$v_1,v_2,\ldots,v_m\in V$$ be a system of linearly independent vectors. Let $$A:V \to \mathbb{R}^n$$ be an isomorphism. Then, $$Av_1,Av_2,\ldots,Av_m$$ is a linearly independent system in $$\mathbb{R}^n$$, and since we know that any linearly generating system in $$\mathbb{R}^n$$ cannot have more than $$n$$ vectors in it, $$m \le n$$. $$\blacksquare$$
            
    - Any generating system in a finite-dimensional vector space $$V$$ must have at least $$\dim V$$ vectors in it.
        - *Proof.*
            
            Let $$v_1,v_2,\ldots, v_m \in V$$ be a generating system in $$V$$, and let $$A: V \to \mathbb{R}^n$$ be an isomorphism. Then $$Av_1,Av_2,\ldots,Av_m$$ is a generating system in $$\mathbb{R}^n$$, and since a generating system in $$\mathbb{R}^n$$ has at least $$n$$ vectors in it, $$n \le m$$. $$\blacksquare$$
            
    - A linearly independent system of vectors in a finite-dimensional space can be completed to a basis, i.e. if $$v_1,v_2,\ldots,v_r$$ are linearly independent vectors in a finite-dimensional vector space $$V$$ then one can find vectors $$v_{r+1},v_{r+2},\ldots,v_n$$ such that the system of vectors $$v_1,v_2,\ldots,v_n$$ is a basis in $$V$$.
        - *Proof.*
            
            If $$v_1,v_2,\ldots,v_r$$ is generating, then we are done. If not, let $$n=\dim V$$ . Consider any vector $$v_{r+1} \notin \text{span}\{v_1,v_2,\ldots,v_r\}$$, and add it to the system. This system is still linearly independent. We know that there will always exist a vector we can take since the system is not generating. Continuing this process until the system is generating, we can always complete a linearly independent system into a basis in $$V$$.
            
- Let $$V$$ be a subspace of a vector space $$W$$, $$\dim W< \infty$$. Then $$V$$ is finite dimensional and $$\dim V \le \dim W$$. If $$\dim V = \dim W,$$  then $$V =W$$.
    - *Proof.*
        
        Consider a non-zero vector $$v_1 \in V$$. If $$V= \text{span}\{v_1\}$$, then $$v_1$$ is a basis in $$V$$. If not, we can use induction to continue. Suppose we have constructed $$r$$ linearly independent vectors $$v_1, \ldots, v_r \in V$$. If $$V = \text{span} \{ v_k:1 \le k \le r\}$$, then this is the basis in $$V$$. If not, there exists a vector $$v_{r+1} \in V$$ such that $$v_{r+1} \notin \text{span}\{v_k:1 \le k \le r \}$$ . The system $$v_1,\ldots, v_r, v_{r+1}$$ is also linearly independent, and we can continue this process until we have found a basis in $$V$$. This basis will be the set of vectors $$S_0=\{v_1,\ldots, v_r, \ldots,v_n\}$$. 
        
        Since $$V$$ is a subspace of $$W$$, then $$v_1,\ldots,v_n$$ will be a linearly independent system of vectors in $$W$$. Suppose that $$v_1,\ldots,v_n$$ is not generating in $$W$$. Then, we can complete the linearly independent system into a basis in $$W$$ by adding $$m>0$$ new vectors $$w_i \notin \text{span}\{v_1,\ldots,v_n\}$$. This set of vectors $$S_1=\{v_1,\ldots,v_n,w_1, \ldots, w_m\}$$ will have cardinality $$|S_1|=m+n=\dim W\ge\dim V =n=|S_0|$$. Since $$\dim W$$ is finite dimensional and $$\dim V \le \dim W$$, $$V$$ is finite dimensional.
        
        Now suppose that $$v_1,\ldots,v_n$$ is generating in $$W$$. Then $$m=0$$ and $$|S_1|=\dim W=|S_0|=\dim V=n$$. Assume that $$V \neq W$$, which implies $$\exists u \in W \setminus V$$. Since $$\{v_1,\ldots,v_n\}$$ is a basis in $$V$$, the system of vectors is linearly independent and $$\{v_1,\ldots,v_n,u\}$$ is also linearly independent, since if it was not, then $$u \in V$$ contradicting the assumption that $$V \neq W$$. Since the cardinality of every linearly independent set of vectors in $$W$$ is less than $$\dim W$$, we have $$|\{v_1,\ldots, v_n,u\}|=n+1 \le \dim W$$, but $$\dim W=n \implies n+1 \le n$$, which is a contradiction. Thus, we must have $$V=W$$. $$\blacksquare$$
        
- Exercises
    
    ![Screen Shot 2022-04-10 at 9.24.59 PM.png](Systems%20of%20Linear%20Equations%2062485af08c1746a1a637c55edf6999ca/Screen_Shot_2022-04-10_at_9.24.59_PM.png)
    
    *Proof.*
    
    Let $$V$$ be a vector space such that $$\dim V = n$$, and $$S=\{v_1,\ldots,v_n\} \in V$$ be a set of $$n$$ vectors that are linearly independent in $$V$$. Construct an $$n \times n$$ matrix $$A= [v_1 \ v_2 \ \cdots \ v_n]$$ with each element in $$S$$ as its columns. Suppose the vectors in $$S$$ are linearly independent. This implies that the echelon form of $$A$$ has a pivot in every column. Since $$A$$ is square, there is also a pivot in every row, and the vectors in $$S$$ are generating and form a basis in $$V$$. The same logic holds for if one supposes the vectors in $$S$$ are generating. $$\blacksquare$$
    
    ![Screen Shot 2022-04-10 at 9.35.09 PM.png](Systems%20of%20Linear%20Equations%2062485af08c1746a1a637c55edf6999ca/Screen_Shot_2022-04-10_at_9.35.09_PM.png)
    
    The proof is a direct corollary of (5.2). $$\blacksquare$$
    
    ![Screen Shot 2022-04-10 at 9.35.45 PM.png](Systems%20of%20Linear%20Equations%2062485af08c1746a1a637c55edf6999ca/Screen_Shot_2022-04-10_at_9.35.45_PM.png)
    

### General Solution of a Linear System:

- A system $$Ax=b$$ is homogeneous if $$b=0$$
- Let $$x_1$$ satisfy the equation $$Ax=b$$, and let $$H$$ denote the set of all solutions of the homogeneous system $$Ax=0$$. Then the set $$\{x=x_1+x_h:x_h\in H\}$$ is the set of all solutions of the equation $$Ax=b$$.
    - *Proof.*
        
        Let $$x_1$$ be a solution of the equation $$Ax=b$$. Let a vector $$x_h$$ satisfy $$Ax_h=0$$. Then for $$x=x_1+x_h$$, we have 
        
        $$
        Ax=A(x_1+x_h)=Ax_1+Ax_h=b+0=b.
        $$
        
        Hence, for any vector of the form $$x=x_1+x_h, \ x_h \in H$$ is a solution of the equation $$Ax=b$$. Now let $$x$$ satisfy $$Ax=b$$, then for $$x_h:=x-x_1$$, we have 
        
        $$
        Ax_h=A(x-x_1)=Ax-Ax_1=b-b=0.
        $$
        
        Therefore, $$x_h \in H$$, and any solution $$x$$ of $$Ax=b$$ can be represented as $$x=x_1+x_h$$ with some $$x_h \in H$$. $$\blacksquare$$
        

### Fundamental Subspaces of a Matrix:

- For any linear transformation $$A:V \to W$$, there are four special subspaces.
    - The kernel: $$\ker A:=\{v \in V:Av=0\} \sub V$$
        - The solution set of the homogeneous equation $$Ax=0$$.
    - The range or image: $$\text{Ran} \ A = \text{im} \ A:= \{w \in W : w=Av  \ \text{for some }v \in V\} \sub W$$.
        - The set of all right sides $$b \in W$$ such that $$Ax=b$$  has a solution.
        - Also known as the column space of matrix $$A$$, denoted $$\text{Col} \ A$$.
        - Any vector $$w \in \text{Ran} \ A$$  can be represented by a linear combination of columns of the columns of $$A$$.
    - The left null space: $$\ker A^T$$
    - The row space: $$\text{Ran} \ A^T$$
- The rank of a linear transformation $$A: V \to W$$ is defined to be the dimension of its range:

$$
\text{rank}  \ A := \dim \text{Ran} \ A.
$$

- Let $$A$$ denote the matrix of a linear transformation $$A:V \to W$$, and $$A_e$$ the echelon form of $$A$$.
    - The pivot columns of $$A$$ give us a basis in $$\text{Col} \ A$$.
        - Since the pivot columns of the rref of matrix $$A$$ form a basis in $$\text{Col}( A_{re})$$ (see proof) (where $$A_{re}$$ denotes $$A$$ left multiplied by some product of elementary matrices), the pivot columns in $$A$$ also are a basis in $$\text{Col}(A_{re})$$ since left multiplication by a product of elementary matrices is an isomorphism and preserves linear independence and generating-ness.
            - *Proof.*
                
                Let $$\{v_1,\ldots v_p\}$$ denote the set of column vectors in the pivot columns of the matrix $$A_{re}$$, the rref of an $$m \times n$$ matrix $$A$$. Since all pivot columns of a matrix in rref have entries $$0$$ except an entry $$1$$ in the $$j$$th column, $$\{v_1, \ldots ,v_p \} \subseteq \{e_1, \ldots, e_m\}$$, where $$\{e_1,\ldots, e_m\}$$ denotes the standard basis in $$\mathbb{R}^m$$. Therefore, $$\{v_1, \ldots, v_p\}$$ is a set of linearly independent vectors. 
                
                Now we will prove $$\{v_1, \ldots, v_p\}$$ is generating in $$\text{Col} (A_{re})$$. Let $$w\in \text{Col} (A_{re})$$ be an arbitrary vector. Then, there always exists a vector $$x$$ such that the equation
                
                $$
                w=A_{re}x=\sum_{k=1}^p\alpha_kv_k+\sum_{k=1}^q\beta_ku_k
                $$
                
                has a solution, where $$u_1, \ldots u_q$$ represent the columns which are not pivot columns. Consider the (non-pivot) column $$u_l$$, and assume that it has $$i$$ pivot columns to the right of it. Then, $$u_l$$ can only have non-zero entries above its $$i$$th entry, or else it would be a pivot column. Formally,
                
                $$
                u_l=\begin{pmatrix} u_{1l} \\ u_{2l}\\ \vdots \\ u_{il} \\ 0 \\ \vdots\\ 0 \end {pmatrix}, u_{cl} \in \mathbb{F}^m, c=1,2,\ldots , i.
                $$
                
                Then, $$u_l=\sum_{r=1}^n\lambda _rv_r$$, since $$v_f=e_f,\ f=1,\ldots, n$$, and every thus we see that 
                
                $$
                w=\sum_{k=1}^p\alpha_k v_k+ \sum_{k=1}^q \beta_k (\sum_{r=1}^n \lambda_rv_r)=\sum_{k=1}^p \alpha_k v_k+\sum_{k=1}^q\sum_{r=1}^n\beta_k\lambda_rv_r,
                $$
                
                and $$\{v_1, \ldots, v_p\}$$ is generating in $$\text{Col}(A_{re})$$. Hence, the pivot columns of the rref of a matrix is a basis in the column space of that matrix. $$\blacksquare$$
                
    - The pivot rows of $$A_e$$ give us a basis in $$\text{Col} \ A^T$$.
        - The pivot rows of the echelon form $$A_e$$ of $$A$$ are linearly independent. Let $$w_1, \ldots, w_r$$be the transposed pivot rows of $$A_e$$. Suppose $$\sum_{k=1}^r\alpha_kw_k=0$$. By the definition of echelon form, $$\alpha_k=0, \forall k=1,\ldots,r$$ . Then the vectors $$w_1,\ldots,w_r$$ are linearly independent.
        - Consider a linear transformation $$A$$ and a set $$X$$, and denote by $$A(X):=\{y=A(X):x \in X\}$$. Suppose $$A$$ is an $$n \times m$$ matrix, and denote by $$A_e$$ its echelon form. Then $$A_e=EA$$, where $$E$$ is just a product of elementary square invertible matrices. Then $$\text{Col}(A^T_e)=\text{Col}(A^TE^T)=A^T\text{Col}(E^T)=A^T(\R^m)=\text{Col}(A^T)$$, so $$\text{Col}(A^T_e)=\text{Col}(A^T)$$. $$\blacksquare$$
    - The solutions of the homogeneous equation equation $$Ax=0$$ with form a basis in $$\ker A$$.
        - Solving this homogeneous equation gives us all the vectors $$v \in V$$ such that $$Av=0$$, then any vector $$v \in \ker A$$ is a linear combination of the vectors we have found. Thus, this is a generating system in $$\ker A$$. Observing the solution we have obtained, we notice that for each of the free variables $$x_k$$, the entry number $$k$$ of the resulting vector is $$x_k$$, so the only way this vector can be $$0$$ is when all free variables are $$0$$.

### Rank:

- For a matrix $$A$$, $$\text{rank}(A)=\text{rank}(A^T)$$.
    - *Proof.*
        
        Consider an $$n\times m$$ matrix $$A$$, and denote its echelon form by $$A_e$$. Then, 
        
        $$
        \text{rank}(A)=\dim \text{Col}(A),\ \text{rank}(A^T)=\dim\text{Col}(A^T).
        $$
        
        We already know that the pivot columns of $$A$$ give us a basis in $$\text{Col} (A)$$, and the pivot rows of $$A_e$$ give a basis in $$\text{Col} (A^T)$$. Let the set of vectors $$S_1=\{v_1,\ldots, v_r\}$$ denote the columns of $$A$$ which are the pivot columns of $$A_e$$. Then, $$|S_1|=\text{rank}(A)=r$$. Now, consider set of vectors $$S_2 = \{w_1,\ldots,w_q\}$$, which denote the pivot rows of $$A_e$$. Then, $$|S_2|=\text{rank}(A^T)=q=|S_1|=\text{rank}(A)=r$$, since the number of pivots in the columns coincides with the number of pivots in the rows. $$\blacksquare$$
        
- Let $$A$$ be an $$m \times n$$ matrix, representing some (linear) transformation $$A:\mathbb{F}^n \to \mathbb{F}^m$$. (Rank Theorem)
    - $$\dim \ker A+\dim \text{Col} \ A=\dim \ker A+ \text{rank} \ A=n$$. (Dimension of the domain of $$A$$).
    - $$\dim \ker A^T+\dim \text{Col} \ A^T = \dim \ker A^T+\text{rank} \ A^T=\dim \ker A^T+\text{rank}  \ A=m$$. (Dimension of the codomain of $$A$$).
    - *Proof.*
        
        The number of free variables ($$\dim \ker A$$) + the number of normal variables ($$\text{rank} \ A$$) adds up to number of columns $$n$$. (1) The same logic applies to (2), combined with the fact that $$\text{rank}(A)=\text{rank}(A^T)$$. $$\blacksquare$$
        
- Let $$A$$ be an $$m \times n$$  matrix. Then the equation $$Ax=b$$ has a solution $$\forall b \in \R^m$$ iff the dual equation $$A^Tx=0$$ has a unique (trivial) solution.
    - *Proof.*
        
        Suppose that the only solution to the equation $$A^Tx=0$$ is $$x=0$$. Then, $$\ker A^T=\{0\}$$, and $$\dim \ker A^T = 0$$. Using the rank theorem, we see that $$\dim \text{Col}\ A^T=\text{rank} \ A^T = \text{rank} \ A=\dim \text{Col} \ A=m=n$$. This implies that the matrix $$A$$ is square and that there is a pivot in each row, and hence the equations $$Ax=b$$ is consistent.
        
        Now suppose that the equation $$Ax=b$$ has a solution $$\forall b \in \R^m$$. Let $$A_e$$ denote the echelon form of $$A$$. The equation will still have the exact same solutions, since elementary row operations do not affect the solutions. This implies that there is a pivot in each row of the $$m \times n$$ matrix $$A_e$$. In other words, $$\dim \text{Col} \ A^T=m$$, since there are $$m$$ pivots, one for each row of the matrix. But $$\dim \ker A^T+ \dim \text{Col} \ A^T =m$$, implying $$\dim \ker A^T=0$$. $$\blacksquare$$
        
- One can easily complete a linearly independent system to a basis.
    - If an $$m \times n$$ matrix is in echelon form, then its non-zero rows are linearly independent. To complete the system to a basis in $$\mathbb{F}^n$$, one just needs add some new rows such that the matrix is still in echelon form, and has pivots in every column.
    - Consider a system of linearly independent vectors $$v_1, \ldots, v_r$$. Compose a matrix with rows $$v_1^T, \ldots, v_r^T$$, and perform row operations to make the matrix into echelon form. These new rows also complete the original set of vectors to a basis.
        - *Proof.*
            
            Let the set of vectors $$v_{r+1},\ldots, v_n$$ denote the vectors that complete the rows of $$A_e$$ to a basis in $$\mathbb{F}^n$$. Then, if we add $$A_e$$ the rows $$v_{r+1}^T,\ldots,v_n^T$$, we get an $$n \times n$$ invertible matrix. Denote this matrix by $$\widetilde{A}_e$$, and let $$\widetilde{A}$$ denote the matrix obtained by adding the rows $$v_{r+1}^T,\ldots, v_n^T$$ to $$A$$. $$\widetilde{A}_e$$ can be obtained from $$\widetilde{A}$$ through a left multiplication of a product of elementary matrices $$E\widetilde{A}=\widetilde{A}_e$$. Then $$\widetilde{A}=E^{-1}$$, and $$\widetilde{A}$$ is invertible as a product of invertible matrices. Since $$\widetilde{A}$$  is invertible, it has a pivot in each row and column, and hence the rows of $$\widetilde{A}$$ form a basis in $$\mathbb{F}^n$$. $$\blacksquare$$
            
- Exercises:
    
    ![Screen Shot 2022-04-16 at 8.45.58 AM.png](Systems%20of%20Linear%20Equations%2062485af08c1746a1a637c55edf6999ca/Screen_Shot_2022-04-16_at_8.45.58_AM.png)
    
    *Proof.*
    
    Let $$X,V$$ and $$Y$$ be vector spaces, and that $$V$$ is a subspace of $$X$$. Also let $$A:X \to Y$$ be a transformation. We know that since $$V \sub X$$, $$\dim V \le \dim X$$. If we represent $$A$$ by a matrix, it can be seen that $$\dim AV \le \dim AX= \dim \text{Col} \ A=\text{rank} \ A$$, since $$AX$$ represents the set of vectors $$\{w:w= Ax, \forall x \in X\}= \text{Col} \ A$$. 
    
    Now let $$V:= \text{Col} \ B$$. Then $$\text{rank} \ B = \dim V$$, and $$\text{Col} \ AB = AV \implies  \text{rank} \ AB = \dim AV \le \dim AX = \text{rank}\ A$$. $$\blacksquare$$
    
    ![Screen Shot 2022-04-16 at 9.21.52 AM.png](Systems%20of%20Linear%20Equations%2062485af08c1746a1a637c55edf6999ca/Screen_Shot_2022-04-16_at_9.21.52_AM.png)
    
    *Proof.*
    
    Let $$v_1,\ldots,v_r$$ be a basis in $$V$$. Then $$\dim V = r$$. We can also see that $$S_0=\{Av_1,\ldots, Av_r\}$$ is a generating system in $$AV$$. Since any generating set $$S_1=\{v_1,\ldots,v_q\}$$ in $$V$$ has cardinality $$|S_1|=q\ge r=|S_0|=\dim V \ge \dim AV$$, since a generating set in $$AV$$ has at least $$\dim AV$$ vectors. 
    
    Now let $$V:=\text{Col} \ B$$. Then $$\text{rank} \ B = \dim V$$, and $$\text{Col} \ AB = AV \implies \text{rank} \ AB = \dim AV \le \dim V = \text{rank} \ B$$. $$\blacksquare$$
    
    ![Screen Shot 2022-04-16 at 9.47.50 AM.png](Systems%20of%20Linear%20Equations%2062485af08c1746a1a637c55edf6999ca/Screen_Shot_2022-04-16_at_9.47.50_AM.png)
    
    *Proof.*
    
    Let $$A$$ and $$B$$ be two $$n \times n$$ square matrices, whose product $$AB$$ is invertible by hypothesis. Then, $$\text{rank}(AB)=n$$, since otherwise $$AB$$ would not be invertible. We know from the previous two problems that $$n=\text{rank}(AB) \le \text{rank} \ A$$ and $$n\le \text{rank} \ B$$. However, $$A$$  and $$B$$ are $$n \times n$$ matrices, so $$\text{rank} \ A= n = \text{rank} \ B$$, since a matrix cannot have more pivot columns than the number of its columns. This implies both $$A$$ and $$B$$ has pivots in every row (when in echelon form), and since both matrices are square, they both have pivots in every row as well. This implies they both have a left and right inverse, hence both matrices are invertible. $$\blacksquare$$
    

### Change of Coordinates and Similar Matrices:

> GENERAL RULE: Ignore the inner indices, the first and final indices will be the bases you are taking w.r.t.
> 
- Let $$V$$ be a vector space with base $$\mathcal{B}:=\{b_1,b_2,\ldots,b_n\}$$. Then any vector $$v \in V$$ can be represented by a linear combination $$v = \sum_{k=1}^nx_kb_k$$.
    - We call $$x_k$$ the coordinates of $$v$$, and we can collect all of these coordinates into a column vector, called a coordinate vector.
    
    $$
    [v]_{\mathcal{B}}=\begin{pmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{pmatrix} \in \mathbb{F}^n.
    $$
    
    - The mapping $$v \mapsto [v]_{\mathcal{X}}$$ (where $$\mathcal{X}$$ is some arbitrary basis in $$V$$) is an isomorphism  $$\phi_\mathcal{X}: V \to \mathbb{F}^n$$. This is known as the coordinate map, or standard representation of $$V$$ with respect to some basis.
        - Transforms $$\{b_1,\ldots, b_n\}$$  to $$\{e_1, \ldots,e_n\} \in \mathbb{F}^n$$ (the standard basis in $$\mathbb{F}^n$$.
- Let $$T:V \to W$$ be a linear transformation, and let $$\mathcal \beta :=\{v_1,\ldots,v_n\}$$ and $$\gamma :=\{w_1,\ldots,w_m\}$$ be bases in $$V$$ and $$W$$.
    - A matrix representing $$T$$ with respect to the bases $$\beta$$ and $$\gamma$$ is an $$m \times n$$ matrix denoted by $$[T]_\beta^\gamma$$.
        
        $$
        [T]^\gamma_\beta=\begin{bmatrix} [Tv_1]_\gamma \ \cdots \ [Tv_n]_\gamma \end{bmatrix} = \begin{bmatrix} \phi_\gamma(Tv_1) \ \cdots \ \phi_\gamma(Tv_n) \end{bmatrix}.
        $$
        
        - In other words, the matrix of a linear map $$T$$ w.r.t. two bases of the domain and codomain is: **the collection of the column vectors in a basis of the domain with the transformation applied onto it, written with respect to the basis in the codomain.**
        - It relates the coordinate vectors $$[Tv]_{\gamma}$$ and $$[v]_\beta$$ by
    
    $$
    [Tu]_\gamma=[T]_{\beta}^\gamma[u]_\beta
    $$
    
    - *Proof.*
        
        From the definition of a coordinate matrix, we can see that
        
        ![Screen Shot 2022-04-17 at 10.40.13 AM.png](Systems%20of%20Linear%20Equations%2062485af08c1746a1a637c55edf6999ca/Screen_Shot_2022-04-17_at_10.40.13_AM.png)
        
        $$\forall u \in V$$, $$\exists! \alpha_1,\ldots,\alpha_m \in \mathbb{R}: u=\sum_{k=1}^n\alpha_kv_k$$. Then, we can also see 
        
        $$
        Tu=T(\sum_{k=1}^n\alpha_kv_k)=\sum_{k=1}^n\alpha_k Tv_k\\ \implies [Tu]_\gamma=\phi_{\gamma}(Tu)=\phi_\gamma(\sum_{k=1}^n\alpha_kTv_k)\\ =\sum_{k=1}^n\alpha_k\phi_\gamma(Tv_k)=\sum_{k=1}^n\alpha_k[T]_\beta^\gamma\\=\begin{pmatrix}[Tv_1]_\gamma \ \cdots \ [Tv_n]_\gamma \end{pmatrix}\begin{pmatrix} \alpha_1 \\ \vdots \\ \alpha_n \end{pmatrix}\\ = [T]_\beta^\gamma[u]_\beta .  \  \ \blacksquare
        $$
        
    - The matrix $$[T]_\mathcal{BA}$$’s $$k$$th column is found by the coordinate vector $$[Ta_k]_\mathcal{B}$$.
- Let $$T_1:X \to Y$$ and $$T_2:Y \to Z$$ be two linear maps, and let $$\mathcal{A,B,C}$$ be bases in $$X, Y,Z$$ respectively. Then for $$T=T_2T_1$$, $$T:X \to Z$$, and $$Tx=T_2(T_1x)$$.
    - We also have
    
    $$
    [T]_\mathcal{CA}=[T_2T_1]_\mathcal{CA}=[T_2]_\mathcal{CB}[T_1]_\mathcal{BA}
    $$
    
    - *Proof.*
        
        Let $$v$$ be an arbitrary vector in $$V$$, and $$\lambda_k, \varphi_q \in \mathbb{R},$$  some arbitrary constant. Using the definition of matrix multiplication,
        
        $$
        [T]_\mathcal{CA}=\phi_\mathcal{C}(Tv)=\phi_\mathcal{C}[(T_2 \circ T_1)(v)]=\phi_\mathcal{C}[T_2(T_1v)]\\= \phi_\mathcal{C}[ \ [(T_2(T_1v_1)] \ \cdots \  [T_2(T_1v_n)]\ ]=[ \ [(T_2(T_1v_1)]_\mathcal{C} \ \cdots \  [T_2(T_1v_n)]_\mathcal{C} ]\\=[ \ [T_2]_\mathcal{B}^\mathcal{C}[T_1v_1]_\mathcal{B} \ \cdots \  [T_2]_\mathcal{B}^\mathcal{C}[T_1v_n]_\mathcal{B}\ ] \\ =[T_2]_\mathcal{B}^\mathcal{C}[T_1]^\mathcal{B}_\mathcal{A}.
        $$
        
        $$\blacksquare$$
        
- Let us have two bases $$\mathcal A :=\{a_1,\ldots,a_n\}$$ and $$\mathcal{B}:=\{b_1,\ldots,b_m\}$$ in a vector space $$V$$. Consider the identity transformation $$I:V \to V$$ and its matrix $$[I]_\mathcal{BA}$$ w.r.t. to these bases, called the change of coordinates matrix. Then, $$[v]_\mathcal{B}=[I]_\mathcal{BA}[v]_\mathcal{A}, \forall v \in V$$.
    - *Proof.*
        
        Since the identity matrix $$I=I_V$$ in the vector space $$V$$ is invertible and for any vector $$v \in V$$, it is by definition that $$Iv=vI=v$$. Since we already know that $$[Tv]_\mathcal{B}=[T]_\mathcal{BA}[v]_\mathcal{A}$$, we let $$T=I=I_V$$, and we have $$[Iv]_\mathcal{B}=[v]_\mathcal{B}=[I]_\mathcal{BA}[v]_\mathcal{A}$$. $$\blacksquare$$
        
    - One can compute the elements of $$[I]_\mathcal{BA}$$, since its columns are the coordinate matrices $$[a_k]_\mathcal{B},\ k=1,\ldots, n$$.
    - We can also easily see that $$[I]_\mathcal{BA}=([I]_\mathcal{AB})^{-1}$$.
- Let $$T:V \to W$$ be a linear map, and let $$\mathcal{A,\widetilde{A}}$$ be two bases in $$V$$, and $$\mathcal{B, \widetilde{B}}$$ be two bases in $$W$$. Suppose $$[T]_\mathcal{BA}=[[a_1]_\mathcal{B} \ \cdots \ [a_n]_\mathcal{B} ]$$ is given.
    - We can find the matrix with respect to the new bases, namely $$[T]_\mathcal{ \widetilde{B} \widetilde {A}}$$, by surrounding it by the change of coordinates matrices.
    - In other words,
    
    $$
    [T]_\mathcal{ \widetilde{B} \widetilde {A}}=[I]_\mathcal{\widetilde{B}B}[T]_\mathcal{BA}[I]_{\mathcal{A \widetilde{A}}}.
    $$
    
    - *Proof.*
        
        We know that $$[T]_{\widetilde{B}\widetilde{A}}=[I]_{\widetilde{B}B}[T]_{B\widetilde{A}}$$, by using the formula for the coordinate representation of the composition of two linear maps. Then, it can be seen that $$[T]_{\widetilde{B}\widetilde{A}}=[I]_{\widetilde{B}B}[T]_{BA}=[I]_{\widetilde{B}B}[T]_{BA}[I]_{A\widetilde{A}}$$. $$\blacksquare$$
        
- Let $$V$$ be a vector space and let $$\gamma:=\{a_1,\ldots,a_n\}$$ be a basis in $$V$$. Consider a linear transformation $$T:V \to V$$, and let $$[T]_{\gamma \gamma}=[T]_\gamma$$. Now let $$\beta:=\{b_1,\ldots,b_n\}$$ be another basis in $$V$$.
    - By the change of coordinates rule, we see that $$[T]_\beta=[I]^\beta_\gamma[T]^\gamma_\gamma[I]_\beta^\gamma$$. We also know that $$[I]^\beta_\gamma=([I]_\beta^\gamma)^{-1}$$. Let $$Q:=[I]^\gamma_\beta$$. Then $$[T]_\beta=Q^{-1}[T]_\gamma Q$$.
    - Any two matrices $$A,B$$ satisfying the property $$A=Q^{-1}BQ$$ are similar.
        - $$A ,B$$ are both square matrices of the same size.
        - $$B=QAQ^{-1}$$.
- If matrices $$A$$ and $$B$$ are similar, then $$\text{trace}(A)=\text{trace}(B)$$.
    - *Proof.*
        
        We know that for two matrices of dimension $$n \times m$$ and $$m \times n$$ respectively, $$\text{trace}(MN)=\text{trace}(NM)$$. Since two similar matrices are both $$i \times i$$ matrices, we know that $$\text{trace}(AB)=\text{trace}(BA)$$. There exists an invertible matrix $$Q$$ such that $$A=Q^{-1}BQ$$ and $$B=QAQ^{-1}$$ since the two matrices are similar. Then, 
        
        $$
        \text{trace}(A)=\text{trace}([Q^{-1}B]Q)=\text{trace}(QQ^{-1}B)=\text{trace}(B). \ \blacksquare
        $$