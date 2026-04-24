# Soft-PINN

This framework presents a new physics-informed neural network (PINN) for soft continuum robot modeling, namely Soft-PINN, that integrates first-principles physics and nonlinear principles into deep learning. Specifically, Soft-PINN systematically incorporates the two primary intrinsic sources of soft robots’ nonlinearity, i.e., geometric and material, into the PINN formulation. The framework enables accurate modeling of large nonlinear deformations in soft continuum robots, while achieving fast convergence and requiring limited training. Four different pneumatic soft continuum robots were fabricated as testbeds to validate the proposed Soft-PINN, including both positive-pressure inflation and vacuumdriven contraction types. The results show that the errors in predicted deformations, quantified by the L2 norm, are on the order of 10−2 to 10−3 for various conditions. With the nonlinearity formulated in the Soft-PINN framework, the training is up to 120 times faster than the PINN model with linear elasticity formulation, and more than 400 times faster than finite element simulations. Additionally, the predicted maximum and minimum deformations, base curvature, and bending angle for various pressure or vacuum inputs closely matched the experimental data across all four soft robot testbeds. By integrating nonlinearity into deep learning, the proposed Soft-PINN framework exhibits high accuracy, fast and stable convergence, and balanced reduction of data and physics residuals, thereby demonstrating strong potential for generalizable modeling across a range of materials, load cases, and geometries.

# Pneumatic soft continuum robot under loading and resulted motion

<img width="627" height="477" alt="image" src="https://github.com/user-attachments/assets/bf29b653-1ddc-4e78-a8eb-038d0a6a6505" />


# The Soft-PINN framework for soft continuum robots
The proposed
architecture as shown in Figure 3 combines an MLP as an FNN with embedded physics constraints to construct physically consistent predictions of soft robot deformation and behavior. While the MLP backbone approximates the mapping from spatial coordinates (x, y and z) and actuation pressure (p) to the displacement components (u_x, u_y and u_z), physical consistency is enforced through TensorFlow’s automatic differentiation of the network outputs. The
spatial derivatives are used to construct the deformation gradient and subsequently the isochoric left Cauchy-Green deformation tensor ¯B. Then, the strain energy function W is defined for both Mooney–Rivlin and Yeoh hyperelastic models, and the stress tensor, σ, is computed analytically by differentiating W regarding the first and second invariants (I_1 and I_2). The resultant stress tensor is then substituted into the Cauchy momentum equations, forming the core of the physics-informed constraints.
The complete physics model comprises three key components: (1) the equilibrium equations derived from the Cauchy momentum equation in equilibrium for soft
continuum materials, (2) ICs that define the undeformed configuration u = u0, and (3) BCs including both Dirichlet (fixed displacements) and Neumann (applied tractions on the inner and outer surfaces). The selection of BCs is robotspecific conditions, and for the systems in this study, inner and outer surface traction conditions are excluded as we are using the face mesh, where the unit normal n is in the zdirection and we are solving the deformation in xy-plane.


<img width="1598" height="778" alt="image" src="https://github.com/user-attachments/assets/f45370c1-9192-411b-87a3-b822e2965b02" />

# The design of the four pneumatic soft continuum robot testbeds
<img width="1740" height="636" alt="image" src="https://github.com/user-attachments/assets/f954034d-2a61-4173-846c-969e1608a59b" />

# 3D-printed soft continuum robots as four testbeds
<img width="1706" height="347" alt="image" src="https://github.com/user-attachments/assets/8abc37cd-29a6-4a68-a4cf-2b766e93e480" />

# Finite element analysis results for the soft fingers
<img width="1455" height="830" alt="image" src="https://github.com/user-attachments/assets/8353252a-bce5-45b9-ba26-5490632ab32e" />

# Finite element analysis results for the soft spring
<img width="653" height="747" alt="image" src="https://github.com/user-attachments/assets/9401a922-4fe1-4f39-9887-65b2d3272033" />

# Prediction results for the soft fingers
<img width="1000" height="881" alt="image" src="https://github.com/user-attachments/assets/9c147b39-a160-4c23-890f-8c61d4f0c2d2" />



# Prediction results for the soft spring
<img width="516" height="575" alt="image" src="https://github.com/user-attachments/assets/b821955f-896e-42eb-99a9-683489d64af9" />



