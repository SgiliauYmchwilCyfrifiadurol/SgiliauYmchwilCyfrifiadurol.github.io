---
layout: post
title: 8. Ymarferion Codio Da - Modiwlareiddio
permalink: 08-modiwlareiddio/
---

Yn union fel darllen rhyddiaith Cymraeg, mae un paragraff hir a dwys o god yn
anodd iawn i'w ddarllen.
Felly dylen ni osgoi blociau mawr o god, a lle'n bosib torri'r cod lawr i mewn i
darnau llai sy'n haws i'w ddarllen.

Mae mantais ychwanegol am hyn hefyd: gall unrhyw ddarn bach o god cael ei
ailddefnyddio.
Mae hwn yn golygu does dim angen ailysgrifennu unrhyw god a ddefnyddir mwy nag
unwaith, sy'n lleihau unrhyw siawns o gael gwallau neu gamgymeriadau.

Edrychwn ar ddwy ffordd o dorri lan cod: defnyddio ffwythiannau a defnyddio
modiwlau.
Mae rhai ieithoedd rhaglennu (gan gynnwys Python) yn galluogi ysgrifennu
dosbarthiadau a gwrthrychau.
Fe elwir hyn yn 'rhaglennu gwrthrych-gyfeiriadol' ("object-orientated
programming"), sy'n ffordd bellach o dorri lan cod, ond ni fyddwn yn edrych arni
yn y tiwtorial yma.


# Ffwythiannau

Yn Python rydym yn diffinio ffwythiant trwy ddefnyddio'r datganiad `def`.
Er enghraifft:

{% highlight python %}
>>> def f(x):
...     return (x + 3) ** 2

>>> f(1)
16
>>> f(4)
49
>>> f(-2)
1
{% endhighlight %}

Maent yn ddefnyddiol er mwyn osgoi ailadrodd cod, ac felly osgoi ailadrodd
camgymeriadau.
Ond unwaith ysgrifennwn y cod `(x + 3) ** 2`, ond fe'i defnyddiwyd tair
gwaith.
Mae pŵer ffwythiannau yn dod yn amlwg os yw'r ffwythiant yn un cymhleth a'i
defnyddiwyd nifer o weithiau.
Ar ben hyn, mae defnyddio ffwythiannau yn fwy darllenadwy, yn enwedig os
defnyddiwn enw ystyrlon ar eu cyfer.

Ystyriwch y cod isod.
Gweithrediad o algorithm i ganfod gwreiddiau polynomial yw hi.

{% highlight python linenos %}
uchaf = 0
isaf = 1
goddefiant = 0.0001
canol = (uchaf + isaf) / 2
poly_canol = 3 * (canol ** 2) - (5 * canol) + 1

while abs(poly_canol) > goddefiant:
	poly_isaf = 3 * (isaf ** 2) - (5 * isaf) + 1
	poly_canol = 3 * (canol ** 2) - (5 * canol) + 1
	arwydd_poly_canol = poly_canol < 0
	arwydd_poly_isaf = poly_isaf < 0
	if arwydd_poly_isaf == arwydd_poly_canol:
		isaf = canol
	else:
		uchaf = canol
	canol = (isaf + uchaf) / 2
	poly_canol = 3 * (canol ** 2) - (5 * canol) + 1

print(canol)
{% endhighlight %}

Un bloc mawr o god yw hon, gyda nifer fawr o linellau wedi'u hailadrodd.
Hyd yn oed gydag enwau newidynnau ystyrlon mae'n anodd iawn deall beth mae'r cod
yn ei wneud.

Sylwch:

+ Mae llinellau 4, 7, 8 ac 16 yn gwneud yr un peth, ond gyda mewnbwn gwahanol.
Bydd y cod yma yn berffaith ar gyfer ffwythiant;
+ Mae llinellau 9 a 10 yn gwneud yr un peth;
+ Mae llinellau 3 ac 15 yn gwneud yr un peth.

Dylai ffwythiannau **gwneud un peth, ac un peth yn dda**.
Mae enwi ffwythiannau yn helpu ni

Ail-ysgrifennwn y cod gan ysgrifennu ffwythiannau ar gyfer y cod sy'n ailadrodd:

{% highlight python linenos %}
def polynomial(x):
    """
    Y polynomial i canfod ei gwraidd
    """
    return 3 * (x ** 2) - (5 * x) + 1

def canolbwynt(uchaf, isaf):
    """
    Canfod canolbwynt rhwng y rhifau uchaf ac isaf
    """
    return (uchaf + isaf) / 2

def arwydd(rhif):
    """
    Canfod arwydd rhif: False os yw'n negatif, True os yw'n positif
    """
    return rhif < 0

def gwraidd(polynomial, isaf, uchaf, goddefiant):
    """
    Canfod gwaidd polynomial yn y cyfwng (isaf, uchaf) o fewn rhyw goddefiant
    """
    canol = canolbwynt(uchaf, isaf)
    while abs(polynomial(canol)) > goddefiant:
        if arwydd(polynomial(isaf)) == arwydd(polynomial(canol)):
            isaf = canol
        else:
            uchaf = canol
        canol = canolbwynt(uchaf, isaf)
    return canol

print(gwraidd(polynomial, 0, 1, 0.0001))
{% endhighlight %}

Mae'r cod yma yn haws i'w ddarllen, nad yw'n ailadrodd unrhyw god, a gellir ei
defnyddio ar gyfer unrhyw baramedrau (unrhyw bolynomial, cyfwng a goddefiant).
Y ffordd yma, mae'r cod yn ailgynhyrchiadwy oherwydd gall ymchwilwyr eraill:

1. Darllen a deall y cod;
2. Ailddefnyddio unrhyw ran o'r cod;
3. Defnyddio'r cod ar gyfer problemau gwahanol.


# Modiwlau

Modiwlau yw sgriptiau eraill rydym yn mewnfudo i mewn i'n cod er mwyn ei
ddefnyddio mewn cyd-destun arall.
Mae'r ffordd o drefnu cod felly nad yw unrhyw un sgript un anniben gan gynnwys
pob darn o god a fu'n rhedeg.
Yn aml bydd un modiwl yn cynnwys nifer o ffwythiannau mewn un thema, a fydd yn
defnyddiol mewn nifer o gyd-destunau.

Er enghraifft, gallwn ysgrifennu un sgript o'r enw `ystadegaeth.py` sy'n cynnwys
y ffwythiannau canlynol:

{% highlight python linenos %}
def cymder(rhestr):
	return sum(rhestr) / len(rhestr)

def canolrif(rhestr):
	trefn = sorted(rhestr)
	hyd = len(rhestr)
	if hyd % 2 == 1:
		return trefn[int(hyd / 2)]
	else:
		canolrifau = [trefn[int(hyd / 2)], trefn[int(hyd / 2) + 1]]
		return cymder(canolrifau)
{% endhighlight %}

Nawr os ydyn ni mewn Python (trwy ddefnyddio'r 'command line / command prompt'
neu yn ysgrifennu sgript arall) o fewn yr un ffolder a'r sgript
`ystadegaeth.py`, gallwn gael mynediad i'r ffwythiannau yma:

{% highlight python %}
>>> import ystadegaeth

>>> rhestr = [5, 7, 3, 2, 1]
>>> ystadegaeth.cymedr(rhestr)
3.6

>>> ystadegaeth.canolrif(rhestr)
3
{% endhighlight %}

Gall hwn tacluso ein cod a, trwy wneud yn siŵr pob enwau ystyrlon i bopeth,
cynyddu ei darllenadwyedd.
Fel arfer bydd codwyr yn gwneud defnydd helaeth o fodiwlau mae pobl eraill
wedi'u hysgrifennu, ac efallai byddwn ni fel ymchwilwyr yn ysgrifennu modiwlau y
bydd ymchwilwyr eraill yn eu defnyddio.
Yn y ffordd yma, yn ogystal â helpu ni darllen y cod a lleihau camgymeriadau,
mae modiwlaredd yn cyfrannu tuag at ailgynhyrchadwyedd ein gwaith.

# Cyfeiriadau

+ "Research software development", Vincent Knight,
  
  [https://vknight.org/rsd/](https://vknight.org/rsd/)

+ "Modular Programming and Modules",
  
  [https://www.python-course.eu/modules_and_modular_programming.php](https://www.python-course.eu/modules_and_modular_programming.php)