# Numerical-Modeling-and-Algorithms-

# LU Factorization Algorithm:

This algorithm implemented in python takes a non-singular matrix and converts it to upper and lower triangular matrices.



# Modeling Temperature Variations in the Ground.

PROBLEM FORMULATION

This problem is concerned with computing temperature variations in the ground. Surface temperature will vary with seasons and time of day, so it is natural to get these oscillations in the temperature. The surface temperature at the ground will not be constant all the time. So, when there is a change in temperature, that change will be propagated into the ground. What we are interested in is how the temperature varies at different depths in the ground as a result of these oscillations of the surface temperature. It is important to note that we are assuming there is no horizontal variation of temperature, at least on a small scale. We are only concerned about the vertical temperature changes. Assuming at some depth, x = L, the heat variations are negligible, we can say ∂u/∂x =0  is the boundary condition for solving the PDE at x = L. We can assume a sinusoidal temperature equation of,

When t = 0, we find that u(x,0) = A +Be^{-rx}*sin(-rx)

Where P represents 24 hours (24 * 60 * 60s). 
The ultimate goal in this problem is to plot both the numerical and analytical solutions as an animation for some number of days. 


OUR APPROACH:

To solve this problem numerically, for N number of mesh points, N-1 number of initial conditions were needed. To get this, the function I(x,t) in our code calculates these initial conditions. The function s(t) calculates the boundary condition for x = 0. Once these values are calculated, the function rhs(u,t,dx)) approximates partial time derivative by using a second order finite difference. The first time derivative is calculated at (x,t) = (0,0). This derivative is then used to calculate u(0+dx, 0+dt) by using Euler's forward method in time. The iterative formula is given by f(x,t+1) = f(x,t) + f'(x,t)*dt. This formula is iteratively applied for the mesh points and time as outlied in our problem formulation.

RELEVANT CONSTANTS

T0 = 30℃:
T0 represents the initial temperature at the surface of the ground, at x = 0. This is shown in the equation by letting x = 0 and t = 0 which results in all the terms except T0 being cancelled out. 


Ta = 15℃ :
Ta is another temperature value, similar to T0. Ta is multiplied with the exponential decay and sinusoidal parts of the equation. Instead of representing the initial surface temperature, Ta relates to how the temperature varies at different depths. 


r = sqrt(ω/2β):

r represents the rate at which the heat is being propagated into the ground. This value is positive, but made negative by the equation. At x = 0 (no depth), the e^-rx term will resolve to 1 because the depth is 0. But, as we look at deeper and deeper levels (increasing x values), the e^-rx term will tend towards 0. This makes sense because less and less heat will be propagated into the ground at deeper levels. In other words, the amount of heat transferred into the ground at a depth of 1 meter will be far greater than the amount of heat at 10 meters.


ω = 2π/P:
ω by definition is 2π/P. The period (P) in this problem is 24 hours but when converted to seconds it is 24 * 60 * 60. 



