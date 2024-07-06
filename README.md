### Deploying new configurations
Install nix-os sd card image (just download the newest version) https://hydra.nixos.org/job/nixos/release-24.05/nixos.sd_image.aarch64-linux
flash it with balena etcher to your sd card https://etcher.balena.io/
put the sd card into the rpi, turn on, wait for it to boot (you might get a flashing display -> wait for 15 minutes -> switch off and back on -> voilà) you should see a command window now.
Run these commands.
You should use `nixos-rebuild` locally:
```
$ sudo -s
$ nix-env -iA nixos.pkgs.gitAndTools.gitFull
$ git clone https://github.com/Jojo09092007/UPDATE-KODAK-3D-PRINTER.git
$ cd UPDATE-KODAK-3D-PRINTER-main
$ nixos-rebuild switch --flake .#akamanto
```
reboot after, if necessary

## General notes
This is a copy of an old config with raspberry pi 3 support from ar (see link)
She changed to a rpi5, so you can't use her repo anymore, here is her documentation https://wiki.hackerspace.pl/infra:tools:kodakportrait
in the archive of the site, there are also the old original files of the Kodak Portrait https://cloud.is-a.cat/s/NsaCHnyDMn8cFWE
I couldn't flash them successfully.
I hope this works. DIDN'T TEST IT YET!!!

Feel free to use this as a basis for your own configuration flakes, the general state might not reflect best
practices. Use caution, and if you feel like you don't really understand
something (and there are some code crimes commited here), don't feel obliged to
use it just because it's already here.

## Additional Documents
https://wiki.nixos.org/wiki/NixOS_on_ARM/Raspberry_Pi_3
More general issues:
https://wiki.nixos.org/wiki/NixOS_on_ARM/Raspberry_Pi

## Persistent Issues
Booting will not show the console
Fix: restart after x minutes OR unplug and replug the HDMI cable inside the 3D Printer OR connect a new display to it and reboot

