### Deploying new configurations
You should use `nixos-rebuild` locally:
```
$ sudo nixos-rebuild switch --flake .#microlith
```

## General notes
Feel free to use this as a basis for your own configuration flakes, but while I
keep things here working for me, the general state might not reflect best
practices. Use caution, and if you feel like you don't really understand
something (and there are some code crimes commited here), don't feel obliged to
use it just because it's already here.
