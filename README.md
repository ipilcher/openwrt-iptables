# OpenWRT-iptables

## Introduction

**OpenWRT-iptables** is a simple ``iptables`` and ``ip6tables`` startup script
for **OpenWRT**.  It is an alternative to OpenWRT's default ``fw3`` firewall
management tool.

## Installation

1. Copy ``init.d/iptables`` to ``/etc/init.d/``.  Make sure that it is
   executable.

1. Symlink ``/etc/init.d/ip6tables`` to ``iptables``.

1. Create a directory &mdash; ``/etc/sysconfig``.

1. Copy ``sysconfig/iptables`` and ``sysconfig/ip6tables`` to
   ``/etc/sysconfig/``.

1. Disable the default ``firewall`` service and enable the new services.
   1. ``service firewall disable``
   1. ``service iptables enable``
   1. ``service ip6tables enable``
   
1. Reboot.

> **NOTE:** The default configuration only allows inbound connections to TCP
> port 22 (``ssh``); IP forwarding and NAT are disabled.  It may be necessary
> to customize the configuration files before enabling the new services.
>
> Proceed with caution to avoid losing access to your WAP/router.

## Additional Commands

The service script supports two additional commands:

1. ``save`` &mdash; Saves current rules to ``/etc/sysconfig/iptables`` (or
   ``/etc/sysconfig/ip6tables``).
   
1. ``dump`` &mdash; Writes current rules to ``stdout``.
