# Ploopy Adept

## Compile Firmware

```
docker build . -t qmk:latest
docker run --rm -it qmk:latest bash
root # qmk compile -kb ploopyco/madromys/rev1_001 -km via
# .uf2 in /root/qmk_firmware/.build/
```
