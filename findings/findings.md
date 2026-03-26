**Finding #001 — Wi-Fi capture with mixed protocols**
**Filter used:** none
**What I observed:**
- Wireshark shows a live capture from the Wi-Fi interface with no display filter applied (filter bar shows the default prompt).
- Early packets in the list include UDP, TCP, TLSv1.2 Application Data, and one frame decoded as protocol 0x7373 with Ethernet II in the Info column.
- TCP/TLS traffic includes ACK segments involving well-known ports such as 443; UDP traffic includes flows toward destination port 6667.

**Screenshot:** screenshots/home.png

---

**Finding #002 — MDNS traffic with an IP address filter**
**Filter used:** `ip.addr ==`
**What I observed:**
- Status bar reports 1432 total packets in the capture file and only 3 packets matching the current display filter (0.2% shown).
- All three listed packets use the MDNS protocol, are 82 bytes long, and show Standard query in the Info column (packets 1374, 1379, 1390 by packet number).
- Source and destination address fields in the packet list are redacted.

**Screenshot:** screenshots/traffic.png

---

**Finding #003 — DNS-only view of the capture**
**Filter used:** `dns`
**What I observed:**
- Display filter `dns` is applied; every visible row in the packet list is labeled Protocol DNS.
- Entries alternate between Standard query and Standard query response in the Info column; packet numbers are not consecutive, so non-DNS frames remain in the file but are hidden.
- Source and destination columns show IPv6 addresses, and timestamps group into separate bursts of DNS activity earlier and later in the capture timeline.

**Screenshot:** screenshots/dns_filter.png
