AMD GPU template uses WMI Query to retrieve sensor and data from OpenHardwareMonitor, it is required to have OpenHardwareMonitor installed on the monitored Windows host.
Template retrieves AMD GPU sensors and data:
1. GPU Name
2. GPU Core Clock
3. GPU Core Load
4. GPU Core Temperature
5. GPU Hot Spot Temperature
6. GPU Memory Clock
7. GPU Memory Load
8. GPU Total Power
9. GPU Fan Speed in %
10. GPU Fan Speed in RPM

Template created and tested with AMD Radeon RX 6700XT on Zabbix 6.4.3, WMI tested on Windows 10 host.
Here's the template in action:

![image](https://github.com/demichel93/AMD_GPU_Zabbix_Template/assets/69034200/86caea4d-f5d3-4f77-a955-48fb27dfa684)


Template does not have any triggers.

NOTE: Zabbix rounds up numeric output of items, If you don't want Zabbix to round up numeric output you need to edit a func.inc.php file of a Zabbix Frontend. You can find it under /usr/share/zabbix/include/ (assuming you have frontend installed on the same server as Zabbix server). 
Open the php file with a text editor of your choice, go to line with $blacklist in it and add Hz, KHz, MHz and GHz to the list of blacklisted units, example below:

$blacklist = ['Hz', 'MHz', 'KHz', 'GHz', '%', 'ms', 'rpm', 'RPM'];

Save the file and restart the Zabbix server service.
