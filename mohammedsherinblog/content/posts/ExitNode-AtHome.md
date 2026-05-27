+++
date = '2026-05-27T19:24:45+03:00'
title = 'How I setup Exit Node through my Home Network'
+++

I managed to do this through Tailscale.

Follow my short and simple guide to setup remote access to home network and Proxmox server here:

- [How I Access My Home Network from Anywhere in The World](https://mdsherinoff.github.io/posts/accesshome-anywhere/)
- [How I Access My Home Server from Anywhere in The World](https://mdsherinoff.github.io/posts/accessserver-tailscale/)

After you are done with setting up tailscale on your home and Proxmox server, go into your device console which is going to be used as your exit node and type this in:

```shell
sudo tailscale set --advertise-exit-node
sudo tailscale up
```

Once you are done with this, all you have to do is go into your tailscale web console and permit the machine to act as an exit node.

Now you have an exit node setup through the network at which your machine is.

Access this exit node from another machine on your tailscale network as normally as connecting to the tailscale VPN and choosing the other machine as your exit node in there.
