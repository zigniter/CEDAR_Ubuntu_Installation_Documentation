# JDK

You most probably already have `jdk` on your system.
The CEDAR developer team uses `Oracle JDK 11`, and we strongly suggest that you use the same, for compatibility reasons.

???+ warning "Important"
    
    Please note, that a JDK is needed to configure and run CEDAR based on this guide. A JRE will not be enough.
    
    We strongly suggest to use the `UbuntuOS Installer` version available at Oracle's download site.

## Download JDK

Please download the latest available version of `JDK 11` from:

[https://www.oracle.com/java/technologies/javase-jdk11-downloads.html](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)

You will need to log in to be able to download the JDK.

## Install JDK

Install the downloaded package.

## Verify JDK

After the installation, please verify the version in a shell: 
```sh
java --version
```

You should see something similar:
```
jopenjdk version "11.0.11" 2021-04-20
OpenJDK Runtime Environment (build 11.0.11+9-Ubuntu-0ubuntu2.20.04)
OpenJDK 64-Bit Server VM (build 11.0.11+9-Ubuntu-0ubuntu2.20.04, mixed mode, sharing)
```

