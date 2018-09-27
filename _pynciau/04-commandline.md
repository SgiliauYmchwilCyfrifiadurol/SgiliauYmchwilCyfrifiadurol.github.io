---
layout: post
title: 4. Sgiliau Awtomeiddio - Y 'Command Line' yn -nix
permalink: 04-commandline/
---

<table align='center'>
<tr>
    <td><a href="/03-sgiliau-awtomeiddio/">&#x23EA; Blaenorol</a></td>
    <td><a href="/05-commandprompt/">Nesaf &#x23E9;</a></td>
</tr>
</table>
<br>

Mae systemau -nix (Unix, Mac, a Linux) yn defnyddio'r 'command line' i siarad
i'r cyfrifiadur.
I fedru gwneud hwn, agorwn y **terminal**.
Dyle fe edrych rhywbeth fel hyn (bydd lliwiau ac efallai ysgrifen wahanol gyda
chi):

![]({{site.baseurl}}/delweddau/terminal.png)

Ar y llinell lle welwn y cyrchwr (cursor), gwelwn ni rhyw ysgrifen (fel arfer
enw ein cyfrifiadur a lle ar y cyfrifiadur ydyn ni ar hyn o bryd), a'r diweddglo
`$`.
Dyma le allwn ni teipio gorchmynion i'r cyfrifiadur.
(Yn y tiwtorial yma, mae unrhyw god sy'n dilyn y symbol `$` yn cynrychioli cod
rydym ni'n ysgrifennu a theipio. Mae unrhyw tecst nad yw'n dilyn `$` yn
cynrychioli allbwn y cyfrifiadur.)

Y fath o orchmynion edrychwn arnynt yn y tiwtorial yma yw triniaeth ffolderi a
ffeiliau.
Hynny yw, awtomeiddio'r pethau byddwch yn gwneud gyda GUI yn 'Finder' neu 'File
Browser'; creu ffolderi newydd, copïo ffeiliau, ail-enwi a symud ffeiliau, ac yn
y blaen.

I redeg gorchymyn:

  + Teipwich y gorchymyn
  + Gwasgwch 'Enter'

Nodwch yn y tiwtorial yma defnyddiwn y geiriau 'cyfeiriadur' (directory) a
'ffolder' i olygu'r un peth.
Mewn gwirionedd cyfeiriaduron yw popeth, ond weithiau mae'r cysyniad o 'ffolder'
yn gweithio'n well er mwyn cynyddu dealltwriaeth.

---

### 1. Ble ydyn ni?

Yn gyntaf gallwn wirio lle ar y cyfrifiadur ydyn ni ar hyn o bryd gan
ddefnyddio `pwd`, sy'n sefyll am "present working directory":

{% highlight bash %}
$ pwd
/Users/geraintianpalmer
{% endhighlight %}

Os welwn enw defnyddiwr, mae hwn yn golygu ein bod ni mewn ein cyfeiriadur
cartref (home directory).

---

### 2. Beth sydd yna?

I weld pa ffeiliau a ffolderi sydd yn y cyfeiriadur yna, defnyddiwn y gorchymyn
`ls`, sy'n sefyll am "list".
Bydd hwn yn allbynnu rhestr o'r holl bethau sydd o fewn y cyfeiriadur presennol.

{% highlight bash %}
$ ls
Applications
Desktop
Documents
Downloads
Library
Movies
Music
Pictures
Public
{% endhighlight %}

Mae'r esiampl uchod yn dangos beth sydd ar fy nghyfrifiadur i, efallai bydd eich
cyfrifiadur chi yn edrych yn wahanol.
Fe allwn agor GUI ('Finder' neu 'File Browser') a chymharu bod y rhestr yma yn
cyfateb a beth ddangosir yna.

---

### 3. Creu ffolder

I greu ffolder neu gyfeiriadur tu fewn ein cyfeiriadur presennol, defnyddiwn y
gorchymyn `mkdir` ("make directory") wedi'i dilyn gan enw'r ffolder newydd
hoffwn greu.
Er enghraifft, hoffwn greu ffolder o'r enw `dysgu-gorchmynion`:

{% highlight bash %}
$ mkdir dysgu-gorchmynion
{% endhighlight %}

Nawr pan restrwn ni'r pethau sydd o fewn ein cyfeiriadur presennol, gwelwn y
ffolder newydd:

{% highlight bash %}
$ ls
Applications
Desktop
Documents
Downloads
dysgu-gorchmynion
Library
Movies
Music
Pictures
Public
{% endhighlight %}

Hefyd gallwn wirio bod y ffolder wedi'i chreu trwy ddefnyddio'r GUI.

