# Distance, closeness and intuition

## Intro

The purpose of this document is to explore the intuitive idea of a distance between two objects. More precisely, given set $X$ we will look at functions $d : X \times X \rightarrow V$, where *usually* $V=[0, + \infty)$, and in general can be some space with "positive values" (which we will define at a later point). In math and engineering we can use the function $d$ either to impose a structure on set $X$ or as an objective function for some optimization problem. This article will categorize different distance functions $d$ based on their properties, and also explore what structure they induce.

## Structure induced by distance

For every distance function $d : X \times X \rightarrow V$ (again think $V=[0, + \infty)$) we can define balls:

* Open ball: $~~B_r(a)=\{x \in X: d(a,x) < r\}$
* Closed ball: $B_r^{\_}(a)=\{x \in X: d(a, x) \leq r \}$

For example if $X=\mathbb{R}$, then $B_r(a)=(a-r,a+r)$, $B_r^{\_}(a)=[a-r,a+r]$.<br>
Or if $X=\mathbb{R}^2$, then $B_r(a)$ is an open disk with a center $a=(x,y)$ where $x,y\in\mathbb{R}$.

FIXME: write a couple words here about what is a topology and what is the a basis.
FIXME: don't explain the consequences, but state that what you will be looking for is when certain distance functions generate the same basis set and thus the same topology.




## When to distance?

Let's talk about two 

Distance functions arise whenever we want to optimize something, they show up when trying to find the best way 


Every piece needs a target audience, it is very murky who the target audience is for me, but since I have been curious about these topics, I will say that the target audience is me, just from a few months past :). I will assume that you are somewhat familiar with metric spaces and topology but will provide some links to read-up on the topic.

This write-up is trying to achieve two goals:
1. Show in which way the funcion $d:\mathbb{R}\times \mathbb{R} \rightarrow [0, +\infty]$, $d(x,y)=|x-y|^2$ even though is not a metric, does "act" like a metric in some sense.
2. Explore ways in which we can play with metric-like functions to achieve a better separation of things we care about (increase their distance). - is this a thing? Maybe something about manipulating metrics to give different weight to things we care about more.



## Metrics

Metrics are one of the first distance functions that we are introduced to in the study of math. They do lead to very pretty theoremsthat Metrics are functions that tell us about the distance between different objects. There are additional properties added to the metrics to

In information theory we might use metrics or other distance measures to describe how far objects are from each other[^2].

