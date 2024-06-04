# Installing the bootloader
Extract the [bootloader](https://github.com/GarlicOS/bootloader_anbernic_rg35xxplus/archive/refs/heads/master.zip) onto your **RG35XX+, RG35XXH, RG35XXSP or RG28XX's stock OS MicroSD card**.
### Uninstalling the bootloader
Remove the **device-resources folder** and **dmenu.bin file** from your **RG35XX+, RG35XXH, RG35XXSP or RG28XX's stock OS MicroSD card**. *Optional :* Remove **boot2 folder** from your **RG35XX+, RG35XXH, RG35XXSP or RG28XX's stock OS MicroSD card**.

# Creating TF1 bootable stock OS MicroSD cards
1. Download the latest portable version of [Rufus](https://github.com/pbatard/rufus/releases/latest)
2. Download and extract the stock OS image ([RG35XX+](https://win.anbernic.com/download/318.html), [RG35XXH](https://win.anbernic.com/download/360.html), [RG35XXSP](https://win.anbernic.com/download/412.html), [RG28XX](https://win.anbernic.com/download/398.html)) with [7zip](https://www.7-zip.org/download.html)
3. Start **Rufus**
4. Select your **MicroSD card** in the **Device** dropdown
5. Click the **SELECT button** and select your extracted stock OS image
6. Click the **START button** to burn your MicroSD card

# Creating TF2 bootable MicroSD cards
To create a TF2 bootable MicroSD card:
1. Format it with an **exfat** filesystem
2. Create a **boot** folder on TF2
3. Copy an OS **init** script of choice into the **boot** folder (ex. [GarlicOS](https://github.com/GarlicOS/init_template/raw/main/init))
4. Extract an **armhf** OS **rootfs** file of choice into the **boot** folder with [7zip](https://www.7-zip.org/download.html) (ex. [GarlicOS](https://github.com/GarlicOS/buildroot/releases/latest))

# Creating TF1 bootable MicroSD cards (Stock OS + Garlic OS)
1. Download the latest portable version of [Rufus](https://github.com/pbatard/rufus/releases/latest)
2. Download and extract the stock OS image ([RG35XX+](https://win.anbernic.com/download/318.html), [RG35XXH](https://win.anbernic.com/download/360.html), [RG35XXSP](https://win.anbernic.com/download/412.html), [RG28XX](https://win.anbernic.com/download/398.html)) with [7zip](https://www.7-zip.org/download.html)
3. Start **Rufus**
4. Select your **MicroSD card** in the **Device** dropdown
5. Click the **SELECT button** and select your extracted stock OS image
6. Click the **START button** to burn your MicroSD card
To add Garlic OS to TF1 bootable MicroSD card:
7. Create a **boot2** folder on TF1
8. Create a **boot** folder in the **boot2** folder on TF1 
9. Copy an OS **init** script of choice into this new **boot** folder (ex. [GarlicOS](https://github.com/GarlicOS/init_template/raw/main/init))
10. Extract an **armhf** OS **rootfs** file of choice into this new **boot** folder with [7zip](https://www.7-zip.org/download.html) (ex. [GarlicOS](https://github.com/GarlicOS/buildroot/releases/latest))

# Boot order
The bootloader will boot the first valid operating system it finds in the following order:
*Normal :*
1. TF2 [/boot] (ex. [GarlicOS](https://github.com/GarlicOS/buildroot/releases/latest))
2. TF1 [/boot2/boot] (ex. [GarlicOS](https://github.com/GarlicOS/buildroot/releases/latest))
3. TF1 (ex. Anbernic's Stock OS ([RG35XX+](https://win.anbernic.com/download/318.html), [RG35XXH](https://win.anbernic.com/download/360.html), [RG35XXSP](https://win.anbernic.com/download/412.html), [RG28XX](https://win.anbernic.com/download/398.html)))
*Forced :*
**Only one force file shall exist** If one of the following files exist on the root of TF1 MicroSD card [**Stock**, **TF1**, **TF2**] the following OS would be started:
1. **TF1** start *Garlic OS* on TF1
2. **Stock** start *Stock OS* on TF1
3. **TF2** start *Garlic OS* on TF2

