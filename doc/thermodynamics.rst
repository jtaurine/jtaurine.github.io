Thermodynamics and constitutive laws
====================================



Legendre transformation
-----------------------

Considering thermo-magnetic-mechanical physics, the arguments for the internal energy density :math:`u` at any scale are the following extensive thermodynamic variables: the entropy density :math:`s`, the magnetization :math:`\pmb{m}`  and the total strain :math:`\boldsymbol{\epsilon}`.

.. math::
	\dot u (\pmb{m},\boldsymbol{\epsilon},s)=\mu_0\pmb{h}\cdot \dot{\pmb{m}}+\boldsymbol{\sigma}:\dot{\boldsymbol{\epsilon}}+T\dot s
	:label: internal_energy

Using Legendre transformation, one can define Helmoltz free energy density :math:`f` such that

.. math::
	f(\pmb{m},\boldsymbol{\epsilon},T)=u-Ts.
	:label: Helmoltz_energy
	
Another Legendre transformation allows to define free enthalpy density

.. math::
	\Psi(\pmb{m},\boldsymbol{\sigma},T)=f-\boldsymbol{\sigma}:\boldsymbol{\epsilon}.
	:label: free_enthalpy


Using :eq:`internal_energy`, :eq:`Helmoltz_energy` and :eq:`free_enthalpy`, one can identify the equations of state

.. math::
	\frac{\partial \Psi(\pmb{m},\boldsymbol{\sigma},T)}{\partial \pmb{m}}=\mu_0 \pmb{h}, \quad
	\frac{\partial \Psi(\pmb{m},\boldsymbol{\sigma},T)}{\partial \boldsymbol{\sigma}}=-\boldsymbol{\epsilon}, \quad \frac{\partial \Psi(\pmb{m},\boldsymbol{\sigma},T)}{\partial T}=-s.
	:label: equations_state

It is sometimes more convenient to have a function of :math:`\pmb{h}` instead of :math:`\pmb{m}`. The Gibbs free energy is then defined as

.. math::
	g(\pmb{h},\boldsymbol{\sigma},T)=\Psi-\mu_0\pmb{h} \cdot \pmb{m}
	:label: gibbs
	
where the second therm denotes the :term:`Zeeman energy`. The equations of state can be used to write the constitutive laws even if it is not mandatory.



Minimal integrity basis for cubic symmetry
------------------------------------------


