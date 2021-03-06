---
title: "Windows Virtual Machine Setup"
description: Setting up a Windows VM on your Mac so you can test Internet Explorer
layout: article
category: "AppDev"
---

## Set up the Virtual Machine in VirtualBox

1. Download and install VirtualBox <br />
   <https://www.virtualbox.org/wiki/Downloads> <br />
   A "no root access" error may appear during installation. Ignore it for now.

2. Download the Windows virtual machine image <br />
   <https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/> <br />
   And unzip the downloaded file

3. Open the VirtualBox app, and use go to **File → Import Appliance...** to install the virtual machine

4. Select the `.ovf` file from the downloaded VM

5. Continue and use all the default settings

6. If you start the virtual machine now you will see another nasty root access error.
   To fix this you need to go to:

    1. **System Preferences → Security & Privacy**
    2. Click the lock icon in the bottom left to unlock. Make sure your PIV is inserted.
    3. Select **Accessibility** and click on the plus
    4. Add VirtualBox (it should be in your `/Applications` folder), and make sure the box is checked
    5. Close System Preferences

7. Start the virtual machine in VirtualBox (**Start → Normal Start**)

8. Log in to the virtual machine

    <div class="usa-alert usa-alert--info">
      <div class="usa-alert__body">
        <p class="usa-alert__text" markdown="1">
          The password is `Passw0rd!`
        </p>
      </div>
    </div>

## Configure the IDP for local development

Windows does not resolve `localhost`, it uses the IP address `10.0.2.2` instead,
so we configure the IDP to use that name instead:

1. Open `config/application.yml` in the [identity-idp](https://github.com/18f/identity-idp) repo

2. Change the `domain_name` key to `10.0.2.2:3000`

    ```
    -  domain_name: localhost:3000
    +  domain_name: 10.0.2.2:3000
    ```

3. Restart rails
4. In your virtual machine, open IE and browse to <http://10.0.2.2:3000/>

## Set up JAWS Screen Reader

For windows 10, I (Aaron) needed to make the following adjustments
1. Increase system base memory to 6GB
2. Use "Intel HD Audio" controller
3. I installed this version: <br />
   <http://jaws2019.vfo.digital/2019.1909.28.400/26B7F1A4-93A1-49A6-8F7D-8D030F3E3900/J2019.1909.28-any.exe>