* They are used to describe distances of things from each other (point on a plane, points on a sphere, [how many handshakes you are away from the president](https://en.wikipedia.org/wiki/Six_degrees_of_separation))
* They can be used to show how good an ML model is during training, by showing the distance between the _ground truth_ and the _prediction_ (although functions with [looser properties than metrics might suffice]())

Let's take a set $X$, then a metric is a funcion $d : X \times X \rightarrow [0, +\infty)$ that satisfies the properties[^4]:

**(M1)** $~~d(x,x) = 0$ <br>
**(M2)** $~~d(x,y) \leq d(x,z) + d(z,y) $ (triangle inequality) <br>
**(M3)** $~~d(x,y) = d(y,x)$ (symmetry) <br>
**(M4)** $~~d(x,y) = 0 \implies x = y$ (separation)

The pair $(X, d)$ is called a [metric space](https://en.wikipedia.org/wiki/Metric_space). 

One reason that metrics spaces are liked/useful is that they have many useful properties, e.g.:
* If you take any set $X$ on which a metric $d$ is defined, you can associate a [topological base](https://en.wikipedia.org/wiki/Base_(topology)) as a set of all open balls $B_r(x) = \{y \in X: d(x,y)<r \}$, which defines a [topology](https://en.wikipedia.org/wiki/Topology) on $X$ in which every open set $U=\bigcup_{x\in U} B_{r(x)}(x)$ 
* The [Banach fixed-point theorem](https://en.wikipedia.org/wiki/Banach_fixed-point_theorem)
* Multiple toplogocial properties[^1]

FIXME: some thing about how to modify a metric in a way to get what you want.


Some things we would expect to be metrics, aren't really metrics. For example, $d_{a^2}: \mathbb{R}\times \mathbb{R} \rightarrow [0,+\infty)$ defined as $d_{a^2}(x,y)=|x-y|^2$. You can see that $d_{a^2}$ satisfies (M1), (M3), (M4), however, it fails on (M2) for points $x=0$, $y=1$, $z=\frac{1}{2}$, since $1 \not\leq \frac{1}{4} + \frac{1}{4}=\frac{1}{2}$.

Additionally, there are real life situaions which use the notion of "distance" that are not captured in the metric definition. For example, on Google Maps the distance from $A\rightarrow B$ might be different than the distance $B\rightarrow A$, since Google Maps might provide us with different routes due to one-way streets. Thus the "distance on Google Maps" is not a metric, because it can violate (M3). 

To remedy this mathematicians have introduced multiple concepts to generalize metrics. Since they don't always agree on their naming convention, I will provide the [Wikipedia](https://en.wikipedia.org/wiki/Metric_space#Generalizations_of_metric_spaces) naming convention:
* Metametrics: these drop (M1), thus sometimes $d(x,x)\neq 0$, for more [see here](https://en.wikipedia.org/wiki/Metric_space#Metametrics_or_partial_metrics).
* Semimetrics: these ease (M2), one way this is done (sometimes called $k$-metric[^3]) is to change the triangle inequality to $d(x,y) \leq k \cdot (d(x,z) + d(z,y))$, where $k\in\mathbb{R}$. If $k=1$ we get back to metrics, if $k<1$ the definition does not make sense.
* Quasimetrics: these drop (M3), that is the function does not have to symmetric, for example  the "distance these on Google Maps" metric. You can define left-open balls or right open balls, and a topology using left-open balls.[^geom-prot-datasets]
* Pseudometrics: these drop (M4), thus some points can be 0-distant even though they are different. It is easy to convert a pseudometric to a metric using [metric identification](https://en.wikipedia.org/wiki/Pseudometric_space#Metric_identification) using the equivalence relation $x \sim y \iff d(x,y)=0$.
* Continuity spaces[^4]: These change the domain of $d$ from $[0, +\infty)$ to a value semigroup, and also sometimes drop (M3) and/or (M4), it can be shown that any topological space is a continuity space.

Let's look to see if we can find some space that intuitively should be a metric, but isn't and see if it still meets most of our theorems.

## Semimetrics

As mentioned 

## Continuity spaces

Imagine you are building a drone and you decide that it must carry 0.5kg of payload and stay in the air for 30 minutes. Those are you minimum requirements, and you want to optimize the drone for cost and weight. That is ideally it would cost $0 and weight 0kg, however, that is not possible, so you need to perform some tradeoff betwen cost and weight. So what you need is some distance function from ideal ($0, 0kg) to some proposal A. If this distance function is a metric, semimetric, etc... then you would need to decide which property, the price or weight, do you care more about (is $1 more worth 10g less?) and then find an optimal location. 

In this section I wanted to focus on things that "should be" metrics, but are not (such as $d_{a^2}$), so we will narrow in on the semimetrics. 


Talk about that I care about M2 because I want the most general 

I want to see how Uniform Spaces show all this together nicely. Ie. show that all semimetrics are Uniform Spaces and thus all the Unform Space theorems hold.



[^1]: Nice topological properties of metric spaces: 
    * Metric spaces are [Hausdorf($T_2$)](https://en.wikipedia.org/wiki/Hausdorff_space)
    * [compactness](https://en.wikipedia.org/wiki/Compact_space) $\implies$ [complete](https://en.wikipedia.org/wiki/Complete_metric_space)
    * [compactness](https://en.wikipedia.org/wiki/Compact_space) $\iff$ [totally bounded](https://en.wikipedia.org/wiki/Totally_bounded_space) and [complete](https://en.wikipedia.org/wiki/Complete_metric_space)
    * The following notions are equivalent: [compactness](https://en.wikipedia.org/wiki/Compact_space), [sequential compactness](https://en.wikipedia.org/wiki/Sequentially_compact_space), [limit point compactness](https://en.wikipedia.org/wiki/Limit_point_compact), [countable compactness](https://en.wikipedia.org/wiki/Countably_compact_space).

[^2]: A. K. Seda and P. Hitzler, ["Generalized Distance Functions in the Theory of Computation"](https://people.cs.ksu.edu/~hitzler/pub/SH07CJ.pdf) in The Computer Journal, vol. 53, no. 4, pp. 443-464, May 2010, doi: 10.1093/comjnl/bxm108. 
[^3]: Šostak, A. [Some remarks on fuzzy k-pseudometric spaces](https://www.pmf.ni.ac.rs/filomat-content/2018/32-10/32-10-16-6697.pdf). Filomat 2017, 32, 3567–3580. 
[^4]: Kopperman, R. (1988) All topologies come from generalized metrics. American Mathematical Monthly, 95, 89–97.

[^5]: Inframetric, Round Trip Delay  https://citeseerx.ist.psu.edu/doc/10.1.1.113.6748
[^geom-prot-dataset]: Stojmirovic, A. (2005) Ph.D thesis, [Quasi-metrics, Similarities and searches: aspects of geometry of protein datasets](https://arxiv.org/pdf/0810.5407.pdf)


Other notes:

https://en.wikipedia.org/wiki/Arzel%C3%A0%E2%80%93Ascoli_theorem

Semi metric proof of Ascoli_theorem
https://arxiv.org/abs/0807.3377



Big picture notes, and ideas:
1. Pareto frontier  
   1. We want to show that when comparing two things you need an order? If you don't what do you end up having? I want to show Pareto frontier in a new light...
   1. Show how to manipulate a metric to get someting that we care about more.
2. I want to show that |a-b|^2 is a as good as a metric for all practical puproses.


Other thoughts:
If we can convert a pseudometric to a metric using metric identification, and uniform spaces are defined using pseudometrics on semivalue groups, does that not mean that we could define uniform spaces using semivalue groups on generalized metrics (and not on generalized semigroups)

## Thoughts Dec 1st 2023

So... the thing is the distance function/metric defines the space (how the space behaves), so we can use it (or maybe some other function or something else to define the space), but then the question is about the objective function, and not  **** the metric... so maybe this whole thing doesn't make sense???

If the metric is there to define the space, and then we just optimize from $\mathbb{R}^n$, then what is the point? We can define the shape of the space however, and then we ?embed? the space in $\mathbb{R}^n$ ?

I guess metric functions can be objective functions(right?), but when are they?
When are metric balls convex  

## Thoughts Dec 2nd 2023

Check what spaces are possible with the possible distance functions for instace directed graph..

One idea for an example is looking at color distances in RGB/HSV or some color spaces since RGB is on a cube amd HSV is on a cylinder.

HyperRogue discord about geometry.

d(u, v) = ||u - v||

||a + b|| <= ||a|| + ||b||

d(a1,a2) = |x1-x2| + |y1-y2|

One distinction for different types of objects, for instance:

1. Finite sets (something like edges and graphss)
    Can you differentiate on them?
    I mean I guess you can