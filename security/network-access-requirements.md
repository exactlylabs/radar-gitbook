# Network Access Requirements

## Objective

This document aims to list all the expected connections to external systems that our agent does. The lists are split in two types: radar systems and third party systems.

## Radar Systems

### Radar Pod service

The pod communicates directly with our radar pods service, sending heartbeats and speed test measurement results. It also updates itself when the server detects that an update is available for that specific pod.

**Domains**: radar.exactlylabs.com

**Protocol**: HTTPS

**SSL**: Yes

**Ports**: 443

## Third Party Systems

### Sentry

In order to detect possible bugs in the agent, we use Sentry as the errors tracing system. Whenever an error occurs, the agent is going to send a notification to Sentry.

**Domains**: o1197382.ingest.sentry.io

**Protocol**: HTTPS

**SSL**: Yes

**Ports**: 443

### NDT7

One of the speed tests the agent runs is the NDT7 speed test, from [Measurement Labs](https://www.measurementlab.net/). Part of the speed test procedure is to detect the nearest server available and then connect to it. Due to this, we list here the subdomains with a wildcard, meaning that the servers are going to have at least that subdomain.

**Domains**: \*.mlab-oti.measurement-lab.org

**Protocol**: WSS or WS \*\*&#x20;

**SSL**: Yes

**Ports**: 443 or 80 \*\*

\*\* If the CPU has no support for AES Encryption instructions, the client will not use SSL, because that would impact in the speed test measurements.

### Ookla

The Ookla speedtest works in a way that there’s no single domain that hosts the servers. Each server can be hosted by other organizations and therefore, have unique domains for each. What can be done, though, is if you are going to use the speed test in specific locations, you can list the nearest servers to that location by navigating to: [https://c.speedtest.net/speedtest-servers-static.php](https://c.speedtest.net/speedtest-servers-static.php)

**Domains**: See [https://c.speedtest.net/speedtest-servers-static.php](https://c.speedtest.net/speedtest-servers-static.php)

**Protocol**: HTTPS

**SSL**: Yes \*\*

**Ports**: 8080, 5060

\*\* Ookla has a proprietary binary, making it impossible to be sure, but although they use ports 8080 and 5060, there’s a requirement for setting up a test server saying that an SSL certificate needs to be generated. Therefore, we are assuming that SSL is enabled.

### Linux Repositories

Since the pods are linux-based, we might want to update some packages due to security reasons or something of the sort.

**Domains**: deb.debian.org, security.debian.org, archive.raspberrypi.org

**Protocol**: HTTP

**SSL**: No\*

**Ports**: 80

\* Debian’s APT checks the signatures.

### **Google Cloud Storage**&#x20;

As part of our security mechanism when updating our software, we use this storage to download a Certificate Revocation List (CRL) from our bucket, to make sure that the signer of the binary we're downloading wasn't revoked.

**Domains:** storage.googleapis.com&#x20;

**Protocol:** HTTPS&#x20;

**SSL:** Yes&#x20;

**Ports:** 443
