# DNS (Domain Name System)

## What is DNS?

DNS (Domain Name System) is a distributed naming system that translates human-readable domain names into machine-readable IP addresses.

Without DNS, users would need to remember IP addresses instead of domain names.

### Example

When you type:

```
google.com
```

DNS converts it into:

```
142.250.183.110
```

and then your browser connects to that IP address.

---

## Why DNS is Required?

Humans can easily remember names like:

- google.com
- github.com
- amazon.com

But computers communicate using IP addresses:

- 142.250.183.110
- 20.205.243.166

DNS acts like a phonebook of the internet.

### Real-Life Example

Imagine you want to call your friend.

You search:

```
Rohit
```

in your phone contacts.

Your phone internally uses:

```
+91XXXXXXXXXX
```

Similarly:

```
google.com
```

is the contact name

and

```
142.250.183.110
```

is the phone number.

---

# How DNS Works?

When a user enters a website URL in the browser:

```
https://google.com
```

the following process occurs.

---

## Step 1: Browser Cache Check

The browser first checks whether it already knows the IP address.

Example:

```
Chrome Cache
```

If found:

```
google.com → 142.250.x.x
```

the request is completed immediately.

No DNS query is needed.

---

## Step 2: Operating System Cache

If the browser cache misses, the operating system cache is checked.

Windows/Linux/Mac maintain DNS cache locally.

Example:

```bash
ipconfig /displaydns
```

---

## Step 3: Recursive Resolver

If the OS also doesn't know the IP address, the request goes to a DNS Resolver.

Usually provided by:

- ISP
- Google DNS (8.8.8.8)
- Cloudflare DNS (1.1.1.1)

Example:

```
User
 ↓
DNS Resolver
```

The resolver's job is to find the IP address on behalf of the user.

---

## Step 4: Root DNS Server

The resolver contacts a Root DNS Server.

The root server doesn't know the exact IP address.

Instead, it knows where the TLD servers are.

Example:

```
google.com
```

Root server responds:

```
Ask the .com server
```

---

## Step 5: TLD Server

TLD = Top Level Domain

Examples:

- .com
- .org
- .net
- .edu

The resolver asks the .com server.

The TLD server replies:

```
Ask Google's Authoritative DNS Server
```

---

## Step 6: Authoritative DNS Server

This server contains the actual DNS records.

Example:

```
google.com → 142.250.183.110
```

The authoritative server returns the IP address.

---

## Step 7: DNS Resolver Stores Result

The resolver stores the result temporarily.

This is called:

```
DNS Caching
```

Future requests become faster.

---

## Step 8: Browser Connects to Website

The IP address is returned to the browser.

Example:

```
google.com
↓
142.250.183.110
```

Browser sends request to the server.

Website opens.

---

# Complete DNS Flow

```text
User
  ↓
Browser Cache
  ↓
OS Cache
  ↓
Recursive Resolver
  ↓
Root DNS Server
  ↓
TLD DNS Server (.com)
  ↓
Authoritative DNS Server
  ↓
Returns IP Address
  ↓
Website Opens
```

---

# Types of DNS Records

DNS records contain information about a domain.

---

## A Record

Maps a domain name to an IPv4 address.

Example:

```text
google.com → 142.250.183.110
```

Use Case:

- Website Hosting

---

## AAAA Record

Maps a domain name to an IPv6 address.

Example:

```text
google.com → 2404:6800:4009:80c::200e
```

Use Case:

- IPv6 Networks

---

## CNAME Record

CNAME stands for Canonical Name.

Used to create aliases.

Example:

```text
www.google.com
      ↓
google.com
```

Instead of creating multiple A records, one domain points to another.

---

## MX Record

MX = Mail Exchange Record

Used to identify mail servers.

Example:

```text
gmail.com
```

may contain:

```text
smtp.google.com
```

Use Case:

- Sending Emails
- Receiving Emails

---

## TXT Record

Stores text-based information.

Used for:

- Domain Verification
- SPF
- DKIM
- DMARC

Example:

```text
google-site-verification=abc123
```

---

## NS Record

NS = Name Server Record

Specifies which DNS server is responsible for a domain.

Example:

```text
ns1.example.com
ns2.example.com
```

---

## PTR Record

PTR = Pointer Record

Used for Reverse DNS Lookup.

Normal DNS:

```text
Domain → IP
```

Reverse DNS:

```text
IP → Domain
```

Example:

```text
142.250.183.110
↓
google.com
```

---

# What is DNS Caching?

DNS results are stored temporarily to improve speed.

Benefits:

- Faster response
- Reduced DNS traffic
- Better performance

---

# What is TTL?

TTL = Time To Live

Defines how long a DNS record can remain cached.

Example:

```text
TTL = 3600
```

Means:

```text
1 Hour
```

After that, DNS lookup will happen again.

---

# Popular Public DNS Servers

## Google DNS

```text
8.8.8.8
8.8.4.4
```

---

## Cloudflare DNS

```text
1.1.1.1
1.0.0.1
```

---

## OpenDNS

```text
208.67.222.222
208.67.220.220
```

---

# DNS Commands

## nslookup

Find IP address of a domain.

```bash
nslookup google.com
```

Output:

```text
Name: google.com
Address: 142.250.x.x
```

---

## dig

Detailed DNS information.

```bash
dig google.com
```

Check MX Record:

```bash
dig gmail.com MX
```

Check A Record:

```bash
dig google.com A
```

Check NS Record:

```bash
dig google.com NS
```

---

## ping

Check connectivity and resolve domain.

```bash
ping google.com
```

---

## host

Another DNS lookup tool.

```bash
host google.com
```

---

# DNS in AWS

AWS provides DNS services through:

Amazon Route 53

Features:

- Domain Registration
- DNS Management
- Health Checks
- Traffic Routing

Example:

```text
mywebsite.com
↓
AWS Route53
↓
EC2 Load Balancer
↓
Application
```

---

# Common Interview Questions

## What is DNS?

DNS is a system that converts domain names into IP addresses.

---

## What is the purpose of DNS?

To allow humans to use easy-to-remember names instead of IP addresses.

---

## Difference Between A Record and CNAME?

A Record:
Maps Domain → IP Address

CNAME:
Maps Domain → Another Domain

---

## What is MX Record?

Used to route emails to mail servers.

---

## What is DNS Resolver?

A server that performs DNS lookups on behalf of users.

---

## What is TTL?

TTL defines how long a DNS record remains cached before refreshing.

---

## What is Reverse DNS Lookup?

Converting an IP address back into a domain name using PTR records.

---

## Which AWS Service Provides DNS?

Amazon Route 53.