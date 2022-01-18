### Work in Progress (Part 1 is complete, other parts will be added soon) ###

<h1> Modelling Forest Fires </h1>

This is a difficult regression task, where the aim is to predict the burned area of forest fires, in the northeast region of Portugal, by using meteorological and other data. 
The dataset can be found at UCI Machine Learning Repository:-
https://archive.ics.uci.edu/ml/datasets/forest+fires

Dataset and attribute Information can be found in info.md file in the main folder.


The output variable 'area' is very skewed towards 0.0, thus we will have to try different approaches/techniques to find a suitable model. The different folders will contain different approaches applied to our dataset and each folder consists of its own readme.md file describing the respective approach.

* Using log(1+x) transformation on the outcome variable
* Using Poisson Zero Inflated Model and rounding off(discretizing) the outcome variable, 
* Discretizing outcome variable into categorical variable by binning them and then using classification methods, 
* Using 2 separate models or a mixture model - With 0 values and other without 0's (Separate models is easier than mixture modelling), 
* Using some advanced upsampling/downsampling techniques like SmoteR (https://core.ac.uk/download/pdf/29202178.pdf) or SMOGN (http://proceedings.mlr.press/v74/branco17a/branco17a.pdf.)
* Using an advanced technique like Density-based Weighting (https://link.springer.com/article/10.1007/s10994-021-06023-5)
* Tweedie Zero gradient boosting for extremely unbalanced zero inflated data (https://www.math.mcgill.ca/yyang/resources/papers/CSSC_EMTboost.pdf)
* Other methods like adding features, outlier treatment, different scaling etc can also be tried to see their effect.

For evaluation we will also be using Regression Error Characteristic (REC) curves, for which we will define a function as it isn't available in sklearn.
Link for the research paper on REC curve by Jinbo Bi and Kristin P. Bennett :-
* http://homepages.rpi.edu/~bennek/papers/rec.pdf


---------------------------------------------------

Relevant Papers:

[Cortez and Morais, 2007] P. Cortez and A. Morais. A Data Mining Approach to Predict Forest Fires using Meteorological Data. In J. Neves, M. F. Santos and J. Machado Eds., New Trends in Artificial Intelligence, Proceedings of the 13th EPIA 2007 - Portuguese Conference on Artificial Intelligence, December, Guimarães, Portugal, pp. 512-523, 2007. APPIA, ISBN-13 978-989-95618-0-9.


Citation Request:

This dataset is public available for research. The details are described in [Cortez and Morais, 2007].
Please include this citation if you plan to use this database:
[Cortez and Morais, 2007] P. Cortez and A. Morais. A Data Mining Approach to Predict Forest Fires using Meteorological Data. In J. Neves, M. F. Santos and J. Machado Eds., New Trends in Artificial Intelligence, Proceedings of the 13th EPIA 2007 - Portuguese Conference on Artificial Intelligence, December, Guimarães, Portugal, pp. 512-523, 2007. APPIA, ISBN-13 978-989-95618-0-9.
