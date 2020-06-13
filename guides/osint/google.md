# Google

Google can be a powerful tool in conducting research against a target. In addition to the regular search query that everybody does, you can narrow down your focus by using some of the operators it supports.

## Operator Reference

| Operator | Example | Description |
| -- | -- | -- |
| `site` | `site:bbc.co.uk` | Filters results that only appear on `bbc.co.uk` |
| `inurl` | `inurl:admin` | Filters results where the url contains the word `admin` |
| `allinurl` | `allinurl:"admin/password"` | Same as `inurl` but results must contain all of the terms |
| `filetype` | `filetype:csv` | Filters results for `csv` files |
|  `intext` | `intext:password` or `intext:"default password" | Filters results that contain the term `default password` |
| `cache` | `cache:bbc.co.uk` | Only search for results in cached versions of `bbc.co.uk` |
| `intitle` | `intitle:"index of"` | Filter results where `index of` appears in the page title |
| `allintitle` | `allintitle:"index of" | Same as `intitle` but must contain all of the words |
| `intext` | `intext:hacking` | Filter results where the term `hacking` appears within the content of a page |
| `allintext` | `allintext:"nginx config"` | Same as `intext` but all the terms have to match |
| `inanchor` | `inanchor:secret` | Searches for anchor (`<a>`) text for the word `secret` |
| `link` | `link:bbc.co.uk/article` | Filters results for pages that contain a link to `bbc.co.uk/article` |
| `-` | `-online` | Filters result where the word `online` does not appear |
| `define` | `define:hacking` | Query for the meaning of a word |
| `map` | `map:london` | Searches Google Maps for a place |

Using the operators, you can find creative ways to utilise Google to search for information useful for your operation. For example, the following query searches for open directory listings that contain a file named `id_rsa`.

```
intext:"index of /" "id_rsa"
```

## Exploit DB

[Exploit DB](https://www.exploit-db.com/google-hacking-database) has a hacking database where people can upload useful search terms for others to use in their OSINT activities.