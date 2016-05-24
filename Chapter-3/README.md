# Chapter 3: Analysis using Volatility
[![Progress](https://img.shields.io/badge/Progress-20%25-orange.svg)]()
[![Status](https://img.shields.io/badge/Status-Incomplete-orange.svg)]()
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Star&maxAge=100)]()
##### This articles use for training purpose only.
In this training we are going to use special tools called Volatility. This tools will analyze memory dump and provide good amount of information from computer memory. In this training also we will use a sample malware from one of the FakeAV or RogueAV malware. You will be teaching on how to capture volatile memory and save it.

## Table of Contents
- [What do you need?](#what-do-you-need)
  - [Tools](#tools)
- [Preparation](#preparation)
- [Questionaire](#questionaire)
- [Eradication and Removal](#eradication-and-removal)
- [What do we have learn?](#what-do-we-have-learn)

## What do you need?
- A binary samples file is '**f8b21dfa3f165329a9c8e62890b9af2d**' (MD5 hash: **f8b21dfa3f165329a9c8e62890b9af2d**)
  - Extract from the Zip file with password '**infected**'.
  - [![Download-Here](https://img.shields.io/badge/Download%20Sample-Here-brightgreen.svg)](https://github.com/alternat0r/training-basic-malware-analysis/raw/master/Chapter-3/sample_fakeav.zip)
  
![Caution](https://img.shields.io/badge/CAUTION-%20%20This%20is%20real%20malware.%20This%20can%20cause%20harmful%20to%20your%20PCs.%20Please%20use%20Virtual%20Machine%20instead.%20-red.svg)

#### Tools
  - [Volatility](http://www.volatilityfoundation.org/#!releases/component_71401)
  - [AccessData FTK Imager](http://accessdata.com/product-download/digital-forensics/ftk-imager-version-3.1.4)
  - [EXEinfo PE](http://exeinfo.pe.hu/)

## Questionaire
  1. [Does it have persistent mechanism?](#does-it-have-persistent-mechanism)
  2. [Do they have multiple process running?](#do-they-have-multiple-process-running)
  3. [Is there any network connection established?](#is-there-any-network-connection-established)
  4. [Are we able to recover its serial number? if any?](#are-we-able-to-recover-its-serial-number)
  5. [Where does this malware came from?](#where-does-this-malware-came-from)

#### Does it have persistent mechanism?
#### Do they have multiple process running?
#### Is there any network connection established?
#### Are we able to recover its serial number? if any?

Now we know that this malware have its own input form to enter a serial number. If the serial number is correct, you will be able to get rid of the malware. In this part, we will try our best guess to get the serial number from the binary itself.

#### Where does this malware came from?

## What you have learned today?

  1. Learn using advance tools like Volatility.
  2. Discover advance feature of the Volatility.
  3. Volatile memory store large amount of useful information.

## Extra Tips

Some of your organisation may need you to use Volatility as their tools. To make things coming handy, you need the following cheat sheet:
  - http://downloads.volatilityfoundation.org/releases/2.4/CheatSheet_v2.4.pdf
