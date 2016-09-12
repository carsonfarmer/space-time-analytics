## Using Weights to Specify Dependence
12 = [(Yi1 - Y-bar1)*(Yi2 - Y-bar2)] / [(Yi1 - Y-bar1)2 * (Yi2 - Y-bar2)2]1/2
display(YouTubeVideo("MQACCcfTpXc"))


* Measured using a **semivariogram** \*
    * Look at pairs of observations separated by a distance $h$
    * Gives us a lot of data — every observation has $n-1$ possible pairs!
    * Illustrates the spatial structure of a variable

</div>
<div class="alert alert-info">
<sup>\*</sup> We usually just call it a variogram (there is a technical difference between the two but for clarity we'll use the term 'variogram' generally)
</div>


## Calculating Semivariance

* For each pair we know the distance between points
    * We measure the similarity of the point pairs (semivariance)
    * We plot the semivariance for a range of distances

</div>
<div class="alert alert-info">
<sup>\*</sup> In practice there is an important distinction between a *theoretical* and an *empirical* variogram — an empirical variogram is used to *fit* a theoretical variogram
</div>


* $N(h)$ denotes the *set* of pairs of observations separated by distance $h$
* $|N(h)|$ is the number of pairs in the set, and
* $h$ is usually an approximate distance implemented using a certain tolerance

$$
\hat\lambda(h) = {1 \over {|N(h)|}} \sum_{(i,j)\in N(h)} (x_i - x_j)^2
$$

</div>
<div class="alert alert-info">
The $\in$ under the summation denotes all $i$,$j$ pairs within the set $N(h)$
</div>


## Meuse Soil Data

* The Maas river bank soil pollution data (Limburg, The Netherlands)
    * Sampled along the Dutch bank of the river Maas (Meuse) north of Maastricht
    * Data are those used in Burrough and McDonnell (1998, pp. 309–311)
* The [version we use here](https://github.com/filipkral/meuse) is a subset of the data provided with the `gstat` and `sp` `R` packages



## Variogram Parts

* Range
    * Distance at which point pairs stop being similar
    * In our `meause` example
        * Nearby samples have similar levels of zinc
        * Means samples separated by less than ... will be similar
        * Beyond 'range' samples are "independent"
* Sill
    * Background level of variance. Sort of a baseline for study region
* Nugget
    * Small scale discontinuity... error?



## Loading/Plotting Data

# Grab the data from online
meuse = pd.read_csv("https://raw.githubusercontent.com/filipkral/meuse/master/meuse.txt")
# Quick plot using simple pandas plotting...
ax = meuse.plot.scatter('x', 'y', c='zinc', s=100).set_axis_off()
# You can see the top of the data frame with:
# meuse.head()
