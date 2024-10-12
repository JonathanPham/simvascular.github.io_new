<!-- ============================================================== -->
<!-- ==================== Linear Solver Subsection ================ -->
<!-- ============================================================== -->

<h3 id="liner_solver_subsection"> Linear Solver Subsection </h3>
The <i>Linear Solver Subsection</i> of the <i>Equation Section</i> defines the linear solver to use to solve the 
linear system generated by FEM and several parameters used to control the solution process.

The <i>Linear Solver Subsection</i> is organized as follows
<div style="background-color: #F0F0F0; padding: 10px; border: 1px solid #d0d0d0; border-left: 1px solid #d0d0d0">
&lt;<strong>LS</strong> type=linear_solver_type</i>&gt;
<br><br>
&lt;<strong>Linear_algebra</strong> type=<i>linear_algebra_package</i>&gt;<br>
[<a href="#liner_algebra_parameters"> Linear Algebra Parameters </a> ]
<br>
&lt;<strong>Linear_algebra</strong>&gt;<br>
<br>
[Linear Solver Parameters]
<br><br>
&lt;<strong>LS</strong>&gt;
</div>

The <strong>LS</strong> keyword adds a linear solver to the enclosing equation.

The value of <i>linear_solver_type</i> can be

<div style="background-color: #F0F0F0; padding: 4px; border: 1px solid #d0d0d0; border-left: 1px solid #d0d0d0">

<ul style="list-style-type:disc;">

  <li> "BICG" - Biconjugate gradient method. This solver is used for the same equations used for GMRES. </li>
  <li> "CG" - Conjugate gradient.  This solver is used for the following equations
     <ul style="list-style-type:square;">
       <li> linear_elasticity </li>
       <li> mesh </li>
       <li> shell </li>
       <li> solid_heat </li>
       <li> structural </li>
     </ul>
  </li>
  <li> "GMRES" - Generalized minimal residual method. This solver is used for the following equations
     <ul style="list-style-type:square;">
       <li> cardiac_electro_physiology </li>
       <li> coupled_momentum </li>
       <li> fluid-solid-interaction </li>
       <li> advection_diffusion </li>
       <li> stokes </li>
       <li> structural_velocity_pressure </li>
     </ul>
  </li>
  <li> "NS" - Navier-Stokes solver based on bipartition method for fluid equations. </li>

</ul>
</div>

<!-- --------------------------------- -->
<!-- ---- Linear solver parameters --- -->
<!-- --------------------------------- -->

<h4 id="liner_solver_parameters"> Linear Solver Parameters </h4>
<div class="bc_param_div">
<strong>&lt;Max_iterations&gt;</strong> <i>integer</i> [5]  <nobr>
<strong>&lt;/Max_iterations&gt;</strong>
</nobr><br>
The maximum number of iterations to use for a linear solve.
<br>
<strong>&lt;Krylov_space_dimension&gt;</strong> <i>integer</i> [200]  <nobr>
<strong>&lt;/Krylov_space_dimension&gt;</strong>
</nobr><br>
The dimension of the Kyrlov matrix used to approximate a linear system.
<br>
<strong>&lt;Tolerance&gt;</strong> <i>real</i> [0.4]  <nobr>
<strong>&lt;/Tolerance&gt;</strong>
</nobr><br>
The solution of a linear system of equations is considered to be converged (solved) if the linear residual is less than this value. 
<br>
<strong>&lt;Absolute_tolerance&gt;</strong> <i>real</i> [1e-10]  <nobr>
<strong>&lt;/Absolute_tolerance&gt;</strong>
</nobr><br>
The solution of a near system of equations is considered to be converged (solved) if the linear residual is less than this value.
<br>
<strong>&lt;NS_GM_max_iterations&gt;</strong> <i>integer</i> [5]  <nobr>
<strong>&lt;/NS_GM_max_iterations&gt;</strong>
</nobr><br>
The solution of a near system of equations is considered to be converged (solved) if the linear residual is less than this value.
<br>
<strong>&lt;NS_GM_tolerance&gt;</strong> <i>real</i> [1e-10]  <nobr>
<strong>&lt;/NS_GM_tolerance&gt;</strong>
</nobr><br>
? 
<br>
<strong>&lt;NS_CG_max_iterations&gt;</strong> <i>integer</i> [5]  <nobr>
<strong>&lt;/NS_CG_max_iterations&gt;</strong>
</nobr><br>
? 
<br>
<strong>&lt;NS_CG_tolerance&gt;</strong> <i>real</i> [1e-10]  <nobr>
<strong>&lt;/NS_CG_tolerance&gt;</strong>
</nobr><br>
? 
<br>
</div>

<!-- ============================================================== -->
<!-- ==================== Linear algebra parameter ================ -->
<!-- ============================================================== -->

<h4 id="liner_algebra_parameters"> Linear Algebra Parameters </h4>
The Linear Algebra Parameters section of the solver parameters input file defines the linear algebra package
to use to solve linear systems using the &lt;<strong>Linear_algebra</strong> type=<i>linear_algebra_type</i>&gt; parameter.

The value of <i>linear_algebra_type</i> can be

<ul style="list-style-type:disc;">
 <li> "fsils" - Custom numerical linear algebra routines included in the svFSIplus implementation </li>
 <li> "petsc" - Portable, Extensible Toolkit for Scientific Computation (PETSc) </li>
 <li> "trilinos" - The Trilinos numerical linear algebra package </li>
</ul>

<div style="background-color: #F0F0F0; padding: 4px; border: 1px solid #d0d0d0; border-left: 1px solid #d0d0d0">
<strong>&lt;Preconditioner&gt;</strong> <i>string [none] </i> <nobr>
<strong>&lt;/Preconditioner&gt;</strong>
</nobr><br>
The preconditioner applied to a linear system. 

The value of the preconditioner can be
<ul style="list-style-type:disc;">
  <li> fsils 
     <ul style="list-style-type:square;">
       <li> fsils</li>
       <li> rcs </li>
     </ul>
  </li>
  <li> petsc 
     <ul style="list-style-type:square;">
       <li> jacobi </li>
       <li> rcs </li>
     </ul>
  </li>
  <li> trilinos 
     <ul style="list-style-type:square;">
       <li> trilinos-diagonal </li>
       <li> trilinos-blockjacobi </li>
       <li> trilinos-ilu</li>
       <li> trilinos-ilut</li>
       <li> trilinos-ic</li>
       <li> trilinos-ict</li>
       <li> trilinos-ml</li>
     </ul>
  </li>
</ul>
<br>
</div>