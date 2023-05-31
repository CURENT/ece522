# UTK ECE 522 - Power System Analysis II

Hands-on Project for using ANDES in Power System Transient Stability Analysis.

# Background

In Spring 2023, Dr. Kevin Tomsovic will offer the graduate course [ECE
522](https://catalog.utk.edu/preview_course_nopop.php?catoid=4&coid=45524) at
University of Tennessee, Knoxville (UTK).

The course covers topic:

- Operation and control of interconnected power systems, transient and dynamic
  stability
- Formulating and solving problems in matrix-vector form with application to
  large-scale power systems

In the course, ANDES of the CURENT Large Scale Testbed is employed as the
teaching tool for power system transient stability studies.

# Objective

In this project, you will learn to:

1. Investigate power system transient stability using ANDES
2. Develop power system dynamic model in ANDES

# Table of Content

1. [Tutorial](./tutorial/)

   1. [Chapter 1 - Getting Started with ANDES](./tutorial/ch1.ipynb)
   2. [Chapter 2 - ANDES File Conversion and Configuration](./tutorial/ch2.ipynb)
   3. [Chapter 3 - Critical Clearing Time](./tutorial/ch3.ipynb)
   4. [Chapter 4 - Model Development of an Open-loop PI Controller](./tutorial/ch4.ipynb)
   5. [Chapter 5 - Model Development of an Close-loop PI Controller](./tutorial/ch5.ipynb)
2. [Final project - Dynamic Model Development in ANDES](./final/FinalProject.md)

# ANDES

ANDES is an open-source Python library for power system modeling, computation,
analysis, and control. It supports power flows calculation, transient stability
simulation, and small-signal stability analysis for transmission systems.

> H. Cui, F. Li and K. Tomsovic, "Hybrid Symbolic-Numeric Framework for Power
> System Modeling and Analysis," in IEEE Transactions on Power Systems, vol. 36,
> no. 2, pp. 1373-1384, March 2021, doi: 10.1109/TPWRS.2020.3017019.

# License

This project is licensed under [MIT License](./LICENSE).
