- `How To Make Spoofrd Param Work`

sudo nano /etc/sysctl.conf

- `Move down to the bottom of sysctl file and add the following lines:`

net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.<your-virtual-interface>.send_redirects = 0
net.ipv4.<your-virtual-interface>.rp_filter=0

net/unix/tcp_window_scaling = 1

- `Change '<your-virtual-interface>' with what ever yours ex: eth0`
- `If you don't know Type 'ifconfig' and all interfaces will show up`
- `Ctrl + X + y to save`
- `type the following`

sudo sysctl -p iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
or 
sudo sysctl -p iptables -A POSTROUTING -o eth0

- `Restart your VPS`

reboot
or
shutdown -r now