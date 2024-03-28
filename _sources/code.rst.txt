MATLAB implementation
=====================

First save the magnetic loading vector :math:`h` in a file. 

.. code-block:: matlab

   hmax=15000;
   NbPts=400;
   h=[linspace(1e-3,hmax,NbPts),linspace(hmax,-hmax,NbPts),linspace(-hmax,hmax,NbPts)];
   save('h','h')

Same thing for the structure CSTES that involves all the material parameters

.. code-block:: matlab

   CSTES.ms=1.5e6;
   CSTES.a=2000;
   CSTES.chi_eq=100;
   CSTES.Hc=2000;
   save('CSTES','CSTES')

The main file is used to implement load a constant structure CSTES, launch the simulation and plot the results. Here, the remanent magnetization :math:`m_\text{r}` is equal to zero.

.. code-block:: matlab

   clear 
   close all
   clc
   
   load('CSTES.mat');
   load('h.mat');
   mr=0;
   [m,hi]=hysteresis(h,mr,CSTES);
   plot(h,m)

Implementing :eq:`full_hysteresis` is straight forward. The inputs are the magnetic field :math:`h`, the remanent magnetization :math:`m_\text{r}` and the structure CSTES.
   

.. code-block:: matlab

   function [m,hi]=hysteresis(h,mr,CSTES)
   %Initialization of variables using the remanent magnetization
   chi_eq=CSTES.chi_eq;
   Hc=CSTES.Hc;
   m(1)=mr;
   hi(1)=h(1)-inv_Man(mr,CSTES);
   for i=2:length(h)
   	dh=h(i)-h(i-1);
   	delta=dh/abs(dh);
   	%Explicit Euler
   	f=@(x) abs((1-delta*hi(i-1)/Hc)/chi_eq*(Man(h(i)-x,CSTES)-m(i-1))+hi(i-1)-x);
   	%Implicit Euler
   	f=@(x) abs((1-delta*x/Hc)/chi_eq*(Man(h(i)-x,CSTES)-m(i-1))+hi(i-1)-x);
   	x0=hi(i-1);
   	hi(i)=fminsearch(f,x0);
   	hr(i)=h(i)-hi(i);
   	m(i)=Man(hr(i),CSTES);
   end
   end
   
It now remains to specify Man and inv_Man functions. The choice of Man is free to the user. For illustration, we have implemented a Langevin function that involves the saturation magnetization :math:`m_\text{s}` and the material constante :math:`a`.

.. code-block:: matlab

   function m=Man(hr,CSTES)
   m=CSTES.ms*(coth(hr./CSTES.a)-CSTES.a./hr);
   end
   
The inverse Langevin function is approximated since no analytical expression exists.

.. code-block:: matlab

   function hr=inv_Man(x,CSTES)
   y=x/CSTES.ms;
   hr=CSTES.a*(y.*(3-y.^2)./(1-y.^2)-0.488*abs(y).^2.243.*y+...
   	3.311*abs(y).^3.789.*y.*(abs(y)-0.76).*(abs(y)-1));
   end
