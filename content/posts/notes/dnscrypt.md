---
date: '2026-09-28T23:26:33+07:00'
draft: true
title: 'Dnscrypt'
tags: []
categories: ['Notes']
---
## Insall DNSCrypt-proxy

```shell
sudo pacman -S dnscrypt-proxy
```

## Konfigurasi

```shell
sudo nvim /etc/dnscrypt-proxy/dnscrypt-proxy.toml
```

### Ubah Listen Addresses

```toml
listen_addresses = ['127.0.0.1:53', '[::1]:53']
```

### Pilih Server DNS

```toml
server_names = ['cloudflare', 'cloudflare-ipv6']
```

### 

```toml
lb_strategy = 'p2'
```

###
```toml
require_dnssec = true
```

## Konfigurasi DNS Resolver Sistem 

```shell
sudo nvim /etc/resolv.conf
```

Tambahkan
```toml
nameserver ::1
nameserver 127.0.0.1
options edns0
```

## Melindungi File `resolv.conf`
```shell
sudo chattr +i /etc/resolv.conf
```

## 
```shell
sudo systemctl enable --now dnscrypt-proxy.service
```
```shell
sudo systemctl status dnscrypt-proxy.service
```

## Test
```shell
nslookup google.com
```
```shell
dig google.com
```
