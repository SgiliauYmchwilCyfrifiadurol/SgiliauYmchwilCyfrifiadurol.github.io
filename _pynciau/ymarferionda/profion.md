---
layout: post
title: 12. Ymarferion Codio Da - Profion Awtomatig
permalink: ymarferionda/profion/
---

Mae profion awtomatig yn sicrhau bod y cod rydym wedi ysgrifennu yn gweithio fel
rydym yn ei ddisgwyl, i wirio cywirdeb ein methodoleg.
Dychmyga nhw fel 'arholiad' ar gyfer y cod, lle rydym yn gwirio 'atebion' y cod
i broblemau yn erbyn yr atebion go iawn.

Mae gan brofion pwrpas ychwanegol hefyd.
Maent yn *hysbysebu i ymchwiliwr eraill* bod ein cod yn gweithio *fel rydym yn
ei ddisgwyl*.
Felly mae hyder ymchwilwyr eraill yn ein gwaith a'n methodoleg yn cynyddu, sy'n
eu galluogi ac yn eu hybu i ailgynhyrchu'r gwaith.
Hefyd mae'r fformat 'cwestiwn ac ateb arholiad' yn dogfennu beth yw pwrpas y
cod, mwy felly na'r cod ei hun.
Hyd yn oed os yw'r ateb yn anghywir (hynny yw beth mae'r cod yn gwneud) bydd y
cwestiwn yn datgelu beth oedd y bwriad.

Mae profion fel arfer ar ffurf sgript, sy'n mewnbynnu'r holl god sydd angen ei
profi.
Mae'r sgript yma yn cynnwys nifer fawr o gwestiynau i ofyn y cod, yr ateb
disgwyliedig, a'r ateb y mae'r cod yn ei rhoi.
Yna mae cymhariaeth rhwng yr ateb a rhoddir a'r ateb disgwyliedig.
Codir gwall (error) os nad ydynt yn unfath, a digwyddir dim os yw'r cod yn
gweithio’n iawn.

Yn y tiwtorial yma dangoswn sut i ddefnyddio datganiadau 'if' i wneud y
cymhariaeth yma, a hefyd datganiadau 'assert'.
Hefyd trafodir sut i brofi hapddigwyddiadau, mathau o brofion awtomatig, y
ffordd o godio a elwir 'datblygiad wedi'i yrru gan brawf' ("test driven
development", "TTD").

Cymerwch y modiwl canlynol `enghreifftiau.py` sy'n cynnwys tri ffwythiant (nodir
defnyddir un ohonynt hapddigwyddiadau gan ddefnyddio'r llyfrgell `random`;
trafodir hyn nes ymlaen).
Dyma'r ffwythiannau byddwn yn profi yn y tiwtorial yma:

{% highlight python linenos %}
import random

def cymedr(rhestr):
	"""Cymedr rhestr o rhifau"""
	return sum(rhestr) / len(rhestr)

def amrywiant(rhestr):
	"""Amrywiant rhestr o rhifau"""
	gweddillion = []
	for rhif in rhestr:
		gweddill_sgwar = (rhif - cymedr(rhestr)) ** 2
		gweddillion.append(gweddill_sgwar)
	return sum(gweddillion) / len(rhestr)

def haprhestr(n):
	"""Creu rhestr o n haprif"""
	rhestr = []
	for rhif in range(n):
		haprif = round(random.random(), 3)
		rhestr.append(haprif)
	return rhestr
{% endhighlight %}


# Datganiadau 'if' ac 'assert'

Y ffordd symlaf o brofi ffwythiant yw defnyddio datganiad 'if'.
Is yw'r ateb a rhoddir yn wahanol i'r ateb a disgwylir, yna printiwch rybudd.
Ystyriwch y sgript profion `profion_enghreifftiau.py`:

{% highlight python linenos %}
import enghreifftiau

if enghreifftiau.cymedr([1, 1, 1, 1]) != 1:
	print('Gwall: enghreifftiau.cymedr([1, 1, 1, 1]) != 1')

if enghreifftiau.amrywiant([1, 1, 1, 1]) != 0:
	print('Gwall: enghreifftiau.amrywiant([1, 1, 1, 1]) != 0')
{% endhighlight %}

