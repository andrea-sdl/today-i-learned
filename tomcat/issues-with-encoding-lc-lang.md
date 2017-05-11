# Fixing text encoding issues in filename reading and overall Java encoding issue #

Suppose you're on a linux system and you use "service tomcat start" to start and stop your tomcat.

your init.d script will sadly take the "POSIX" language encoding, even though the OS is configured with LC_LANG=UTF_8.

How to fix it? 
in the /etc/init.d/tomcat script add in the beginning

```bash
export LANG='it_IT.UTF-8'
```

BTW if you start the script with /etc/init.d/tomcat directly it will work as it takes the info from the console.
This issue can be attributed (I think) to the fact that some starting tomcat scripts don't take into consideration the profile file. by doing "source /etc/profile" or something alond those lines.