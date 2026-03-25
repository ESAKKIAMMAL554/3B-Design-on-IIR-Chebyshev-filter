# IIR-FILTER-DESIGN

# EXP 3 B: DESIGN OF LOW PASS CHEBYSHEV IIR FILTER USING BILINEAR TRANSFORMATION

# AIM: 

# To a design of low pass Chebyshev IIR filter using Bilinear Transformation.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc ; 
close ; 
wp=input('Enter the pass band frequency (Radians )= ' ); 
ws=input('Enter the stop band frequency (Radians )= ' ); 
alphap=input( ' Enter the pass band attenuation (dB)=' ); 
alphas=input( ' Enter the stop band attenuation(dB)=' ); 
T=input('Enter the Value of sampling Time='); 
//Pre warping- Bilinear Transformation 
omegap=(2/T)*tan(wp/2); 
disp(omegap,'omegap='); 
omegas=(2/T)*tan(ws/2); 
disp(omegas,'omegas='); 
//Order of the filter 
N=acosh(sqrt(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1)))/(acosh(omegas/omegap));  
disp(N,'N='); 
N=ceil(N); 
disp(N,'Round off value of N='); 
//Cut off frequency 
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N))); 
disp(omegac,'omegac='); 
Epsilon = sqrt ((10^(0.1*alphap))-1); 
disp(Epsilon,'Epsilon='); 
[pols ,gn] = zpch1(N, Epsilon,omegap ); 
disp(gn,'Gain'); 
disp(pols,'Poles'); 
hs=poly(gn,'s','coeff')/real(poly(pols,'s'));  
disp(hs,'Analog Low pass Chebyshev Filter Transfer function'); 
z=poly(0,'z');//Defining variable z
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation 
disp(Hz,'Digital LPF Transfer function H(Z)='); 
HW=frmag(Hz,512); // Frequency response 
w=0:%pi/511:%pi ; 
plot(w/%pi,abs(HW)); 
xlabel(' Normalized Digital Frequency w'); 
ylabel('Magnitude '); 
title(' Frequency Response of Chebyshev IIR LPF');
```
## calculations:
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/b0ed11d9-e35d-4efc-9256-b825d1b04382" />
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/29e69b27-6b7d-4a33-bc67-efa40bec53cd" />
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/ff3de191-9901-4270-8774-2aae053c3358" />


# OUTPUT: 
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/f1f6e617-da08-42a6-9c70-5afefefbcea3" />
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/51245df3-51b8-4a8c-95e1-827723cdeede" />


# RESULT: 
Thus design of Chebyshev Low pass IIR filter waveforms were plotted and output was
verified.