Wrth gwrs nid yw'r rhain yn unig yn ddigon i brofi'r ffwythiannau.
Mae'r bosib ysgrifennu rhyw ffwythiant distadl a elwir yn `cymedr` sy'n rhoi'r
ateb cywir ar gyfer yr enghraifft hon.
Felly dylai'r sgript yma cynnwys nifer fawr o wahanol enghreifftiau.
Ceisiwn ddewis ystod eang o enghreifftiau, er mwyn dal pob un achos arbennig,
neu achosion a all fod yn broblem.

Fel arall, gallwn ddefnyddio'r datganiad `assert`.
Nodwch bydd gan bob iaith rhaglennu rhyw ddatganiad gyda'r un swyddogaeth.
Fel y datganiadau 'if' uchod, mae datganiad 'assert' yn gwneud dim os yw'r
datganiad ar ei ôl yn wir, ac yn codi gwall os yw'r datganiad er ei ôl yn anwir:

{% highlight python linenos %}
import enghreifftiau

assert enghreifftiau.cymedr([1, 2, 2, 3]) == 2
assert enghreifftiau.amrywiant([1, 2, 2, 3]) == 0.5
{% endhighlight %}

Mae'n bwysig cyhoeddi'r sgript profion ar y cyd gyda'r sgript cod ei hun,
oherwydd dyma'r ffordd o hysbysebu a phrofi i ymchwilwyr a defnyddwyr eraill bod
y cod yn gweithio, ac ar ba sail gallwch ddweud hynny (pa enghreifftiau y
profwyd).
Mae hwn yn cadw'r broses ymchwil yn dryloyw.


# Profi hapddigwyddiadau

Mewn nifer o feysydd efallai bydd angen codio hapddigwyddiadau ("random
events"), er enghraifft mewn dulliau efelychu, dulliau hewristig, dulliau
samplu, neu ddulliau dysgu peiriannau.

Gall profi hapddigwyddiadau bod yn her, gan nad oes ateb disgwyliedig pendant.
Mae ffyrdd i brofi'r cod:

+ **Gosod hedyn:** Nid yw haprifau ar gyfrifiaduron yn haprifau go iawn.
Maent yn dod o lif o ffug-haprifau, lle mae'r rhif nesaf yn y llif yn hollol
penderfynol ar y rhif cynt. Gallwn ail-ddechrau'r llif yma gyda rhyw rif
pendant, haden, felly bydd pob 'hapddigwyddiad' o'r pwynt yna ymlaen yn hollol
rhagweladwy.
+ **Profi priodweddau:** Yn hytrach na phrofi'r union hapddigwyddiadau, gallwn
profi bod gan yr hapddigwyddiad priodweddau disgwyliedig.

Yn Python, y modiwl `random` sy'n rheoli’r haprifau yma:

{% highlight python linenos %}
>>> import enghreifftiau
>>> import random

>>> random.seed(0)
>>> enghreifftiau.haprhestr(4)
[0.844, 0.758, 0.421, 0.259]

>>> random.seed(0)
>>> enghreifftiau.haprhestr(4)
[0.844, 0.758, 0.421, 0.259]

>>> random.seed(1)
>>> enghreifftiau.haprhestr(3)
[0.134, 0.847, 0.764]
{% endhighlight %}

Nawr mae gennym ni'r atebion disgwyliedig ar gyfer cymharu:

{% highlight python linenos %}
import enghreifftiau
import random

random.seed(0)
assert enghreifftiau.haprhestr(4) == [0.844, 0.758, 0.421, 0.259]

random.seed(1)
assert enghreifftiau.haprhestr(3) == [0.134, 0.847, 0.764]
{% endhighlight %}

Wrth gwrs mae gennym ddadl gylchol fan hyn, ond maent dal yn ddefnyddiol i
sicrhau bod allbynnau ddim yn newid wrth newid y cod.
Ond rhaid hefyd profi rhai priodweddau'r allbynnau (fan hyn profwn fod hyd y
rhestr fel y disgwylir):

{% highlight python linenos %}
import enghreifftiau

assert len(enghreifftiau.haprhestr(3)) == 3
assert len(enghreifftiau.haprhestr(4)) == 4
assert len(enghreifftiau.haprhestr(5)) == 5
{% endhighlight %}


# Mathau o brofion

Mae yna nifer o fathau o brofion awtomatig gallwn gyflogi i brofi’n cod.
Mae set o brofion da yn cynnwys pob math:

