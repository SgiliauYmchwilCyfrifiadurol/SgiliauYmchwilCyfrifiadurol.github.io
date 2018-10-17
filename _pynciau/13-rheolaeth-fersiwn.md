---
layout: post
title: 13. Rheolaeth Fersiwn gyda Git
permalink: 13-rheolaeth-fersiwn/
---

<table align='center'>
<tr>
    <td><a href="/12-awtomeiddio-canlyniadau/">&#x23EA; Blaenorol</a></td>
    <td><a href="/14-cydweithio/">Nesaf &#x23E9;</a></td>
</tr>
</table>
<br>

Mae system rheolaeth fersiwn yn offeryn sy'n tracio hanes set o ffeiliau.
Mae hwn yn golygu gallwn ddweud wrth y system rheolaeth fersiwn i arbed *cyflwr*
ein ffeiliau ar unrhyw bwynt.
Yna gallwn barhau i newid ac ychwanegu i'n ffeiliau, ac arbed a storio'r
cyflyrau ffeiliau hwn hefyd.
Mae arbed cyflwr ffeil yn debyg i greu copi o'r cyfeiriadur presennol fel
'backup'.

Mae nifer o fanteision i ddefnyddio system rheolaeth fersiwn yn lle arbed nifer
o gopïau fel 'backup'.

  + Mae'r holl hanes wedi'i arbed, felly gallwn neidio nôl i unrhyw bwynt.
  + Yn lle enwi fersiynau o ffeiliau megis 'fersiwn_1', 'fersiwn_2',
  'fersiwn_olaf'; mae gan bob pwynt mewn hanes y cyfeiriadur neges ystyrlon
  sy'n esbonio yn union pa newidiadau a ddigwyddir ers y fersiwn blaenorol.

Yn y tiwtorial yma defnyddiwn un system rheolaeth fersiwn penodol, Git.
Git yw un o'r systemau mwyaf poblogaidd.
Opsiynau eraill yw Mercurial, Subversion, a Penforce.

Yn Git pan rydym yn arbed cyflwr y cyfeiriadur, fe elwir hwn yn 'commit'.
Pan rydym yn gwneud commit gyda Git, rydym yn ychwanegu 'neges commit' sy'n
esbonio pa newidiadau a ddigwyddodd ers y commit diwethaf.
Gall Git dangos hanes pob commit a'u negeseuon commit.
Mae hyn yn ddefnyddiol iawn wrth geisio darganfod pryd a ble gwnaeth camgymeriad
neu byg digwydd.
Gallwn hefyd cymharu ffeil rhwng dau commit i weld yn union pa linellau a
newidiodd.

---

## 0. Gosod Git

### (Bydd ond angen gwneud hwn unwaith)