Nodwch, wrth greu ffeiliau a ffolderi gan ddefnyddio'r 'command line', nid
ydym fel arfer yn rhoi bylchau yn eu henwau, gan fod bylchau yn dynodi bod
gorchymyn neu enw wedi gorffen.
*(Os oes rhaid defnyddio bylchau, gallwn ddweud wrth y cyfrifiadur eu hanwybyddu
trwy ddefnyddio ôl-slaes cyn y blwch, er enghraifft `mkdir dysgu\ gorchmynion`.
Bydd rhaid defnyddio'r ôl-slaes yma pob tro rydym eisiau defnyddio'r ffeil neu
ffolder yna. Ni argymhellir hwn.)*

---

### 4. Symud i leoliad arall

I symud o'r cyfeiriadur presennol i gyfeiriadur arall, gallwn ddefnyddio'r
gorchymyn `cd` ("change directory") wedi dilyn gan y lleoliad newydd.
Y symud i mewn i'r ffolder `dysgu-gorchmynion`:

{% highlight bash %}
$ cd dysgu-gorchmynion
{% endhighlight %}

Ac i wirio:

{% highlight bash %}
$ pwd
/Users/geraintianpalmer/dysgu-gorchmynion
{% endhighlight %}

Mae hwn yn gweithio oherwydd bod y ffolder `dysgu-gorchmynion` o fewn y lleoliad
presennol.
Os ydyn ni eisiau mynd nôl lan i'r cyfeiriadur cartref, gallwn fynd 'i fyny' i
gyfeiriadur rhiant y lleoliad presennol trwy ddefnyddio dau ddot:

{% highlight bash %}
$ cd ..
$ pwd
/Users/geraintianpalmer
{% endhighlight %}

I dangos symudiadau pellach, crëwn dau ffolder arall.
Crëwn `dysgu-symudiadau` yn y cyfeiriadur cartref, a chrëwn `lluniau` o fewn y
ffolder `dysgu-gorchmynion`.
Ceisiwch ddeall a dilyn y gorchmynion isod ar gyfer gwneud hyn:

{% highlight bash %}
$ mkdir dysgu-symudiadau
$ cd dysgu-gorchmynion
$ mkdir lluniau
{% endhighlight %}

Nawr rydym ni o fewn y ffolder `dysgu-gorchmynion` ac rydym ni eisiau symud i'r
ffolder `dysgu-symudiadau`.
Mae'r gorchymyn isod yn galluogi ni i wneud hwn:

{% highlight bash %}
$ cd ../dysgu-symudiadau
{% endhighlight %}

Yn gyntaf mae'r `..` yn dweud mynd i fyny i'r cyfeiriadur rhiant, yn unwaith
rydym ni yna rydym yn symud i mewn i'r ffolder `dysgu-symudiadau`.

Yn yr un modd os ydyn ni eisiau mynd i'r ffolder `lluniau` o fan hyn:

{% highlight bash %}
$ cd ../dysgu-gorchmynion/lluniau
{% endhighlight %}

---

### 5. Trin ffeiliau

**RHYBUDD: Wrth ddefnyddio'r 'command line' ni fydd rhybudd na chadarnhad yn
ymddangos os byddwch yn dileu neu drosysgrifennu unrhyw ffeil! Byddwch yn
ofalus!**

Er mwyn barhau gyda'r tiwtorial yma, bydd angen rhoi rhyw lun (.jpeg neu tebyg)
yn y ffolder 'lluniau' a chrëwn yn gynharach.
Fe allwch lawrlwytho rhyw lun o'r we, a'i arbed yn y ffolder yma trwy
defnyddio'r GUI.
I sicrhau eich bod wedi gwneud yn iawn, dylech weld y ffeil wrth ddefnyddio'r
gorchymyn `ls`:

{% highlight bash %}
$ pwd
/Users/geraintianpalmer/dysgu-gorchmynion/lluniau

$ ls
crwban.jpeg
{% endhighlight %}

---

### 5a. Copïo ffeil

I gopïo ffeil, defnyddiwn y gorchymyn `cp` ("copy").
Mae dwy ddadl yn dilyn y gorchymyn yma:
`cp <enw_ffeil_i_gopio> <enw_neu_leoliad_y_copi>`.
I greu copi o'r ffeil `crwban.jpeg`, a galw'r copi yn `anifail.jpeg`, rhedwch y
gorchymyn yma:

{% highlight bash %}
$ cp crwban.jpeg anifail.jpeg
{% endhighlight %}

Ac i wirio fod y copi wedi'i chreu:

{% highlight bash %}
$ ls
anifail.jpeg
crwban.jpeg
{% endhighlight %}

I greu copi a'i rhoi mewn lleoliad gwahanol, gallwn ddefnyddio'r ail ddadl i
ddweud lle i roi'r copi.
I greu copi o `crwban.jpeg` a'i rhoi yn y cyfeiriadur rhiant, defnyddiwn:

