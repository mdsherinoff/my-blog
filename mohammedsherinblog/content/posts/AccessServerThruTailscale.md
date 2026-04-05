# How I Access my Proxmox Server from Anywhere using Tailscale

I started by creating an Ubuntu container inside my Proxmox Environment. I usually make the container ID the same as my static IP address I have determined for this container, so as to easily navigate. Don't start your container yet.

After the container is setup, I went to the host kernel into its:

```
vi /etc/pve/lxc/{container ID}.conf
```

In there using the vi editor, I added a couple of lines:

```
lxc.cgroup2.devices.allow: c 10:200 rwm
lxc.mount.entry: /dev/net/tun dev/net/tun none bind,create=file
```

Exit from the vi editor and now start your container.

Open the container's console and update, upgrade and then install curl:

```
apt update
apt upgrade
apt install curl
```

Now install Tailscale onto your device through the console, find the link to install onto device from:

```
https://tailscale.com/download
```

OR use this:

```
curl -fsSL https://tailscale.com/install.sh | sh
```

Use the linux curl provided, once Tailscale installation is completed, type in

```
tailscale up --ssh
```

You will receive a link provided, use the provided link to go to the Tailscale website and setup your account. Once completed install Tailscale on your desired device be it mobile or laptop.

And VOILA now you can access your Proxmox Server from anywhere in the world.
