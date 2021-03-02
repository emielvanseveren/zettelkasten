---
Title: Dig
Description: dns-tool
Date: 17-02-2021
Tags: #dns, #linux, #command
References: 
Editor: markdown
---

# Dig

DNS lookup utility. Alternative for 

## Common usage

 ```bash 
 	# Returns A record by default.
	dig catalysm.net

	# Define type of record. ANY returns all resource records.
	dig -t ANY catalysm.net 

	#Returns the short response form.
	dig catalysm.net +short

	# To perform a reverse look up using the ip-addr.
	dig -x 10.210.20.50

	# By default dig uses the DNS servers defined in your 
	# /etc/resolv.conf file. This example uses Cloudflare's 
	# DNS server.
	dig @1.1.1.1 catalysm.net
	```