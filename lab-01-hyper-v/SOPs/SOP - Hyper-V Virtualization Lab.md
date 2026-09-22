# SOP - Hyper-V Virtualization Lab

Requirements:

- Windows 10/11 Pro, Enterprise, or Education

- x64 processor with virtualization (Intel VT-x / AMD-V) enabled in BIOS

- Administrator privileges on the host machine if Hyper-V is not installed

- Minimum of 8 GB of RAM, 16 GB recommended

- 100 GB or more of free disk space

## Table of Contents

### Section 1 - Virtualization Prerequisites

Section 1.1 - Enable Hyper-V 

Section 1.2 - Download Windows 11 ISO

Section 1.3 - Hash Verification

### Section 2 - Hyper-V Configuration

Section 2.1 - Virtual Machine Creation

Section 2.2 - Enabling the Trusted Platform Module (TPM)

### Appendices
Appendix A - Common Feature Installation Issues

## Section 1 - Virtualization Prerequisites

### Section 1.1 - Enable Hyper-V 

**SKIP THIS** if Hyper-V is already installed on host machine.
> **NOTICE:** See Appendix A if issues are encountered.

Step 1: Use the Start menu to search for "Turn Windows features" and click Open.

Step 2: Scroll until you see the feature named "Hyper-V" and click the checkbox.

Step 3: Expand the "Hyper-V" feature and verify that both "Hyper-V Management Tools" and "Hyper-V Platform" are enabled. They should have the same checkmark as the "Hyper-V" feature.

Step 4: Click OK.

Step 5: Wait for files to download and apply.

Step 6: Click "Restart now".

Step 7: After the reboot is complete, verify Hyper-V is enabled using either option below.

1. Windows Features verification
		
    - Use the Start menu to search for **Turn Windows features on or off** and click Open.

    - Scroll until you see the feature named **Hyper-V**.

    - Expand the Hyper-V feature and verify that both **Hyper-V Management Tools** and **Hyper-V Platform** are enabled.

    - Close the window.
		
2. Windows Terminal (PowerShell) verification
		
	- Right-click on the Start button and open **Terminal** with elevated permissions. [Displayed as **Terminal (Admin)** on submenu]

	- Confirm the tab title reads **Administrator: Windows PowerShell**. If it doesn't, open a Windows PowerShell tab by clicking the ˅ button and selecting **Windows PowerShell**.

    - Run the following command: `Get-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V`

    - Verify **State** displays as **Enabled**.

    - Close the window.

### Section 1.2 - Download Windows 11 ISO

Step 1: Open a web browser.

Step 2: Navigate to https://www.microsoft.com/en-us/software-download/windows11

Step 3: Scroll to the section labeled "Download Windows 11 Disk Image (ISO) for x64 devices".

Step 4: Click the "Select Download" dropdown menu and select "Windows 11 (multi-edition ISO for x64 devices)". Once selected, click the Confirm button.

Step 5: Use the dropdown menu to select "English (United States)" as the product language. Once selected, click the Confirm button. 

Step 6: Click the "64-bit download" button to download your ISO file.

Step 7: Keep web browser open for use in the following section.

### Section 1.3 - Hash Verification

Step 1: Open Windows Terminal by right-clicking the Start menu and selecting "Terminal". 

Step 2: Confirm the tab title reads Windows PowerShell. If it doesn't, open a Windows PowerShell tab by clicking the ˅ button and selecting "Windows PowerShell".

Step 3: Run the following command and copy the hash value to your clipboard: `Get-FileHash [ISO FILE PATH]` 
> **NOTICE:** If any part of the file path contains spaces, you must use quotation marks around your file path. Example: "C:\Users\John Doe\Downloads\win11.iso"

Step 4: Return to web browser and click on "Verify your download" to expand it.

Step 5: Use Ctrl+F and paste the hash output into your Find text box, and confirm it matches the hash listed with "English 64-bit" as the country locale.
> **NOTICE:** If the hash does not match any known hashes on the Microsoft website, delete the file and start again from Section 1.2.

## Section 2 - Hyper-V Configuration

### Section 2.1 - Virtual Machine Creation
Step 1: Open **Hyper-V Manager**.

Step 2: Once open, verify your computer name is listed and click on it once.

Step 3: In the **Actions** pane click on **New** and then select **Virtual Machine** from the submenu.

Step 4: When **New Virtual Machine Wizard** opens click **Next**.
> **NOTICE:** If you do not want that introduction to be shown again select the *Do not show this page again* checkbox.

Step 5: Click on the name textbox **New Virtual Machine** and update to a name of your choosing and click **Next**.

> **NOTICE:** If you wish to move the virtual machine from the default directory you must select the *Store virtual machine in a different location* checkbox then click **Browse** before proceeding.

Step 6: Ensure the generation selected is **Generation 2** then click **Next**.

Step 7: Select the *Startup memory* textbox and update the value to how much RAM to allocate to the virtual machine then click **Next**.
> **NOTICE:** RAM allocation is set to megabytes instead of gigabytes so you must convert your RAM amount to megabytes before continuing.

- **Optional** but recommended: Disable the ***Dynamic Memory*** checkbox. This feature changes how much RAM the virtual machine uses depending on how much demand is coming from it.

Step 8: If networking is required select the *Connection* dropdown menu and select *Default Switch* then click **Next**.

Step 9: Ensure **Create a virtual hard disk** is selected then click on the textbox ***New Virtual Machine.vhdx*** and update to a name of your choosing then click **Next**.
> **NOTICE:** If you wish to update the file path or size of the virtual hard disk you must select the respective textboxes for each before proceeding.

Step 10: Select *Install an operating system from a bootable image file* then click **Browse**.

Step 11: Navigate to the directory where you saved your Windows 11 ISO file, select it, then click **Open**. Once your **Image file** is selected click **Next**.

Step 12: Click **Finish** to create the virtual machine.

### Section 2.2 - Enabling the Trusted Platform Module (TPM)

Step 1: Ensure your computer name is selected in the ***Hyper-V Manager*** tree on the left.

Step 2: In **Virtual Machines** right click on your newly created virtual machine and click on **Settings** in the submenu.

Step 3: Once the **Settings** window is open select *Security* on the menu to the left.

Step 4: Click on the ***Enable Trusted Platform Module*** checkbox and ensure it is enabled then click **OK**.

**You are now ready to start the virtual machine.**

## Appendix A - Common Feature Installation Issues

Issue 1: Installation stalls at "Searching for required files."

Potential Solutions

- Restart the system. Windows sometimes downloads the features but doesn't update the GUI to show it is complete. Once you open Windows Features, it should be enabled.

Issue 2: Hyper-V checkbox is grayed out/missing

Potential Solutions

- Virtualization is disabled in your BIOS. Enable it based on your motherboard manufacturer's documentation.

- Unsupported Windows edition. Make sure you are on Windows 10/11 Pro, Enterprise, or Education (not Home or S mode).
