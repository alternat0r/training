# Chapter 2: Analysis on malware2.exe
[![Progress](https://img.shields.io/badge/Progress-20%25-orange.svg)]()
[![Status](https://img.shields.io/badge/Status-Incomplete-orange.svg)]()
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Star&maxAge=100)]()
##### This articles use for training purpose only.
This second training articles designed to archive a very basic skills in malware analysis. We will show you how to analyze a sample of malware called 'malware2.exe'. Consider this binary file is unknown binary (for training purpose). The malware sample given are slightly advance and we will analyze the sample using several more tools.

## Table of Contents
- [What do you need?](#what-do-you-need)
  - [Tools](#tools)
- [Preparation](#preparation)
- [Questionaire](#questionaire)
- [Eradication and Removal](#eradication-and-removal)
- [What do we have learn?](#what-do-we-have-learn)

## What do you need?
- A binary samples called '**malware2.exe**' (MD5: **a30246c162a9a33cd12f0bd7a62619de**)
  - Extract from the Zip file with password '**infected**'.
  - [![Download-Here](https://img.shields.io/badge/Download%20Sample-Here-brightgreen.svg)](https://github.com/alternat0r/training-basic-malware2/raw/master/malware2.zip)

#### Tools
  - [EXEinfo PE](http://exeinfo.pe.hu/)
  - [UPX](http://upx.sourceforge.net/)
  - [Frhed](http://frhed.sourceforge.net/en/)

## Questionaire
  1. [Is it packed? If so, what kind of packer?](#is-it-packed-if-so-what-kind-of-packer)
  2. [Does it potentially perform any kind of network activity?](#does-it-potentially-perform-any-kind-of-network-activity)
  3. [Is it malicious? If so, what kind of malware is this?](#is-it-malicious-if-so-what-kind-of-malware-is-this)

#### Is it packed? If so, what kind of packer?

To detect whether the **malware2.exe** has been packed or not. You can simply use **EXEinfo PE**. Simply drag and drop malware2.exe on top of EXEinfo PE program.

![train-exeinfo](https://cloud.githubusercontent.com/assets/1006000/14888961/3761e57a-0d8f-11e6-9256-4f48cbdafbe9.png)

You can see from the image above EXEinfo PE able to detect the file is packed with UPX tools. **UPX** is a free and open source file executable compressor. Its also provide special option to unpack the packed PE file.

To confirm this is really packed with UPX, we can see it in hex editor program view. We use **Frhed** to do this:

[![Download Frhed](https://img.shields.io/badge/Download-FrHed-brightgreen.svg)](http://frhed.sourceforge.net/en/)

Simply open the **Frhed** program and load the **malware2.exe**. You should see as image below:

![train-frhed](https://github.com/alternat0r/training-basic-malware-analysis/raw/master/Chapter-2/src/train-frhed.png)

The image above show you there is UPX signature on PE header. Usually, UPX packer will leave a 'UPX' string signature along with its version number. Now it is comfirmed the malware2.exe is packer with UPX packer.

To unpack the the malware2.exe download the UPX tool below:

[![Download UPX](https://img.shields.io/badge/Download-UPX-brightgreen.svg)](http://upx.sourceforge.net/)

To unpack, follow these step:
   1. Open command prompt and type **upx -d malware2.exe** and hit ENTER
   2. You should see the file is successfully unpacked as shown in image below.

![train-upx](https://cloud.githubusercontent.com/assets/1006000/14889620/24775212-0d92-11e6-8b87-6a2c52f454c8.png)

Now to answer the question, the **malware2.exe** is packed. The packer it's used is **UPX**.

**NOTE:** At this point you will notice the **malware2.exe** file size is increased. This is due to the unpacking process done by UPX. The **malware2.exe** now back to its original file size.

#### Does it potentially perform any kind of network activity?

Now this time we will use another tools originally produced by iDefense Group called **fakeDNS**. It is free and available with source code. Download here:

[![Download FakeDNS](https://img.shields.io/badge/Download-FakeDNS-brightgreen.svg)](https://github.com/alternat0r/MAP/raw/master/fakeDNS.exe)

**NOTE**: You may need additional dependencies file called **MSWINSCK.OCX** in order to run this program.

---

**To Install Dependencies**
  1. Download MSWINSCK.OCX [file here](https://github.com/alternat0r/MAP/raw/master/dependancies/MSWINSCK.OCX).
  2. Register MSWINSCK.OCX using command **regsvr32 MSWINSCK.OCX** at Command Prompt.

---

#### Is it malicious? If so, what kind of malware is this?

## Eradication and removal

We already identify all [indicator of compromise](https://en.wikipedia.org/wiki/Indicator_of_compromise) (IoC) that we need. At this point, we can make our own remover to simplified the task. We can use as simple as Windows batch script. To begin with the removal step lets take a look what IoC we have so far:

  * Process
  * Files
  * Registry
  * Network firewall
  
```
REM Windows Batch Script for Generic Malware Removal
REM This will force to terminate the specified process name.
taskkill /F /IM xxx.exe

REM This will check if the location file of malware exist or not. If exist, delete it.
if exist "C:\xxx.exe" goto REMOVEIT
:REMOVEIT
del C:\xxx.exe

REM This will check for malware persistence in Windows registry. If exist, delete it.
reg delete HKLM\Software\Microsoft\Windows\Current\Version\Run /v xxx
```


## What you have learned today?

  1. Learn using more useful tools.
  2. Learn more advanced technique.
