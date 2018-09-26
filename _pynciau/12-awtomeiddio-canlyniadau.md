---
layout: post
title: 12. Cyfathrebu - Awtomeiddio Canlyniadau
permalink: 12-awtomeiddio-canlyniadau/
---

Gwelwn yn y tiwtorial blaenorol bod LaTeX yn ddefnyddiol iawn ar gyfer creu
dogfennau ysgrifenedig sy'n edrych yn broffesiynol iawn.
Un o gryfderau mwyaf LaTeX yw'r gallu i *strwythuro* ffynonellau’r ddogfen mewn
ffordd ystyrlon.
Y peth sy'n galluogi hyn yw'r gallu i alw un ddogfen o'r llall.

Crëwch gyfeiriadur o'r enw `tiwrorial-latex`, a thu fewn y cyfeiriadur yma crëwch
cyfeiriadur arall o'r enw `tex`.
Yn y cyfeiriadur `tex` crëwch ddogfen o'r enw `pennod-1.tex`:

{% highlight tex %}
Byddwn yn archwilio symiau cyfanrifau.
{% endhighlight %}

Yn y cyfeiriadur uchaf crëwch ddogfen o'r enw `prif.tex`:

{% highlight tex %}
\documentclass{article}

\title{Swm cyfanrifau}

\begin{document}
    \maketitle
    \input{tex/pennod-1.tex}
\end{document}
{% endhighlight %}

Fe ddylach eich cyfeirnod edrych fe hyn:

{% highlight bash %}
tiwtorial-latex
|    prif.tex
|----tex/
     | pennod-1.tex
{% endhighlight %}

Nawr pan rydym ni o fewn y cyfeiriadur uchaf `tiwtorial-latex`, gallwn
adeiladu'r ddogfen `prif.tex`, a gwelwn bydd cynnwys y ddogfen
`tex/pennod-1.tex` wedi cynnwys yn y ddogfen.

{% highlight bash %}
pdflatex prif.tex
{% endhighlight %}

---

### Cynnwys allbwn ymchwil

Os oes gennych allbwn ymchwil a chafodd eu creu gan feddalwedd:

  + Rhifau sbesiffig
  + Hafaliadau cymhleth
  + Tablau data
  + Plotiau

mae'n hawdd iawn gwneud camgymeriadau trwy ysgrifennu'r rhain gyda llaw i mewn
i'r dogfen LaTeX.
Mae hefyd yn hawdd iawn i'r allbynnau yma mynd "out-of-date" wrth i'r ymchwil
mynd yn ei flaen.
Ymarferion gorau yw allbynnu'r rhain yn syth o'ch meddalwedd yn uniongyrchol i
ffeil a bydd yn cael ei gynnwys yn y ddogfen LaTeX.

Er enghraifft, os oes gennym ffeil Python sy'n cynnwys cod i gyfrifo swm y 100
rhif cyntaf, gallwn allbynnu'r canlyniad i ffeil `cyfanswm_100_cyntaf.tex`:

{% highlight python %}
cyfanswm = 0
for i in range(101):
    cyfanswm += i

with open('tex/cyfanswm_100_cyntaf.tex', 'w') as f:
    f.write(cyfanswm)
{% endhighlight %}

Nawr o fewn ein ffeil `pennod-1.tex` gallwn fewnbynnu'r allbwn yn uniongyrchol,
sy'n osgoi unrhyw gamgymeriadau ac yn sicrhau bod y canlyniadau yn cyfateb a'r
cod diweddaraf:

{% highlight tex %}
Byddwn yn archwilio symiau cyfanrifau.

Swm y 100 cyfanrif cyntaf yw \input{cyfanswm_100_cyntaf.tex}.
{% endhighlight %}

Ar gyfer Python (bydd gan ieithoedd eraill pethau tebyg):

 + I allbynnu tablau, yn llyfrgell ddefnyddiol yw [pandas](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.to_latex.html)
 + I allbynnu hafaliadau cymhleth, yn llyfrgell ddefnyddiol yw [sympy](https://docs.sympy.org/latest/tutorial/printing.html)

Mae'r rhain yn allbynnu i mewn i gystrawen LaTeX yn uniongyrchol!

---

# Cyfeiriadau

+ "Research software development", Vincent Knight,
  
  [https://vknight.org/rsd/](https://vknight.org/rsd/)
