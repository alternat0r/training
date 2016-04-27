# Basic Malware Analysis on malware1.exe
[![Progress](https://img.shields.io/badge/Progress-90%25-blue.svg)]()
[![Status](https://img.shields.io/badge/Status-Incomplete-orange.svg)]()
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Star&maxAge=100)]()
##### This articles use for training purpose only.
This training articles designed to archive a very basic skills in malware analysis. We will show you how to analyze a sample of malware called 'malware1.exe'. Consider this binary file is unknown binary (for training purpose). You will learn at very basic how to identify whether the binary file is malicious or not.

## Table of Contents
- [What do you need?](#what-do-you-need)
  - [Tools](#tools)
- [Preparation](#preparation)
- [Questionaire](#questionaire)
- [What do we have learn?](#what-do-we-have-learn)

## What do you need?
- A binary samples called '**malware1.exe**' (MD5: **a025fcd7649bb3538081aadedda48569**)
  - Extract from the Zip file with password '**infected**'.
  - [![Download-Here](https://img.shields.io/badge/Download%20Sample-Here-brightgreen.svg)](https://github.com/alternat0r/training-malware1/raw/master/malware1.zip)
- Tools
  - [FileAlyzer](https://www.safer-networking.org/products/filealyzer/ "Download FileAlyzer here if you dont have yet")
  - [PEview](http://wjradburn.com/software/PEview.zip "Download PEview here")
  - [PE Explorer](http://www.heaventools.com/download-pe-explorer.htm "Download PE Explorer here")
  - [EXEinfo PE](https://sourceforge.net/projects/exeinfope/files/exeinfope.zip/download)
  - [Dependency Walker](http://www.dependencywalker.com/)
  - [Wireshark](https://www.wireshark.org/#download)
  - [RawCap](http://www.netresec.com/?page=RawCap)
- Virtual Machine - [VMware Workstation](https://my.vmware.com/web/vmware/info?slug=desktop_end_user_computing/vmware_workstation/10_0) or [Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads)

## Preparation

Before we start analyzing the malware sample, you need to do/have the following:
  1. Install VMWare Workstation or Virtual Box.
  2. Installed with Microsoft Windows operating system. Windows 7 should be fine.
  2. Take a clean Snapshot.

## Questionaire

In this training you will be given a malware samples called '**malware1.exe**'. You will be analyzed based on the question below:
  1. [What type of file format is this?](#what-type-of-file-format-is-this)
  2. [Is it packed?](#is-it-packed)
  3. [Does it potentially perform any kind of network activity?](#does-it-potentially-perform-any-kind-of-network-activity)
  4. [Is it malicious? If so, what kind of malware is this?](#is-it-malicious-if-so-what-kind-of-malware-is-this)

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

#### Is it packed?

There is a lot of tools we can use to identify whether the binary file is packed or not. We can simply use tools called '**EXEinfo PE**'.

[![Download EXEinfo PE](https://img.shields.io/badge/Download-EXEinfo%20PE-brightgreen.svg)](https://sourceforge.net/projects/exeinfope/files/exeinfope.zip/download)

To use this tools, just simply drag and drop **malware1.exe** on top of **EXEinfo PE** program.

![3](https://cloud.githubusercontent.com/assets/1006000/14825298/db1b2bac-0c0b-11e6-9572-16d2eb84635a.png)

From the tools (image above), you can see its saying '**Not packed**'. Now we know that the **malware1.exe** is not packed with any file executable compressor.

#### Does it potentially perform any kind of network activity?

There is several way to identify whether the **malware1.exe** contain any kind of network activity. The easiest way is by using  **Dependency Walker** to identify its PE import table.

[![Download Dependency Walker](https://img.shields.io/badge/Download-Dependency%20Walker-brightgreen.svg)](http://www.dependencywalker.com/)

![5](https://cloud.githubusercontent.com/assets/1006000/14826524/d5d289ec-0c10-11e6-94a2-b6e50e6a46fd.jpg)

From the image above show you that there is two(2) DLL files has been used. Which is **WSOCK32.DLL** and **WININET.DLL**. Both DLL files are used to make network communication. In this case, the malware is capable to make network communication over the internet based on its function as shown on the top-right pane.

Another way to identify malware network activity is by executing the **malware1.exe** inside Virtual Machine and captured its network packet using **Wireshark** software.

[![Download Wireshark](https://img.shields.io/badge/Download-Wireshark-brightgreen.svg)](https://www.wireshark.org/#download)

But first, you need to download another additional tools called **RawCap**. This will allow us to capture network packet on localhost adaptor as new Wiresharp no longer supporting it.

[![Download RawCap](https://img.shields.io/badge/Download-RawCap-brightgreen.svg)](http://www.netresec.com/?page=RawCap)

![train-rawcap](https://cloud.githubusercontent.com/assets/1006000/14843410/86cd5bf2-0c82-11e6-8b72-723f155621b4.png)

To capture network packet from the malware, follow these step:
  1. Once you have download the **RawCap**, all you have to do is run the **RawCap.exe** using command prompt.
  2. Select an adapter. Make sure to choose '**Loopback**' interface.
  3. Press Enter to start capturing. By default .pcap file will be save at the same directory as **RawCap.exe**.
  4. Then, run the **malware1.exe** and wait few seconds or minutes.
  5. Press **CTRL+C** to stop capturing.
  6. By default, the pcap file name is '**dumpfile.pcap**'.

Analyzing **dumpfile.pcap**:
  1. Open the **dumpfile.pcap** using **Wireshark**.
  2. Start looking for TCP with port number range from 6667 to 6669. This will indicate to IRC port number.
  3. Also, look at the data packet containing **NICK** and **USER**. This indicate to IRC client trying to connect to IRC server with user nickname.

![train-wireshark](https://cloud.githubusercontent.com/assets/1006000/14847029/2954d98e-0c99-11e6-8a30-adab3a0c5cb4.png)

As image above show you the packet containing several information related to IRC.

Other useful tool you can use is **Mandiant ApateDNS**. You can download it free from the link below:

[![Download ApateDNS](https://img.shields.io/badge/Download-ApateDNS-brightgreen.svg)](https://www.fireeye.com/services/freeware/mandiant-apatedns.html)

Before we can use this tools, you need to stop a specific Windows Service first called 'Internet Connection Sharing (ICS)'. To do that:

  1. Simply open command prompt and type **net stop SharedAccess** and press ENTER.

To begin the analysis using **ApateDNS**:

  1. Run **apatedns.exe**.
  2. Make sure on '**Selected Interface:**', choose **Microsoft Loopback Adapter**.
  3. Press **Start Server** button.
  4. Run **malware1.exe**.
  5. See the result.

![train-apatedns](https://cloud.githubusercontent.com/assets/1006000/14844386/974d460c-0c89-11e6-98e2-66c48924023a.png)

Based on the image above, we can see ApateDNS captured a domain name that trying to communicate with IRC server.

#### Is it malicious? If so, what kind of malware is this?

Yes, based on earlier analysis. It is most likely an IRC bot.

Last but not least, we can use another tools that can simplified all your task above with single tools called '**PEstudio**'. PEstudio is a free software developed by **Marc Ochsenmeier** to help CERT identify the risk of specific binary files.

![4](https://cloud.githubusercontent.com/assets/1006000/14825578/1430c86a-0c0d-11e6-8894-f8a584fa7128.png)

## What do we have learn?

  1. A basic concept of malware analysis
  2. Using multiple tools
  3. Learn basic malware behaviour.
  
