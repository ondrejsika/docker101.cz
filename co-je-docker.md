---
layout: default
title: Co je Docker
---

# Co je Docker

Docker je nastroj, ktery umoznuje efektivne pracovat s Linuxovymi kontejnery. A co jsou ty kontejnery? Predstavte si to jako klasicke virtualni servery, kde mate oddeleny disk (root filesystem), procesy, pamet a sit. Rozdil proti virtualizaci je v tom ze jsou tyto zdroje oddeleny pomoci jmenych prostoru primo v Kernelu narozdil od emulovaneho hardware jako dela klasicka virtualizace. Proto jsou kontejnery mnohem efektivnejsi nez klasicka virtualizace a nemaji skoro zadny overhead.

Zajem o Docker (a kontejnery) v poslednich letech velmi roste a tuto technologii pouziva stale vice velkych firem jako je Google, Facebook nebo Microsoft.

Popularita Dockeru je tak velka ze jej muzete pouzivat i z Windows a OSX.


### Rozdil mezi kontejnery a virtualizaci

Takze jake jsou rozdily mezi kontajnery a virtualami? Hlavnim rozdilem, ze ktereho plynou klicove vlastnosti, je to ze virtualizace emuluje hardware a kontejnery bezi v jednom kernelu, ale v ruznych namespacech.

Z toho vypliva, ze na virtualizaci (napriklad KVM nebo HyperV) muzete bezet jakykoliv system a nezavisi na systemu hosta. Napriklad mohu mit host OS Linux a ve virtualu mit Windows a naopak. Pro virtualizaci to neni zadny problem.

Kdyzto Docker bezi v jednom Kernelu, host OS musi byt Linux a kontejnery musi byt take Linuxy a maji stejnou verzi Kernelu. To ovsem neni zadny problem. Rikal jsem ze Docker muzeme spustit i na Windows a OSX, k tomu se jeste dostanu.

Virtualizovane stroje jsou vicemene nezavysle na hostu. Narozdil kontejnery nektere zdroje s hostem sdileji, treba cas. Nerikam ze je nutne mit c kazdem kontejneru vlastni cas, ale jsou urcite veci, ktere si proste nenastavite, ale vetsinou to neni zadna komplikace.

