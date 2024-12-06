---
title: Can a doughnut eat a doughnut?
date: 2020-09-26
tags: [MathsLite]
tagline: Translated from the Chinese original
abstract: |
  Two fun problems about doughnuts.
---

Here are two fun problems about doughnuts.

{{< toc >}}

## Problem A

Here are two doughnuts, one of which has a mouth.

{{<centre width="30em">}}
![Figure 1](/posts/2020/can-a-doughnut-eat-a-doughnut/1.png)
**Figure 1** Two doughnuts
{{</centre>}}

Assume that the doughnuts are made of elastic film and can stretch arbitrarily, but cannot be torn. Then, the doughnut with a mouth can eat the other doughnut.

{{<centre width="30em">}}
![Figure 2](/posts/2020/can-a-doughnut-eat-a-doughnut/2.png)
**Figure 2** Open mouth
{{</centre>}}

The small doughnut is now completely swallowed by the large doughnut.

{{<centre width="30em">}}
![Figure 3](/posts/2020/can-a-doughnut-eat-a-doughnut/3.png)
**Figure 3** Swallow doughnut
{{</centre>}}

Now, if the two doughnuts are initially linked together, like this:

{{<centre width="30em">}}
![Figure 4](/posts/2020/can-a-doughnut-eat-a-doughnut/4.png)
**Figure 4** Two doughnuts
{{</centre>}}

Can the doughnut with a mouth still eat the other doughnut?

## Problem B

Doughnuts can be knotted with themselves.

{{<centre width="30em">}}
![Figure 5](/posts/2020/can-a-doughnut-eat-a-doughnut/5.png)
**Figure 5** Knotted doughnut
{{</centre>}}

Moreover, the hole in the doughnut can also be knotted.

{{<centre width="30em">}}
![Figure 6](/posts/2020/can-a-doughnut-eat-a-doughnut/6.png)
**Figure 6** Knotted glass doughnut
{{</centre>}}

This figure looks like a glass jar, but it is essentially still a doughnut.

Of course, the reason for using glass is obvious --- to see the hole in the middle. However, we imagine that this glass can stretch arbitrarily, just like an elastic film.

As topologists know, the two kinds of knots mentioned above cannot be untied, unless the doughnut is torn or the glass is broken.

Now, there is a doughnut with two holes.

{{<centre width="30em">}}
![Figure 7](/posts/2020/can-a-doughnut-eat-a-doughnut/7.png)
**Figure 7** Glass doughnut with two holes
{{</centre>}}

The two holes inside it can be tied together into a knot.

{{<centre width="30em">}}
![Figure 8](/posts/2020/can-a-doughnut-eat-a-doughnut/8.png)
**Figure 8** Tied glass doughnut
{{</centre>}}

So, can this knot be untied?

## Answer A

Can a doughnut eat a doughnut that is wrapped around it?

This seems impossible. We can even write down a 'proof': Consider two circles on the two doughnuts, shown in blue in the figure below.

{{<centre width="30em">}}
![Figure 9](/posts/2020/can-a-doughnut-eat-a-doughnut/9.png)
**Figure 9** Circles on the doughnuts
{{</centre>}}

During elastic transformation, these two circles always lie on the surface of the two doughnuts, and are always linked together. However, if one doughnut eats the other, then these two circles will be separated.

Such separation is impossible. Therefore, we have 'proved' that the doughnut cannot be eaten.

This 'proof' seems very reasonable. But in any case, the doughnut can indeed be eaten:

First, open the mouth of the doughnut, and make an exaggerated expression.

{{<centre width="30em">}}
![Figure 10](/posts/2020/can-a-doughnut-eat-a-doughnut/10.png)
**Figure 10** Open mouth
{{</centre>}}

Then, widen the mouth. At this point, the doughnut is actually only left with two thin bands.

{{<centre width="30em">}}
![Figure 11](/posts/2020/can-a-doughnut-eat-a-doughnut/11.png)
**Figure 11** Widen mouth
{{</centre>}}

Now, we can slowly close the mouth that was opened.

{{<centre width="30em">}}
![Figure 12](/posts/2020/can-a-doughnut-eat-a-doughnut/12.png)
**Figure 12** Close mouth
{{</centre>}}

Finally, the poor little doughnut is entirely swallowed by the large doughnut.

{{<centre width="30em">}}
![Figure 13](/posts/2020/can-a-doughnut-eat-a-doughnut/13.png)
**Figure 13** Swallow doughnut
{{</centre>}}

So, where is the error in the previous 'proof'? Notice that the two blue circles have never been separated throughout the entire process. We mistakenly assumed that the two circles would be separated after the doughnut was eaten, but this is not necessarily the case.

Also, we note that in this process, the large doughnut was flipped inside out, with its previous inner side becoming the current outer side.

So, what if the large doughnut cannot be flipped inside out? Then, the answer will be negative. The reader who knows topology can try to prove this:

{{<block title="Exercise">}}
If the large doughnut is not allowed to be flipped inside out, then the large doughnut cannot eat the small doughnut.
{{</block>}}

## Answer B

Can the knotted glass doughnut be untied?

{{<centre width="30em">}}
![Figure 8](/posts/2020/can-a-doughnut-eat-a-doughnut/8.png)
**Figure 8′** Tied glass doughnut
{{</centre>}}

If the tunnel on the left side was not there, then the answer would be no. But after adding this tunnel, the knot can actually be untied.

The first step is to move the bottom of the knotted tunnel to the wall of the left tunnel.

{{<centre width="30em">}}
![Figure 14](/posts/2020/can-a-doughnut-eat-a-doughnut/14.png)
**Figure 14** First step
{{</centre>}}

Next, keep moving this endpoint along the top of the jar, then to the side.

{{<centre width="30em">}}
![Figure 15](/posts/2020/can-a-doughnut-eat-a-doughnut/15.png)
**Figure 15** Second step
{{</centre>}}

Finally, move the endpoint along the side of the jar, around the back.

{{<centre width="30em">}}
![Figure 16](/posts/2020/can-a-doughnut-eat-a-doughnut/16.png)
**Figure 16** Third step
{{</centre>}}

The knot is now untied.

{{<centre width="30em">}}
![Figure 7](/posts/2020/can-a-doughnut-eat-a-doughnut/7.png)
**Figure 7′** Untied knot
{{</centre>}}

This solution was given by
\[[Bing 1966](#references)\],
who used this example to illustrate that even familiar shapes in three-dimensional space can have very unintuitive properties.

## References

For problem A:

- **Gardner,** M. (1997).
  Pool-ball triangles and other problems.\
  {{<dimmed>}}
  _Penrose tiles to trapdoor ciphers,_ revised edition, 119--136. Mathematical Association of America.
  {{</dimmed>}}

For problem B:

- **Bing,** R. H. (1966).
  Mapping a 3-sphere onto a homotopy 3-sphere.\
  {{<dimmed>}}
  _Topology seminar Wisconsin, 1965,_ 89–99.
  Annals of Mathematics Studies 60.
  {{</dimmed>}}\
  ([doi](https://doi.org/10.1515/9781400882076-012))
  ([zbMATH](https://zbmath.org/0152.22603))
