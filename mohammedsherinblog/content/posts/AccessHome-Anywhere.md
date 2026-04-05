+++
date = '2026-04-05T12:50:07+03:00'
title = 'How I Access my home network from anywhere in the world'
+++

First setup Tailscale, follow my short and simple guide here:

```
Link here
```

After you are done with that, go into your Tailscale container's console and type in:

```
sudo sysctl -w net.ipv4.ip_forward=1
```

```
echo "net.ipv4.ip_forward=1" | sudo tee -a /etc/sysctl.conf
```

Verify it by:

```
sysctl net.ipv4.ip_forward
```

It should show:

```
net.ipv4.ip_forward = 1
```

Start Tailscale again by:

```
sudo tailscale up --advertise-routes={your subnet} --ssh
```

```
ex: sudo tailscale up --advertise-routes=192.168.1.0/24 --ssh
```

After that part is completed go into Tailscale admin panel, find your container in there and enable subnet routes.
