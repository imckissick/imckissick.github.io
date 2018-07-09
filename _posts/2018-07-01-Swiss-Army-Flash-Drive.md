---
layout: post
title: The Swiss Army Flash Drive
author: Ian McKissick
date: 2018-07-01 22:00:00 -0400
tags: weekend-projects tools
---

# The Swiss Army Flash Drive

## Introduction

## Part 0: The Drive Itself

First things first, a flash drive. While any flash drive laying around  _will_ work, you're going to want something that:

1. Is large enough to store various ISO images, tools, and whatever else you intend to toss on there
2. Is fast enough, especially if you're booting ISO images
3. Is reliable/durable enough as you go from rescuing one machine to the next

## Part 1: Boot ALL the ISOs

There's nothing novel about bootable flash drives anymore. With optical media on it's way out, you probably installed your OS from flash drive. There's plenty of tools do this. Installing Windows 10? Use Microsoft's Media Creation Tool. Need all-purpose tool? Try Rufus.

But with these tools, you're making bootable media for a single ISO. That's all well and good for a one-off, but we're going Swiss Army Knife levels of utility here, so we need a way to boot multiple ISOs. There's a few options out there. The three most notable I found are:

1. Easy2Boot
2. WinSetupFromUSB
3. YUMI - Multiboot USB Creator

All three of these are quite solid. And the best solution will depend on your personal needs. For this project, here's my (relatively basic) requirements:

* I need something where I can just drop the ISO images into place and go
* I need something that can boot multiple OS's (Windows **and** Linux)
* I need it to support booting from an NTFS formatted drive

Note: I would greatly prefer UEFI support, as UEFI is standard on all machines made in the last several years.
However I discovered very quickly while researching this, **NTFS support and UEFI support are effectively mutually exclusive** as the UEFI Standard does not require NTFS support.
Hopefully more manufactuers will start including an NTFS driver out of the box. But until then... Oh well...

So, how did the three of these hold up?

YUMI ([Official Site](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/))

* Can I Drag-and-drop ISOs?
  * No. Adding and removing ISO images from the drive requires running the YUMI setup tool every time you want to make changes
* Does it support booting Multiple OS's
  * Yes, but requires the drive to be formatted as FAT32
* Can I boot from NTFS/ExFAT?
  * Yes, NTFS can be used, but _only_ if booting Windows ISOs.
* Does it support booting from UEFI?
  * Yes, UEFI support is currently in Beta

WinSetupFromUSB ([Official Site](http://www.winsetupfromusb.com))

* Can I Drag-and-drop ISOs?
  * No. Adding and removing ISO iamges from the drives requires running WinSetupFromUSB to add or remove sources
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
* NTFS/ExFAT support?
  * Easy2Boot supports NTFS, but not ExFAT
* Does it support booting from UEFI?
  * Kinda. The process is rather convoluted as it requires swapping out the NTFS partition with a FAT32 partition (and back when you're done).
  * See [here](http://www.easy2boot.com/useful-things-to-know/) for more information

So, based on my needs, Easy2Boot was the clear winner. It was the only one that can boot multiple OS's from NTFS and allows me to easily drag-and-drop ISOs onto the drive.

## Part 2: Setting up the drive for Multiboot

[To do, finish]