# Infracheck for Windows 1.1

**Local-first Windows network diagnostics, Wi-Fi analysis, Ethernet inspection, LAN discovery and connection troubleshooting.**

## Official product links

- **Product website:** [infracheck.app](https://infracheck.app/)
- **Documentation and user guides:** [infracheck.app/docs.html](https://infracheck.app/docs.html)
- **Windows download:** [Infracheck for Windows 1.1](releases/v1.1/Infracheck.Windows-v1.1.exe)
- **Developer and publisher:** [ATG Services](https://atgserv.ro/)
- **Support and bug reports:** [GitHub Issues](https://github.com/gatgserv/infracheck-win.app/issues)

Infracheck for Windows is a network diagnostic application for Windows 10 and Windows 11. It combines a Wi-Fi analyzer, Wi-Fi signal monitor, channel analyzer, Ethernet adapter inspector, safe LAN scanner, network inventory and focused internet troubleshooting tools in one desktop interface.

Infracheck is developed, published and digitally signed by [ATG Services](https://atgserv.ro/), a Romanian software and IT services company.

The application is designed for home users, field technicians, help desks, network administrators and managed service providers who need to answer questions such as:

- Why is this Windows PC's internet connection slow or unstable?
- Is the problem caused by Wi-Fi signal, channel congestion, DNS, the gateway or the internet path?
- Which Wi-Fi networks and access points are visible nearby?
- Which devices are present on the selected local network?
- Is Ethernet negotiating at the expected speed?
- Are a website, TCP port or TLS certificate reachable and valid?
- What diagnostic evidence can be shared with technical support?

Infracheck is local-first: no account is required, local diagnostics work without an Infracheck Appliance, and the application does not change network settings.

## Download

### Latest version

[Download Infracheck for Windows 1.1](releases/v1.1/Infracheck.Windows-v1.1.exe)

- Version: `1.1.0`
- Platform: Windows 10 or Windows 11, 64-bit
- Runtime: [.NET 8 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/8.0)
- Digital signature: **ATG Services**
- SHA-256:

```text
C6735DF8457284410CA7FFE8B1DCAA820E2A862BF813168695EFBBAEFD0E110F
```

Previous stable version: [Infracheck for Windows 1.0](releases/v1.0/Infracheck.Windows-v1.0.exe)

Before running the application, right-click the downloaded executable, select **Properties**, and verify the **ATG Services** signature under **Digital Signatures**.

## Main features

### Automatic PC health check

The Overview page runs a health check automatically after the application opens. It summarizes:

- active Wi-Fi or Ethernet connection;
- gateway address, latency, packet loss and jitter;
- DNS response time;
- HTTP connectivity and response time;
- public IP address;
- network adapter state;
- findings and practical recommendations.

Select **Check this PC now** to collect a new sample. The check does not modify the PC or network.

### Wi-Fi Live and nearby network scanner

The Wi-Fi Live page requests a fresh Windows Wi-Fi scan and displays visible networks and BSSIDs. Available evidence can include:

- SSID and BSSID;
- security type;
- 2.4 GHz, 5 GHz or 6 GHz band;
- Wi-Fi channel and frequency;
- radio information;
- Windows-reported signal strength and estimated dBm;
- BSS Load and client information when reported by the access point;
- first-seen and last-seen state.

Search, band and security filters make a large Wi-Fi scan easier to inspect. Nearby-network snapshots can be saved locally and compared to identify newly visible, missing or changed access points.

Windows Location services must be enabled for desktop applications before Windows will expose nearby Wi-Fi scan results.

### Wi-Fi signal monitor

The connected Wi-Fi signal monitor samples the current connection only after **Start monitoring** is selected. It correlates:

- SSID and BSSID;
- channel changes;
- signal strength;
- gateway round-trip time;
- access-point and connection events.

This helps diagnose intermittent Wi-Fi, weak signal, unstable latency and unexpected transitions between access points.

### Wi-Fi channel graph and channel recommendation

The channel graph visualizes nearby 2.4 GHz, 5 GHz and 6 GHz Wi-Fi channels. Channel analysis compares visible competing BSSIDs and their reported signal strength.

Each candidate receives a recommendation score from **1 to 10**:

- `9–10`: highly recommended based on the current scan;
- `7–8`: good candidate;
- `5–6`: usable, with some visible competition;
- `1–4`: less suitable under the observed conditions.

A higher score means the channel appears more suitable based on the current Windows scan. This is an estimate of visible competing signal, not a spectrum analyzer or a direct measurement of access-point airtime utilization.

Use **Rescan channels** before making a decision, because nearby Wi-Fi conditions change over time.

### Guided Wi-Fi validation

Guided Wi-Fi validation performs a structured PASS/WARN/FAIL review of the current connection. It checks available Wi-Fi evidence together with local gateway, DNS, HTTP and HTTPS connectivity.

An HTTPS failure can be caused by a captive portal, proxy, TLS inspection, firewall policy, certificate problem or interrupted internet access. The result is diagnostic evidence, not an automatic change to Windows or the router.

### Wi-Fi roaming monitor

The roaming monitor records changes affecting the connected wireless session, including transitions between BSSIDs or channels. It is useful when investigating roaming between access points in a home, office, school, warehouse or managed Wi-Fi deployment.

### Ethernet and network adapter diagnostics

The Ethernet & LAN page lists wired and virtual adapters with relevant Windows-reported details:

- adapter type and link state;
- IPv4 and IPv6 addresses;
- default gateway;
- negotiated link speed;
- MTU;
- DHCP state;
- received and transmitted traffic;
- available error or discard counters.

This can reveal a disconnected cable, unexpected 100 Mbps negotiation, missing gateway, unusual MTU or adapter configuration issue.

### Safe LAN discovery and network inventory

Safe LAN discovery scans a selected active private network or a custom private CIDR/range. Custom discovery is limited to 1,024 addresses and does not attempt to authenticate to devices.

The observed LAN inventory can track:

- responding and recently observed devices;
- current and previous IP addresses;
- MAC address, hostname and vendor evidence when available;
- common discovered services and ports;
- first seen and last seen time;
- new, known and missing state;
- local trust, category, tags and notes.

Select the intended LAN before scanning. This is a local network discovery tool, not an internet-wide scanner.

## Connection and internet diagnostic tools

Selecting a tool only opens its parameters. No diagnostic test starts until the explicit **Run** button is selected.

### Connection quality and speed test

- approximate download and upload throughput;
- latency, packet loss and jitter;
- P95 latency;
- timed connection-quality sampling;
- loaded download and upload latency;
- bufferbloat indication.

Results depend on the current PC, network, test endpoint and internet conditions. They are diagnostic estimates rather than ISP certification.

### Traceroute and path quality

- progressive traceroute from the Windows PC to a selected target;
- hop address and reverse DNS name;
- per-hop packet loss;
- minimum, average, maximum and P95 latency;
- local, private or public path scope;
- path-quality evidence across repeated probes.

Intermediate `TTL expired` replies are expected during traceroute: routers use them to reveal each hop. A router that does not answer ICMP is not necessarily offline.

### DNS diagnostics

- DNS lookup for host names;
- A and AAAA record inspection;
- DNS response-code evidence;
- response-time comparison between resolvers;
- detection of slow, failed or inconsistent DNS resolution.

### HTTP, TCP and TLS checks

- HTTP and HTTPS reachability;
- DNS, TCP, TLS and time-to-first-byte timing;
- HTTP redirects and final destination;
- checks for one or multiple TCP ports;
- TLS protocol and certificate inspection;
- certificate subject, issuer and validity evidence.

These tools help distinguish a DNS problem from a blocked port, server failure, redirect, proxy or TLS/certificate issue.

### DHCP, MTU, VPN, proxy and route inspection

- DHCP configuration and lease-related adapter evidence;
- MTU discovery to identify fragmentation or path-MTU problems;
- VPN adapter detection;
- Windows proxy inspection;
- IPv4 route and default-route inspection.

## Evidence reports and history

**Export PDF report** creates a human-readable diagnostic report. The report can include the latest PC health check and every connection tool completed during the current application session, with timestamps, parameters, summaries and detailed results.

The History page stores up to 200 PC health checks in the current Windows user profile. Use **Clear** to remove that local history.

## Optional Infracheck Appliance mode

Appliance mode is optional and disabled by default. All PC-side diagnostics remain available without an Appliance.

Enable the **Appliance** toggle only when connecting to an existing Infracheck Appliance by URL and token. The configured Appliance can provide an independent network vantage point for comparison and additional appliance-side diagnostics.

## Privacy and safety

- No account is required for local Windows diagnostics.
- Wi-Fi observations, LAN inventory and diagnostic history remain on the PC unless explicitly exported.
- Appliance mode starts disabled and does not contact an Appliance until enabled and configured.
- The Appliance URL may be remembered locally; its token is kept only for the current session.
- LAN discovery is limited to a selected private network or private custom range.
- The application does not change Wi-Fi channels, router settings, DNS settings, routes or firewall rules.

## Troubleshooting

### Nearby Wi-Fi networks are empty or incomplete

Enable **Settings > Privacy & security > Location > Location services**, allow location access for desktop applications, verify that **WLAN AutoConfig** is running, and select **Refresh nearby** again.

### Wi-Fi signal monitor reports no connection

Connect the PC to Wi-Fi, reopen the monitor and select **Start monitoring**. The monitor refreshes the current Windows connection when it starts.

### HTTPS validation fails

Complete any captive-portal login first. Then review proxy configuration, TLS inspection, firewall rules, antivirus web filtering, system date/time and certificate trust.

### Gateway does not answer ping

Some routers intentionally block ICMP. Review DNS and HTTP/HTTPS results before concluding that internet access is unavailable.

### The application does not start

Install the [.NET 8 Desktop Runtime for Windows](https://dotnet.microsoft.com/download/dotnet/8.0), then retry.

## Frequently asked questions

### What is Infracheck for Windows?

Infracheck is a local-first Windows network diagnostic tool. It combines Wi-Fi scanning and channel analysis, signal monitoring, Ethernet inspection, LAN discovery, traceroute, DNS, HTTP, TCP, TLS, DHCP, MTU, VPN and route diagnostics.

### Is Infracheck a Wi-Fi analyzer?

Yes. It lists Windows-reported nearby Wi-Fi networks, visualizes channels, estimates visible channel competition, scores candidate channels and monitors the connected signal. It is not a radio-frequency spectrum analyzer.

### Can Infracheck find devices on my LAN?

Yes. Safe LAN discovery scans the selected private network or a limited custom private range and maintains a local observed-device inventory.

### Does Infracheck change my network configuration?

No. Diagnostic tests are read-only and do not automatically change Windows, router, Wi-Fi, DNS, route or firewall settings.

### Does Infracheck require an Appliance?

No. Appliance mode is optional and off by default. The Windows diagnostics work independently.

### Can I send the results to technical support?

Yes. Export a PDF evidence report after completing the relevant health checks and diagnostic tools.

## Website, documentation, publisher and support

- [Infracheck website](https://infracheck.app/)
- [Infracheck documentation](https://infracheck.app/docs.html)
- [ATG Services — developer and publisher](https://atgserv.ro/)
- [Windows application downloads and manual](https://github.com/gatgserv/infracheck-win.app)
- [Report a bug or request support](https://github.com/gatgserv/infracheck-win.app/issues)
- [Latest Windows 1.1 release folder](https://github.com/gatgserv/infracheck-win.app/tree/main/releases/v1.1)

---

Infracheck for Windows is intended for authorized diagnostics on networks and devices you own or are permitted to inspect.
