# Print the request lookup time, connect, transfer and total time with curl #

The -w parameter allows to choose and select what to print about the curl result

```bash
curl -w '\nLookup time:\t%{time_namelookup}\nConnect time:\t%{time_connect}\nPreXfer time:\t%{time_pretransfer}\nStartXfer time:\t%{time_starttransfer}\n\nTotal time:\t%{time_total}\n' -o /dev/null -s DOMAIN
```