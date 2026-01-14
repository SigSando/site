---
layout: post
title: "Part 3 - Parrot (Linux setup)"
categories: Security
parent: Network & Security Home Lab Module 1
nav_order: 4
nav_exclude: false
---

{: .text-center }
# Network & Security Home Lab: 

![banner](/site/assets/banner.png){: width="auto" height="auto" }
###### Posted ***June 16, 2024***

{: .text-center }
## <span style="color: orange; font-weight: bold;">Part 3 - Parrot Linux setup</span>


In this module, we are going to install a linux of your choice. My recommendations are Parrot or Kali operating systems for use in the cyber range. Additionally I will go over a brief installation of Cachy OS to seperate workflows. Cachy OS is a good linux for productivity, automation etc.

We will use the management VM of choice in the next module also to complete the pfSense final setup.

## <span style="color: royalblue; font-weight: bold;">Download Parrot Linux</span>

Go to the following link: `Download` > [Parrot linux] 

As of writing the latest version of Parrot is `7.0`

![vbox41.png](/site/assets/vbox41.png){: width="auto" height="auto" }

- Download the recommended VirtualBox `.ova`. The image is around 7GB in size so it will take some time to download.

> Once it is downloaded we should have an `.ova` file.

- Move this file to the folder where the pfSense iso was also stored.

{: .warning}
Since this is a .ova file, you will `import` not Create `new`. In VirtualBox.

----

## <span style="color: royalblue; font-weight: bold;">ParrotSec VM Creation</span>

- Open VirtualBox. 

- Select `Machine` from the toolbar and then click on `Import`.

<details markdown="block">
<summary> <span style="color: orange; font-weight: bold;">Image Ref. (click me!)</span> </summary>

![vbox42.png](/site/assets/vbox42.png){: width="auto" height="auto" }

</details>

- Select the folder where the Parrot `.ova` is stored, then hit `Next`

<details markdown="block">
<summary> <span style="color: orange; font-weight: bold;">Image Ref. (click me!)</span> </summary>

![vbox43.png](/site/assets/vbox43.png){: width="auto" height="auto" }

</details>


> For the Appliance Settings, select Generate new mac addresses, then hit `Next`. 

<details markdown="block">
<summary> <span style="color: orange; font-weight: bold;">Image Ref. (click me!)</span> </summary>

![vbox44.png](/site/assets/vbox44.png){: width="auto" height="auto" }

</details>

{: .warning }
You are able to change values later on for hardware resources if need be.

> Click on `Finish`.

> Lastly, there will be an Agreenment to Accept or Deny. Once accepted, the `.OVA` appliance will begin importing.

<details markdown="block">
<summary> <span style="color: orange; font-weight: bold;">Image Ref. (click me!)</span> </summary>

![vbox45.png](/site/assets/vbox45.png){: width="auto" height="auto" }

</details>

----

## <span style="color: royalblue; font-weight: bold;">Adding VM to Group </span>

> Right-click on the Parrot VM from the sidebar, select Move to Group -> `New`.

> Right-click on the group name and select `Rename Group`. Name the group `Management`.

> Now we are going to create a nested group for our home lab.

Select the Firewall and Management group `(Ctrl+Click)`. Right-click on the name of one of the groups. From the menu select Move to Group -> [New].

Now both the groups should be nested inside the `New Group` . Right-click on the group and choose `Rename Group`. Give our group the name `Home Lab`.

Double check, now we should have the following structure:

<details markdown="block">
<summary> <span style="color: orange; font-weight: bold;">Image Ref. (click me!)</span> </summary>

![vbox46.png](/site/assets/vbox46.png){: width="auto" height="auto" }

</details>

----

# <span style="color: royalblue; font-weight: bold;">Parrot Updating</span>

- When Parrot boots, after a couple seconds it will ask to search for updates.

- Hit `Yes` to check for updates.

![vbox47.png](/site/assets/vbox47.png){: width="auto" height="auto" }

## <span style="color: royalblue; font-weight: bold;">Default password</span>

- It will ask for a root password.

{: .warning }
We need to change the default credentials, they are by default: 

```scss
user: parrot
password: parrot
```
<details markdown="block">
<summary> <span style="color: orange; font-weight: bold;">Image Ref. (click me!)</span> </summary>

![vbox48.png](/site/assets/vbox48.png){: width="auto" height="auto" }

