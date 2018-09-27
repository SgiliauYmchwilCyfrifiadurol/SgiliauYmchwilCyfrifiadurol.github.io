---
layout: post
title: 17. Ysgrifennu Meddalwedd - Meddalwedd Cyfeiriadwy
permalink: 17-cyfeirio/
---

<table align='center'>
<tr>
    <td><a href="/16-fersiynnau/">&#x23EA; Blaenorol</a></td>
    <td><a href="/18-trwyddedau/">Nesaf &#x23E9;</a></td>
</tr>
</table>
<br>

Yn union fel darllen papurau ymchwil neu llyrfrau, mae defnydd meddalwedd yn
cyfraniad bwysig i'r broses ymchwil.
I dangos, profi, cadarnhau a cydnabod ffynhonellau cyfraniadau i ymchwil rydym
yn dyfynu a cyfeirio at cyfeiriadau mewn llyfryddiaeth.
Nid yw meddalwedd yn wahanol.

Rhaid cydnabod gwaith unrhyw ymchwiliwr neu rhaglennwr sydd wedi cyfrannu at
eich gwaith, felly rhaid cyfeirio at meddalwedd yn iawn, ar yr un lefel o
bwysigrwydd â cyfnodolyn neu llyfr.
Mae hwn yn rhoi meddalwedd ar yr un lefel o cyflawniad a bri â moddau
traddodiadol o gwneud ymchwil, papurau.
Mae codi lefel canfyddedig creu meddalwedd a rhoi credyd llawn i'w ddatblygwyr
yn codi proffil ymchwilwyr sy'n ysgrifennu meddalwedd, ac yn ei tro yn codi
ansawdd meddalwedd ymchwil ar gyfer pob ymchwiliwr (yn union fel mae rhoi credyd
i awduron papurau ymchwil yn ei wneud).

Mae cyfeirio at y meddalwedd a ddefnyddwyd mewn darn o waith hefyd yn hanfodol
ar gyfer ailgynhyrchadwyedd gwaith: ni all ymchwilwyr arall ailgynhyrchu'r
gwaith os nad ydynt yn gwybod union pa meddalwedd a ddefnyddwyd.

I sicrhai bod ein meddalwedd ni yn cyfeiriadwy (citable), mae yna cwpl o pethau
allwn rhaid i ni meddwl amdanynt:

1. **Credyd:** Dylai cyfeiriadau meddalwedd rhoi credyd ysgolheigaidd, a
adnabyddiaeth cyfreithol i awduron a chyfranwyr i'r meddalwedd.

2. **Adnabyddiaeth unigryw:** Dylai cyfeiriadau meddalwedd bod yn ffordd o
adbabod meddalweddau unigryw, sydd â chydnabyddiaeth gan y cymuned academaidd.

3. **Dyfalbarhad:** Dylai cyfeiriadau meddalwedd para, efallai am cyfnod o amser
ar ôl i cyfnod bywyd y meddalwedd ei hun gorffen, fel bod y cyfeiriadau yma yn
dogfennau hanesyddol defnyddiol.

4. **Hygyrchedd:** Dylai cyfeiriadau meddalwedd hwylso mynediad i'r meddalwedd
ei hun, a'i ddogfennaeth, data, metadata ac unrhyw deunyddiau defnyddiol eraill.

5. **Penodoldeb:** Dylai cyfeiriadau meddalwedd cyfeirio at fersiynnau penodol
o'r meddalwedd.

---

# Sut i wneud meddalwedd yn cyfeiriadwy

I sicrhau bod cyfeiriadau meddalwedd yn **unigryw**, a bod ganddo
**dyfalbarhad**, **hygyrchedd** a **phenodoldeb**, rhaid *archifo*'r meddalwedd.

Mae archifo meddalwedd yn gwneud cwpl o bethau:

+ Rhoi DOI ("Digital Object Identifier") i'r fersiwn penodol yma o'r meddalwedd.
DOIau yw asgwrn cefn y system credyd academaidd, mae gan pob papur digidol
arlein DOI unigryw i fedru cyfeirio atynt, felly dylai fod gan pob darn o
meddalwedd DOI hefyd.
+ Cadw'r gwaith mewn storfa arlein cyhoeddus. Mae hwn yn sicrhau gall ymchwilwyr
eraill cael gafael ar y meddalwedd penodol hyn, ac nid oes posibilrwydd o'r
meddalwedd diflannu ar unrhyw pwynt yn y dyfodol.
+ Cadw trac ar fersiynnau gwahanol y meddalwedd (os defnyddir gyda systemmau
rheolaeth fersiwn fel Git a GitHub).

Storfeudd poblogaidd sy'n gwneud hyn yw [Zenodo](https://zenodo.org/) a
[Figshare](https://figshare.com/).

Unwaith bod y meddalwedd wedi'i archifo (ac, trwy defnyddio systemmau rheolaeth
fersiwn, mae pob fersiwn gorffenol wedi'u archifo a bydd pob fersiwn dyfodol yn
cael eu archifo), rhaid bod ffordd o gyfarthrebu i defnyddwyr y meddalwedd i'w
cyfeirio ato.

Mae nifer o ffyrd o gwneud hyn, rhai ffyrdd poblogaidd:

+ Ysgrifennu papur academaidd am y meddalwedd sy'n cynnwys ei holl wybodaeth
DOI, a gofyn i defnyddwyr cyfeirio at y papur yma pan ddefnyddir y meddalwedd.
(Rhai cyfnodolion sy'n arbenigo mewn hwn yw [JOSS](https://joss.theoj.org/) a
[JORS](https://openresearchsoftware.metajnl.com/), ond mae cyfnodolion
traddodiadol hefyd yn derbyn papur o'r natur yma.)
+ Cyfarthrebu ar wefan y meddalwedd (dogfennaeth y meddalwedd, neu README yn
sorfa'r meddalwedd) yr union cyfeiriad rydych eisiau i defnyddwyr ei ddefnyddio
(e.e. trwy rhoi'r union tecst BibTex i copïo a gludo).
+ Ychwanegu ffeil tecst `CITATION` o fewn y meddalwedd ei hun. Mae nifer o
ffyrdd o ysgrifennu un o rhaid, un strwythurau poblogaidd yw
[CFF](https://citation-file-format.github.io/). Mae gan yr iaith `R` ffwythiant
i ddarllen y ffeiliau yma: `citation()`!

---

# Cyfeiriadau

+ "Software citation principles", Smith, A.M., Katz, D.S., Niemeyer, K.E., ac FORCE11 Software Citation Working Group,
  
  [https://peerj.com/articles/cs-86.pdf](https://peerj.com/articles/cs-86.pdf)

+ "Making Your Code Citable", GiHub,
  
  [https://guides.github.com/activities/citable-code/](https://guides.github.com/activities/citable-code/)

+ "Encouraging citation of software – introducing CITATION files", Wilson, R.,
  
  [https://www.software.ac.uk/blog/2016-10-06-encouraging-citation-software-introducing-citation-files](https://www.software.ac.uk/blog/2016-10-06-encouraging-citation-software-introducing-citation-files)

<table align='center'>
<tr>
    <td><a href="/16-fersiynnau/">&#x23EA; Blaenorol</a></td>
    <td><a href="/18-trwyddedau/">Nesaf &#x23E9;</a></td>
</tr>
</table>
