# MATLAB Programming for Finite Element Methods

## Arrangement of the ongoing Toolbox

 We shall establish an iFEM-like package or a simplified version with certain extensions, named mFEM toolbox.

- The toolbox has two important folders：fem and variational.

  - fem: It includes all kinds of source code.
  - variational: A new feature is the variational formulation based programming. It extends the applicaton in fem folder.
                 We have already provided P1, P2 and P3 Lagrange elements for one dimensional and two dimensional problems as well as    the vectorized problems, e.g. the linear elasticity problem.  

- example: All running programs are placed in the example folder.

- tool: You can find functions involving visulization, boundary setting, mesh generation, and numerical integration and so on.

- pdedata: It provides information of equations associated with examples in example folder. 

- meshdata: It stories mesh data used in all kinds of examples.

## Display and marking of polygonal meshes
We present some basic functions to show the polygonal meshes, including 
   marking of the nodes, elements and (boundary) edges.

## Auxiliary mesh data and setboundary.m
For the convenience of computation, we introduce some auxiliary mesh data. The idea stems from the treatment of triangulation in iFEM, which is generalized to polygonal meshes with certain modifications.  

## 1-D problems

Folder FEM1D introduces FEM programming of one dimensional problems. 
The assembly of stiffness matrix and load vector is explained in detail.

## 2-D Poisson equation
Folder FEM2D includes the source codes of solving the 2-D Poisson equation.
   See chapter 2 for illustration.

## Adaptive finite element method and Newest-node bisection
The adpative finite element method (AFEM) is introduced in Chapter 5 for the Poisson equation with homogeneous Dirichlet 
   conditions.  Each step was explained in detail, viz. the loops of the form: 

           SOLVE -> ESTIMATE -> MARK -> REFINE

The newest-node bisection for the local mesh refinement was clearly stated  thanks to the smart idea in iFEM.  
The MATLAB codes are in Folder AFEM2D. 

## Linear elasticity equations

For linear elasticity problems, we give a unified programming framework. Specifically, 
- The entrices of stiffness matrix are analyzed in the vectorized finite element space;
- The assembly is accomplished in the scalar FE space of each component.

We consider three forms of variational problems. 
  - The first and the second are commonly used in linear elastic problems in the form of strain and/or stress tensors. 
  - The third is just a variant of the second one with Laplacian replacing the strain tensors.
  - For each formulation, sparse assembling indices and detailed explanation are given.

For the first two formulations,  “Neumann”  boundary conditions and Dirichlet boundary conditions are applied. 
For the third fomulation, only Dirichlet conditions are used in view of the practical problems.

## Plate bending problems

- The plate bending problem is to describe the small transverse deformation of thin plates. A special case of the equilibrium equation is the biharmonic equation, which is a typical fourth-order partial differential equation. The nonconforming element is usually applied to reduce the degrees of freedom. Among the nonconforming finite elements in two dimensional case, the Morley element is perhaps the most interesting one. It has the least number of degrees of freedom on each element for fourth order boundary value problems as its shape function space consists of only quadratic polynomials.

    It should be noted that the normal derivative values at the midpoint of interior edge sharing by two triangles have different signs. Apparently, this feature will be inherited by the corresponding local nodal basis functions given by the global ones restricted to the adjacent elements. The problem can be easily resolved by using signed edges.
    
    A more general method is added by introducing symbolic stiffness matrix and symbolic load vector. 
	Such prodecure can be extended to other problems with d.o.fs varing in directions and can be furter applied to polygonal meshes.
	
- Besides Morley element, Zienkiewicz element and Adini element are two other commonly used nonconforming elements. 
  The former is incomplete cubic triangular element and the latter is incomplete bicubic rectangular element.
  In addition to directional problems, all three non-conforming elements (and conforming elements) can be programmed in the unified framework given in the document.
  
- 新增双调和方程的混合元方法. 
  

  
## Variational formulation based programming for 1-D problems
We present a variational formulation based programming for 1-D problems in Folder variational1D. The arrangement is entirely process-oriented and thus easy to understand (see Section 1.5). 

## Multigrid V-cycle method for linear elements

  - We present a multigrid method by adding two grids one by one, so that the pseudo-code of V-cycle method can be obtained directly.
  
  - The MG method can be also analyzed by using subspace correction method proposed by Xu Jinchao (for example, iFEM). 
    However, it may be not straightforward by adding two grids.

  - The programming of one-dimensional problems is described in detail, and the multigrid program is universal to all linear element problems.
  
  - For 2D and 3D linear elements, only slight changes of 1D problems are needed since they can be regarded as 1D problems.
    See the document for details (two-dimensional problem).


PS:

     对前面各章节的重新整理将会在未来的适当时间完成。

Undo: 

           --- Variational formulation based toolbox
   
           - high-order FEM
	   
           - mesh generation   
   
           - Solver: multigrid methods (mg)   
   
           - 3-D FEM      

           - mixed FEM (e.g. Stokes equation)   
  
            - time-dependent problems     

            - ... ...