![vbox49.png](/site/assets/vbox49.png){: width="auto" height="auto" }

</details>

- Once updated, find the terminal on the top right of the machine.

> Run the following command: 

```scss
sudo apt autoremove
```

<details markdown="block">
<summary> <span style="color: orange; font-weight: bold;">Image Ref. (click me!)</span> </summary>

</details>

> Now run:

```scss
sudo shutdown now
```

----

## <span style="color: royalblue; font-weight: bold;">Network Configuration</span>

Go to `Network -> Adapter 1`. For the Attached to field select `Internal Network`. For Name select `LAN 0`. Expand the 
*Advanced* section. For *Adapter Type* select `Paravirtualized Network (virtio-net)`.

![vbox50.png](/site/assets/vbox50.png){: width="auto" height="auto" }


## <span style="color: royalblue; font-weight: bold;">Changing Default password</span>

> Select pfSense from the sidebar and click on `Start` on the toolbar.

> Select Parrot OS Security Edition from the sidebar and click on `Start` on the toolbar.

> Once Parrot starts, find the terminal in the top left.

{: .warning}
You should always change the default username as well as root just to start.


```scss
ip a
```

![vbox51.png](/site/assets/vbox51.png){: width="auto" height="auto" }

- We can confirm the right subnet is designated by cross referencing the pfSense router config.

<details markdown="block">
<summary> <span style="color: orange; font-weight: bold;">Image Ref. (click me!)</span> </summary>

![vbox53.png](/site/assets/vbox53.png){: width="auto" height="auto" }

</details>


```scss
passwd user

sudo su

passwd root

```

![vbox52.png](/site/assets/vbox52.png){: width="auto" height="auto" }


{: .warning }
If you often forget your passwords, you can stop at this point and create a new *clone* using VirualBox.

 
### <span style="color: royalblue; font-weight: bold;">Post-Installation Configuration (Optional)</span>

> Use the following command in the terminal to update the system:

```scss
sudo apt update && sudo apt full-upgrade
```

Enter password when prompted.

Once the sources have been fetched we will be asked if we want to continue. Enter `Y` and then press Enter to start the update.

After the update is complete run the following command to remove the unused packages:

```scss
sudo apt autoremove
```

## <span style="color: royalblue; font-weight: bold;">Download additional linux distros</span>

This next section is optional and up to your preference. Since both Kali and Kubuntu come in `.iso` format we can do both installations in the same manner.

Go to the following links: `Download` > [Kubuntu] > [Kali] 


![kdown.png](/site/assets/kdown.png){: width="auto" height="auto" }

![cdown.png](/site/assets/cdown.png){: width="auto" height="auto" }

- Make sure to download the recommended VirtualBox `.iso`s and desktop edition for cachy os. The images are around 2.8GB & 3.5GB in size so it will take some time to download these.

> Once it is downloaded we should have an 2 `.iso` file.

- Move this file to the folder where the images for the home lab have been also stored.

{: .warning}
Since these are .iso files, you will hit `Create new`. In VirtualBox.

----

## <span style="color: royalblue; font-weight: bold;">VM Creation</span>

- I will not be going over the inital setup for these since they are additional, parrot can do what we need and the steps are largely the same. Here are 2 guides to assist with the installation if desired. 

(quick breakdown, assign 2048-4096mb of memory, 2cores and 20gb storage -> change the network settings -> start the VM -> then run the install. Lastly disconnect the `.iso` (see below for some help.))


[Kali install]

- I will go over the necessary steps.


## <span style="color: royalblue; font-weight: bold;">Network Configuration</span>

For Kali linux:
Go to `Network -> Adapter 1`. For the Attached to field select `Internal Network`. For Name select `LAN 0`. Expand the 
*Advanced* section. For *Adapter Type* select `Paravirtualized Network (virtio-net)`.

We want these machines to all have connectivity to  the pFsense machine.



![netcon.png](/assets/netcon.png){: width="auto" height="auto" }



In the next module, we will access the pfSense Web UI and complete the remaining configuration.

### [Home Lab Part 4]({{site.baseurl}}/docs/layout/Security/2024-05-16-homelabpart4/){: .btn .btn-green }




[Parrot linux]: https://parrotsec.org/download/
[Kubuntu]: https://kubuntu.org/download/
[Kali]: https://www.kali.org/get-kali/#kali-virtual-machines
[Kali install]:  https://www.kali.org/docs/installation/hard-disk-install/