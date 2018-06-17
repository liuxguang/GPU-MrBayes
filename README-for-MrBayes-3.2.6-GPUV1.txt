   GPU MrBayes V3.2.6 Manual 

          Mingming Ren, Qiang Ren, Yilin Wang, Zhuangzhuang Liu, Rebecca Stones, Xiaoguang Liu, Gang Wang

    June 16, 2018



1.  Introduction
2.  Getting Started
3.  License and Warranty
-------------------------------------------------------------------------

1. Introduction
===============

Welcome to use our modified MrBayes. We implement an efficient GPU MrBayes V3.2.6 on CUDA.

This work has submitted manuscript to MBE (Molecular Biology and Evolution) 2018 

in the area of Software and Database Updates. 


We provide you GPU MrBayes as a modified version of MrBayes 3.2.6 (the latest version), 

which enables running Metropolis-Coupled  Markov Chain Monte Carlo (MC)^3 sampling on one or multipile GPU(s). 


The modified MrBayes support you to analyze three kinds of frequently-used models 

-DNA, Protein and codon- on GPU with a significant speedup over serial MrBayes. 


GPU MrBayes requires NVIDIA's CUDA, therefore non-NVIDIA GPUs will not run GPU MrBayes. 

GPU MrBayes has to be ran on the NVIDIA cards with Compute Capability of 2.0 and above.


-------------------------------------------------------------------------


2. Getting Started
==================

The following instructions take you through a sequence of steps to get

the default configuration of GPU-MrBayes up and running.


(a) Pre-Requirements:

    * gcc
    * GPU cards & CUDA (a newer version is recommended)
    * MPICH2 (if you have multi-GPUs)


(b) Unpack the zip file and go to the top level directory:

    * unrar MrBayes-3.2.6-GPU-V1.rar
  
    * cd MrBayes-3.2.6-GPU-V1


(c) Specify the building configure according to your need and hardware environment

  open 'Makefile' modify CUDA & MPI path:

    * CUDA path: modify parameter 'CDUA_INSTALL_PATH' to the path where you install CUDA       on your computer. 
      For UNIX-like environments, the path probably to be in '/usr/local/cuda-*.*'.

    * MPI include: 'MPIINCLUDE' should point to the include path of MPI library.

    * If you don't use MPI, set parameter 'MPI' to 'no' which is also the default value.

    * As we modify MrBayes to use CUDA, the value of 'CUDA' should always be 'yes'. 
      Of course you can change it to 'no', then you will use MrBayes as serial version.

    * MPI: if you want to use mpi, then change 'MPI ?= no' to 'MPI ?=	yes'


(d) Build GPU MrBayes:

    for all shells execute the command:

      make


(e) Run GPU MrBayes: ('mb' and data set file should be in the same directory)

    if compile without mpi: ./mb dataset.nex
 
    otherwise: mpirun -np n ./mb dataset.nex
 
    For example:  mpirun -np 2 ./mb dataset.nex

    (Here 'n' means the number of GPUs you want to and can use, and its value should be
    the number of chains at most. 

    For example, MrBayes always run eight chains by default, 
    so you can set 'n' from 1 to 8.)
 
-------------------------------------------------------------------------



3. License and Warranty
=======================

GPU MrBayes is free software; you can redistribute it and/or modify it under the

terms of the GNU General Public License as published by the Free Software

Foundation; either version 3 of the License, or (at your option) any later version.

The program is distributed in the hope that it will be useful, but WITHOUT

ANY WARRANTY; without even the implied warranty of

MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the

GNU General Public License for more details

(http://www.gnu.org/copyleft/gpl.html).
