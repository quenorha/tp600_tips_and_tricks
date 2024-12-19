Debug mode or development tools can be useful to analyze a web page which is not rendered properly on a WAGO HMI webbrowser (TP600 or WP400). It can be used to check the console, or to see the security settings.
To enable debug mode it, the webbrowser must be started with the "-remote-debugging-port" option.
To do this, connect to the screen via SSH (via Putty for example).
Edit the file "/etc/script/start_webbrowser.sh" using the nano editor (make a backup copy beforehand)

```
cp /etc/script/start_webbrowser.sh /etc/script/start_webbrowser.sh.save
nano /etc/script/start_webbrowser.sh
```
Replace the line

```
/usr/bin/webenginebrowser $URL &
```
With the following content:

```
/usr/bin/webenginebrowser $URL --remote-debugging-port=1080 &
```
It is also necessary to be able to view the different tabs to switch from the development tab to the page to be analyzed.
Edit the file "/etc/specific/webengine/webengine.conf" using the nano editor (make a backup copy beforehand)

```
cp /etc/specific/webengine/webengine.conf etc/specific/webengine/webengine.conf.save
nano /etc/specific/webengine/webengine.conf
```
And edit the different properties as follows:

```
tabbar=1
zoom=0
navbar=1
menubar=0
```
After these changes, restart the screen

```
sync reboot
```
Now it is possible to run the following command to display the development tools tab.

```
echo newtab=http://127.0.0.1:1080 > /dev/webenginebrowser
```
In the development tab, select the page to analyze.
