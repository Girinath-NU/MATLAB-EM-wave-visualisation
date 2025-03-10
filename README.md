# Polarization of Electromagnetic Waves

This repository contains a MATLAB script that visualizes different types of **electromagnetic wave polarizations** in 3D using animations.

## Overview
The script simulates and plots **three types of wave polarizations**:
- **Linear Polarization**: The electric field oscillates in a single direction.
- **Circular Polarization**: The electric field rotates in a circular motion in the XY-plane.
- **Elliptical Polarization**: The electric field traces an ellipse due to different amplitudes in the X and Y directions.

## Code Explanation

### **1. Initialization**
```matlab
clc;
clear;
close all;
```
- Clears the command window, workspace, and closes all figures.

### **2. Defining Constants**
```matlab
A = 1;                % Amplitude of the wave
k = 2 * pi;           % Wave number
omega = 2 * pi;       % Angular frequency
```
- These values define the oscillations of the electromagnetic wave.

### **3. Creating a Time and Space Grid**
```matlab
t = linspace(0, 4, 200); 
z = linspace(0, 4, 200); 
[T, Z] = meshgrid(t, z);
```
- `t` (time) and `z` (position) are defined from 0 to 4 with 200 points for smooth animations.
- `meshgrid` generates a 2D grid for calculations.

### **4. Wave Equations for Different Polarizations**

#### **Linear Polarization**
```matlab
Ex_linear = A * cos(omega * T - k * Z);
Ey_linear = zeros(size(Ex_linear));
```
- `Ex_linear` follows a cosine wave.
- `Ey_linear` is always zero, meaning no Y-component.

#### **Circular Polarization**
```matlab
Ex_circular = A * cos(omega * T - k * Z);
Ey_circular = A * sin(omega * T - k * Z);
```
- `Ex` and `Ey` have equal amplitudes but are 90° phase-shifted, forming a circular trajectory.

#### **Elliptical Polarization**
```matlab
Ex_elliptical = A * cos(omega * T - k * Z);
Ey_elliptical = 0.5 * A * sin(omega * T - k * Z);
```
- `Ey_elliptical` has a lower amplitude (0.5A), forming an **elliptical path** instead of a circle.

### **5. Plotting and Animating the Graphs**

Each subplot represents a different polarization:
```matlab
for i = 1:length(t)
```
- The loop iterates over time to animate the wave propagation.

#### **Linear Polarization (Red)**
```matlab
subplot(1, 3, 1);
plot3(Ex_linear(:, i), Ey_linear(:, i), Z(:, i), 'r', 'LineWidth', 2);
```
- Displays a straight-line oscillation.

#### **Circular Polarization (Green)**
```matlab
subplot(1, 3, 2);
plot3(Ex_circular(:, i), Ey_circular(:, i), Z(:, i), 'g', 'LineWidth', 2);
```
- Shows a **circular motion** in the XY-plane.

#### **Elliptical Polarization (Blue)**
```matlab
subplot(1, 3, 3);
plot3(Ex_elliptical(:, i), Ey_elliptical(:, i), Z(:, i), 'b', 'LineWidth', 2);
```
- Displays an elliptical trajectory.

### **6. Animation Control**
```matlab
pause(0.03);
if i < length(t)
    clf;
end
```
- `pause(0.03);` slows down the animation for better visualization.
- `clf;` clears the figure for the next frame.

---

## **Graph Interpretations**

### **1. Linear Polarization** (Left Subplot - Red)
- The **electric field oscillates in a straight line** along `Ex`.
- `Ey` remains zero, meaning no Y-component.
- Common in **radio waves and linearly polarized light**.

### **2. Circular Polarization** (Middle Subplot - Green)
- The **electric field rotates in a circular pattern** in the XY-plane.
- `Ex` and `Ey` have equal amplitudes but **90° phase difference**.
- Used in **GPS signals, antennas, and 3D glasses**.

### **3. Elliptical Polarization** (Right Subplot - Blue)
- Similar to circular polarization, but `Ey` has a lower amplitude.
- Forms an **elliptical trajectory** instead of a circle.
- Found in **optical fibers and certain reflected light waves**.

---

## **Conclusion**
- This script effectively **visualizes different types of wave polarizations** in 3D.
- The animations help in understanding **how electric fields behave in different polarization states**.
- The code can be modified for **different frequencies, amplitudes, or time steps** for further analysis.
