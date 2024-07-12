### DNS (Domain Name System) Cheat Sheet

#### Basics
- **DNS**: Translates human-readable domain names to IP addresses.
- **Hierarchy**: Organized in a hierarchical structure with different levels.
  - **Root Level**: Represented by a dot (".").
  - **Top-Level Domains (TLDs)**: Examples include `.com`, `.org`, `.net`.
  - **Second-Level Domains**: Directly below TLDs, e.g., `example.com`.
  - **Subdomains**: Below second-level domains, e.g., `sub.example.com`.

#### DNS Record Types
- **A (Address)**: Maps a domain name to an IPv4 address.
  - Example: `example.com. IN A 93.184.216.34`
- **AAAA (IPv6 Address)**: Maps a domain name to an IPv6 address.
  - Example: `example.com. IN AAAA 2606:2800:220:1:248:1893:25c8:1946`
- **CNAME (Canonical Name)**: Alias for another domain name.
  - Example: `www.example.com. IN CNAME example.com.`
- **MX (Mail Exchange)**: Specifies mail servers for the domain.
  - Example: `example.com. IN MX 10 mail.example.com.`
- **NS (Name Server)**: Specifies authoritative DNS servers for the domain.
  - Example: `example.com. IN NS ns1.example.com.`
- **PTR (Pointer)**: Maps an IP address to a domain name (reverse DNS).
  - Example: `34.216.184.93.in-addr.arpa. IN PTR example.com.`
- **SOA (Start of Authority)**: Provides information about the DNS zone.
  - Example: `example.com. IN SOA ns1.example.com. admin.example.com. 2023071001 3600 1800 1209600 300`
- **SRV (Service)**: Specifies the location of services.
  - Example: `_sip._tcp.example.com. IN SRV 10 60 5060 sipserver.example.com.`
- **TXT (Text)**: Holds arbitrary text, often for verification and policy purposes.
  - Example: `example.com. IN TXT "v=spf1 ip4:93.184.216.34 -all"`

#### Common DNS Commands
- **nslookup**: Query DNS servers.
  - Example: `nslookup example.com`
- **dig**: Detailed DNS queries.
  - Example: `dig example.com`
- **host**: Simple DNS lookup utility.
  - Example: `host example.com`

#### DNS Zone Files
- **Format**: Plain text file containing DNS records for a domain.
- **Fields**:
  - **$ORIGIN**: Specifies the domain name.
  - **$TTL**: Specifies the default TTL (Time to Live) for records.
- **Example Zone File**:
```
  $ORIGIN example.com.
  $TTL 86400
  @   IN  SOA ns1.example.com. admin.example.com. (
          2023071001 ; Serial
          3600       ; Refresh
          1800       ; Retry
          1209600    ; Expire
          300 )      ; Minimum
      IN  NS  ns1.example.com.
      IN  NS  ns2.example.com.
  www IN  A   93.184.216.34
  mail IN MX 10 mail.example.com.
```

#### DNS Caching
- **Purpose**: Improves performance by storing DNS query results.
- **TTL (Time to Live)**: Defines how long a record is cached.
- **Cache Clearing**:
  - **Windows**: `ipconfig /flushdns`
  - **Linux**: `sudo systemd-resolve --flush-caches` or `sudo /etc/init.d/nscd restart`
  - **Mac**: `sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder`

#### DNS Security
- **DNSSEC (DNS Security Extensions)**: Adds security to DNS by enabling DNS responses to be authenticated.
  - **RRSIG**: Contains digital signatures.
  - **DNSKEY**: Contains public signing keys.
  - **DS**: Delegation signer record, links parent and child zones.
- **DDoS Mitigation**: Use of Anycast, rate limiting, and robust infrastructure.
- **Secure Configurations**: Disable recursion on authoritative servers, use split-horizon DNS, and regular monitoring.

#### Troubleshooting DNS Issues
- **Check DNS Resolution**:
  - `nslookup example.com`
  - `dig example.com`
  - `host example.com`
- **Verify DNS Propagation**: Use online tools like DNS Propagation Checker.
- **Inspect Zone Files**: Ensure syntax and records are correct.
- **Monitor DNS Logs**: Look for unusual activity or errors.
- **Test Connectivity**: Ensure the DNS server is reachable.

#### Advanced DNS Concepts
- **Split-Horizon DNS**: Different DNS responses based on the query source.
- **Dynamic DNS (DDNS)**: Automatically updates DNS records for IP address changes.
- **GeoDNS**: Directs users to different servers based on geographic location.

#### Best Practices
- **Regularly Update and Patch DNS Servers**: Protect against vulnerabilities.
- **Implement DNSSEC**: Ensure integrity and authenticity of DNS data.
- **Monitor DNS Traffic**: Detect and respond to suspicious activities.
- **Use Redundant DNS Servers**: Ensure high availability and reliability.
- **Document DNS Changes**: Maintain accurate records of DNS configurations and changes.