Cyn dechrau mae cwpl o bethau mae rhaid i ni wneud i osod Git.
Lawrlwythwch Git a'i osod ar eich cyfrifiadur, trwy dilyn cyfawryddiadau
fan hyn: [https://git-scm.com/](https://git-scm.com/).

Cofiwch fod Git yn cadw trac o holl hanes prosiect, gan gynnwys pwy wnaeth y
newidiadau (sy'n bwysig iawn ar gyfer prosiectau cydweithredol).
Felly rhaid dweud wrth Git pwy ydyn ni.

Agorwch y 'Command Line' neu'r 'Command Prompt', a theipiwch:

{% highlight bash %}
git config --global user.name "Eich enw"
{% endhighlight %}

{% highlight bash %}
git config --global user.email "Eich cyfeiriad ebost"
{% endhighlight %}

**Noder** mae'r data yma yn aros ar eich cyfrifiadur, ni chasglir can
unrhyw wasanaeth.

Weithiau bydd angen i Git agor golygydd testun.
Rhaid dweud wrth Git pa olygydd testun i'w ddefnyddio.
Ar gyfer y tiwtorial yma, dewiswn naill ai 'Atom' neu 'VS Code'.

+ I ddefnyddio Atom ar Windows:

  {% highlight bash %}
  git config --global core.editor "C:\Program Files (x86)\atom.exe --wait"
  {% endhighlight %}

+ I ddefnyddio VS Code ar Windows:

  {% highlight bash %}
  git config --global core.editor "'C:\Program Files (x86)\Microsoft VS Code\code.exe' -n --wait"
  {% endhighlight %}

+ I ddefnyddio Atom ar systemau -nix:

  {% highlight bash %}
  git config --global core.editor "atom --wait"
  {% endhighlight %}

+ I ddefnyddio VS Code ar systemau -nix:

  {% highlight bash %}
  git config --global core.editor "code --wait"
  {% endhighlight %}

**Noder** efallai bydd y path yn wahanol (ar Windows) yn dibynnu ar le mae'r
golygydd testun wedi'i osod ar eich cyfrifiadur.

---

# 1. Ymgychwyn Cyfeiriadur Git

Dechreuwn trwy greu cyfeiriadur newydd: `tiwtorial-git`.

Tu fewn i'r cyfeiriadur hwn crëwch ddogfen `main.tex` lle ysgrifennwn restr
o'r pethau y dysgwn yn y cwrs yma:

{% highlight tex %}
\documentclass{article}

\title{Rhestr pynciau Sgiliau Ymchwil Cyfrifiadurol}

\begin{document}
\maketitle
\end{document}
{% endhighlight %}

Nawr dywedwn wrth Git i ddechrau cadw trac ar y cyfeiriadur yma.
Yn y 'Command Line' teipiwch:

{% highlight bash %}
git init
{% endhighlight %}

Fe ddylech weld neges yn dweud eich bod yn llwyddiannus yn wedi ymgychwyn
cyfeiriadur Git.

---

## 2. Llwyfannu newidiadau a gwneud commit

Gallwn weld statws ein cyfeiriadur:

{% highlight bash %}
git status
{% endhighlight %}

Gwelwn rywbeth fel hwn:

{% highlight bash %}
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        main.tex

nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}

Mae lot o wybodaeth fan hyn.
Yn gyntaf, nid yw Git yn tracio'r ffeil `main.tex`.
I dracio'r ffeil yna:

{% highlight bash %}
git add main.tex
{% endhighlight %}

Nawr os rhedwn `git status` gwelwn:

{% highlight bash %}
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   main.tex
{% endhighlight %}

Felly mae'r newidiadau sydd wedi'i wneud i'r ffeil `main.tex` (h.y. creu'r ffeil)
yn barod i wneud commit.

{% highlight bash %}
git commit
{% endhighlight %}

Wrth wneud hyn bydd y golygydd testun a dewisoch chi'n gynharach yn agor.
Mae angen ysgrifennu neges commit, sy'n esbonio'r newidiadau a ddigwyddodd ers
y commit diwethaf.

Teipiwch y neges ganlynol:

{% highlight tex %}
Ysgrifennu rhestr wag

Mae'r ffeil yn wag ar hyn o bryd ond bydd yn cynnwys rhestr o cysyniadau gwaith
cyfrifiadurol ailgynhyrchiadwy a ddysgir yn y cwrs yma.
{% endhighlight %}

Unwaith rydych wedi teipio hwnna, arbed y ffeil a chau'r golygydd testun.
Bydd Git nawr yn cadarnhau eich bod wedi gwneud eich commit cyntaf.

{% highlight bash %}
[master (root-commit) cbb4481] Ysgrifennu rhestr wag
 1 file changed, 7 insertions(+)
 create mode 100644 main.tex
{% endhighlight %}

Nawr of rhedwn `git status`, gwelwn neges yn dweud bod popeth yn y cyfeiriadur
wedi diweddaru:

{% highlight bash %}
On branch master
nothing to commit, working directory clean
{% endhighlight %}

**Noder** Mae neges commit yn cynnwys dau brif gydran:

{% highlight tex %}
<Teitl y commit>

