---
layout: post
title: 17. Cydweithio gyda GitHub
permalink: cydweithio/
---

Tra bod Git yn offeryn pwysig a phwerus i ddefnyddio wrth weithio ar ben ein
hunain, mae'n dod yn fwy pwerus byth wrth gydweithio gyda phobl eraill.
Mae'r cysyniad o weithio ar ganghennau paralel yn estyn i unigolion gwahanol yn
gweithio ar ganghennau paralel.

I wneud hwn rydym yn defnyddio fersiwn `remote` o'r cyfeiriadur.
Gall hyn fod unrhyw le, ond un o'r gwasanaethau mwyaf poblogaidd ar gyfer cadw
cyfeiriadau pell yw [GitHub](https://github.com/).
Nodwch taw un o gryfderau Git a GitHub yw bod holl hanes unrhyw gopi o
cyfeiriadur trwy'r amser yn aros gyda'r cyfeiriadur yna.

---

## 0. Mewngofnodi i GitHub

Cyn dechrau, rhaid sefydlu cyfrif GitHub.
Ewch i [www.github.com](www.github.com), ac crëwch cyfrif gan ddefnyddiwch eich
e-bost.

Mae GitHub yn ffordd o gydweithio ac i gynnal cod mewn lle agored a hygyrch.
Er efallai bod rhai ohonoch yn awyddus cuddio'ch hunaniaeth ar y we; cofiwch
bydd eich cyfrif GitHub yn cyfrif proffesiynol, ac eich enw defnyddiwr yw awdur
swyddogol eich gwaith.
Er mwyn hyrwyddo onestrwydd a thryloywder ymchwil, mae'n gwell peidio cuddio'ch
hunaniaeth ar GitHub.

---

## 1. Fforcio cyfeiriadur

Ar GitHub yn barod mae cyfeiriadur ar gyfer y tiwtorial yma:

+ [https://github.com/SgiliauYmchwilCyfrifiadurol/sya-cydweithio](https://github.com/SgiliauYmchwilCyfrifiadurol/sya-cydweithio).

Dechreuwn trwy greu copi ein hun o'r cyfeiriadur yna.
Galw ni hwn yn 'Fforc' o'r cyfeiriadur, a bydd yn creu copi o'r cyfeiriadur yna
ar GitHub ar eich cyfrif chi.

Ar ôl arwyddo mewn i GitHub, a mynd i'r linc uchod, cliciwch ar y botwm `Fork`.

![]({{root}}/delweddau/forc.png){: .center-image }

Mae hwn yn creu copi o'r cyfeiriadur o dan eich cyfrif chi.

![]({{root}}/delweddau/repo-wedi-copio.png){: .center-image }

---

## 2. Clonio cyfeiriadur

Nawr byddwn eisiau copi o'r cyfeiriadur yma yn lleol.
Galwn ni hwn yn glôn o'r cyfeiriadur.

Cliciwch ar y botwm `Clone or Download`, a chopïwch gyfeiriad y cyfeiriadur:

![]({{root}}/delweddau/clonio.png){: .center-image }

Yn y 'Command Line' neu'r 'Command Prompt', llywiwch eich hun i rywle hoffwn
rhoi clôn o'r cyfeiriadur yma (e.e. mewn 'Documents').
Yna teipiwch:

{% highlight bash %}
git clone <cyfeiriad-a-copiwyd>
{% endhighlight %}

Fe ddylach gweld rhywbeth fel hwn:

{% highlight bash %}
$ git clone https://github.com/<enw-defnyddiwr-github>/sya-cydweithio.git
Cloning into 'sya-cydweithio'...
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 5 (delta 0), reused 5 (delta 0), pack-reused 0
Unpacking objects: 100% (5/5), done.
{% endhighlight %}

Mae hwn yn creu copi o holl ffeiliau sydd yn y cyfeiriadur, a'r holl hanes.
(Cofiwch gallwn deipio `git log` i weld yr holl hanes).

---

## 3. Gwneud newidiadau

Os agorwch chi'r ffeil `prif.tex` gwelwch chi restr o "Top Tips" sgiliau
ymchwil cyfrifiadurol.
Byddwch chi nawr yn ychwanegu "Top Tip" gwreiddiol arall i'r rhestr.

Yn gyntaf, byddwn yn gweithio ar gangen newydd o'r enw `ychwanegu-toptip-newydd`:

{% highlight bash %}
git branch ychwanegu-toptip-newydd
git checkout ychwanegu-toptip-newydd
{% endhighlight %}

Nawr agorwch y ffeil `prif.tex` gyda golygydd testun.
O fewn y rhestr `itemize` ychwanegwn linell *gwreiddiol* ychwanegol sy'n
dechrau gyda `\item`: er enghraifft:

{% highlight tex %}
  \item Defnyddio meddalwedd agored.
{% endhighlight %}

Unwaith bod y newid wedi'i wneud, byddwn yn gwneud commit:

{% highlight bash %}
git add prif.tex
git commit
{% endhighlight %}

Ysgrifennwch neges commit synhwyrol, er enghraifft:

{% highlight bash %}
ychwanegu top tip am defnyddio meddalwedd agored
{% endhighlight %}

Ar hyn o bryd mae'r newid yma ond yn bodoli ar eich cyfrifiadur.
Er mwyn i'r newid bodoli ar y copi gwreiddiol, bydd angen i rywun sydd a
rheolaeth dros y cyfeiriadur yna cyfuno'ch newidiadau chi i mewn i'r cod
gwreiddiol.

Mae angen i chi nawr gwneud "cais" er mwyn i'r cyfuno yna digwydd.
Mae gan GitHub y gallu i wneud hwn, a elwir hwn yn *"Pull request"* (PR).

---

## 4. Gwneud PR

Yn gyntaf rhaid anfon y newidiadau lleol yn ôl i'ch copi ar GitHib.
Rydym yn galw'ch copi chi ar GitHub y `remote`.
I weld os yw Git yn gwybod am y 'remote':

{% highlight bash %}
git remote -v
{% endhighlight %}

(Mae'r `-v` yn llaw-fer ar gyfer "verbose").

Mae hwn yn rhoi:

{% highlight bash %}
origin https://github.com/StephanieAngharad/sya-cydweithio.git (fetch)
origin https://github.com/StephanieAngharad/sya-cydweithio.git (push)
{% endhighlight %}

Mae hwn yn dangos bod gennym un 'remote' gyda'r alias `origin` (nodwch bydd y
cyfeiriad a welwch ar eich cyfrifiadur chi yn wahanol).

Nawr rydyn ni eisiau gwthio'r newidiadau i'r 'remote' yna:

{% highlight bash %}
git push origin ychwanegu-toptip-newydd
{% endhighlight %}

Ar ôl rhedeg y gorchymyn hwnna a dilysu'ch manylion, bydd eich newidiadau ar
cangen ei hun ar GitHub:

![]({{root}}/delweddau/ar-ol-gwthio.png){: .center-image }

Nawr rydych yn barod i wneud cais i gyfuno'r newidiadau i'r cyfeiriadur
gwreiddiol.
I wneud hwn cliciwch ar y botwm "Compare and pull request", ac yna ysgrifennwch
neges.

Pan fyddwch yn agor PR byddwch yn sylwi mae GitHub cyn ceisio defnyddio'ch
negeseuon commit fel y neges PR.
Gall hyn fod yn ddefnyddiol, ond fe ddylech gofio bod neges PR yn dechrau sgwrs
gyda rhywun arall.
Ceisiwch ddilyn y cyngor isod:

 + Cynnwys pwrpas y PR: 'bydd y newid yma yn ...'
 + Gofynnwch am adborth: 'Ceisiais ... ond hoffwn adborth ar ...'
 + Byddwch yn gwrtais: efallai bod y person sy'n adolygu'r PR yn brysur.

Unwaith rydych wedi ysgrifennu'r neges, gallwch anfon y cais PR trwy glicio ar
"Create a pull request".


![]({{root}}/delweddau/anfon-pr.png){: .center-image }

---

## 5. Adolygu PR

Unwaith anfonwch chi'r PR, bydd rhywun yn ei adolygu.
Efallai bydd yr adolygiad yn gofyn am newidiadau.

Os bydd hwn yn digwydd, gallwn wneud unrhyw newidiadau yn lleol, ar yr un
gangen.
Llwyfannwch y newidiadau a gwnewch commit.
Gwthiwch y newidiadau yn ôl i'r un gangen ar GitHub.
Bydd hwn yn diweddaru'r PR yn awtomatig.

Fe ddylai adolygu PR bod yn brofiad defnyddiol a phositif i bawb.
Os ydych chi mewn sefyllfa lle rydych chi'n adolygu PR rhywun arall, cofiwch:

 + Peidiwch ofyn am newidiadau ar sail rhagfarn gyfarwydd: Efallai bydd rhywun
 yn gwneud rhywbeth mewn ffordd wahanol i'r ffordd y byddwch chi, ond does dim
 angen gofyn am newid heblaw bod rheswm da (bygs, aneffeithlonrwydd, ayyb...).
 + Peidiwch fod yn amwys, gofyn am newidiadau spesiffig, gan ysgrifennu
 llinellau o god os oes angen.
 + Wrth awgrymu llinellau spesiffig o god, sicrhewch eich bod wedi trio nhw eich
 hun a bod nhw'n gweithio. Wrth gwrs bydd hwn yn cymryd amser, ond mae
 adolygiad PR da yn cymryd amser.
 + Rhowch gyd-destun: os oes rheswm i ofyn am newidiadau, rhowch y rheswm.
 + Byddwch yn bositif, a byddwch yn gwrtais.
 + Mae'r pwysig cofio dylai adolygiad PR fod yn sgwrs.

