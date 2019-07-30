## rpi-sundtek-tvheadend
Raspberry Pi based :tv: docker container for tvheadend with sundtek dvb adapter

Tvheadend is a TV streaming server and recorder for Linux, FreeBSD and Android supporting DVB-S, DVB-S2, DVB-C, DVB-T, ATSC, ISDB-T, IPTV, SAT>IP and HDHomeRun as input sources.  

[tvheadend.org](https://tvheadend.org/)

The 'stable' version of tvheadend is used. 

### Pull
```bash
docker pull docker pull juergenkersten/rpi-sundtek-tvheadend:latest
```

### Run:
Notes:
- We do NOT pass the sundtek adapter to the docker instance, because it is not installed on the host.
- Do NOT install the sundtek driver on the host

```bash
docker run \
--name="tvheadend" \
--restart=always \
--privileged \
--net=bridge \
-v /media/8tb.wd.red/recordings/:/recordings \
-v /home/docker/tvheadend/:/config \
-v /home/docker/picons/:/picons \
-v /etc/localtime:/etc/localtime:ro \
-p 9981:9981 \
-p 9982:9982 \
--device=/dev/dvb/* \
-d juergenkersten/rpi-sundtek-tvheadend
```

### Important Notice - First Start
Don't install sundtek driver on your host.

### Build
```bash

git clone https://github.com/juergenkersten/rpi-sundtek-tvheadend.git
cd rpi-sundtek-tvheadend
docker build -t juergenkersten/rpi-sundtek-tvheadend .
```

### Picons:
https://github.com/picons/picons-source

## License
See the [LICENSE](LICENSE.md) file for license rights and limitations (MIT).
