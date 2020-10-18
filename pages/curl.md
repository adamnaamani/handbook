# cURL

## Table of Contents
1. [Flags](#flags)

## Flags
`-s`: silent mode.
```curl
curl -s
```

`-L` or `--location`: follows redirects.
```curl
curl -L
```

`-o` or `-O`: saves the output to a file.

With predefined filename:
```curl
curl -o listings.js https://resider.ca/listings.js
```
With original filename:
```curl
curl -O https://resider.ca/listings.js
```