<ul>
  <li><b>Profion uned:</b> ("Unit tests") Mae'r rhain yn profi un darn bach o'r
  	cod. Fel arfer un ffwythiant yn unig. Nid yw'r darn o god a phrofir yn
  	dibynnu ar unrhyw god arall i'w rhedeg. Felly os yw un prawf uned yn methu,
  	rydym yn gwybod yn union le mae'r gwall.</li>
  <li><b>Profion cyfannu:</b> ("Integration tests") Mae'r rhain yn profi darnau
  	bach mwy o god. Eu pwrpas yw gwirio fod y ffwythiannau ar wahân (a phrofir
  	gan brofion uned) yn gweithio gyda'i gilydd.</li>
  <li><b>Profion bocs du:</b> ("Black box tests / End-to-end tests") Mae'r rhain
  	yn gwirio bod yr holl god yn gweithio gyda'i gilydd. Hynny yw er enghraifft
  	profi un algorithm llawn, neu un wefan llawn. Maent yn gwirio bod yr allbwn
  	terfynol yn cyd-fynd gyda'r mewnbynnau dechreuol.</li>
  <li><b>Profion priodweddau:</b> ("Property based tests") Ffordd wahanol o
  	feddwl am brofion yw hyn. Yn lle profi gwerthoedd penodol, rydym yn profi
  	priodweddau allbynnau be bynnag y mewnbwn (er enghraifft hyd restr yn yr
  	enghraifft flaenorol, neu fod yr allbwn yn di-sero, neu eu bod yn y math
  	cywir o allbwn, ayyb). Fan hyn yn lle mewnbwn penodol, profir nifer fawr
  	iawn o fewnbynnau ar hap, a ni edrychir ar werthoedd yr allbynnau, ond
  	priodweddau'r allbynnau.
  
  Er enghraifft ar gyfer profi'r ffwythiant \(g(t) = |t|\), gallwn brofi:
  	<ul>
  		<li>Mae \(g(t)\) yn rhif</li>
  		<li>\(g(t) \geq 0\)</li>
  		<li>\(g(t) = t\) neu \(g(t) = -t\)</li>
  	</ul>
  Mae nifer o offerynnau ar gyfer profion priodweddau hefyd yn gwneud pethau 
  clyfar, fel nodi mewn bas data pa hapenghreifftiau gwnaeth achosi methiant, a
  defnyddio'r enghreifftiau yna pob amser o hyn ymlaen.
  </li>
</ul>

Cysyniad pwysig arall yw gorchudd profion ("test coverage").
Mae yna offerynnau sy'n mesur faint o'r cod gwreiddiol sydd yn rhedeg pan rydym
yn rhedeg ein sgript profion awtomatig.
Y nod yw bwrw 100% o'r cod, ac felly profi 100% o'r cod.
Mae hwn fel arfer yn golygu ysgrifennu profion gyda digon o enghreifftiau i
wirio pob achos arbennig (e.e. pob achos pob datganiad 'if').

# TTD

Mae TTD neu 'datblygiad wedi'i yrru gan brawf' ("test driven development") yn
ffordd o fynd ati i ysgrifennu cod wedi'i seilio o gwmpas profion awtomatig.
Fe'i gwelir fel ffordd dda o ysgrifennu cod dibynadwy.
Gallwch feddwl am hwn fel steil 'uwch' neu 'pellach' o ysgrifennu cod sy'n
sicrhau profion da, ond nid yw pawb yn dewis codio fel hyn.

Y camau fan hyn yw:

1. Ysgrifennu prawf awtomatig.
2. Rhedeg y prawf i sicrhau bod y prawf yn methu (oherwydd nad oes cod eto).
3. Ysgrifennu cod i sicrhau bod y prawf yn pasio.
4. Ail ysgrifennu'r cod mewn ffordd wahanol (mae hyn yn sicrhau bod ni heb
ysgrifennu cod ddistadl sydd ond yn pasio oherwydd atebion disgwyliedig penodol
y prawf).

ac ailadrodd hwn pob tro rydym ni eisiau ychwanegu cod newydd.


# Cyfeiriadau

+ "Research software development", Vincent Knight,

  [https://vknight.org/rsd/](https://vknight.org/rsd/)
  
+ "Test-Driven Development with Python", Harry Percival,
  
  [http://www.obeythetestinggoat.com/](http://www.obeythetestinggoat.com/)