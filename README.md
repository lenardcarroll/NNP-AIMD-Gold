# NNP-AIMD-Gold

Using a constant number of particles, volume and temperature ensemble alongside the equipartitition theorem, we can calculate the temperature of the system from the mass of the particle and its velocity using:

$$\text{T}_\text{actual}  = \frac{3}{2NK_B}\sum_{i=1}^N \text{KE}_i$$

where $N$ is the number of particles in the system, $K_B$ is the Boltzmann constant and $\text{KE}_{i}$ is the kinetic energy of the particle such that:

$$\text{KE}_i = \frac{1}{2}m_iv_i^2$$

An important part of an NVT ensemble is proper thermostatting, not just of the entire system, but individual groups of atoms too. Often times the Nose-Hoover thermostat struggles with thermostatting individual groups of atoms, but does a thorough job with the entire system. As such, in our model, we want to apply a penalty function to ensure not only proper thermostatting of the entire system, but the adsorbates and the metal separately as well. For this, we use the following protocol:

$$\text{T}_\text{actual,adsorbates} = \frac{3}{2N_aK_B}\sum_{i=1}^N_a \text{KE}_i$$
$$\text{T}_\text{actual,metal} = \frac{3}{2N_mK_B}\sum_{i=1}^N_m \text{KE}_i$$
$$$$\text{T}_\text{actual,system} = \frac{3}{2NK_B}\sum_{i=1}^N \text{KE}_i$$

$\sum_{i=1}^N \text{KE}_i$

$$\left( \sum_{k=1}^n a_k b_k \right)^2$$

$\text{Temperture}_\text{Target} = N$
