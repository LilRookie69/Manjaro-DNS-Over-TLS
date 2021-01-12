# Manjaro-DNS-Over-TLS

## Activate DNS over TLS
change the config of /etc/system.d/resolved.conf
```shell
sudo nano /etc/system.d/resolved.conf
```

and change the config into
```shell
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See resolved.conf(5) for details

[Resolve]
# Some examples of DNS servers which may be used for DNS= and FallbackDNS=:
# Cloudflare: 1.1.1.1 1.0.0.1 2606:4700:4700::1111 2606:4700:4700::1001
# Google:     8.8.8.8 8.8.4.4 2001:4860:4860::8888 2001:4860:4860::8844
# Quad9:      9.9.9.9 2620:fe::fe
DNS=1.1.1.1 1.0.0.1
FallbackDNS=1.1.1.1 9.9.9.10 8.8.8.8 2606:4700:4700::1111 2620:fe::10 2001:4860:4860::8888
Domains=~.
DNSSEC=yes
DNSOverTLS=yes
#MulticastDNS=yes
#LLMNR=yes
#Cache=yes
#DNSStubListener=yes
#DNSStubListenerExtra=
#ReadEtcHosts=yes
#ResolveUnicastSingleLabel=no
```

then enable and start the services
```shell
sudo systemctl enable systemd-resolved.service
sudo systemctl start systemd-resolved.service
```

you cant activate it alongside laravel valet, so you have to stop the services, before using laravel valet.