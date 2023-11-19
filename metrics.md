# Metrics, closeness and intuition

## Intro

Every piece needs a target audience, it is very murky who the target audience is for me, but since I have been curious about these topics, I will say that the target audience is me, just from a few months past :). I will assume that you are somewhat familiar with metric spaces and topology but will provide some links to read-up on the topic.

This write-up is trying to achieve two goals:
1. Show in which way the funcion $d:\mathbb{R}\times \mathbb{R} \rightarrow [0, +\infty]$, $d(x,y)=|x-y|^2$ even though is not a metric, does "act" like a metric in some sense.
2. Explore ways in which we can play with metric-like functions to achieve a better separation of things we care about (increase their distance). - is this a thing? Maybe something about manipulating metrics to give different weight to things we care about more.

## Metrics

Metrics are functions that tell us about the distance between different objects. There are additional properties added to the metrics to

* They are used to describe distances of things from each other (point on a plane, points on a sphere, [how many handshakes you are away from the president](https://en.wikipedia.org/wiki/Six_degrees_of_separation))
* They can be used to show how good an ML model is during training, by showing the distance between the _ground truth_ and the _prediction_ (although functions with [looser properties than metrics might suffice]())

Let's take a set $X$, then a metric is a funcion $d : X \times X \rightarrow [0, +\infty)$ that satisfies the properties[^3]:

**(M1)** $~~d(x,y) = 0$ <br>
**(M2)** $~~d(x,y) \leq d(x,z) + d(z,y) $ (triangle inequality) <br>
**(M3)** $~~d(x,y) = d(y,x)$ (symmetry) <br>
**(M4)** $~~d(x,y) = 0 \implies x = y$ (separation)

The pair $(X, d)$ is called a [metric space](https://en.wikipedia.org/wiki/Metric_space). 

One reason that metrics spaces are liked/useful is that they have many useful properties, e.g.:
* If you take any set $X$ on which a metric $d$ is defined, you can associate a [topological base](https://en.wikipedia.org/wiki/Base_(topology)) as a set of all open balls $B_r(x) = \{y \in X: d(x,y)<r \}$, which defines a [topology](https://en.wikipedia.org/wiki/Topology) on $X$ in which every open set $U=\bigcup_{x\in U} B_{r(x)}(x)$ 
* The [Banach fixed-point theorem](https://en.wikipedia.org/wiki/Banach_fixed-point_theorem)
* Multiple toplogocial properties[^1]

Some things we would expect to be metrics, aren't really metrics. For example, $d_{a^2}: \mathbb{R}\times \mathbb{R} \rightarrow [0,+\infty)$ defined as $d_{a^2}(x,y)=|x-y|^2$. You can see that $d_{a^2}$ satisfies (M1), (M3), (M4), however, it fails on (M2) for points $x=0$, $y=1$, $z=\frac{1}{2}$, since $1 \not\leq \frac{1}{4} + \frac{1}{4}=\frac{1}{2}$.

Additionally, there are real life situaions which use the notion of "distance" that are not captured in the metric definition. For example, on Google Maps the distance from $A\rightarrow B$ might be different than the distance $B\rightarrow A$, since Google Maps might provide us with different routes due to one-way streets. Thus the "distance on Google Maps" is not a metric, because it can violate (M3). 

To remedy this mathematicians have introduced multiple concepts to generalize metrics. Since they don't always agree on their naming convention, I will provide the [Wikipedia](https://en.wikipedia.org/wiki/Metric_space#Generalizations_of_metric_spaces) naming convention:
* Metametrics: these drop (M1), thus sometimes $d(x,x)\neq 0$, for more [see here](https://en.wikipedia.org/wiki/Metric_space#Metametrics_or_partial_metrics).
* Semimetrics: these ease (M2), one way this is done (sometimes called $k$-metric) is to change the triangle inequality to $d(x,y) \leq k \cdot (d(x,z) + d(z,y))$, where $k\in\mathbb{R}$
* Quasimetrics: these drop (M3), that is the function does not have to symmetric, for example  the "distance these on Google Maps" metric.
* Pseudometrics: these drop (M4), thus some points can be 0-distant even though they are different. It is easy to convert a pseudometric to a metric using [metric identification](https://en.wikipedia.org/wiki/Pseudometric_space#Metric_identification) using the equivalence relation $x \sim y \iff d(x,y)=0$.
* Continuity spaces[^3]: These change the domain of $d$ from $[0, +\infty)$ to a value semigroup, and also sometimes drop (M3) and/or (M4), it can be shown that any topological space is a continuity space.



## Semimetrics

As mentioned 

In this section I wanted to focus on things that "should be" metrics, but are not (such as $d_{a^2}$), so we will narrow in on the semimetrics. 


Talk about that I care about M2 because I want the most general 

I want to see how Uniform Spaces show all this together nicely. Ie. show that all semimetrics are Uniform Spaces and thus all the Unform Space theorems hold.



[Link text Here](https://link-url-here.org)
[^1]: Nice topological properties of metric spaces: 
    * Metric spaces are [Hausdorf($T_2$)](https://en.wikipedia.org/wiki/Hausdorff_space)
    * [compactness](https://en.wikipedia.org/wiki/Compact_space) $\implies$ [complete](https://en.wikipedia.org/wiki/Complete_metric_space)
    * [compactness](https://en.wikipedia.org/wiki/Compact_space) $\iff$ [totally bounded](https://en.wikipedia.org/wiki/Totally_bounded_space) and [complete](https://en.wikipedia.org/wiki/Complete_metric_space)
    * The following notions are equivalent: [compactness](https://en.wikipedia.org/wiki/Compact_space), [sequential compactness](https://en.wikipedia.org/wiki/Sequentially_compact_space), [limit point compactness](https://en.wikipedia.org/wiki/Limit_point_compact), [countable compactness](https://en.wikipedia.org/wiki/Countably_compact_space).


[2] Inframetric, Round Trip Delay  https://citeseerx.ist.psu.edu/doc/10.1.1.113.6748

[^3]: Kopperman, R. (1988) All topologies come from
generalized metrics. American Mathematical Monthly,
95, 89–97.


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