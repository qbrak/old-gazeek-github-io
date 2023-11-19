# Metrics, closeness and intuition

## Intro

Every piece needs a target audience, it is very murky who the target audience is for me, but since I have been curious about these topics, I will say that the target audience is me, just from a few months past :). I will assume that you are somewhat familiar with metric spaces and topology but will provide some links to read-up on the topic.

This write-up is trying to achieve two goals:
1. Show in which way the funcion $d:\mathbb{R}\times \mathbb{R} \rightarrow [0, +\infty]$, $d(x,y)=|x-y|^2$ even though is not a metric, does "act" like a metric in some sense.
2. Explore ways in which we can play with metric-like functions to achieve a better separation of things we care about (increase their distance).

## Metrics

Let's take a [topological space](https://en.wikipedia.org/wiki/Topological_space) $X$, then a metric is a funcion $d : X \times X \rightarrow [0, +\infty)$ that satisfies the properties [3]:

**(M1)** $~~d(x,y) = 0$ <br>
**(M2)** $~~d(x,y) \leq d(x,z) + d(z,y) $ (triangle inequality) <br>
**(M3)** $~~d(x,y) = d(y,x)$ (symmetry) <br>
**(M4)** $~~d(x,y) = 0 \implies x = y$ (separation)

The pair $(X, d)$ is called a [metric space](https://en.wikipedia.org/wiki/Metric_space). There is a lot that can be said about metric spaces, but here are a few bullet points:

* They are used to describe distances of things from each other (point on a plane, points on a sphere, [how many handshakes you are away from the president](https://en.wikipedia.org/wiki/Six_degrees_of_separation))
* They are "tame" in the sense that many useful theorems hold for them, e.g.:
  * You can define a [topological base](https://en.wikipedia.org/wiki/Base_(topology)) as a set of all open balls $B_r(x) = \{y \in X: d(x,y)<r \}$, which means every open set $U=\bigcup_{x\in U} B_{r(x)}(x)$ 
  * The [Banach fixed-point theorem](https://en.wikipedia.org/wiki/Banach_fixed-point_theorem)
  * The following notions are equivalent: [compactness](https://en.wikipedia.org/wiki/Compact_space), [sequential compactness](https://en.wikipedia.org/wiki/Sequentially_compact_space), [limit point compactness](https://en.wikipedia.org/wiki/Limit_point_compact), [countable compactness](https://en.wikipedia.org/wiki/Countably_compact_space).
  * The following are also true [1]:
    * [compactness](https://en.wikipedia.org/wiki/Compact_space) $\implies$ [complete](https://en.wikipedia.org/wiki/Complete_metric_space)
    * [compactness](https://en.wikipedia.org/wiki/Compact_space) $\iff$ [totally bounded](https://en.wikipedia.org/wiki/Totally_bounded_space) and [complete](https://en.wikipedia.org/wiki/Complete_metric_space)
  * Metric spaces are [Hausdorf($T_2$)](https://en.wikipedia.org/wiki/Hausdorff_space)

Even though metric spaces are so nice, they do not capture all the possible real-life situations where one might want to think of distances between objects. For instance, on Google Maps the distance from $A\rightarrow B$ might be different than the distance $B\rightarrow A$, since Google Maps might provide us with different routes due to one-way streets. Thus the "distance on Google Maps" is not a metric, because it can violate (M3). 

To remedy this mathematicians have introduced concept of generalized metrics, however, they have not agreed on their naming convention. So here I will provide the [Wikipedia](https://en.wikipedia.org/wiki/Metric_space#Generalizations_of_metric_spaces) naming convention:
* Metametrics: these drop (M1), thus sometimes $d(x,x)\neq 0$, for more [see here](https://en.wikipedia.org/wiki/Metric_space#Metametrics_or_partial_metrics).
* Semimetrics: these ease (M2), here the triangle inequality can be either
* Quasimetrics: these drop (M3), that is the function does not have to symmetric, for example  the "distance these on Google Maps" metric.
* Pseudometrics: these drop (M4), thus some points can be 0-distant even though they are different. It is easy to convert a pseudometric to a metric using [metric identification](https://en.wikipedia.org/wiki/Pseudometric_space#Metric_identification) using the equivalence relation $x \sim y \iff d(x,y)=0$. 


Talk about that I care about M2 because I want the most general 

I want to see how Uniform Spaces show all this together nicely. Ie. show that all semimetrics are Uniform Spaces and thus all the Unform Space theorems hold.



[Link text Here](https://link-url-here.org)
[1] https://www.ucl.ac.uk/~ucahad0/3103_handout_2.pdf
[2] Inframetric, Round Trip Delay  https://citeseerx.ist.psu.edu/doc/10.1.1.113.6748
[3] Kopperman, R. (1988) All topologies come from
generalized metrics. American Mathematical Monthly,
95, 89–97.


Other notes:

https://en.wikipedia.org/wiki/Arzel%C3%A0%E2%80%93Ascoli_theorem

Semi metric proof of Ascoli_theorem
https://arxiv.org/abs/0807.3377