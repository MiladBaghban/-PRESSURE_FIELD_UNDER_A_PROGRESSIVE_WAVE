The pressure field associated with a progressive wave is determined from the 
unsteady Bernoulli equation developed for an ideal fluid and the velocity 
potential appropriate to this case. The dynamic pressure is a result oftwo 
contributions; the first and most obvious contributor is the surcharge of 
pressure due to the presence of the free surface displacement. If the pressure 
response factor were unity, the pressure contribution from the free surface 
displacement would be purely hydrostatic. However, associated with the wave 
motion is the vertical acceleration, which is 180” out of phase with the free 
surface displacement.

<pre>
import numpy as np                                            # library of python for calculate the calculation of below
import matplotlib.pyplot as plt                               # library of python for calculate the calculation of below 

x = np.linspace(-2 * np.pi, 2 * np.pi, 500)                   # increase number of points at x direction
z = np.linspace(-1, 1, 300)
X, Z = np.meshgrid(x, z)
Y = 0.9 * np.cos(X) * np.exp(-Z**2)                           # function for contourline

wave_z = 0.1 * np.cos(x)                                      # wave function
mask = Z > wave_z[np.newaxis, :]  
Y_masked = np.ma.masked_where(mask, Y)  

plt.figure(figsize=(14, 8))
contour = plt.contour(X, Z, Y_masked, levels=np.linspace(-1, 1, 20), cmap='coolwarm', linewidths=1.5)
plt.clabel(contour, inline=True, fontsize=8, fmt='%1.2f')     # numbers format

plt.plot(x, wave_z, color='red', linewidth=2, label='Wave Profile')  

plt.title('Isolines of $p_D/[\\rho g(H/2)]$ with Wave Profile', fontsize=14)
plt.xlabel('x (rad)', fontsize=12)  
plt.ylabel('z', fontsize=12)
plt.axhline(0, color='black', linewidth=0.8, linestyle='--')  
plt.axvline(0, color='black', linewidth=0.8, linestyle='--')  
plt.ylim(-1, 1)  # محدود کردن محور z
plt.xlim(-2 * np.pi, 2 * np.pi)                               # show the period time
plt.legend(fontsize=12)                                       # increase the size of font

plt.savefig('wave_contour_plot_no_upper_lines.png', dpi=300)  
plt.show()

<image align="center" alt="Milad" width = "600" src="http://up44.ir/previews/7e9a7d8c34baa67b3b1325a2751bf35e.png"> 
