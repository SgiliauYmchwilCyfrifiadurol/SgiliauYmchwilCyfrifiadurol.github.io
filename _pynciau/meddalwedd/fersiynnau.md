---
layout: post
title: 19. Ysgrifennu Meddalwedd - Fersiynnau
permalink: meddalwedd/fersiynnau/
---

Mae nodi pa fersiwn o meddalwedd a ddefnyddiwyd mewn darn o waith yn hollbwysig
ar gyfer ailgynhyrchadwyedd.
Gall canlyniadau a generadwyd gan fersiwn henach new mewy newydd o'r un
meddalwedd bod yn wahanol, a gall y methodoleg (cystrawen y cod a ysgrifenwyd)
newid o fersiwn i fersiwn.

Rhaid ystyried hyn wrth ysgrifennu meddalwedd:

+ Nodwn rhif ferswin y meddallwedd yn glir o fewn y meddalwedd ei hun, yn y
dogfennaeth, ac ar unrhyw storfa lle ellir lawrlwytho'r meddalwedd.
+ Gwnewn yn siŵr bod pob un hen fersiwn o'r meddalwedd ar gael yn hawdd.
+ Nodwn yn ofalus y gwahaniaethau rhwng pob fersiwn mewn dogfen sydd ar gael o
fewn y meddalwedd ac hefyd yn y dogfennaeth.


# Fersiynu Semantig

Mae fersiynu semantig yn ffordd systematig o rhifo fersiynnau i'w wneud yn fwy
ystyrlon a chlir.

Maent yn helpu adnabod **ôl-gytunedd** rhwng fersiynnau.
Os oes ôl-gytunedd rhwng dau fersiwn, yna mae defnydd, cystrawen a canlyniadau
yr hen fersiwn yn gweithio'n unfath yn y fersiwn newydd.
Os yw ôl-gytunedd wedi torri rhwng fersiynnau, yna bydd defnydd, cystrawen neu
canlyniadau'r fersiwn newydd yn gwahanol i'r hen fersiwn.
Fel datblygwyr meddalwedd ceisiwn osgoi torri ôl-gytunedd yn amal gan ei fod yn
gorfodi defnyddwyr ail-ddysgu'r meddalwedd ac ail-ysgrifennu hen waith, ac mae'n
achosimethodoleg ymchwil mynd 'out-of-date'.

Mae fersiynu semantig yn defnyddio pedwar lefel o fersiynu, a dynodir y fersiwn
gan tair rhif `x.y.z`.

+ Y lefel isaf yw'r lefel '*commit*'. Mae newidiadau rhwng y lefelau yma yn bach
iawn, fel arfer cwpl o llinellau o cod ar y tro. Defnyddir rhain ar gyfer
ysgrifennu meddalwedd yn unig, a'i rheolir gan systemau rheolaeth fersiwn megis
Git. NI RHYDDHEIR NEWIDIADAU AR Y LEFEL YMA, ac fellu nid ydym yn newid y rhif
fersiwn.

+ Y lefel nesaf yw'r lefel '*patch*'. Ar ôl nifer o newidiadau ar y lefel commit
bydd gennym fersiwn o'r meddalwedd sy'n gweithio ac sy'n barod i'w rhyddhau. Mae
newidiadau ar y lefel yma yn fach, ac fel arfer yn trwsio bygs. Nid yw patch yn
torri ôl-gytunedd. Cynyddir y rhif `z` pan rhyddheir newid fel hyn.

+ Y lefel nesa yw'r lefel 'mân' (minor). Mae newidiadau ar y lefel yma fel arfer
yn ychwanegu nodweddion newydd i'r meddalwedd. Nid yw newid mân yn torri
ôl-gytunedd. Cynyddir y rhif `y` ac osodir y rhif `z` i sero pan rhyddheir newid
fel hyn.

+ Y lefel nesa yw'r lefel 'mawr' (major). Mae newidiadau ar y lefel yma yn
sylweddol, ac yn torri ôl-gytunedd. Cynyddir y rhif `x` ac osodir y rhifau `y` a
`z` i sero pan rhyddheir newid fel hyn.

> Enghraifft: Gwyddon fod y gwahaniaeth rhwng fersiwn `1.1.3` ac `1.1.4` yn fach megis trwsio byg.

> Enghraifft: Gwyddon fod y gwahaniaeth rhwng fersiwn `1.1.3` ac `1.2.0` yn sylweddol megis ychwanegu nodwedd newyhdd, ond nid y'r torri ôl-gytunedd.

