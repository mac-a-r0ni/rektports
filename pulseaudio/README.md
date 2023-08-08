pulseaudio
==========

## server shutting down when used with a WM

If you are not running a fully fledged DE you might have trouble
with pulseaudio shutting down after being idle for a while. You can
work around this by starting pulseaudio like this:

~/.xinitrc
#!/bin/bash
pulseaudio --start --exit-idle-time=-1 --log-target=syslog &
exec /usr/bin/myawesomewm

## system mode

See [What is wrong with system mode? – PulseAudio](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/WhatIsWrongWithSystemWide/)
for more information.

This was previously a pre-install script:

```sh
#!/bin/sh

# check for pulseaudio group or add one
getent group pulse || /usr/sbin/groupadd pulse
getent group pulse-access || /usr/sbin/groupadd pulse-access

# check for pulseaudio user or add one
getent passwd pulse || /usr/sbin/useradd -g pulse -d /var/lib/pulse -s /bin/false -c "Pulseaudio User" pulse

# lock the account
/usr/bin/passwd -l pulse
```
