# About
Generate a "default" [seccomp](https://en.wikipedia.org/wiki/Seccomp), suitable for most non-admin applications. Can be later used by e.g. [bubblewrap](https://github.com/containers/bubblewrap).

While this might not be as well-tuned as a seccomp file created specifically for a certain application, it should still be quite good in limiting the obviously questionable syscalls while allowing those that are commonly needed by "normal" apps.

# Build
Install dependencies (ArchLinux):
```sh
pacman -S libseccomp
```

Install dependencies (Ubuntu):
```sh
apt install libseccomp-dev
```

On NixOS execute:
```sh
nix-shell -p gcc libseccomp
```

Compile:
```sh
gcc seccomp-gen.c -lseccomp -Wall -pedantic -o seccomp-gen
```

Run:
```sh
./seccomp-gen
```

At last step, a file named `seccomp.bpf` will be generated.
This seccomp filter can then be used in other apps (e.g. bubblewrap).


# Credits
Originally taken from [https://github.com/kurnevsky/dotfiles/tree/master/.seccomp](https://github.com/kurnevsky/dotfiles/tree/master/.seccomp), which in turn was taken from somewhere else AFAIR.

# License
I'm not sure honestly, but I don't care much either, the code is super-direct given the libseccomp library's API. Any my contributions, in this repo or in the referenced one, are CC0.
