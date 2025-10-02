Project Sentinel
A Two-Factor Biometric Security Framework for Windows that adds a mandatory facial recognition layer for both system logon and individual application access.

This project serves as a high-performance security enhancement for PCs, especially those lacking built-in biometric hardware like Windows Hello. The system is being developed as a two-year bachelor thesis.

Table of Contents
About The Project

Key Features

System Architecture

Technology Stack

Development Roadmap

Getting Started

License

Contact

About The Project
Project Sentinel is a C++ based security application designed to add a robust layer of biometric security to the Windows operating system. It operates through a single core biometric engine that powers two primary security functions: second-factor authentication at the system logon level and granular, per-application access control once the user is logged in.


The core vision is to provide a seamless yet high-security solution that integrates deeply with the operating system for maximum reliability and performance.

Key Features

Windows Logon Lock (Second-Factor Authentication): After a user successfully enters their standard Windows password, Project Sentinel intercepts the login process and requires a successful face scan before granting access to the desktop. This serves as the "main gate" security layer.



Application Lock (Internal Security): A silent background service continuously monitors for attempts to launch specific, user-protected applications (e.g., browsers, finance software). It freezes the application launch and requires a face scan to proceed, acting as a "secure vault" for sensitive software.


System Architecture
The project is built on a three-component architecture, with each part designed for a specific, low-level task. Communication between the high-privilege components and the user-facing GUI is handled securely via Named Pipes.


The Credential Provider (.dll)

A specialized COM library that integrates directly with the Windows Logon UI (Winlogon).


Its primary function is to trigger the facial scan 

after a successful password entry but before the desktop is shown.

The Background Security Service (.exe)

A persistent Windows Service that runs with high privileges from system startup.

It is responsible for monitoring running processes, intercepting the launch of protected applications, and initiating the verification process.

The Verification GUI (.exe)

A lightweight, pop-up graphical interface that displays the camera feed and performs the face scan.

It is launched by either the Credential Provider (at logon) or the Background Service (for apps) and communicates the success or failure result back to the calling process.

Technology Stack
The project leverages C++ for performance and low-level system access.


Platform: Windows (64-bit) 


IDE: Visual Studio 2022 

Core Libraries:


Windows API (Win32/Win64): The primary tool for creating the Service, Credential Provider, and for process control.


OpenCV: Used for camera access and real-time image handling.


Dlib: Used for high-accuracy face detection and the generation of biometric facial embeddings.


Dear ImGui: Used to create the simple, lightweight pop-up verification GUI.

Development Roadmap
The project is being built in six distinct phases to ensure a structured and manageable development process.

[x] Phase 0: Project Architecture & Planning


Phase 1: Foundation & Environment Setup 


Phase 2: The Core Security Service (Process Interceptor) 


Phase 3: The C++ Biometric Engine (Model Training) 


Phase 4: The Verification GUI 


Phase 5: The Credential Provider (Logon Integration) 


Phase 6: Final Integration, Communication & Packaging (Installer) 

Getting Started
This project is currently in the planning phase. The source code will be made available as development progresses through the roadmap.

To contribute or build the project in the future, you will need the following prerequisites:

Windows 10/11 (64-bit)

Visual Studio 2022 with the "Desktop development with C++" workload

vcpkg or manual setup for the following libraries:

OpenCV

Dlib

Dear ImGui

License
Distributed under the MIT License. See LICENSE for more information.

Contact
alouanemoad@gmail.com

Project Link: [https://github.com/your-username/project-sentinel](https://github.com/AlouaneMoad/Low-Level-System-Integration-Biometrics-Architecture)









