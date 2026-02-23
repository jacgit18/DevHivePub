---
tags:
  - web
  - protocol
  - DNS
  - networking
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses why to avoid DNS-over-HTTPS.
Status: Done
Started: 2024-01-31
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
DNS-over-HTTPS is a protocol that encrypts DNS queries, enhancing privacy and security by preventing potential eavesdropping or manipulation of DNS requests. However, in certain situations or network setups, there might be reasons to disable it. Here are some possible reasons:

1. **Network Monitoring:** In some environments, network administrators may need to monitor DNS traffic for security or policy enforcement purposes. DNS-over-HTTPS can potentially hinder traditional monitoring methods.

2. **Local Policy Compliance:** Certain organizations or networks might have policies that require the use of specific DNS servers for filtering or monitoring purposes, and DNS-over-HTTPS might bypass these policies.

3. **Integration with Local Services:** Some local services or applications may rely on unencrypted DNS for their functioning, and enabling DNS-over-HTTPS could disrupt these dependencies.

4. **Configuration Preferences:** It could be a matter of personal or organizational preference. Some might prefer the traditional DNS for various reasons, such as compatibility with existing setups or familiarity.

It's essential to carefully consider the specific needs and requirements of the network or system in question before deciding to enable or disable DNS-over-HTTPS. Security and privacy considerations should be balanced with the operational needs of the environment.