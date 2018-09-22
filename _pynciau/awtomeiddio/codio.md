---
layout: post
title: 9. Sgiliau Awtomeiddio - Codio
permalink: awtomeiddio/codio/
---

Ffordd gyffredin a ddefnyddiol o awtomeiddio tasgau cyfrifiadurol yw codio.
Fel rheol bydd rhan fwyaf o ddadansoddiad data, efelychiadau ac algorithmau yn
cael eu cyflawni yn y modd yma.

Ar gyfer y cwrs yma yr iaith rhaglennu a ddefnyddiwn yw Python.
Mae tri rheswm am hyn:
 
 1. Mae'n agored, felly'n rhad ac am ddim.
 2. Mae'n boblogaidd yn y gymuned gwyddoniaeth, gyda nifer o lyfrgelloedd
 defnyddiol (megis [`pandas`](https://pandas.pydata.org/) ar gyfer dadansoddiad
 data, [`sklearn`](http://scikit-learn.org/stable/) ar gyfer dysgu peiriannau,
 [`matplotlib`](https://matplotlib.org/) ar gyfer plotio,
 [`astropy`](http://www.astropy.org/) ar gyfer seryddiaeth).
 3. Cydnabyddir fel iaith ddarllenadwy sy'n ddelfrydol ar gyfer dysgu codio.

Mae nifer o opsiynau da eraill hefyd (e.e.
[Java](https://java.com/en/download/), [R](https://www.r-project.org/),
[C++](http://www.cplusplus.com/) a mwy).

Fan hyn rhoddir sylfeini cystrawen yr iaith.
**Nid** tiwtorial llawn yw hwn, ond rhoddir digon o wybodaeth i fedru cyflawni'r
cwrs sgiliau ymchwil ailgynhyrchiadwy yma.

---

## Gosod Python

Ar gyfer y tiwtorial yma argymhellir
[Anaconda](https://www.anaconda.com/download/)
([https://www.anaconda.com/download/](https://www.anaconda.com/download/)) fel y
modd o osod Python ar eich cyfrifiadur.
Dilynwch y cyfarwyddiadau ar y wefan honno er mwyn gallu dechrau defnyddio
Python.

---

## Defnyddio'r dehonglydd Python

Agorwch y 'Command Line' neu'r 'Command Prompt', a theipiwch:

{% highlight bash %}
python
{% endhighlight %}

Fe ddechreuir hwn promt a fydd yn edrych rhywbeth fel hyn:

{% highlight bash %}
Python 3.5.2 |Anaconda custom (64-bit)| (default, Jul  2 2016, 17:53:06) 
[GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
{% endhighlight %}

Mae'r `>>>` yn dynodi'r pwynt lle allwn deipio cod Python.

Teipiwch `2 + 2` a gwasgwch 'enter'.
Fe allwn weld beth ddylai hwn edrych fel isod:

{% highlight python %}
>>> 2 + 2
4
{% endhighlight %}

## Creu newidynnau rhifol

Fe allwn aseinio newidynnau gan ddefnyddio'r gweithredydd `=`:

{% highlight python %}
>>> ystyr_bywyd = 42
>>> ystyr_bywyd = ystyr_bywyd + 2
>>> ystyr_bywyd
44
{% endhighlight %}

---

## Creu newidynnau Boolean

Gallwn greu newidynnau Boolean trwy ddefnyddio nifer o weithredyddion cymharu,
gan gynnwys:

- `==` yn hafal i
- `!=` ddim yn hafal i
- `>` yn fwy na
- `>=` yn fwy na neu'n hafal i

{% highlight python %}
>>> yw_42 = ystyr_bywyd == 42
>>> yw_42
False
>>> mwy_na_42 = ystyr_bywyd > 42
>>> mwy_na_42
True
{% endhighlight %}

---

## Creu rhestrau

Mae gan Python strwythurau y gellir indecsio, rhestrau:

{% highlight python %}
>>> rhifau = [1, 2, 4, 5]
>>> max(rhifau)
5
>>> min(rhifau)
1
>>> sum(rhifau)
12
>>> rhifau[0]
1
>>> rhifau[-2]
4
>>> rhifau.append(50)
>>> rhifau
[1, 2, 4, 5, 50]
{% endhighlight %}

I cau'r dehonglwr teipwich:

{% highlight python %}
exit()
{% endhighlight %}

---

## Defnyddio sgriptiau Python

I ddechrau ysgrifennu cod mwy defnyddiol, gallwn ysgrifennu'r cod o fewn ffeil,
ac yna gallwn redeg y cod trwy ddefnyddio'r 'Command Line' neu'r 'Command
Prompt'.


### Ysgrifennu sgript Python

Agorwch olygydd testun (*text editor*, mae rhestr o olygyddion testun
argymhellir ar ddiwedd y tiwtorial yma), a chrëwch ffeil newydd o'r enw
'01-helo-byd.py'.
O fewn y ffeil ysgrifennwch y cod canlynol:

{% highlight python %}
print("helo byd")
{% endhighlight %}

Sylwch nid ydym yn ysgrifennu `>>>`.

### Rhedeg sgript Python

Gan ddefnyddio'r 'Command Line' neu'r 'Command Prompt', gallwn ddweud wrth y
cyfrifiadur i gyflawni'r cyfarwyddiadau sydd yn y sgript.
Fe elwir hwn yn "rhedeg" y sgript.
I wneud hwn, ysgrifennwch y canlynol i mewn i'r 'Command Line' neu'r 'Command
Prompt':

{% highlight bash %}
python 01-helo-byd.py
{% endhighlight %}

Nid yw hwn yn unigryw i Python, gallwn redeg rhan fwyaf o ieithoedd rhaglennu
yn y modd yma: trwy arbed ffeil a'i rhedeg gyda'r gorchymyn cywir.
Mae hwn yn rhoi hyblygrwydd i ni ddewis unrhyw olygydd testun rydym yn
gyfforddus yn ei ddefnyddio.

---

## Datganiadau-If

Gallwn ddefnyddio newidynnau Boolean i greu datganiadau rhesymegol.

Ysgrifennwch ffeil o'r enw `02-datganiadau-if.py`, sy'n cynnwys y cod canlynol,
a rhedwch y ffeil.

{% highlight python %}
N = 572
if N % 2 == 0:
    print("Mae N yn eilrif")
else:
    print("Mae N yn odrif")
{% endhighlight %}

**Noder** Mae gwagle gwyn a chilisodiadau yn bwysig mewn Python.
Mae bloc cod a chilosodwyd yn dynodi pa god i redeg *os* yw'r newidyn Boolean
`N % 2 == 0` yn `True`.

## Lwpiau-'While'

Mae'n bosib ailadrodd cod trwy ddefnyddio lwpiau-`while`, a fydd yn gwirio
newidyn Boolean tro ar ôl tro.

Ysgrifennwch ffeil o'r enw `03-lwpiau-while.py` sy'n cynnwys y cod canlynol:

{% highlight python %}
N = 0
nifer_o_eilrifau = 0
while N < 10:
    if N % 2 == 0:
        nifer_o_eilrifau = nifer_o_eilrifau + 1
    N = N + 1
print(nifer_o_eilrifau)
{% endhighlight %}

Rhedwch y ffeil yma.

---

## Ffwythiannau

Mae'n bosib creu ffwythiannau mewn Python.
Darnau o god yw'r rhain sydd ond yn rhedeg pan ddefnyddir y ffwythiant; ac fe
allwn defnyddio’r ffwythiant po gymaint o weithiau a dymunwn.
Gall ffwythiant cymryd paramedrau hefyd.

Ysgrifennwch ffeil o'r enw `04-ffwythiannau.py` sy'n cynnwys y cod canlynol, a
rhedwch y ffeil.

{% highlight python %}
def cyfri_eilrifau(terfan_uchaf):
    N = 0
    nifer_o_eilrifau = 0
    while N < terfan_uchaf:
        if N % 2 == 0:
            nifer_o_eilrifau = nifer_o_eilrifau + 1
        N = N + 1
    return nifer_o_eilrifau

print(cyfri_eilrifau(10))
print(cyfri_eilrifau(42))
{% endhighlight %}

Nodwch fod cod y ffwythiant `cyfri_eilrifau` ond yn rhedeg pan ddefnyddir y
ffwythiant yn y ddwy llinell olaf (cyfri'r eilrifau o dan 10, a chyfri'r
eilrifau o dan 42).

---

# Golygyddion testun

+ Notepad++ ([https://notepad-plus-plus.org/](https://notepad-plus-plus.org/))
+ Nano ([https://www.nano-editor.org](https://www.nano-editor.org))
+ Vim ([www.vim.org](www.vim.org))
+ Sublime ([www.sublimetext.com](www.sublimetext.com))
+ Atom ([https://atom.io](https://atom.io))
+ VS Code ([code.visualstudio.com](code.visualstudio.com))
+ CLion ([www.jetbrains.com/clion/](www.jetbrains.com/clion/))
+ PyCharm ([www.jetbrains.com/pycharm/](www.jetbrains.com/pycharm/))

---

# Cyfeiriadau

+ "Research software development", Vincent Knight,
  
  [https://vknight.org/rsd/](https://vknight.org/rsd/)
