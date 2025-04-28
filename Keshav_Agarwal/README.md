11.4.25
comit by Keshav created me own branch

cat << 'EOF' > README.md
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
EOF

