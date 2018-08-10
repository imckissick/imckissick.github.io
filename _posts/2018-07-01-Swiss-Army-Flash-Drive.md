---
layout: post
title: The Swiss Army Flash Drive
author: Ian McKissick
date: 2018-07-01 22:00:00 -0400
tags: weekend-projects tools
---

# The Swiss Army Flash Drive

## Introduction

## Part 1: The Drive Itself

First things first, I needed a flash drive. And while I've collect many flash drives over the years, all of them are 8GB or smaller. That just wouldn't do. Here's what I was looking for in a flash drive:

1. High capacity
2. Good read/write speed (should be USB 3.0/3.1)
3. Good build quality/durable. Most of my flash drives over the years have died from physical wear-and-tear (I usually keep it on my keychain)

One thing I didn't take into consideration is USB Type-C. While that would be nice, the age of ubiquitous USB Type-C isn't quite here just yet.

I ended picking up a 128 GB [SanDisk Extreme Pro (SDCZ880-128G)](https://www.amazon.com/SanDisk-SDCZ880-128G-G46-Extreme-128GB-Solid/dp/B01MU8TZRV/) on Amazon. At the time of purchase, it was going for ~$70. It's basically a USB 3.1 Solid State Drive. It's complete overkill for this project, but it's also going to be my daily driver flashdrive that I keep on my keychain.

Besides, there's no kill like overkill.

## Part 2: Boot ALL the ISOs

There's nothing novel about bootable flash drives anymore. With optical media on it's way out, you probably installed your OS from flash drive. There's plenty of tools do this. Installing Windows 10? Use Microsoft's Media Creation Tool. Need an all-purpose tool? Try Rufus.

But with these tools, you're making bootable media for a single ISO. That's all well and good for a one-off, but I'm going Swiss Army Knife levels of utility here and need a way to boot multiple ISOs. There's a few options out there. The three most notable I found are:

1. Easy2Boot
2. WinSetupFromUSB
3. YUMI - Multiboot USB Creator

For this project, here's my (relatively basic) requirements:

* I need something where I can just drop the ISO images into place and go
* I need something that can boot multiple OS's (Windows **and** Linux)
* I need it to support booting from an NTFS formatted drive (since this is going to be my daily driver)

Note I didn't mention UEFI support. While I would greatly prefer it, I discovered very quickly while researching this, **NTFS support and UEFI support are effectively mutually exclusive** as the UEFI Standard does not require NTFS support.
Some motherboards do support booting from NTFS, but most are limited to FAT32.
Hopefully more manufactuers will start including an NTFS driver out of the box. But until then... Oh well...

So, how did the three of these hold up? Let's see...

YUMI ([Official Site](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/))

* Can I Drag-and-drop ISOs?
  * No. Adding and removing ISO images from the drive requires running the YUMI setup tool for every change
* Does it support booting Multiple OS's
  * Yes, but requires the drive to be formatted as FAT32
* Can I boot from NTFS?
  * Partially, NTFS _can_ be used, but _only_ if booting Windows ISOs.
* Does it support booting from UEFI?
  * UEFI support is in Beta

WinSetupFromUSB ([Official Site](http://www.winsetupfromusb.com))

* Can I Drag-and-drop ISOs?
  * No. Like YUMI, adding and removing ISO iamges from the drives requires running the WinSetupFromUSB setup tool for every change
* Does it support booting Multiple OS's
  * Yes
* Can I boot from NTFS/ExFAT
  * No. WinSetupFromUSB requires the drive to be formatted as FAT32
* Does it support booting from UEFI?
  * Yes.

Easy2Boot ([Official Site](http://www.easy2boot.com))

* Can I Drag-and-drop ISOs?
  * Yes
* Does it support booting Multiple OS's
  * Yes
* Can I boot from NTFS?
  * Easy2Boot supports NTFS
* Does it support booting from UEFI?
  * Kinda. The process is rather convoluted as it requires swapping out the NTFS partition with a FAT32 partition (and back when you're done).
  * See [here](http://www.easy2boot.com/useful-things-to-know/) for more information

Easy2Boot was the clear winner. While YUMI or WinSetupFromUSB could very well be better tools, Easy2Boot was the only one that can boot multiple OS's from NTFS and allows me to easily drag-and-drop ISOs onto the drive.

## Part 3: Setting up the drive for Multiboot

[To do, finish]