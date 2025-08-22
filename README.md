# Burpsuite CA Installer

A Magisk/KernelSU module to install the Burpsuite CA certificate (9a5ba575.0) into the Android system certificate store.

## Overview

This module installs the Burpsuite CA certificate as a system certificate, allowing applications to trust connections through PortSwigger tools like Burp Suite without certificate warnings.

## Features

- Installs Burpsuite CA certificate (9a5ba575.0) into system certificate store
- Compatible with Android 14+ (includes APEX support)
- Works with both Magisk and KernelSU
- Proper SELinux context handling
- Automatic cleanup and safety checks

## Building

To create the magisk / kernelsu installer ZIP:
```bash
git clone https://github.com/n4igme/rootca-burp.git
cd rootca-burp/
zip -r rootca-burp.zip ./*
```

## Installation

1. Download the module ZIP file
2. Install via Magisk Manager or KernelSU Manager
3. Reboot your device
4. The Burpsuite CA certificate will be installed as a system certificate

## Demo Video
[<img src="https://img.youtube.com/vi/hGPznMY4v8M/hqdefault.jpg" width="300" height="425"/>](https://youtu.be/hGPznMY4v8M)

## Compatibility

- **Root Method**: Magisk or KernelSU
- **Android Version**: All versions (special handling for Android 14+)
- **Architecture**: All supported architectures

## How it Works

The module uses Magisk's systemless interface to inject the Burpsuite CA certificate into:
- `/system/etc/security/cacerts/` (standard location)
- `/apex/com.android.conscrypt/cacerts/` (Android 14+ APEX location)

For Android 14+, the module uses a tmpfs mount approach since Magisk doesn't support APEX file injection directly.

## Certificate Details

- **File**: 9a5ba575.0
- **Issuer**: Burpsuite CA
- **Purpose**: SSL/TLS interception for security testing
- **Format**: PEM-encoded X.509 certificate

## Logs

Module execution logs are stored in `/data/local/tmp/rootca_burp.log` for troubleshooting.

## Uninstallation

Simply disable or remove the module through your root manager and reboot.

# Credits  
Inspired by and building upon the implementation work of:  
- [Custom CACert](https://github.com/WindSpiritSR/CustomCACert) by WindSpiritSR  
- [reqable Magisk](https://github.com/reqable/reqable-magisk-module) module by reqable 