<Disgrifiad o beth digwyddodd>
{% endhighlight %}

Mae commit yn giplun mae Git yn cymryd o'ch cyfeiriadur, a dylwn wneud commit
ar gyfer pob cam ystyrlon yn ddatblygiad y prosiect.

---

## 3. Tracio newidiadau i ffeiliau

Ychwanegwn ein enw i'r ddogfen:

{% highlight tex %}
\documentclass{article}

\title{Rhestr pynciau Sgiliau Ymchwil Cyfrifiadurol}
\author{Sion Corn}

\begin{document}
\maketitle
\end{document}
{% endhighlight %}

Arbed y ffeil a rhedwch `git status`.
Fe welwn nawr bod Git yn ymwybodol o'r newidiadau i'r ffeil:

{% highlight bash %}
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   main.tex

no changes added to commit (use "git add" and/or "git commit -a")
{% endhighlight %}

I lwyfannu'r ffeil ar gyfer commit defnyddiwn `git add` eto:

{% highlight bash %}
git add main.tex
{% endhighlight %}

Ac i wneud y commit:

{% highlight bash %}
git commit
{% endhighlight %}

Gyda'r neges commit canlynol:

{% highlight bash %}
ychwanegu enw'r awdur
{% endhighlight %}

Yn yr achos yma ond teitl y neges commit sydd angen, does dim rhagor i'w ddweud.

Yn olaf, gallwn wirio'r statws: `git status` i gadarnhau bod popeth wedi'i
wneud yn gywir.

---

## 4. Anwybyddu ffeiliau

Nawr os adeiladwn y ddogfen LaTex:

{% highlight bash %}
pdflatex main.tex
{% endhighlight %}

Nawr os gwiriwn statws ein cyfeiriadur:

{% highlight bash %}
git status
{% endhighlight %}

Gwelwn fod holl ffeiliau ategol hefyd wedi'i rhestri yn ogystal â'r pdf:

{% highlight bash %}
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        main.aux
        main.log
        main.pdf

nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}

I ddweud wrth Git i anwybyddu'r ffeiliau yma (ond y ffeil `tex` sydd angen),
rhestrant nhw mewn ffeil gwag o'r enw `.gitignore`.
Agorwch eich golygydd testun a theipiwch

{% highlight bash %}
main.aux
main.log
main.pdf
{% endhighlight %}

Arbedwch y ffeil fel `.gitignore`, a rhedwch `git status` eto.
Nawr gwelwn fod Git yn anwybyddu'r tri ffeil yma, ond nid yw'r anwybyddu'r ffeil
`.gitignore`.
Nawr gwnewch commit sy'n ychwanegu'r ffeil `.gitignore`:

{% highlight bash %}
git add .gigignore
git commit
{% endhighlight %}

Fel neges commit defnyddiwch `ychwanegu .gitignore`.

Gallwn newid y ffeil yma pryd bynnag rydym ni eisiau (efallai byddwn hefyd
eisiau i Git cadw trac ar y pdf hefyd).

--

## 5. Chwilota a defnyddio'r hanes

Rydym wedi gwneud job dda hyd yn hyn o gadw trac ar hanes y prosiect, a nawr
cawn weld sut all hwn fod yn ddefnyddiol.

Yn gyntaf, gadewch i ni gadarnhau bod ein cyfeiriadur yn y statws disgwyliedig
gyda `git status`:

{% highlight bash %}
On branch master
nothing to commit, working directory clean
{% endhighlight %}

Nawr edrychwn ar yr hanes:

{% highlight bash %}
git log
{% endhighlight %}

Mae hwn yn dangos log llawn y prosiect:

{% highlight bash %}
commit 2f96757d96ded19a729f6deb211bb309cfbff168
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 14:04:22 2018 +0100

    ychwanegu .gitignore

commit d95276c618ebc91137b585570b036a94f43ef99d
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 14:02:55 2018 +0100

    ychwanegu enw'r awdur

