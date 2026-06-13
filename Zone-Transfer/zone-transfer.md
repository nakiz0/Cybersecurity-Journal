# DNS Zone Transfer (AXFR)

## What is a DNS Zone Transfer?

A DNS Zone Transfer is the process of copying DNS records from a primary DNS server (Master) to a secondary DNS server (Slave/Backup).

This mechanism ensures that multiple DNS servers maintain the same DNS database and can provide reliable name resolution.

```text
Primary DNS Server
        │
        │ AXFR/IXFR
        ▼
Secondary DNS Server
```

---

# Why Are Zone Transfers Used?

Zone transfers are used to:

- Synchronize DNS records between servers.
- Provide redundancy and fault tolerance.
- Improve DNS availability.
- Ensure backup DNS servers have updated records.

Without zone transfers, secondary DNS servers would not know about new hosts, mail servers, or other DNS changes.

---

# Types of Zone Transfers

## Full Zone Transfer (AXFR)

Transfers the entire DNS zone database.

```text
AXFR = Full Copy of DNS Records
```

Example:

```bash
dig axfr example.com @ns1.example.com
```

---

## Incremental Zone Transfer (IXFR)

Transfers only the records that have changed since the last update.

```text
IXFR = Changed Records Only
```

Benefits:

- Faster synchronization
- Lower bandwidth usage
- Reduced server load

---

# Why is Zone Transfer Important in Cybersecurity?

Misconfigured DNS servers may allow anyone to perform a zone transfer.

If successful, an attacker can obtain a complete list of DNS records and discover valuable information about the target organization.

Instead of manually finding subdomains, the attacker receives them all at once.

---

# Information Revealed During a Zone Transfer

A successful zone transfer may reveal:

- Web Servers
- Mail Servers
- VPN Gateways
- Development Servers
- Test Environments
- Internal Hostnames
- Backup Servers
- Domain Controllers

Example:

```text
www.example.com
mail.example.com
vpn.example.com
dev.example.com
api.example.com
admin.example.com
```

---

# Common DNS Records Exposed

## A Record

Maps a hostname to an IPv4 address.

```text
www.example.com → 192.168.1.10
```

---

## AAAA Record

Maps a hostname to an IPv6 address.

```text
www.example.com → 2001:db8::1
```

---

## MX Record

Specifies mail servers.

```text
example.com → mail.example.com
```

---

## NS Record

Specifies authoritative name servers.

```text
example.com → ns1.example.com
```

---

## CNAME Record

Creates aliases for hosts.

```text
blog.example.com → www.example.com
```

---

## TXT Record

Stores text information.

Often used for:

- SPF
- DKIM
- Domain Verification

---

# DNS Zone Transfer Attack

## Step 1: Discover Name Servers

Using Whois:

```bash
whois example.com
```

Output:

```text
ns1.example.com
ns2.example.com
```

---

## Step 2: Attempt Zone Transfer

Using Dig:

```bash
dig axfr example.com @ns1.example.com
```

---

## Step 3: Analyze Results

If successful:

```text
www.example.com
vpn.example.com
mail.example.com
dev.example.com
admin.example.com
```

The attacker now has a detailed map of the organization's infrastructure.

---

# Performing Zone Transfer Using Dig

Syntax:

```bash
dig axfr domain.com @dns-server
```

Example:

```bash
dig axfr zonetransfer.me @nsztm1.digi.ninja
```

---

# Performing Zone Transfer Using Host

Syntax:

```bash
host -l domain.com dns-server
```

Example:

```bash
host -l example.com ns1.example.com
```

---

# Performing Zone Transfer Using Fierce

```bash
fierce --domain example.com
```

Fierce can automate DNS reconnaissance and zone transfer testing.

---

# Zone Transfer During Reconnaissance

```text
Information Gathering
        │
        ▼
DNS Enumeration
        │
        ▼
Zone Transfer Attempt
        │
        ▼
Subdomain Discovery
        │
        ▼
Further Enumeration
```

Because of the amount of information it may reveal, checking for zone transfers is a standard reconnaissance technique.

---

# Risks of Unrestricted Zone Transfers

An attacker may discover:

- Internal Network Structure
- Hidden Subdomains
- VPN Infrastructure
- Administrative Systems
- Mail Servers
- Development Environments

This information can be used to plan future attacks.

---

# Why Most Zone Transfers Fail Today

Modern DNS servers restrict zone transfers to authorized DNS servers only.

Example:

```text
Primary DNS
      │
      ▼
Authorized Secondary DNS
```

Requests from unauthorized systems receive:

```text
REFUSED
```

or

```text
Transfer Failed
```

This is the expected and secure behavior.

---

# Preventing Zone Transfer Attacks

## Restrict AXFR Requests

Allow transfers only from trusted secondary DNS servers.

---

## Use Access Control Lists (ACLs)

Specify which IP addresses may perform zone transfers.

---

## Monitor DNS Logs

Detect unauthorized AXFR attempts.

---

## Disable Unnecessary Zone Transfers

If no secondary DNS server exists, disable zone transfers completely.

---

# Advantages of Zone Transfers

- DNS Redundancy
- Improved Reliability
- Automatic Synchronization
- High Availability

---

# Disadvantages of Misconfigured Zone Transfers

- Information Disclosure
- Easier Reconnaissance
- Increased Attack Surface
- Exposure of Internal Infrastructure

---

# Key Points for Exams and Interviews

- Zone Transfer copies DNS records between DNS servers.
- AXFR performs a full zone transfer.
- IXFR performs an incremental zone transfer.
- Misconfigured zone transfers can expose all DNS records.
- Attackers use zone transfers during reconnaissance.
- The command commonly used is:

```bash
dig axfr domain.com @dns-serve
```

- Secure DNS servers restrict zone transfers to authorized hosts only.