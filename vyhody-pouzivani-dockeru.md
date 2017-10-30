---
layout: default
title: Vyhody pouzivani Dockeru
---

# Vyhody pouzivani Dockeru

Vyhody Dockeru se daji rozdelit do ruznych oblasti:

- Vyvoj
- Testovani
- Produkce

Docker umi velmi rychle a efektivne vytvaret a mazat kontejnery, z cehoz plynou tyto hezke vlastnosti. Rychly setup vyvojoveho prostredi. Determininsticke testovani, to znamena, ze testovaci prostredi se pro kazdy test vytvori znovu. Rekneme si k tomu vice pozdeji.

Kontejnery se spousteji z takzvanych obrazu (rootfs a nastaveni), ktere jsou definovane v souboru, to znamena ze presne vime jak dany obraz, nasledne kontejner, vznikl. Ne jako u virtualniho serveru, ktery neni vetsinou jednoucelovy a pokud nepouzivame provisioning tak netusime, v jakem stavu je.

Dalsi vyhodou Dockeru je distribuce obrazu, tkazvana [Docker Registry](/docker-registry.html). Pomoci ni muzeme velmi jednoduse distribuvat obrazy. Vice se o Docker Registry dozvite v samostatnem [clanku](/docker-registry.html).


## Vyhody Dockeru ve vyvoji

Jak jsem rikal, rychly start kontejneru a Docker Registy nam umoznuje rychle spusteni vyvojhoveho (ale i testovaciho prostredi). Pri vyvoji nepracuji vsichni jen na Linuxu, hodne lidi dela na OSX a na Windows, kde si instalovat ruzne jazyky, prostredi neni uplne prijemne. Proto se hodne lidi kloni k vyvoji v Dockeru. Ma to vyhodu ze ve stejnem prostredi jako mam vyvojar se bude aplikace testovat a bude nasazena na produkci. Tento setup minimalizuje riziko spojene s problemy ruzneho nastaveni ve vyvoji, testovani a produkci.


## Vyhody Dockeru v testovani

Automaticke testovani si jiz bez Dockeru a kontejneru nedokazu predstavit. Diky Dockeru a jeho rychlemu vytvareni kontejneru mohu testy poustet v oddelenych prostredich bez toho, aniz by se behy vzajemne ovlivnovali a mohu vzdy testovat na cistem prostredi.

Dalsi velkou vyhodou je to, ze testuji aplikaci v presne stejnem prostredi jako je na produkci a nemusim se bat napriklad ruznych verzi zavislosti nebo systemu. Pokud testy projdou, vim ze na produkci to pujde take.

Vice o testovani s Dockerem se dozvite v clanku [Docker v CI](/docker-v-ci.html).


## Vyhody Dockeru v Produkci

Kdyz uz v Dockeru vyvijime, testujeme neni nic jednodussiho nez nase kontejnery poustet v produkci. Nemusime se starar o to, co je nainstalovane na nase produkcni servery, staci kdyz na nich mame Docker. Vsechny zavislosti jsou svazany s konkretni aplikaci (obrazem). Cely proces nasazovani do produkce se velmi urychli.

Muzeme nase aplikace jednoduse skalovat a nebo nasadit do clusteru Docker Swarm nebo napriklad Kubernetes. O Swarmu, nativnim Docker clusteru, se doctete vice v samostatnem clanku [Docker Swarm](/swarm-docker-cluster.html).

