# SOP 1 - Virtualization Prerequisites

Requirements:

- Windows 10/11 Pro, Enterprise, or Education

- x64 processor with virtualization (Intel VT-x / AMD-V) enabled in BIOS

- Administrator privileges on the host machine

- Minimum of 8 GB of RAM, 16 GB recommended

- 100 GB or more of free disk space

## Section 1.1 - Enable Hyper-V 
> **NOTICE:** See Appendix A if issues are encountered.

Step 1: Use the Start menu to search for "Turn Windows features" and click Open.

Step 2: Scroll until you see the feature named "Hyper-V" and click the checkbox.

Step 3: Expand the "Hyper-V" feature and verify that both "Hyper-V Management Tools" and "Hyper-V Platform" are enabled. They should have the same checkmark as the "Hyper-V" feature.

Step 4: Click OK.

Step 5: Wait for files to download and apply.

Step 6: Click "Restart now".

Step 7: After the reboot is complete, verify Hyper-V is enabled using either option below.

1. Windows Features verification
		
    - Use the Start menu to search for "Turn Windows features" and click Open.

    - Scroll until you see the feature named "Hyper-V".

    - Expand the "Hyper-V" feature and verify that both "Hyper-V Management	Tools" and "Hyper-V Platform" are enabled.

    - Close the window.
		
2. Windows Terminal (PowerShell) verification
		
	- Right-click on the Start button and open "Terminal" with elevated permissions. [Displayed as "Terminal (Admin)" on submenu]

	- Confirm the tab title reads Administrator: Windows PowerShell. If it doesn't, open a Windows PowerShell tab by clicking the ˅ button and selecting "Windows PowerShell".

    - Run the following command: Get-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V

    - Verify "State" displays as "Enabled".

    - Close the window

## Section 1.2 - Download Windows 11 ISO

Step 1: Open a web browser.

Step 2: Navigate to https://www.microsoft.com/en-us/software-download/windows11

Step 3: Scroll to the section labeled "Download Windows 11 Disk Image (ISO) for x64 devices".

Step 4: Click the "Select Download" dropdown menu and select "Windows 11 (multi-edition ISO for x64 devices)". Once selected, click the Confirm button.

Step 5: Use the dropdown menu to select "English (United States)" as the product language. Once selected, click the Confirm button. 

Step 6: Click the "64-bit download" button to download your ISO file.

Step 7: Keep web browser open for use in the following section.

## Section 1.3 - Hash Verification

Step 1: Open Windows Terminal by right-clicking the Start menu and selecting "Terminal". 

Step 2: Confirm the tab title reads Windows PowerShell. If it doesn't, open a Windows PowerShell tab by clicking the ˅ button and selecting "Windows PowerShell".

Step 3: Run the following command and copy the hash value to your clipboard: 'Get-FileHash [ISO FILE PATH]' 
> **NOTICE:** If any part of the file path contains spaces, you must use quotation marks around your file path. Example: "C:\Users\John Doe\Downloads\win11.iso"

Step 4: Return to web browser and click on "Verify your download" to expand it.

Step 5: Use Ctrl+F and paste the hash output into your Find text box, and confirm it matches the hash listed with "English 64-bit" as the country locale.
> **NOTICE:** If the hash does not match any known hashes on the Microsoft website, delete the file and start again from Section 1.2.

## Appendix A - Common Feature Installation Issues

Issue 1: Installation stalls at "Searching for required files."

Potential Solutions

- Restart the system. Windows sometimes downloads the features but doesn't update the GUI to show it is complete. Once you open Windows Features, it should be enabled.

Issue 2: Hyper-V checkbox is grayed out/missing

Potential Solutions

- Virtualization is disabled in your BIOS. Enable it based on your manufacturer's documentation.

- Unsupported Windows edition. Make sure you are on Windows 10/11 Pro, Enterprise, or Education (not Home or S mode).