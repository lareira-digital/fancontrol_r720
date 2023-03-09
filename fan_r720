#!/usr/bin/env bash

# Reference materials
# https://gist.github.com/kaysond/35f63c32a0a11daa9e0a53a9c200c1a4
# https://github.com/edlitmus/freebsd-r720/blob/main/fanspeed.sh
# https://i.imgur.com/u1HMyqI.png
# https://www.reddit.com/r/homelab/comments/d7u7jt/dell_r720_fan_noise_control_via_ipmi/


ENABLE_AUTO_CONTROL="raw 0x30 0x30 0x01 0x01"
DISABLE_AUTO_CONTROL="raw 0x30 0x30 0x01 0x00"
SET_FAN_SPEED="raw 0x30 0x30 0x02 0xff "

PARAMETER="$1"
VALUE="$2"

if [[ $1 == "enableauto" ]]; then
    ipmitool $ENABLE_AUTO_CONTROL
elif [[ $1 == "disableauto" ]]; then
    ipmitool $DISABLE_AUTO_CONTROL
elif [[ $1 == "set" && $2 != '' ]]; then
    HEX_VALUE=$(printf "0x%x" $VALUE)
    ipmitool $DISABLE_AUTO_CONTROL
    ipmitool $SET_FAN_SPEED$HEX_VALUE
else
    echo "ERROR: One option is required (enableauto, disableauto, set N)"
fi