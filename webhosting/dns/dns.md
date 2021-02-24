---
Title: DNS
Description: DNS common knowledge
Date: 16-02-2021
Tags: #dns
References: [[dig]]
Editor: markdown
---


# DNS
## Common DNS records:
| type  | name                  | value                    |
| ----- | --------------------- | ------------------------ |
| A     | domain name           | IPv4                     |
| AAAA  | domainname            | IPv6                     | 
| NS    | domainname            | hostname authoritive DNS |
| MX    | mail alias domainname | canonical hostname       |
| CNAME | alias                 | canonical hostname       |

**A**-record translates hostname and ip (default record)
**AAAA**-record identical to A-record but with ipv6.
**NS**-record identifies the name servers, responsible for your DNS zone. 
**MX**-record is a way to point a certain e-mail domainname to another e-mail domainname.
**CNAME**-record is a way to point a certain domain name to another domain name.

DNS information gathering utility: `dig command` [[dig]]