commit cbb44813df4bd7ac1f2524b0fe13f41fcfc6b294
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 13:59:57 2018 +0100

    Ysgrifennu rhestr wag
    
    Mae'r ffeil yn wag ar hyn o bryd ond bydd yn cynnwys rhestr o cysyniadau gwaith
    cyfrifiadurol ailgynhyrchiadwy a ddysgir yn y cwrs yma.
{% endhighlight %}

Gwelwn fod yna tri commit fan hyn, pob un gyda rhyw set of rhifau a llythrennau
a edrychir fel y teipir ar hap.
Fe elwir y set o gymeriadau yma yn "hash".

Mae gan y commit cyntaf y teitl `Ysgrifennu rhestr wag`, a'r hash:
`cbb44813df4bd7ac1f2524b0fe13f41fcfc6b294`.
**Noder** ar eich cyfrifiadur chi bydd yr hash yma yn wahanol.
Mae pob hash a generadur gan Git yn fathemategol o sicr i fod yn unigryw, felly
y maen wedi'i aseinio'n unigryw i'r newidiadau a ddigwyddodd yn y commit yna.

Un o'r pethau mae'r hash yma yn ein galluogi ni i'w wneud yw mynd nôl mewn
amser.
Byddwn yn mynd nôl i'r ffeil `main.tex` cyn i ni ychwanegu enw'r awdur.
Rydym yn gwneud hwn gyda'r gorchymyn `checkout` a'r hash (copïo a gludo'r
cymeriadau o'r log.).
Yn yr achos yma, defnyddiwn yr hash:

{% highlight bash %}
git checkout cbb44813df4bd7ac1f2524b0fe13f41fcfc6b294 main.tex
{% endhighlight %}

Nawr os rhedwn `git status` gwelwn fod y ffeil wedi newid:

{% highlight bash %}
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   main.tex
{% endhighlight %}

(Agorwch `main.tex` a gwelwch nad yw enw'r awdur yna rhagor.)
Gallwn nawr gwneud mwy o newidiadau i `main.tex` a gwneud commit fel gwnaethon
ni o'r blaen.

Neu, ar gyfer y tiwtorial yma, rydym yn mynd i ddychwel y ffeil i'r cyflwr yr
oedd ar y commit diwethaf.
Defnyddiwn `checkout` eto, gyda hash y commit diwethaf.
Y tro yma, amnewid yr hash gyda `HEAD`, sy'n llaw fer ar gyfer hash y commit
diwethaf:

{% highlight bash %}
git checkout HEAD main.tex
{% endhighlight %}

Os rhedwn `git status` fe welwn fod popeth nôl i'r statws blaenorol, a bod enw'r
awdur wedi dychwelyd i `main.tex`.

---

## 6. Creu canghennau

Un o fanteision mawr Git yw'r gallu i weithio mewn paralel.
Y ffordd o wneud hwn yw trwy ddefnyddio "canghennau".

Wrth deipio `git status` gwelwn un darn o wybodaeth yn aml: `On branch master`.
Mae hwn yn dweud wrthon ni pa gangen o'r hanes rydym arno ar hyn o bryd.
I weld pob cangen:

{% highlight bash %}
git branch
{% endhighlight %}

Sy'n dangos:

{% highlight bash %}
* master
{% endhighlight %}

Felly ar hyn o bryd ond un gangen sydd, o'r enw `master`.
Gadewch i ni greu cangen arall o'r enw `rhestr-pynciau`:

{% highlight bash %}
git branch rhestr-pynciau
{% endhighlight %}

Nawr pan deipiwn `git branch` fe welwn fod dwy gangen yn bodoli.
Mae'r gangen weithredol wedi'i nodi gan `*`:

{% highlight bash %}
  add-list-of-topics
* master
{% endhighlight %}

I symud i'r gangen newydd:

{% highlight bash %}
git checkout rhestr-pynciau
{% endhighlight %}

Rhedwch `git branch` ac yna `git status` i weld sut mae hwn yn gweithio.

Nawr crëwch ffolder newydd o fewn y cyfeiriadur yma o'r enw `tex`, ac o fewn o
ffolder yna crëwch ddogfen newydd o'r enw `rhestr-o-bynciau.tex`:

{% highlight tex %}
\begin{itemize}
    \item Deall pwysigrwydd ailgynhyrchadwyedd. \checkmark
    \item Deall technegau ymchwil agored. \checkmark
    \item Sgiliau awtomeiddio. \checkmark
    \item Ysgrifennu cod gydag ymarferion da. \checkmark
    \item Cyfathrebu canlyniadau gyda LaTeX. \checkmark
    \item Deall rheolaeth fersiwn gyda Git.
    \item Cydweithio gyda GitHub.
    \item Deall cydrannau meddalwedd.
\end{itemize}
{% endhighlight %}

Ychwanegu'r ffeil yma a gwneud commit:

{% highlight bash %}
git add tex/rhestr-o-bynciau.tex
git commit
{% endhighlight %}

Nawr byddwn yn dychwelyd i'r gangen `master` (dawn nôl i'r rhestr yma nes
ymlaen).

{% highlight bash %}
git checkout master
{% endhighlight %}

Nawr crëwn gangen newydd o'r enw `newid-lled-tudalen`.
Defnyddiwn y gangen yma i newid lled y tudalen:

{% highlight bash %}
git branch newid-lled-tudalen
git checkout newid-lled-tudalen
{% endhighlight %}

Newidiwn `main.tex` i gynnwys y llinellau canlynol yn y rhaglith:

{% highlight tex %}
\documentclass{article}

\usepackage[margin=1.5cm, includefoot, footskip=30pt]{geometry}

\title{Rhestr pynciau Sgiliau Ymchwil Cyfrifiadurol}
\author{Sion Corn}

\begin{document}
\maketitle
\end{document}
{% endhighlight %}

Os adeiladwch y ddogfen pdf nawr gwelwn fod yr ymylon wedi newid lled.
Llwyfannwch y newidiadau a gwnewch commit.
Edrychwn ar y log:

{% highlight bash %}
commit a3690555fd89fd1d4086f2363f13aabce421f8bd
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 15:09:17 2018 +0100

    newid lled tudalen

commit 2f96757d96ded19a729f6deb211bb309cfbff168
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 14:04:22 2018 +0100

    ychwanegu .gitignore

commit d95276c618ebc91137b585570b036a94f43ef99d
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 14:02:55 2018 +0100

    ychwanegu enw'r awdur

commit cbb44813df4bd7ac1f2524b0fe13f41fcfc6b294
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 13:59:57 2018 +0100

    Ysgrifennu rhestr wag
    
    Mae'r ffeil yn wag ar hyn o bryd ond bydd yn cynnwys rhestr o cysyniadau gwaith
    cyfrifiadurol ailgynhyrchiadwy a ddysgir yn y cwrs yma.
{% endhighlight %}

Nid yw'r commit cafodd ei wneud ar y gangen `rhestr-pynciau` yn ymddangos fan
hyn.
Mae `git log` ond yn dangos hanes y gangen weithredol.

Nawr dychwelwn i'r gangen `master`, a gwelwn sut i gyfuno'r gwaith a ddigwyddodd
ar y ddwy gangen yma:

{% highlight bash %}
git checkout master
{% endhighlight %}

---

## 7. Cyfuno canghennau

Gallwn gyfuno gwaith un gangen i mewn i gangen arall, ac elwir hwn yn "merge".
I gyfuno’r gangen `newid-lled-tudalen` i mewn i'r gangen `master` (sef ein
cangen weithredol presennol).

