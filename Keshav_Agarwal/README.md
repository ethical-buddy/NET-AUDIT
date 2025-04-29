11.4.25
comit by Keshav created me own branch


# KIET Internet Login Page Scan Report

**Date:** 28.04.2025

## Overview
I performed a scan on the login page used for accessing KIET's internet services. The scan was done using **Nmap**, targeting the IP address \`172.16.16.16\`.

**Command used:**
\`\`\`bash
nmap -A 172.16.16.16
\`\`\`

KIET uses **Sophos** as their third-party service provider for firewall and internet security. Sophos has set up \`172.16.16.16\` as the default login IP for users to access the internet at KIET.

## Objective
The aim of the scan was to identify open ports and services currently running on \`172.16.16.16\`.

## Findings
| Port | Service | Description |
|:----:|:-------:|:-----------:|
| 8090 | User Access Portal | Provides the web interface for normal users to enter credentials and log in. |
| 4444 | Firewall Access Portal | Default port for accessing the Sophos firewall admin panel. Accessing this pops up the firewall login page. |
| 443  | VPN Access Portal | Used for VPN access. Accessing this port brings up the VPN login page. |

Additionally, there are some services running on the server that are currently **not accessible** via standard methods.




# KIET's website login page found
**Date: 29.04.2025**

#Overview
# Security Report - KIET Website Login Page

I discovered a potential way in KIET's website that leads to a login page for the Plesk Obsidian Control Panel. Here's the **step-by-step process** to reproduce this finding:


1. **Ping the website**  
   Use the following command to identify the website's IP address:
   ```bash
   ping kiet.edu.in

2. **Note the IP Address**
After running the ping command, take note of the IP address.

3. **Access the IP with Port 443**
Enter the IP address followed by port :443 in your browser's address bar:

    http://<IP-ADDRESS>:443

    You will be redirected to the Plesk Obsidian Login Page.

Login Details

    For General User:
    Username: administrator

    For Root Access:
    Username: root

Note: The password is yet to be bypassed.


Next Steps

    Password Bypass:
    Further steps are required to bypass the password for the root/admin accounts.
