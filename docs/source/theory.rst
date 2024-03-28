Some elements of theory
=======================

In order to split dissipative and non-disspative effects, on can split the total magnetic field :math:`\pmb{h}` into a reversible :math:`\pmb{h}_\mathrm{r}` and irreversible :math:`\pmb{h}_\mathrm{i}` part such that

.. math::
	\pmb{h}=\pmb{h}_\mathrm{r}+\pmb{h}_\mathrm{i}.
	:label: split_h

Magnetization is related to :math:`\pmb{h}_\text{r}` following the constituve law

.. math::
	\pmb{m}=\text{M}_\text{an}(\pmb{h}_\mathrm{r})
	:label: man
	
where :math:`\text{M}_\text{an}` is an arbitrary function that describe the non-dissipative behavior. The magnetization dissipation is 

.. math::
	\mathcal{D}=\mu_0 \pmb{m} \cdot \dot{\pmb{h}_\text{i}}
	:label: dissipation
	
with :math:`\pmb{m}_\text{i}` the variable associated with :math:`\pmb{h}_\text{i}` and :math:`\mu_0` the :term:`permeability of free space`. To ensure that :math:`\mathcal{D}` is always positive, one can consider the evolution law

.. math::
	\dot{\pmb{h}}_\text{i}=\dot{\lambda} \boldsymbol{\chi}^{-1}\cdot\pmb{m}_\text{i}
	:label: evolution_law

with :math:`\dot{\lambda}` being a positive multiplier and :math:`\boldsymbol{\chi}` a positie definite magnetic susceptibility tensor. We consider

.. math::
	\dot{\lambda}=\dfrac{1}{\tau_1}\left(1-\dfrac{\pmb{h}_\text{i}}{H_\text{c}} \cdot \pmb{e}_{\dot{\pmb{h}}}\right)
	:label: lambda_dot

and

.. math::
	\dot{\pmb{m}}_\text{i}=\tau_{2}\dot{\pmb{m}}.
	:label: mi
	
The full hysteresis model is 

.. math::
	\begin{cases}
		\pmb{h}_\mathrm{r}=\pmb{h}-\pmb{h}_\mathrm{i}. \\
		\dot{\pmb{h}}_\text{i}=\dfrac{\tau_2}{\tau_1}\left(1-\dfrac{\pmb{h}_\text{i}}{H_\text{c}} \cdot \pmb{e}_{\dot{\pmb{h}}}\right) \boldsymbol{\chi}^{-1}\cdot\dot{\pmb{m}}\\
		\pmb{m}=\text{M}_\text{an}(\pmb{h}_\mathrm{r})
	\end{cases}
	:label: full_hysteresis
