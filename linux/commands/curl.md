---
Title: curl
Description:
Date: 2021-03-02 18:32
References:
Tags: #linux #command
---

# curl

Tool to transfer data from or to a server, supports loooots of protocols, mainly used for HTTP-requests.

## Common usage 

- `curl catalysm.net`
A GET request for a website URL.

- `curl -X POST`
Specify a custom request method, e.g. POST.

- `curl -I catalysm.net`
Only fetch the HTTP headers.

- `curl -o file.ext catalysm.net/file.ext`
Fetch content and save it in a file.

- `curl -H "headerKey: val" catalysm.net`.
Add extrea headers

- `curl -v catalysm.net`
Verbose output

- `curl catalysm.net @json-file`
This posts data exactly as specified with no extra processing whatsover. If you start the data with the letter @, the rest should be a filename.  E.g. In the case the post body is json data. You can pass a json file which will be used as body.





