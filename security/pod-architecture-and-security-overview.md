# Pod Architecture and Security Overview

The Telehealth Broadband Pilot Project has developed a custom broadband measurement tool called Radar. Radar is comprised of a server for centralized management and reporting, and “pods” that run software to test the speed, quality, and reliability of Internet connections. The pods are physically installed at clinics, community institutions, private businesses and homes as part of a multi-state project to better understand and map broadband availability. Internet speed data collected by the pods are sent to the centralized server for review.

### Pod Hardware & Operating System

Pods are hardware-based devices built around the Raspberry Pi 4b, a small, low-cost, single-board computer.  Pods run a locked down version of Raspberry Pi OS Lite / Debian Linux 11 that automatically installs security updates.  The operating system is configured to disallow local log in if a user has physical access to the device, and blocks all inbound ports to prevent access to the device from external locations. More specifically, the SSHD and Getty services have been disabled in addition to starting with the more minimal “Lite” version of Debian.

### Pod Software

Two custom processes run on Pods – a client and a “watchdog”.  These software perform a limited set of activities and cannot be used for execution of arbitrary code on the system.

The client is responsible for:

* Communication with the server to establish a unique client ID
* Collection of basic information about the local operating system on the Raspberry Pi
* Performance of speed tests through the Ookla Speedtest CLI and Measurement Lab NDT7 testing tools
* Reporting of speed test results to the server
* Checking its software against the server and downloading a code-signed upgrade if available

The watchdog process is responsible for:

* Providing device and client details via the local console if an HDMI cable is plugged in
* Managing operating system configuration updates
* Monitoring for unauthorized operating system changes

### Pod Updates

The operating system automatically performs software updates published to Debian’s stable and security repositories.

Software updates to the pod client and watchdog services are performed automatically.  Updates are published by the software developer and deployed to a set of testing pods before being marked as available for download.  When pods detect that an update is available, they will download and install the updates automatically and report back their current version to the server.

To prevent unauthorized updates from being deployed to the pods, pod software updates can only be installed when they have been signed by a private key that is managed and secured by the software developer.

The signing key is not available on the Radar server, which means that if an attacker were to compromise the Radar server, they would not be able to sign and deploy malicious code to pods.  As unsigned code cannot be deployed to the pod, an attacker would be unable to push an exploit to the pods through the code update and pod management system.  Additionally, since the pods have had inbound ports blocked, an attacker is unable to remotely log in or access the pods from the central server.

### Server Architecture & Functionality

The Radar server is made up of several components which together perform remote client management, data collection, data processing, and data presentation.  Server components include a database server (_PostgreSQL_), caching server (_Redis_), durable file storage technology (_Google Cloud Storage_), and a custom Radar software package.  The Radar server application is written primarily with the Ruby on Rails framework.  Within Ruby, end-user authentication for the management user interface is provided by the “_Devise_” software package.

The Radar server package exposes a single HTTP-based API/Web endpoint for receiving and servicing requests by the clients, as well as to serve the web-based user experience.  The Radar server package uses a PostgreSQL server and Google Cloud Storage to store information from the Radar pod clients, including configuration details and testing results.  Additionally, the Radar server stores information from the Radar pod management website, including details about organizational accounts, users, location details, and performance metrics.&#x20;

Radar pods establish a TLS connection with the Radar server over ports 443 to check for requests from the Radar management interface to run a test, to report back any speed test results for storage on the server, and to determine if the Radar pod client or watchdog applications need to be upgraded.  The pod identifies itself to the server using a pod ID and secret; these values are used for pod identification and verification, but do not grant the pod access to the server.  Spoofed or leaked IDs and secrets could potentially allow a malicious actor to report false speed tests to the server but would not allow additional actions to be performed on the server.

### Server Security

The PostgreSQL and Cloud Storage endpoints are not exposed on the public internet; necessary communication between the Radar packages and the data store occurs through firewalls as required to operate the Radar software.

All servers use industry standard TLS 1.2 (with modern cipher suites) and 1.3 on all endpoints, and are routinely and automatically patched with the latest security updates. Additionally, the Radar software is monitored for use of outdated software packages with reported security issues, and will receive a new update with patched packages for any issues that are found.