{% highlight bash %}
$ cp crwban.jpeg ../
{% endhighlight %}

Ac i wirio fod y copi wedi'i chreu:

{% highlight bash %}
$ ls ../
crwban.jpeg
lluniau
{% endhighlight %}

---

### 5b. Symud ffeil

Yn union fel copïo ffeil, gallwn symud ffeil trwy ddefnyddio'r gorchymyn `mv`
("move").
Symudwn y ffeil `anifail.jpeg` i'r cyfeiriadur rhiant:


{% highlight bash %}
$ mv anifail.jpeg ../
{% endhighlight %}

A gwirio ei fod yna:

{% highlight bash %}
$ cd ..
$ ls
anifail.jpeg
crwban.jpeg
lluniau
{% endhighlight %}

A'i symud yn ôl:

{% highlight bash %}
$ mv anifail.jpeg lluniau
{% endhighlight %}

A gwirio:

{% highlight bash %}
$ ls
crwban.jpeg
lluniau

$ cd lluniau
$ ls
anifail.jpeg
crwban.jpeg
{% endhighlight %}

Nodwch fod symud ac ailenwi ffeil yr un peth!
Os hoffwn ailenwi `anifail.jpeg` i `crwban2.jpeg`:

{% highlight bash %}
$ mv anifail.jpeg crwban2.jpeg
{% endhighlight %}

---

### 5c. Dileu ffeil

I ddileu ffeil defnyddiwn y gorchymyn `rm` ("remove") wedi dilyn gan enw'r ffeil
i'w ddileu.
Mae hyn yn cael gwared ar y ffeil *am byth*.
**Nid yw'r ffeil yn mynd i mewn i'r bin ailgylchu!**

I ddileu'r ffeil `crwban.jpeg`:

{% highlight bash %}
$ rm crwban.jpeg
{% endhighlight %}

A gwirio:

{% highlight bash %}
$ ls
crwban2.jpeg
{% endhighlight %}

---

### 5ch. Copïo a dileu ffolderi

Nid yw'r gorchmynion uchod yn gweithio ar ffolderi neu gyfeiriaduron.

I gopïo neu ddileu ffolder rhaid ychwanegu'r opsiwn `-r` i'r gorchymyn.
Llywiwch i'r ffolder `dysgu-gorchmynion`:

{% highlight bash %}
$ cd ..

$ pwd
/Users/geraintianpalmer/dysgu-gorchmynion
{% endhighlight %}

I greu copi o'r ffolder `lluniau` a'i alw yn `lluniau2`:

{% highlight bash %}
$ cp -r lluniau lluniau2

$ ls
crwban.jpeg
lluniau
lluniau2
{% endhighlight %}

I ddileu'r ffolder `lluniau`:

{% highlight bash %}
$ rm -r lluniau

$ ls
crwban.jpeg
lluniau2
{% endhighlight %}

---

## Crynodeb ac awgrymiadau

Yn y tiwtorial yma rydyn ni wedi gweld sut i agor y 'command line' yn systemau
-nix.
Gwelwn orchmynion ar gyfer:

+ Gweld eich cyfeiriadur presennol (`pwd`)
+ Rhestri beth sydd tu fewn i gyfeiriadur (`ls`)
+ Creu ffolder (`mkdir`)
+ Symud o un lleoliad i leoliad arall (`cd`)
+ Copïo ffeil (`cp`)
+ Symud neu ailenwi ffeil (`mv`)
+ Dileu ffeil (`rm`)
+ Copïo ffolder (`cp -r`)
+ Dileu ffolder (`rm -r`)


Y olaf dyma gwpl o awgrymiadau gall cyflymu defnyddio’r gorchmynion yma:

+ Mae rhan fwyaf o offerynnau 'command line' yn cefnogi cwblhau tab. Mae hwn yn
golygu gallwn ddechrau teipio cwpl o lythrennau cyntaf enw ffeil neu ffolder,
yna gwasgu tab a fydd yn cwblhau gweddill yr enw.
+ Hefyd gallwn ddefnyddio'r botwm saeth i fyny a saeth i lawr i seiclo trwy
unrhyw gorchmynion a defnyddiwyd yn ddiweddar.

---

# Cyfeiriadau

+ "Research software development", Vincent Knight,
  
  [https://vknight.org/rsd/](https://vknight.org/rsd/)

<table align='center'>
<tr>
    <td><a href="/03-sgiliau-awtomeiddio/">&#x23EA; Blaenorol</a></td>
    <td><a href="/05-commandprompt/">Nesaf &#x23E9;</a></td>
</tr>
</table>
