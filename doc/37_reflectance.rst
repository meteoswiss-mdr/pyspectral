Derivation of the 3.7 micron reflectance
----------------------------------------

The monochromatic reflectivity (or reflectance) :math:`\rho_{\lambda}` is the
ratio of the reflected (backscattered) radiance to the incident radiance. In
the case of solar reflection one can write:

.. math::

    \rho_{\lambda} = \frac{L_{\lambda}}{\mu_0 L_{\lambda 0}}

where :math:`L_{\lambda}` is the measured radiance, :math:`L_{\lambda 0}` is
the incoming solar radiance, and :math:`\mu_0` is the cosine of the solar
zenith angle :math:`\theta_0`.


Assuming the solar radiance is independent of direction, the equation for the
reflectance can be written in terms of the solar flux :math:`F_{\lambda 0}`:

.. math::

    \rho_{\lambda} = \frac{L_{\lambda}}{\frac{1}{\pi} \mu_0 F_{\lambda 0}}

For the :math:`3.7\mu m` channel the outgoing radiance is due to solar
reflection and thermal emission. Thus in order to determine a :math:`3.7\mu m`
channel reflectance, it is necessary to subtract the thermal part from the
satellite signal. To do this, the temperature of the observed object is
needed. The usual candidate at hand is the :math:`11 \mu m` brightness temperature
(e.g. VIIRS I5 or M12), since most objects behave approximately as blackbodies
in this spectral interval.

The :math:`3.7\mu m` channel reflectance may then be written as

.. math::

    \rho_{3.7} = \frac{L_{3.7} - \epsilon_{3.7} \int_0^\infty \Phi_{3.7}(\lambda) B_{\lambda} (T_{11}) \mathrm{d}\lambda } {\frac{1}{\pi} \mu_0 F_{3.7, 0}}

where :math:`L_{3.7}` is the measured radiance at :math:`3.7\mu m`, 
:math:`\Phi_{3.7} (\lambda)` is the :math:`3.7 \mu m` channel
spectral response function, :math:`B_{\lambda}` is the Planck radiation, 
and :math:`T_{11}` is the :math:`11\mu m` channel brightness temperature.

If the observed object is optically thick (transmittance equals zero) then:

.. math::

    \epsilon_{3.7} = 1 - \rho_{3.7}

and then

.. math::

    \rho_{3.7} = \frac{L_{3.7} - \int_0^\infty \Phi_{3.7}(\lambda) B_{\lambda} (T_{11}) \mathrm{d}\lambda } {\frac{1}{\pi} \mu_0 F_{3.7, 0} - \int_0^\infty \Phi_{3.7}(\lambda) B_{\lambda} (T_{11}) \mathrm{d}\lambda }


Derive the emissive part of the 3.7 micron band
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Now that we have the reflective part of the :math:`3.x` signal, it is easy to derive
the emissive part, under the same assumptions of completely opaque (zero
transmissivity) objects. 

.. math::

   L_{3.7, thermal} = (1 - \rho_{3.7}) \int_0^\infty \Phi_{3.7}(\lambda) B_{\lambda} (T_{11}) \mathrm{d}\lambda


Brightness temperature to spectral radiance 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If the satellite observation is given in terms of the brightness temperature,
then the corresponding spectral radiance can be derived by convolving the relative
spectral response with the Planck function and diving by the equivalent band width:

.. math::

    L_{3.7} = \frac{\int_0^\infty \Phi_{3.7}(\lambda) B_{\lambda} (T_{3.7}) \mathrm{d}\lambda}{\widetilde{\Delta \lambda}}

where the equivalent band width :math:`\widetilde{\Delta \lambda}` is defined as:

.. math::

    \widetilde{\Delta \lambda} = \int_0^\infty \Phi_{3.7}(\lambda) \mathrm{d}\lambda

This gives the spectral radiance given the brightness temperature and may be
expressed in :math:`W/m^2 \mu m^{-1}`. In order to get the total radiance over
the band one has to multiply with the equivalent band width.

Inserting the Planck radiation:

.. math::

    L_{3.7} = \frac{2hc^{2} \int_0^\infty \frac{\Phi_{3.7}(\lambda)}{{\lambda}^{5}} \frac{\mathrm{d}\lambda} {e^{\frac{hc}{\lambda k_B(T_{3.7})}} - 1}}{\widetilde{\Delta \lambda}}


This is expressed in wavelength space. But the spectral radiance can also be
given in terms of the wavenumber :math:`\nu`, provided the relative spectral
response is given as a function of :math:`\nu`:

.. math::

    L_{{\nu}(3.7)} = \frac{\int_0^\infty \Phi_{3.7}(\nu) B_{\nu} (T_{3.7}) \mathrm{d}\nu}{\widetilde{\Delta \nu}}

where the equivalent band width :math:`\widetilde{\Delta \nu}` is defined as:

.. math::

    \widetilde{\Delta \nu} = \int_0^\infty \Phi_{3.7}(\nu) \mathrm{d}\nu

and inserting the Planck radiation:

.. math::

    L_{{\nu}(3.7)} = \frac{\frac{2h}{c^2} \int_0^\infty \Phi_{3.7}(\nu) \frac{{\nu}^3 \mathrm{d}\nu}{e^{\frac{h c}{\lambda k_B T:{3.7}}} - 1} }{\widetilde{\Delta \nu}}



Determination of the in-band solar flux
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The solar flux (SI unit :math:`\frac{W}{m^2}`) over a spectral sensor band can
be derived by convolving the top of atmosphere spectral irradiance and the
sensor relative spectral response curve, so for the :math:`3.7\mu m` band this
would be:

.. math::

    F_{3.7} = \int_0^\infty \Phi_{3.7}(\lambda) S(\lambda) \mathrm{d}\lambda 

where :math:`S(\lambda)` is the spectral solar irradiance.
