# fancontrol_r720

Fan control script for Dell PowerEdge R720 (BSD/IPMI)

# Requirements
* ipmitool
# Running the script

The script has 3 commands:

 * enableauto: Enables automatic control of the fans
 * disableauto: Disable automatic control of the fans
 * set <n>: Set new speed for the fans (from 1-100)

Examples:

Set fan speed to 100% (this disables automatic control before setting the speed)

    $ ./fan_r720 set 100

Enable automatic control

    $ ./fan_r720 enableauto

# Persist changes after reboot

This script will NOT perist changes to the fan speeds afetr rebooting.
It is not recommended to intervene in the automatic control unless it's needed,
you may cause damage to your server by accident.
If for some reason you need to persist the changes, you can create a boot service
that will do that for you, but we won't explain it here.

# Using it over the network
This script is meant to be handled locally by the server itself. IF for some reason you need control over LAN, you can use ipmitool's parameters to do so. Some of the
reference materials inside the script will be helpful for that.