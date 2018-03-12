# Sensitivity Analysis 

## Introduction
In this notebook, I present how to calculate the sensitivity of the response (target)
with respect to the factors (features) based on the ordinary least square (OLS) method.
Sensitivity has various definitions for various contexts.For data sets which show
some levels of linearity, the coefficients of the linear regression model can be used
to identify the influence of each factor on the response.

## Methodology
Let x1,x2, ...,xn be the features and y the response, then a linear
model can be written as 
y=a0+a1*x1 + a2*x2+...+an*xn + error (1)
In this model only the primary features are considered polynomial terms (interaction terms) can 
also be included.

After finding the suitable set of coefficients a_i by minimizing the L2 norm of the error, we
can determine the influence of each parameter by comparing the absolute value of the associated
coefficient. Basically, we calculate dy/dx_i as the sensitivity of y with respect to x_i (other parameters constant).

The sensitivity in this case may be interpreted as one unit of increase in x_i leads to a_i unit
of increase or decrease in y. 

It is important to note that the coefficient matrix must be appropriately standardized so that
all parameters values are in the same range e.g. [0,1].

In the same vein, we can establish a linear model of the form

log(y) = b_0+b_1*log(x_1)+b_2*log(x_2)+...+b_n*log(x_n) + error. (2)

The coefficients in this case, represent the elasticity of the target
to the change in the input parameters. Mathematically,
b_i= (dy/y)/(dx/x). (3)
In other words, 1% of change in the input leads to b_i% of change in the output.
the formula above can be obtained by tkaing the differential form both sides of Eq(2).

## Data 

### source
The data set to be studied is taken from this [website](http://people.sc.fsu.edu/~jburkardt/datasets/regression/x08.txt).
I am not sure whether this data represents real-life situation or not but it serves the 
porpuse of this investigation.

### synopsis
The description provided with the data (see [data file](./data_info.txt)) is sufficient.
The data set lists the number of murder per million population per annum for 20
regions with various populations; for each region, the percentage of population
whose income is less than 5000 dollars and the percentage of unemployment is also specified.
More insights is provided along side the calculations of this note book.

It should be noted that, I do not engage in discussing the validity of these features 
and their relation with respect to each other. One might argue that
people with income less than 5000 dollars are unemployed and receive some sort of
social welfare; hence the two features are not independent. I avoid these considerations.
I take the data as is for the sole purpose of demonstrating how sensitivity can be calculated and interpreted.

## Goal
The goal is to find out which parameter (population, income factor and unemployment) has
the largest influence on the muerder rate.

## Author
Mehdi Paak

## License
This project is licensed under the MIT License - see the [LICENSE](./LICENSE)  file for details.