# Script Presentation

Hello everyone!

Thanks for the invitation and giving me the opportunity to present our current work and the work of the last years. And also to give some perspectives on vegetation modeling and representation shift in this seminar.

I think there is a lot to do in the intersection of Remote Sensing, Environmental Science and Machine learning where a vital exchange and common understanding will be beneficial and push the developments forward. Effectively to address meaningful and real-world applications that have an actual positive impact on a global scale.

## Slide Structure

So, in this presentation I gave the title in three particular segments. I want to address sequentially throughout the next slides.

First, Data-driven vegetation modeling. Why it is a vegetation classification a meaningful and still challenging application and how we use modern machine learning for classifying crop types compared to prior model-driven methods.
Second, how does representation shift arise naturally when doing vegetation classification on a large scale. In a real-world case we typically never want to train and test data from the same location. Still on our experiments benchmarks we do regularly to avoid this issue.
Third, the meta-learning perspective to see our datasets as "datasets-of-datasets". And model-agnostic meta-learning in particular as one algorithm to address this representation shift using few labeled samples (few-shot learning).


# Vegetation Modeling

So, lets start with the first point. Vegetation Modeling.
We can use the sustainable development goals as a general compass on what applications are meaningful to tackle.
And in particular, the classification of vegetation touches three points:
  * Zero hunger via crop type monitoring on a global scale, via estimating cultivated area of one crop and subsequently crop yield to predict food prices and foresee shortages
  * Climate action by observing how vegetation changes over time due to climate change. In particularly, changes in land use and desertification,
  * Life on Land where modern agriculture is essential for human life and an understanding of Biotopes directly connects to animal life.

# Remote Sensing Data in Abundance

Fortunately, today, we have satellite data in abundance.
Three categories of satellite products are available to us.
* There is MODIS for global analyses with a detailed spectral resolution, but fairly coarse spatial resolution. Daily images are available but it is common to take the cloud-free 16-day composite instead.
* For a regional scale, we have Sentinel-2 and Landsat satellites provide data for free at 30 minute resolution every few days with 13 spectral bands.
* On a local scale, we can buy PlanetScope imagery that pushes the limits with 4 spectral bands at (potentially) daily resolution with 4 spectral bands thanks to a swarm of cube-sats.

# Photosynthesis

What we measure at each observation is the reflectance on a several spectral bands.
We know that the chlorophyll of photosynthetically active plants absorb strongly in the red and blue wavelengths while the geometry of the leaf cells scatter light in near infrared wavelengths.
This leads to a red edge effect where the ratio of near infrared reflectance to red absorbtion is a good indicator for photosynthetic activity.
One spectral features that is widely used the the normalized difference vegetation index as shown below.

# Time Series

When we now look at all observations throughout the year, we can can see some class characteristic profiles, as shown here.
Highlighted are are two meadow and corn fields in Germany on PlanetScope data in thick stroke. Other meadow and corn examples are plotted in thinner lines to see that there are differences between these two classes that we can exploit.

# Classification

An intuitive and conventional strategy for this corn-meadow classification would be to design features "mean-NDVI" throughout the year and "max NDVI after September".
We effectively use our domain knowledge about the problem to design good features so that a comparatively generic classifier can separate the data in categories.
