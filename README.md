# Infracheck for Windows 1.1

Infracheck is a local-first Windows application for checking the health of the current network connection, inspecting Wi-Fi and Ethernet details, discovering devices on a selected private LAN, and running focused diagnostic tools.

## Download and requirements

Download the latest signed version:

- [Infracheck for Windows 1.1](releases/v1.1/Infracheck.Windows-v1.1.exe)
- [Previous version 1.0](releases/v1.0/Infracheck.Windows-v1.0.exe)

Requirements:

- Windows 10 or Windows 11, 64-bit
- [.NET 8 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/8.0)
- Windows Location services enabled for nearby Wi-Fi scanning

The executable is digitally signed by **ATG Services**. Its SHA-256 checksum is:

```text
C6735DF8457284410CA7FFE8B1DCAA820E2A862BF813168695EFBBAEFD0E110F
```

To verify the signature, right-click the downloaded file, open **Properties**, and check the **Digital Signatures** tab before running it.

## Getting started

1. Run `Infracheck.Windows-v1.1.exe`.
2. The PC health check starts automatically and summarizes the connection, gateway, DNS, web access, packet quality, public IP, findings, and network adapters.
3. Use **Check this PC now** whenever you want a fresh health sample.
4. Use **Export PDF report** to create a readable report containing the latest health check and the diagnostic evidence collected in the current session.

The application does not change network settings.

## Wi-Fi Live

- Select **Refresh nearby** to request a fresh Windows Wi-Fi scan and list visible access points.
- Signal strength is displayed as both a percentage and an estimated dBm value.
- Use the filters to narrow the list by band or security and save local snapshots for comparison.
- Open **Signal monitor** to follow signal, BSSID/channel events and gateway latency over time.
- Open **Channel graph** to compare visible 2.4, 5 and 6 GHz channels. The channel score ranges from 1 to 10, where a higher score means a channel is more suitable based on visible competing networks and their signal.
- Open **Roaming monitor** to observe access-point changes.
- Open **Validate Wi-Fi** for a guided PASS/WARN/FAIL validation of the current connection.

If nearby networks cannot be listed, open **Settings > Privacy & security > Location** and enable Location services for desktop applications, then retry.

## Ethernet and LAN

- **Refresh list** displays wired adapters, link state, addressing, gateway, negotiated speed, traffic, and error counters.
- **Safe LAN discovery** lets you select one of the active private networks or enter a custom private CIDR/range.
- Select **Scan local network** to observe responding or recently discovered devices and common service ports.

LAN discovery is capped at 1,024 addresses and does not attempt to authenticate to discovered devices.

## Connection tools

Select a tool first. Configure only the submenu fields shown for that tool, then select the explicit **Run** button. Selecting a tool does not start a test.

Available tools include:

- Speed test
- Trace route
- DNS lookup and DNS resolver comparison
- HTTP and TCP port checks
- MTU discovery
- VPN, proxy, and IPv4 route inspection
- DHCP inspection
- TLS certificate and protocol inspection
- Timed connection-quality testing for latency, packet loss, jitter, and p95

Every completed tool run is kept in the current application session and included in the next PDF export. Closing the application clears this temporary tool session.

## History

The History page stores up to 200 PC health checks in the current Windows user profile. Use **Clear** to delete this local history.

## Optional Appliance mode

Appliance mode is optional and starts disabled. Enable the **Appliance** toggle only when you want to connect to an existing Infracheck Appliance by URL and token. All PC-side diagnostics remain available without an Appliance.

## Privacy

- Diagnostic history and Wi-Fi observations remain on the PC unless you explicitly export a PDF.
- Appliance mode starts off and does not contact an Appliance until enabled and configured.
- The last Appliance URL may be remembered locally; the token is kept only for the current application session.
- No account is required for local PC diagnostics.

## Troubleshooting

- **Application does not start:** install the .NET 8 Desktop Runtime listed above.
- **Wi-Fi list is empty or incomplete:** enable Windows Location services, ensure WLAN AutoConfig is running, and select **Refresh nearby** again.
- **Wi-Fi signal monitor reports no connection:** connect to Wi-Fi first, then reopen the monitor.
- **Trace route contains intermediate TTL-expired rows:** this is normal; intermediate routers use those replies to identify each hop.
- **Gateway does not answer ping:** some routers block ICMP. Review DNS and HTTP results before concluding that internet access is unavailable.
