<p align="center">
 <strong>:hatching_chick: New release! Beta Update May 2022</strong>.
  <a href="https://github.com/netbirdio/netbird/releases/tag/v0.6.0">
       Learn more
     </a>   
</p>

<br/>
<div align="center">

<p align="center">
  <img width="234" src="docs/media/logo-full.png"/>
</p>

  <p>
     <a href="https://github.com/netbirdio/netbird/blob/main/LICENSE">
       <img src="https://img.shields.io/badge/license-BSD--3-blue" />
     </a> 
     <a href="https://hub.docker.com/r/wiretrustee/wiretrustee/tags">
        <img src="https://img.shields.io/docker/pulls/wiretrustee/wiretrustee" />
     </a> 
    <br>
    <a href="https://www.codacy.com/gh/wiretrustee/wiretrustee/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=wiretrustee/wiretrustee&amp;utm_campaign=Badge_Grade"><img src="https://app.codacy.com/project/badge/Grade/d366de2c9d8b4cf982da27f8f5831809"/></a>
     <a href="https://goreportcard.com/report/wiretrustee/wiretrustee">
        <img src="https://goreportcard.com/badge/github.com/wiretrustee/wiretrustee?style=flat-square" />
     </a>
    <br>
    <a href="https://join.slack.com/t/wiretrustee/shared_invite/zt-vrahf41g-ik1v7fV8du6t0RwxSrJ96A">
        <img src="https://img.shields.io/badge/slack-@wiretrustee-red.svg?logo=slack"/>
     </a>    
  </p>
</div>


<p align="center">
<strong>
  Start using NetBird at <a href="https://app.netbird.io/">app.netbird.io</a>
  <br/>
  See <a href="https://netbird.io/docs/">Documentation</a>
  <br/>
   Join our <a href="https://join.slack.com/t/wiretrustee/shared_invite/zt-vrahf41g-ik1v7fV8du6t0RwxSrJ96A">Slack channel</a>
  <br/>
 
</strong>
</p>

<br>

**NetBird is an open-source VPN management platform built on top of WireGuard® making it easy to create secure private networks for your organization or home.**

It requires zero configuration effort leaving behind the hassle of opening ports, complex firewall rules, VPN gateways, and so forth.

NetBird creates an overlay peer-to-peer network connecting machines automatically regardless of their location (home, office, datacenter, container, cloud or edge environments) unifying virtual private network management experience.

**Key features:**
* Automatic IP allocation and management.
* Automatic WireGuard peer (machine) discovery and configuration.
* Encrypted peer-to-peer connections without a central VPN gateway.
* Connection relay fallback in case a peer-to-peer connection is not possible.
* Network management layer with a neat Web UI panel ([separate repo](https://github.com/netbirdio/dashboard))
* Desktop client applications for Linux, MacOS, and Windows.
* Multiuser support - sharing network between multiple users.
* SSO and MFA support. 
* Multicloud and hybrid-cloud support.
* Kernel WireGuard usage when possible.
* Access Controls - groups & rules (coming soon).
* Private DNS (coming soon).
* Mobile clients (coming soon).
* Network Activity Monitoring (coming soon).

### Secure peer-to-peer VPN with SSO and MFA in minutes
<p float="left" align="middle">
  <img src="docs/media/peerA.gif" width="400"/> 
  <img src="docs/media/peerB.gif" width="400"/>
</p>

**Note**: The `main` branch may be in an *unstable or even broken state* during development. 
For stable versions, see [releases](https://github.com/netbirdio/netbird/releases).

### Start using NetBird
* Hosted version: [https://app.netbird.io/](https://app.netbird.io/).
* See our documentation for [Quickstart Guide](https://netbird.io/docs/getting-started/quickstart).
* If you are looking to self-host NetBird, check our [Self-Hosting Guide](https://netbird.io/docs/getting-started/self-hosting).
* Step-by-step [Installation Guide](https://netbird.io/docs/getting-started/installation) for different platforms.
* Web UI [repository](https://github.com/netbirdio/dashboard).
* 5 min [demo video](https://youtu.be/Tu9tPsUWaY0) on YouTube.


### A bit on NetBird internals
* Every machine in the network runs [NetBird Agent (or Client)](client/) that manages WireGuard.
* NetBird features [Management Service](management/) that holds network state, manages peer IPs, and distributes network updates to peers.
* Every agent is connected to Management Service.
* NetBird agent uses WebRTC ICE implemented in [pion/ice library](https://github.com/pion/ice) to discover connection candidates when establishing a peer-to-peer connection between machines.
* Connection candidates are discovered with a help of [STUN](https://en.wikipedia.org/wiki/STUN) server. 
* Agents negotiate a connection through [Signal Service](signal/) passing p2p encrypted messages.
* Signal Service uses public WireGuard keys to route messages between peers.
* Sometimes the NAT traversal is unsuccessful due to strict NATs (e.g. mobile carrier-grade NAT) and p2p connection isn't possible. When this occurs the system falls back to a relay server called [TURN](https://en.wikipedia.org/wiki/Traversal_Using_Relays_around_NAT), and a secure WireGuard tunnel is established via the TURN server. 
 
[Coturn](https://github.com/coturn/coturn) is the one that has been successfully used for STUN and TURN in NetBird setups.

<p float="left" align="middle">
  <img src="https://netbird.io/docs/img/architecture/high-level-dia.png" width="700"/>
</p>

See a complete [architecture overview](https://netbird.io/docs/overview/architecture) for details.

### Roadmap
- [Public Roadmap](https://github.com/netbirdio/netbird/projects/2)

### Testimonials
We use open-source technologies like [WireGuard®](https://www.wireguard.com/), [Pion ICE (WebRTC)](https://github.com/pion/ice), and [Coturn](https://github.com/coturn/coturn). We very much appreciate the work these guys are doing and we'd greatly appreciate if you could support them in any way (e.g. giving a star or a contribution).

### Legal
 [WireGuard](https://wireguard.com/) is a registered trademark of Jason A. Donenfeld.

