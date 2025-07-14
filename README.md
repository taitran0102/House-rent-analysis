# Project Summary
### Introduction
A Directed Graphical Model (often called a Bayesian Network) consists of a joint probability distribution and a directed acyclic graph (DAG), such that the joint distribution can be factorized according to the structure of the DAG. For example, if we have the DAG:
<p align="center">
  <img src="https://github.com/taitran0102/House-price-analysis/blob/main/intro_DAG.png" alt="Directed Graphical Models" width="250"/>
</p>

Then the joint probability distribution factorizes as: `p(x,y,z)=p(x)p(y|x)p(z|x,y)`. That is, the joint probability distribution is factorized into the product of conditional probability distributions. Specifically, for each variable at the end of an arrow (i.e., a child node), its distribution is conditioned on the variables at the start of the arrows pointing to it (i.e., its parents). For any variable with no incoming arrows (i.e., no parents), its distribution appears as a marginal distribution. 

Directed Graphical Models are useful for reasoning, decision-making, and prediction tasks. In this project, I will select a directed graphical model from a dataset to analyze relationships, extract meaningful insights, and make predictions.

### Key takeaways
The dataset used in this project is integrated within the `LinRegInteractive` package and is described as follows:
```{r}
# R code to see the dataset description
library(LinRegInteractive)
data(munichrent03)
?munichrent03
```
Sample of 2,053 appartments from the data collected for the preparation of the Munich rent index 2003. A data frame with 2,053 observations on the following 12 variables:
- `rent`: Net rent in EUR (numeric).
- `rentsqm`: Net rent per square meter in EUR (numeric).
- `area`: Floor area in square meters (numeric).
- `rooms`: Number of rooms (numeric).
- `yearc`: Year of construction (numeric).
- `bathextra`: High quality equipment in the bathroom? (Factor)
- `bathtile` : Bathroom tiled?(Factor)
- `cheating` : Central heating available? (Factor)
- `district`: Urban district where the apartment is located. (Factor with 25 levels)
- `location`: Quality of location. Ordered factor with levels "normal", "good" and "top".
- `upkitchen`: Upscale equipment in kitchen? (Factor)
- `wwater` : Hot water supply available? (Factor)

Source: [https://data.ub.uni-muenchen.de/2/](https://data.ub.uni-muenchen.de/2/), for more details see the [Package description](https://cran.r-project.org/web/packages/LinRegInteractive/LinRegInteractive.pdf) (page 26).



From the description of this dataset, we can come up with several business questions, such as: What factors (direct or indirect) influence the rent? Which district has the highest rental prices? If a house is equipped with premium amenities, what price segment is it most likely to belong to? and so on. These business questions can be addressed through common data analysis methods, including data exploration, descriptive statistics, and visual tools that reveal patterns and relationships. 

A Directed Graphical Model, on the other hand, can help us explore conditional independence relationships between variables. For example, we may want to know whether the number of rooms in a house is related to its rental price when the living area is already known. Beyond that, if we have questions that involve certain known conditions, the model allows us to compute conditional probabilities to answer them. This process is known as querying the model.

This project explores the factors that influence rental prices in Munich and makes predictions under given conditions using Directed Graphical Models. The workflow mainly uses `R`, since the project involves only simple data exploration and processing tasks that `R` handles efficiently. Moreover, in the domain of Bayesian Networks, numerous researchers have contributed R packages that greatly facilitate modeling, inference, and visualization. The full `R` code is provided in the file [`Munich_BN.ipynb`](https://github.com/taitran0102/House-price-analysis/blob/main/Munich_BN.ipynb), with the key steps highlighted in this [Report](https://github.com/taitran0102/House-rent-analysis/blob/main/Rmd/Munich_BN.pdf). In the end, we arrive at the following result:
<p align="center">
  <img src="https://github.com/taitran0102/House-price-analysis/blob/main/Rmd/figuresBN/unnamed-chunk-30-2.png" alt="Directed Graphical Models" width="500"/>
</p>
<p align="center">
  <em>Directed Acyclic Graph of the Final Model</em>
</p>

The rental price (`rent`) is directly related to the property's area (`area`), year of construction (`year_group`, a grouped version of `yearc` with reduced number of levels), and the presence of high-quality bathroom and upscale kitchen equipment (`bathextra` and `upkitchen`). The remaining factors are indirectly related to the rental price through these direct factors. Given information about the direct factors, the indirect factors become conditionally independent of the rental price (see Section ... of the [Report](https://github.com/taitran0102/House-price-analysis/blob/main/Report/Report.pdf)).

For predicting purpose, we can compute the conditional probability like ... (see Section ... of the [Report](https://github.com/taitran0102/House-rent-analysis/blob/main/Rmd/Munich_BN.pdf) ) which answer for the question ...

