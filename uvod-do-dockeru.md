---
layout: default
title: Uvod do Dockeru
---

## Uvod do Dockeru

Je na case pustit prvni kontajner. Uz jsme Docker nainstalovali a funguje nam, pokud ne, podivejte se na clanek [Instalace Dockeru](instalace-dockeru.html).

Jako prvni si zkusime pustit Debian Stretch (9) a na nem si vysvetlime jak Docker zakladne ovladat.

Spustime prikaz `docker run -ti debian`:

```
sika@sika-x1:~$ docker run -ti debian:9
Unable to find image 'debian:9' locally
9: Pulling from library/debian
3e17c6eae66c: Pull complete
Digest: sha256:2e43e863a4ab6e53caf87a37d01d8c144cdcb732ad1b944fcf45cbfd7248a02a
Status: Downloaded newer image for debian:9
root@bbc6c22feddb:/#
```

Co jsme vlastne provedli? Spustili jsme novy kontejner z obrazu __debian:9__. Pri prvnim spusteni se musel obraz Debianu stahnout, proto bylo spouteni delsi. Pokud si chceme obrazy stahnout dopredu, muzeme pouzit `docker pull debian:9`, ale neni to potreba. Parametr `-ti` je zkratka pro `-t` (otevre TTY) a `-i` (protuneluje standartni vstup do kontejneru), ktere jsou nutne pro iterakci s aplikaci jako je napriklad bash.

Pokud nas zajima, co mame za stazene obrazy, muzeme je vypsat prikazem `docker image ls`:

```
sika@sika-x1:~$ docker image ls
REPOSITORY               TAG                 IMAGE ID            CREATED             SIZE
debian                   9                   874e27b628fd        2 weeks ago         100MB
hello-world              latest              05a3bd381fc2        6 weeks ago         1.84kB
```

Pokud budeme chtit spustit v tomto tento Debian ale misto defaultniho bashe spustit jinou aplikaci, napriklad klasicky sh shell, muzeme kontajner spustit takto `docker run -ti debian:9 sh`:

```
sika@sika-x1:~$ docker run -it debian sh
#
```

Kdyz chceme spustit nejakou aplikaci nebo prikaz primo z kontejneru a neni to zrovna shell nebo textovy editor, nemusime pouzivat prepinac `-ti`, pokud chceme napriklad pustit prikaz `date`, udelame to takto `docker run debian:9 date`:

```
sika@sika-x1:~$ docker run debian:9 date
Mon Oct 30 15:49:32 UTC 2017
sika@sika-x1:~$
```

Pokud se chceme podivat na aktualne bezici kontejnery, pouzijeme `docker ps`, pokud nas zajimaji vsechny kontejnery (i ty ktere nebezi) pridame parametr `-a`:

```
sika@sika-x1:~$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
9d5325c3ae71        debian:9            "bash"              4 seconds ago       Up 3 seconds                            modest_lovelace
```

```
sika@sika-x1:~$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                        PORTS    NAMES
9d5325c3ae71        debian:9            "bash"              38 seconds ago      Up 37 seconds                          modest_lovelace
cf39012ec4d5        debian:9            "date"              10 minutes ago      Exited (0) 10 minutes ago              goofy_bohr
6a5c51e364dd        debian:9            "sh"                15 minutes ago      Exited (0) 15 minutes ago              gracious_kilby
bbc6c22feddb        debian:9            "bash"              27 minutes ago      Exited (0) 26 minutes ago              quirky_leakey
```

Na jako prvni je ID kontejneru a na konci je jeho jmeno. Pokud ho nespecifikujeme, tak jej Docker zvoli nahodne. Muzeme ho specifikovat parametrem `--name`:

```
sika@sika-x1:~$ docker run -ti --name mydebian debian:9
root@1fbe24f0050f:/#
```

Pak bude vypis vypadat takto:

```
sika@sika-x1:~$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
1fbe24f0050f        debian:9            "bash"              6 seconds ago       Up 6 seconds                            mydebian
```

Jmeno kontajneru musi byt unikatni, pokud budeme chtit spustit novy kontajner se stejnym jmenem, musime ten minuly nejprve odstranit `docker rm mydebian`:

```
sika@sika-x1:~$ docker rm mydebian
mydebian
```