**Noder** Cyn cyfuno canghennau mae'n syniad da i wirio `git status` i sicrhau
bod popeth yn y cyflwr cywir (e.e. ein bod ni ar y gangen gywir ayyb...).

{% highlight bash %}
git merge newid-lled-tudalen
{% endhighlight %}

Fe ddylwn ni gweld rhywbeth fel hyn:

{% highlight bash %}
Updating b116460..f252f5a
Fast-forward
 main.tex | 2 ++
 1 file changed, 2 insertions(+)
{% endhighlight %}

Cofiwch, os anghofiwn enw unrhyw gangen gallwn redeg `git branch` i weld yr holl
ganghennau.

Nawr cyfunwn y gangen `rhestr-pynciau`:

{% highlight bash %}
git merge rhestr-pynciau
{% endhighlight %}

Wrth gyfuno canghennau, weithiau bydd Git yn agor golygydd testun yn gofyn i ni
cadarnhau'r cyfuno gyda neges commit.
Os yw hyn yn digwydd, does dim angen newid y neges commit (os nad ydych eisiau).

{% highlight bash %}
Merge made by the 'recursive' strategy.
 tex/rhestr-o-bynciau.tex | 10 ++++++++++
 1 file changed, 10 insertions(+)
 create mode 100644 tex/rhestr-o-bynciau.tex
{% endhighlight %}

