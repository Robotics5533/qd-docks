# Disabaling The RoboRio Web Server

the roborio comes with a standard web server for convinient configuration,
unfortionetly this web server eats ~ 20% of the ram on a roborio 1 so for 
ram heavy programs it can be benifitial to turn off the default web server.

links to do so can be found at this location [https://docs.wpilib.org/en/stable/docs/software/basic-programming/java-gc.html#disabling-the-system-web-server](https://docs.wpilib.org/en/stable/docs/software/basic-programming/java-gc.html#disabling-the-system-web-server)

the short of it is 


## Disabaling The Web Server

run the following commands as admin on the roborio to disable the server

```bash
/etc/init.d/systemWebServer stop; update-rc.d -f systemWebServer remove; sync
chmod a-x /usr/local/natinst/etc/init.d/systemWebServer; sync
```

## Enabaling The Web Server

run the following commands as admin to re-enable the web server

```bash
update-rc.d -f systemWebServer defaults; /etc/init.d/systemWebServer start; sync
chmod a+x /usr/local/natinst/etc/init.d/systemWebServer; sync
```


