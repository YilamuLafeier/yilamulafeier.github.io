---
layout: project
type: project
image: img/hackintosh/hackintosh.png
title: "Hackintosh (macOS 11.2.2 \"Big Sur\")"
date: 2021
published: True
labels:
  - Solo
  - Apple
  - OS
  - Hardware
  - Software
summary: "**DISCLAIMER: Installing Apple software, while NOT illegal, does violate the End User License Agreement (EULA) I will take down this project if need be** macOS 11.2.2 Big Sur running on an HP 800 G1 SFF."
---

**I will continue to add to this article- I am unable to find the EFI folder I used at the moment**

Being able to successfully boot and run macOS on a machine designed to run Windows is one of my greatest and most challenging achievements yet. While against Apple's EULA, I learned a lot from the experience regarding computer hardware and OSes, and I gleaned a basic understanding of kernels. My discovery of "hackintoshing" is actually what pushed me to pursue an education in computer science in the first place. While I have not revisited the scene since a security patch broke my installation, I hope to work with similar topics in my career.

The entire endeavor took me a few months to get working smoothly. Using [Dortania's guide]([url](https://dortania.github.io/OpenCore-Install-Guide/)https://dortania.github.io/OpenCore-Install-Guide/), I used the tools offered in the guide and essentially took a crash course on the subject. While I did not have to code for this project, most of my work lay in fully understanding my machine and how the kernels I was injecting into the installation worked. Opencore serves as the tweak injector. It is a boot loader designed to allow most machines (Apple and non-Apple) compatibility with macOS. My processor type is what decided most of what I could install especially now that Apple is fully transitioning to pure Apple Silicon support. The architecture of the processor (Intel Core i7-4790 @3.90GHz) I had- Haswell -is supported up to macOS 12. Big Sur also required my machine's USB ports to be mapped out as well as the Thunderbolt functionalities disabled (Thunderbolt was originally made for Apple by Intel so during installation it would cause issues since it did not have supported firmware- I will have to check the kernel panic bug reports when I find the EFI folder). Another issue I did not find a solution to was getting my PC's audio codec to work with the macOS. Much of the process is a trial-and-error process with numerous layout IDs linked with specific codecs.

While the entire endeavor involved using automated tools for certain tasks, it served as a learning experience for me. I had never done something so technical in the field of computers before and most of what I know now about computers (Mac and macOS specifically) was gleaned from this project. I still have to PC used for the project as well- the boot files will be shared here (I will open it only to @hawaii.edu emails).
