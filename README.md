# NixOS-KDE-PJATK-VPN-Configurations-For-MSSQL
For students going crazy because of some small VPN setting derivation not allowing them to connect to our schools servers since our school only provides a guide on a Debian based Gnome system.

This is what has worked for me, I am just tring to help if you are looking for a solution online, I take no responsibility, I dont even know for what.

# Guide

You can copy the file name "PJWSTK VPN" this and fill here with your student mail.
user=sXXXXX@pjwstk.edu.pl 

The file doesn't include uuid, OS autogenerates it as far as I know, if not you can run uuidgen in your terminal and add uuid=YOUR_UUID under [connection] section in your configuration. Your password is also handled by your DE secrets manager. It is very hard to get this right under KDE because of the naming differences and most importantly requiring MPPE or using it very confusing. Not to mention confusing routing panes and stuff.  
So basically copy this, fill your mail, paste it into the file under "/etc/NetworkManager/system-connections/PJWSTK VPN", like `sudo mkdir "/etc/NetworkManager/system-connections/PJWSTK VPN"` or `sudo nvim "/etc/NetworkManager/system-connections/PJWSTK VPN"' for editing. then run the following 
1. `sudo chmod 600 "/etc/NetworkManager/system-connections/PJWSTK VPN"` 
2. `sudo chown root:root "/etc/NetworkManager/system-connections/PJWSTK VPN"`
3. `sudo nmcli connection reload`
4. `sudo nmcli connection up "PJWSTK VPN"`
    - If you havent tried connecting before, go to your KDE or any network settings and give it your password in the VPN settings, it will store it for you, and click connect.
5. If there are no errors test your connection to database with `nc -zv db-mssql.pjwstk.edu.pl 1433`  
6. *Try in DataGrip* by first choosing User&Password authentication method in the dropdown and in the user section write PJWST/sXXXXX and give your pass too. It will give error and turn automatically to Domain credentials. Hit test, it will download drivers, and you should be all set! Yippie `._.)/\(._.`

![Screenshot for DataGrip Database Configurations](DataGrip_Setup.png?raw=true)

