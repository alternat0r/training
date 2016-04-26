# Basic Malware Analysis on malware1.exe
[![Waffle.io](https://img.shields.io/waffle/label/evancohen/smart-mirror/in%20progress.svg?maxAge=2592000)]()
[![Wercker](https://img.shields.io/wercker/ci/wercker/docs.svg?maxAge=2592000)]()
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Star&maxAge=100)]()
##### This articles use for training purpose only.
This training articles designed to archive a very basic skills in malware analysis. We will show you how to analyze a sample of malware called 'malware1.exe'. Consider this binary file is unknown binary (for training purpose). You will learn at very basic how to identify whether the binary file is malicious or not.

## Table of Contents
- [What do you need?](#what-do-you-need)
  - [Tools](#tools)
- [Preparation](#preparation)
- [Questionaire](#questionaire)

## What do you need?
- A binary samples called '**malware1.exe**' (MD5: **a025fcd7649bb3538081aadedda48569**)
  - Extract from the Zip file with password '**infected**'.
  - [![Download-Here](https://img.shields.io/badge/Download%20Sample-Here-brightgreen.svg)](https://github.com/alternat0r/training-malware1/raw/master/malware1.zip)
- Tools
  - Notepad
  - [FileAlyzer](https://www.safer-networking.org/products/filealyzer/ "Download FileAlyzer here if you dont have yet")
  - [PEview](http://wjradburn.com/software/PEview.zip "Download PEview here")
  - PE Explorer
  - EXEinfo PE

## Preparation

Before we start analyzing the malware sample, you need to do/have the following:
  1. Install VMWare Workstation or Virtual Box.
  2. Installed with Microsoft Windows operating system. Windows 7 should be fine.
  2. Take a clean Snapshot.

## Questionaire

In this training you will be given a malware samples called '**malware1.exe**'. You will be analyzed based on the question below:
  1. [What type of file format is this?](#what-type-of-file-format-is-this)
  2. Is it packed?
  3. Does it potentially perform any kind of network activity?
  4. Is it malicious? If so, what kind of malware is this?

#### What type of file format is this?

There is several way to identify what file format of the specific file. In this training we will use free tool called PEview.

[![Download PEview](https://img.shields.io/badge/Download-PEview-brightgreen.svg)](http://wjradburn.com/software/PEview.zip)

![1](https://cloud.githubusercontent.com/assets/1006000/14823868/9a5947e8-0c06-11e6-82f5-9b8fa0116d03.png)

##### To detect what format of the file:
1. Just simple drag and drop the file on top of the PEview program.
2. Navigate to **IMAGE_DOS_HEADER** at PEview left pane.
3. At the right pane, you should see the first row saying '**IMAGE_DOS_SIGNATURE MZ**'.
  - This is where the signature of Portable Executable file is identified.

##### You also can use other tools such as PE Explorer to identify more details:

[![Download PE Explorer](https://img.shields.io/badge/Download-PE%20Explorer-brightgreen.svg)](http://www.heaventools.com/download/pexsetup.exe)

![2](https://cloud.githubusercontent.com/assets/1006000/14824704/795331aa-0c09-11e6-8ec7-6484fa84c3da.png)

From the image above show you the magic number which is **010F**. This magic number indicate the executable file is compiled with 32-bit compiler or simply known as **PE32**.

#### It is packed?

There is a lot of tools we can use to identify whether the binary file is packed or not. We can simply use tools called '**EXEinfo PE**'.

[![Download EXEinfo PE](https://img.shields.io/badge/Download-EXEinfo%20PE-brightgreen.svg)](https://sourceforge.net/projects/exeinfope/files/exeinfope.zip/download)

To use this tools, just simply drag and drop **malware1.exe** on top of **EXEinfo PE** program.

![3](https://cloud.githubusercontent.com/assets/1006000/14825298/db1b2bac-0c0b-11e6-9572-16d2eb84635a.png)

From the tools (image above), you can see its saying '**Not packed**'. No we know that the **malware1.exe** is not packed with any file executable compressor.

