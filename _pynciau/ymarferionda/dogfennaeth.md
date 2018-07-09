---
layout: post
title: Dogfennaeth
permalink: ymarferionda/dogfennaeth/
---

Dogfennaeth mewn cod yw agweddau o'r cod sydd yn bodoli i helpu person medru
darllen a deall y cod yn well.
Oherwydd bod cod yn ffordd fanwl iawn (union) o gyfathrebu methodoleg, mae'n
pwysig iawn bod y cod, yn ogystal â rhedeg y fethodoleg, yn gwneud y swydd o'i
chyfathrebu.
Mae hwn yn golygu bod angen i god bod yn ddarllenadwy ac yn ddealladwy.
Mae hwn yn cefnogi unrhyw ymchwilwyr eraill sy'n dod at y cod i ddilyn beth sy'n
mynd ymlaen, sy'n hanfodol ar gyfer deall, ail-redeg ac ailgynhyrchu'r
methodoleg.

Edrychwn ar dair agwedd o ddogfennaeth o fewn cod: sylwadau, 'docstrings', ac
enwau newidynnau a ffwythiannau.

# 1. Sylwadau

Sylwadau ("comments") yw cymeriadau a darnau o tecst o fewn cod, nad yw'n cael
eu rhedeg.
Eu pwrpas yw egluro darnau o god efallai nad yw'n ddarllenadwy ar ben eu hun.

Yn Python mae unrhyw ysgrifen sy'n dod ar ôl y symbol `#` yn sylw, a ni ffydd y
cod yn rhedeg.
Mae sylw yn gorffen pan ddechreuir llinell newydd.

Edrychwch ar yr enghraifft isod o god heb sylwadau, sy'n symio'r holl gyfanrifau
hyd at ugain:

{% highlight python %}
>>> cyfanswm = 0
>>> for rhif in range(20):
...     cyfanswm += rhif
>>> print(cyfanswm)
{% endhighlight %}

Gallwn ychwanegu sylwadau esboniadwy i bob llinell o'r cod yma er mwyn ei wneud
yn fwy darllenadwy:

{% highlight python %}
>>> cyfanswm = 0  # i dechrau y cyfanswm yw sero
>>> for rhif in range(20):  # lwpio trwy pob cyfanrif hyd at ugain
...     cyfanswm += rhif  # ychwanegu'r cyfanrif i'r cyfanswm
>>> print(cyfanswm)  # printio'r cyfanswm
{% endhighlight %}

Nid yw swyddogaeth y cod wedi newid, a rhedwyd union yr un llinellau o god.
Ond, yn hollbwysig, mae'r cod yn haws i'w ddeall.

Sylwch mewn nifer o lefydd does dim agen sylw, gan fod y cod digon darllenadwy
fel y mae.
Does dim angen ailadrodd pethau gyda sylwadau:

{% highlight python %}
>>> cyfanswm = 0  # i ddechrau y cyfanswm yw sero
>>> for rhif in range(20):
...     cyfanswm += rhif  # ychwanegu'r cyfanrif i'r cyfanswm
>>> print(cyfanswm)
{% endhighlight %}

Mewn gwirionedd gall *gormod* o sylwadau fod yn broblemus.
Mae sylwadau ond yn ddefnyddiol os ydynt yn gywir, ac yn gwneud y gyferbyn, yn
rhwystro dealltwriaeth, os ydynt yn anghywir.
Natur rhaglennu yw bydd y cod yn newid.
Po fwyaf nifer y sylwadau, po fwyaf tebygol y bydd y cod yn newid heb y sylw.
Felly mae'n gwell i ond defnyddio sylwadau ar gyfer darnau o god sydd
wirioneddol angen mwy o esboniad neu eglurhad.



# 2. 'Docstrings'

Sylwadau penodol yw 'docstrings', sydd â phwrpas bach yn wahanol i sylwadau
arferol.
Y gwahaniaeth yw pwy ydy'r gynulleidfa:

+ Darllenir sylwadau gan godwyr eraill sydd eisiau deall sut mae'r cod yn
gweithio.
+ Darllenir 'docstrings' gan ddefnyddwyr y cod, sydd eisiau gwybod sut i
ddefnyddio'r cod.

