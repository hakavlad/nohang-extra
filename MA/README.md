
# memavaild

A new way to improve responsiveness during intense swapping.

## How to install

```
$ git clone https://github.com/hakavlad/nohang-extra.git && cd nohang-extra/MA
$ sudo make install
$ sudo systemctl enable --now memavaild.service
```

## Demo

`stress -m 9 --vm-bytes 99G` without full freezing: https://www.youtube.com/watch?v=DJq00pEt4xg