Nawr fe ddylwn ein cyfeiriadur edrych fel hwn:

{% highlight bash %}
|---tiwtorial-git
    |--- main.tex
    |--- main.aux
    |--- main.log
    |--- main.pdf
    |--- tex/
         |--- rhestr-o-bynciau.tex
{% endhighlight %}

Byddwn yn gwneud un newid olaf i `main.tex` i gynnwys y ffeil
`rhestr-o-bynciau.tex`:

{% highlight tex %}
\documentclass{article}
\usepackage{amssymb}

\usepackage[margin=1.5cm, includefoot, footskip=30pt]{geometry}

\title{Rhestr pynciau Sgiliau Ymchwil Cyfrifiadurol}
\author{Sion Corn}

\begin{document}
\maketitle

\input{tex/list-of-topics.tex}
\end{document}
{% endhighlight %}

Adeiladwch y ddogfen ad edrychwch ar y rhestr!

Cyn gwneud y commit olaf, edrychwn ar un gorchymyn arall:

{% highlight bash %}
git diff
{% endhighlight %}

Mae hwn yn dangos y gwahaniaeth rhwng cyflwr presennol y cyfeiriadur a'r commit
diwethaf:

{% highlight bash %}
diff --git a/main.tex b/main.tex
index a97e945..0cde0d1 100644
--- a/main.tex
+++ b/main.tex
@@ -1,4 +1,5 @@
 \documentclass{article}
+\usepackage{amssymb}
 
 \usepackage[margin=1.5cm, includefoot, footskip=30pt]{geometry}
 
@@ -7,4 +8,6 @@
 
 \begin{document}
 \maketitle
+
+\input{tex/rhestr-o-bynciau.tex}
 \end{document}
\ No newline at end of file
{% endhighlight %}

Ychwanegon ni'r llinellau `\usepackage{amssymb}` ac
`\input{tex/rhestr-o-bynciau.tex}`.
Nawr lwyfannwn y newidiadau a gwnawn commit.
Edrychwn ar y log:

{% highlight bash %}
commit 24c525778a029e058c25313c03724d81e28c9213
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 15:33:35 2018 +0100

    ychwanegu rhestr o bynciau mewn main.tex

commit e4ddde4da5e47790e430bcee600f075f688ffef6
Merge: a369055 c6ecfc4
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 15:20:06 2018 +0100

    Merge branch 'rhestr-pynciau'

commit a3690555fd89fd1d4086f2363f13aabce421f8bd
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 15:09:17 2018 +0100

    newid lled tudalen

commit c6ecfc4c8565789af213e4f84c7bcb3aaa167e8d
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 15:05:18 2018 +0100

    Ysgrifennu rhestr o bynciau

commit 2f96757d96ded19a729f6deb211bb309cfbff168
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 14:04:22 2018 +0100

    ychwanegu .gitignore