N.B. Efallai taw 'defnyddwyr y cod' yw codwyr eraill, neu hyd yn oed eich hun yn
ail-ddefnyddio rhannau o'r cod nes ymlaen.

Ysgrifennir 'docstring' ar gyfer pob ffwythiant.
Ei phwrpas yw esbonio beth mae'r ffwythiant yn gwneud, beth sydd angen rhoi fel
mewnbwn i'r ffwythiant, a beth rydym yn disgwyl fel allbwn.
Mewn Python dynodir `docstrings` o fewn tri phâr o ddyfynodau `"""`.

Ystyriwch y ffwythiant canlynol sy'n cyfrifo swm yr $$n$$ cyfanrif cyntaf;
ysgrifennir y 'docstring' fel llinell gyntaf y ffwythiant:

{% highlight python %}
def f(n):
    """
    Swm yr n rhif cyntaf

    Dadleuon mewnbwn:
    n -- cyfanrif
    """
    cyfanswm = 0
    for rhif in range(n + 1):
        cyfanswm += rhif
    return cyfanswm
{% endhighlight %}

Mae'r 'docstring' yn dweud yn union beth mae'r ffwythiant yn gwneud, ac yn
cyfathrebu yn union beth yw mewnbwn y ffwythiant.

Nawr wrth ddefnyddio'r ffwythiant gallwn ddarllen y darn o ddogfennaeth yma trwy
defnyddio `f.__doc__`:

{% highlight python %}
>>> f(100)
5050

>>> f.__doc__
'\n    Swm yr n rhif cyntaf\n    \n    Dadleuon mewnbwn:\n    n -- cyfanrif\n    '
{% endhighlight %}

Neu yn well:

{% highlight python %}
>>> help(f)
{% endhighlight %}



# 3. Enwau newidynnau a ffwythiannau

Mae rhan sylweddol o'r cod rydyn ni'n ysgrifennu yn safonol iawn, mae fel arfer
ond un ffordd o ysgrifennu datganiad-'if' er enghraifft.
Fodd bynnag mae rhan o'r cod gallwn siapio ein hun, a gallwn fod yn greadigol i
ceisio gwneud y cod mor ddarllenadwy a dealladwy ac sy'n bosib.
Y rhannau o'r cod sydd gyda ni'r rhyddid i wneud hyn yw trwy enwi newidynnau a
ffwythiannau.

Mae'n gyffredin iawn i enwi newidynnau a ffwythiannau mewn cod fel yn
mathemateg, mor gryno ac mor amwys ac sy'n bosib!
Does dim rheswm i wneud hyn wrth raglennu.
Trwy ddewis enwau hir ac ystyrlon, gall ein cod darllen mwy fel brawddegau na
fel mathemateg amwys.

Ystyriwch y ffwythiant isod:

{% highlight python %}
def g(N):
    A = []
    for i in range(1, N + 1):
        if (N % i == 0):
            A.append(i)
    return A
{% endhighlight %}

Cyn symud ymlaen gyda'r tiwtorial, cymerwch amser i geisio gweithio allan beth
sy'n mynd ymlaen yn y ffwythiant yma:

+ Beth yw pwrpas y ffwythiant `g`?
+ Beth y `N`, `A` ac `i`?

Allan o'r holl god (heblaw am strwythur y cod a gweithrediad yr algorithm), dim
ond enwau'r pedwar peth yma mae gennym unrhyw reolaeth a dewis amdanynt.

Isod mae'r union un cod, ond gydag enwau ystyrlon.
Yw'r cod yn fwy darllenadwy nawr?

{% highlight python %}
def canfod_ffactorau(rhif):
    ffactorau = []
    for ffactor_potensial in range(1, rhif + 1):
        if (rhif % ffactor_potensial == 0):
            ffactorau.append(i)
    return ffactorau
{% endhighlight %}

Nawr gwelwn fod y cod yn canfod ffactorau rhyw rif, trwy lwpio trwy holl
ffactorau potensial ac ychwanegu'r ffactorau go iawn i mewn i restr o ffactorau.
Mae dewis enwau newidynnau a ffwythiannau sy'n ystyrlon yn gallu trawsnewid cod
amwys i mewn i ddogfen ddealladwy.


# Cyfeiriadau

+ "Research software development", Vincent Knight,

  [https://vknight.org/rsd/](https://vknight.org/rsd/)