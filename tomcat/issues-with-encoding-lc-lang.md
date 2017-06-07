# Fixing text encoding issues in filename reading and overall Java encoding issue #

Suppose you're on a linux system and you use "service tomcat start" to start and stop your tomcat.

your init.d script will sadly take the "POSIX" language encoding, even though the OS is configured with LC_LANG=UTF_8.

How to fix it? 
2 options
first, test it by adding (if you don't have it)

```bash
. /etc/init.d/functions
```
in the beginning

you can test if it works by creating an empty shell script (```/etc/init.d/test```) like
```bash
#!/bin/bash
. /etc/init.d/functions
locale
```
remember to ```chmod +x /etc/init.d/test``` before trying it.

Then call it both with ```./etc/init.d/test``` and with ```service test start``` and see the differences.

if you still see POSIX go with the hard solution and add in the /etc/init.d/tomcat script, at the beginning

```bash
export LANG='it_IT.UTF-8'
```


BTW if you start the script with /etc/init.d/tomcat directly it will work as it takes the info from the console.
This issue can be attributed (I think) to the fact that some starting tomcat scripts don't take into consideration the profile file. by doing "source /etc/profile" or something along those lines.