commit d95276c618ebc91137b585570b036a94f43ef99d
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 14:02:55 2018 +0100

    ychwanegu enw'r awdur

commit cbb44813df4bd7ac1f2524b0fe13f41fcfc6b294
Author: Geraint Palmer <palmer.geraint@googlemail.com>
Date:   Sat Sep 22 13:59:57 2018 +0100

    Ysgrifennu rhestr wag
    
    Mae'r ffeil yn wag ar hyn o bryd ond bydd yn cynnwys rhestr o cysyniadau gwaith
    cyfrifiadurol ailgynhyrchiadwy a ddysgir yn y cwrs yma.
{% endhighlight %}

Nawr gwelwn hanes llawn beth ysgrifennwn, ac mae gennym y potensial i fynd nôl i
unrhyw gam.
Yn bellach mae ein cyfeiriadur yn daclus, a does dim angen nifer o gopïau o'r un
ffeil gydag enwau yn dynodi pa fersiwn ydyn nhw.

**Noder** Mae creu cangen newydd yn "rhad" o ran faint o le mae'n meddiannu yn
storfa'r cyfrifiadur; felly'n mae'n syniad da i greu cangen newydd mewn prosiect
pob tro rydym eisiau trio rhywbeth newydd.

**Noder** Wrth gyfuno canghennau, mae'n bosib creu rhywbeth a elwir yn "merge
conflict".
Digwyddir hwn pan nad yw Git yn gallu cyfuno canghennau yn awtomatig (e.e. pan
mae'r un llinell o god wedi newid ar y ddwy gangen ers i'r ymganghennu digwydd).
Yn yr achos yma bydd Git yn gofyn i ni newid y ffeil cyn gwneud y commit.

---

## 8. Crynodeb

Dyma'r gorchmynion Git defnyddiwn yn y tiwtorial yma:

- `git init`: Ymgychwyn cyfeiriadur Git newydd.
- `git add <ffeil>`:Dechrau tracio `<ffeil>` ac/neu lwyfannu’r newidiadau i
  `<ffeil>` yn barod ar gyfer gwneud commit.
- `git status`: Gweld statws presennol y cyfeiriadur.
- `git commit`: Creu ciplun o'r newidiadau presennol.
- `git checkout <hash> <ffeil>`: Gosod cyflwr y `<ffeil>` i fod mewn yr un
  cyflwr ag oedd e ar commit `<hash>`. Nodwch fod `HEAD` yn llaw fer ar gyfer
  hash y commit diwethaf.
- `git branch`: Rhestri'r holl ganghennau.
- `git branch <enw-cangen>`: Creu cangen newydd o'r enw `<enw-cangen>`.
- `git checkout <enw-cangen>`: Symud i'r gangen `<enw-cangen>`.
- `git merge <enw-cangen>`: Cyfuno'r gwaith sydd ar `<enw-cangen>` mewn i'r
  cangen weithredol bresennol.
- `git diff`: Dangos y gwahaniaethau rhwng y cyflwr presennol a chyflwr y commit
  diwethaf.

**Awgrym:** Mae Git yn cadw trac o bethau llinell wrth linell.
Felly mae newid un cymeriad yn cyfateb â newid y holl linell.
Mae'n ddefnyddiol felly i gadw llinellau yn fyr er mwyn cadw newidiadau commit
yn fwy ystyrlon.

---

# Cyfeiriadau

+ "Research software development", Vincent Knight,
  
  [https://vknight.org/rsd/](https://vknight.org/rsd/)

+ "Introduction to Git and GitHub for Python Developers", Jim Anderson ,
  
  [https://realpython.com/python-git-github-intro/](https://realpython.com/python-git-github-intro/)

<table align='center'>
<tr>
    <td><a href="/12-awtomeiddio-canlyniadau/">&#x23EA; Blaenorol</a></td>
    <td><a href="/14-cydweithio/">Nesaf &#x23E9;</a></td>
</tr>
</table>
