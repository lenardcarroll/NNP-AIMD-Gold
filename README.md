# Thermostatting Protocol

Using a constant number of particles, volume and temperature ensemble alongside the equipartitition theorem, we can calculate the temperature of the system from the mass of the particle and its velocity using:

$$\text{T}_\text{actual}  = \frac{3}{2Nk_B}\sum_{i=1}^N \text{KE}_i$$

where $N$ is the number of particles in the system, $k_B$ is the Boltzmann constant and $\text{KE}_{i}$ is the kinetic energy of the particle such that:

$$\text{KE}_i = \frac{1}{2}m_iv_i^2$$

An important part of an NVT ensemble is proper thermostatting, not just of the entire system, but individual groups of atoms too. Often times the Nose-Hoover thermostat struggles with thermostatting individual groups of atoms, but does a thorough job with the entire system. As such, in our model, we want to apply a penalty function to ensure not only proper thermostatting of the entire system, but the adsorbates and the metal separately as well. For this, we use the following protocol:

$$\text{T}_\text{actual,adsorbates} = \frac{3}{2{N_a}k_B}\sum_{i=1}^{N_a} \text{KE}_i$$

$$\text{T}_\text{actual,metal} = \frac{3}{2{N_m}k_B}\sum_{i=1}^{N_m} \text{KE}_i$$

$$\text{T}_\text{actual,system} = \frac{3}{2Nk_B}\sum_{i=1}^N \text{KE}_i$$

$$\text{T}_\text{Tol} = \sigma\text{T}_\text{target}$$

If the target temperature is 0 (thus a DFT computation), then:

$$v_{\text{predict}_i} = (0, 0, 0)$$

this ensures that the temperature and velocity of the system remains 0. In the event where the actual temperature of the system, adsorbates or the metal doesn't lie withn the range:

$$[\text{T}_\text{target} - \text{T}_\text{Tol}, \text{T}_\text{target} + \text{T}_\text{Tol}]$$

we rescale the velocities of the adsorbates, metal or the entire system using:

$$v_{\text{predict}_i} = \sqrt{\frac{\text{T}_\text{target}+q\text{T}_\text{Tol}}{\text{T}_\text{actual}}}v_{\text{actual}_i}$$

If the actual temperature lies within the acceptable range, we accept the velocities and continue. In the set of equations above, $\sigma$ is a coefficient we will choose to decide the amount of tolerance for the thermostatting, and $q$ is a random factor between -1 and +1. 