> Enghraifft: Gwyddon fod y gwahaniaeth rhwng fersiwn `1.0.3` ac `2.0.0` yn sylweddol, ac bydd ôl-gytunedd wedi torri.


# Log Newidiadau

Ffeil yw log newidiadau (changelog) sy'n cynnwys rhestr cronolegol o'r holl
newidiadau sylweddol ar gyfer pob fersiwn o meddalwedd.
Mae'n gwenud e'n haws i defnyddwyr y meddalwedd a chyfranwyr i'r meddalwedd
gweld yn union pa newidiadau sydd rhwng pob fersiwn o'r meddalwedd.
Pwrpas log newidiadau yw i cael ei ddarllen gan pobl, gan defnyddwyr.

Mae'n gwahanol i log 'commit' a rhoddir gan systemau rheolaeth fersiwn: dim ond
nodi newidiadau rhwng fersiynnau a rhyddheir sydd angen (newidiadau ar lefel
'patch', 'mân', a 'mawr').
Dylai esbonio newidiadau o safbwynt defnyddiwr.

Awgrymiadau:

+ Dylai fod cofnod ar gyfer *pob* fersiwn;
+ Dylai'r fersiwn diwethaf dod yn gyntaf, a pob fersiwn arall dod ar ei hôl mewn
trefn gronolegol gwrthdro;
+ Dylai dangos dyddiad rhyddhai pob fersiwn;
+ Dylai newidiadau fod o'r fath:
  + `Ychwanegu` nodweddion newydd,
  + `Newid` nodweddion,
  + `Dibrisio` nodweddion a ddileuir yn fuan,
  + `Dileu` nodweddion,
  + `Trwsio` bygs, a
  + `Diogelwch` ar gyfer gwendidau.

Cymerwch cipolwg ar yr enghraifft ffug isod.
Ffeil tecst, markdown neu .rst yw hwn o'r enw `CHANGES` neu `CHANGELOG`:

{% highlight text %}
Hanes
-----

v1.0.1 (2018-06-28)
~~~~~~~~~~~~~~~~~~~
- Trwsio camsillafu a camdreigliadau yn y dogfennaeth.

v1.0.0 (2018-06-20)
~~~~~~~~~~~~~~~~~~~
- Newid cystrawen profion ystadegol (yn torri ôl-gytunedd).
- Newid steiliau graffio.
- Ychwanegu ffwythiannau profion ystadegol pellach.
  - prawf Mann-Whitney
  - prawf Kruskal-Wallis
  - profion ANOVA
- Trwsio byg yn y ffwythiant 'modd'.
- Dileu ffwythiant 'siart_cylch'.

v0.1.2 (2018-04-04)
~~~~~~~~~~~~~~~~~~~
- Newidiadau mewnol i gwella cyflymder y cod.
- Newid a gwella dogfennaeth ffwythiannau graffio.

v0.1.1 (2018-03-18)
~~~~~~~~~~~~~~~~~~~
- Trwsio byg mewn ffwythiant graphio bar.

v0.1.0 (2018-02-20)
~~~~~~~~~~~~~~~~~~~
- Ychwanegu profion ystadegol.
  - prawf-t
  - prawf chi-sgwâr
  - prawf Wilcoxon
- Ychwanegu ffwythiannau graffio.

v0.0.3 (2018-02-09)
~~~~~~~~~~~~~~~~~~~
- Trwsio byg yn y ffwythiant 'modd'.
- Trwisio cma sillafu yn y dogfennaeth.

v0.0.2 (2018-01-06)
~~~~~~~~~~~~~~~~~~~
- Trwsio byg yn y ffwythiant 'cymder'.
- Trwsio byg yn y ffwythiant 'canolrif'.

v0.0.1 (2017-12-14)
~~~~~~~~~~~~~~~~~~~
- Rhyddhad cychwynnol.
{% endhighlight %}


# Cyfeiriadau

+ "Semantic Versioning: Why You Should Be Using it", Hugo Giraudel,
  
  [https://www.sitepoint.com/semantic-versioning-why-you-should-using/](https://www.sitepoint.com/semantic-versioning-why-you-should-using/)

+ "Keep a changelog", Olivier Lacan,
  
  [https://keepachangelog.com/en/1.0.0/](https://keepachangelog.com/en/1.0.0/)
