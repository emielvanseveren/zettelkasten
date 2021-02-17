---
Title: Dig
Description: dns-tool
Date: 17-02-2021
Tags: #dns, #linux, #command
References: 
Editor: markdown
---

# Dig

DNS lookup utility

## Common usage

- `dig catalysm.net`
	Returns A record by default.

- `dig -t ANY catalysm.net`. 
	Define type of record. ANY returns all resource records.

- `dig catalysm.net +short`
	Returns the short response form.

- `dig -x 10.210.20.50`
	To perform a reverse look up using the ip-addr.

- `dig @1.1.1.1 catalysm.net` 
	By default dig uses the DNS servers defined in your /etc/resolv.conf file. This example uses Cloudflare's DNS server.