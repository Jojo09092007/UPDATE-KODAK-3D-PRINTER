### Deploying new configurations
1. Download nix-os sd card image. (just download the newest version) (Link 1)
2. Flash it with balena etcher to your sd card. (Link 2)
3. Put the sd card into the rpi, turn it on, wait for it to boot (you might get a flashing display -> wait for 15 minutes -> switch off and back on -> voilà) you should see a command window now.
4. Run these commands. To change keyboard layout. To create a swap file, because the ram isn't enough. 
```
$ loadkeys de "Optional, if you want to change keyboard layout"
$ sudo fallocate -l 2G /swapfile
$ sudo chmod 600 /swapfile
$ sudo mkswap /swapfile
$ sudo swapon /swapfile
```
5. Check if available
```
$ free -h
```
6. Kinda optional, to create it persistently create "/etc/nixos/configuration.nix" put the following in. (with nano)
```
swapDevices = [
  { device = "/swapfile"; }
];
```
7. To make it permanent. (Kinda optional)
```
$ sudo nixos-rebuild switch
```
8. And now to the actual installation. You should use `nixos-rebuild` locally:
```
$ sudo -s
$ date -s JJJJ-MM-DD
$ nix-env -iA nixos.pkgs.gitAndTools.gitFull
$ git clone https://github.com/Jojo09092007/UPDATE-KODAK-3D-PRINTER.git
$ cd UPDATE-KODAK-3D-PRINTER
$ chmod +x *
$ nixos-rebuild switch --flake .#akamanto
```
reboot after, if necessary

## General notes
- This is a copy of an old config with raspberry pi 3 support from ar. (Link 5)
- She changed to a rpi5, so you can't use her repo anymore, here is her documentation. (Link 3)
- In the archive of the site, there are also the old original files of the Kodak Portrait 3D Printer. (Link 4)
* I couldn't flash them successfully.
- I hope the before mentioned method works. DIDN'T TEST IT YET!!!

Feel free to use this as a basis for your own configuration flakes, the general state might not reflect best
practices. Use caution, and if you feel like you don't really understand
something (and there are some code crimes commited here), don't feel obliged to
use it just because it's already here.
For Contact(I will take my time): Open an Issue.

## Additional Documents
1. https://hydra.nixos.org/job/nixos/release-24.05/nixos.sd_image.aarch64-linux
2. https://etcher.balena.io/
3. https://wiki.hackerspace.pl/infra:tools:kodakportrait
4. https://cloud.is-a.cat/s/NsaCHnyDMn8cFWE
5. https://github.com/arachnist/nibylandia/tree/251448dd13d61c8fa925592305783edb28f5fa8c
- Might be useful: https://wiki.nixos.org/wiki/NixOS_on_ARM/Raspberry_Pi_3

- More general issues:
https://wiki.nixos.org/wiki/NixOS_on_ARM/Raspberry_Pi

## Persistent Issues
Booting will not show the console
- (Maybe permanent) Fix: restart after x minutes OR unplug and replug the HDMI cable inside the 3D Printer OR connect a new display to it and reboot

