java c
Assignment   6
EMATM0061:   Statistical   Computing and   Empirical   Methods, TB1,   2024
Introduction
This   is the   sixth assignment   for   Statistical   Computing and   Empirical   Methods. This   assignment is mainly based   on   Lectures   15,   16, and   17   (see the   Blackboard).
You   can optionally submit this assignment by   13:00   Monday   4th   November.   This   will help us understand your work but   will   not count   towards   your   final   grade.   The   submission point   can be found under the   assignment tab   at   Blackboards   (click   the         title “Assignment   06”   and upload   a pdf file).
Load   packages
Some   of   the   questions in this assignment require the tidyverse   package.   If it   hasn’t   been installed   on your computer, please   use “install.packages()”   to   install   them   first.
To load the tidyverse   package:library(tidyverse)
1. The   Gaussian   distribution
Gaussian random variables   are an   important family   of continuous random   variables.
In this assignment, we will first explore   several   properties   of the   Gaussian   distribution.
Use the help function to look   up the   following   four   functions:   “dnorm()”,   “pnorm()”,   “qnorm()” and “rnorm()”   .
Also, the probability density function   of a   Gaussian   random variable was   introduced   in   Lecture   14.
(Q1)   Generate a plot which displays the probability   density function   for three      Gaussian random variables X1   ∼ N(μ1,   σ1(2)), X2   ∼ N(μ2,   σ2(2)), and   X3   ∼   N(μ3,   σ3(2))   with μ1   = μ2   = μ3   = 1   and σ1(2)   = 1,   σ2(2)   = 2,   σ3(2)   =   3.
Your plot   should look like   this:
   
(Q2)   Generate a plot which displays the cumulative   distribution function   for   three   Gaussian random variables X1   ∼   N(μ1,   σ1(2)), X2   ∼   N(μ2,   σ2(2)),   and X3   ∼   N(μ3,   σ3(2))   with μ1   =   μ2   =   μ3   =   1   and   σ1(2)   =   1,   σ2(2)   =   2,   σ3(2)   =   3.
(Q3)   Generate a plot for the quantile   function   for the   same three   Gaussian   distributions   as above.   Describe the relationship between the   quantile   function   and   the   cumulative   distribution function.
(Q4)
Now use “rnorm()” to generate a   random   independent   and   identically   distributed   sequence z1,   ⋯   ,zn   ∼   N(0,1)   so that each zi   ∼   N(0,1)   has standard   Gaussian distribution.   Set n   =   100.   Make sure your   code is reproducible by   using the “set.seed()” function.   Store your random sample   in   a vector   called   ““standardGaussianSample””   .
(Q5)
Suppose z   ∼   N(0,1)   is a   Gaussian   random variable. Take α,   β   ∈   ℝ   and let   W:   Ω   →   ℝ   be the random variable given by W   =   αz   +   β   . Then W   is   also   a   Gaussian   random   variable. We will use this fact to   create   samples of   Gaussian   random   variables   from   samples   of standard   Gaussian random variables.
Use your   existing sample   stored   in “standardGaussianSample” to generate a   new   sample   of   the   form   y1,   ⋯   ,   yn   ∼   N(1,3)   with expectation μ   =   1   and population variance   σ   2   =   3.   The   i-th   observation   in this sample   should be   of the   form   yi   =   α   ⋅   zi   +   β,   for   appropriately   chosen   α,   β   ∈   ℝ, where zi   is the   i-th   observation   in the sample “standardGaussianSample”.   Store the generated   sample   of y1,   ⋯   ,   yn   in   a   vector called “mean1Var3GaussianSampleA”   .   So to answer this   question you   need   to   decide the value   of α   and β,   such that   yi   has the   required   expectation and   variance.
(Q6)
Reset the random seed to the   same value   as the   one you   used   in   (Q4)   using   the   “set.seed()” function and generate an   i.i.d.   sample   of the   form   y1,   ⋯   ,   yn   ∼   N(1,3)         using the “rnorm()” function   (instead   of   using “standardGaussianSample”).   Store   this sample in a vector   called “mean1Var3GaussianSampleB”   .   Are   the   entries   of   the   vectors “mean1Var3GaussianSampleA”   and “mean1Var3GaussianSampleB” the   same?
(Q7)
Now generate   a graph which includes both   a      for your   sample   “mean1Var3GaussianSampleA” and a plot of   the population   density   (the   probability   density function) generated using “dnorm()”   . You   can   also   include two   vertical   lines   which   display respectively the population mean and   the   sample   mean.
Some guidance for creating the   plot:   It would   be   helpful to   look   at   the   example provided in Section   3.3(Q4) of   Assignment   5. You may   want   to   use   the   “geom_density()”   and “geom_vline()” functions.   代 写EMATM0061: Statistical Computing and Empirical Methods, TB1, 2024 Assignment 6
代做程序编程语言In particular, both “geom_density()”   and “geom_line()” have an   argument   called “data” that you   may   want   to   explore.
Also, you   can specify your own   color by using the   “scale_color_manual”   and   your   own line type by “scale_linetype_manual”   .
Your plot   should look similar to the   following:
   
(Q8)   (*)
This   is an   optional   question   (*).   If   you are   short   on time you   can work   on   the   other   questions first.
Recall that for a   random variable X:   Ω   →   ℝ   is   said to be   Gaussian with   expectation μ   and variance σ   2   (i.e.,   X   ∼   N(μ,   σ   2)) if for   any   a,   b   ∈   ℝ, we have

Suppose Z ~ N(0,1) is a Gaussian random variable. Take   α, β ∈ R and let W:   Ω → R   be the random variable given by W   =   αZ   +   β.   In   (Q5) we have assumed that   W   constructed   in this way is a   Gaussian random   variable.   Now,   apply   a   change   of         variables to show that W   is   a   Gaussian random variable with   expectation β   and   variance   α   2.
Hint: can you derive the expression of ℙ(c   ≤   W   ≤   d)?
2.   Location estimators with   Gaussian data
In this   question we   compare two estimators for   the   population   mean μ0   in   a
Gaussian   setting in which we have   independent and   identically   distributed   data   X1,   ⋯   ,Xn   ∼   N(μ0,   σ0(2)).
The following   code generates a   data frame   consisting   of   the   mean   squared   error   of   the sample median   as an   estimator   of   μ0.set.seed(0)num_trials_per_sample_size <- 1000min_sample_size <- 30max_sample_size <- 500sample_size_inc <- 5mu_0 <- 1sigma_0 <- 3# create data frame. of all pairs of sample_size and trialsimulation_df<-crossing(trial=seq(num_trials_per_sample_size),sample_size=seq(min_sample_size,max_sample_size,sample_size_inc)) %>%# simulate sequences of Gaussian random variablesmutate(simulation=pmap(.l=list(trial,sample_size),.f=~rnorm(.y,mean=mu_0,sd=sigma_0))) %>%# compute the sample mediansmutate(sample_md=map_dbl(.x=simulation,.f=median)) %>%group_by(sample_size) %>%summarise(msq_error_md=mean((sample_md-mu_0)^2))
(Q1)   Derive the mathematical expression for the   population   median   of a   Gaussian random variable xi   ~ N(μ0,   σ0(2)).
(Q2)
Modify the above   code to include   estimates   of the mean square   error   of the   sample   mean. Your data frame. “simulation_df” should   have   a   new   column   called   “msq_error_mn” which   estimates the   mean   squared   error   of   the   sample mean as an   estimator   of   μ0.
Then generate a plot which includes   both   the   mean   square   error   of   the   sample   mean   and the   sample   median as a function   of   the   sample   size.
Your plot   might look like the   following:
   
3.   (**) The   law of large   numbers and   Hoeffding’s inequality
This   is an   optional   question.   . You   can answer the   other   questions first   before   working   on this   one.
(Q1)   Prove the following version   of   the weak law   of large   numbers.
Theorem   (A law   of large numbers).   Let x:   Ω   →   ℝ   be a random variable with a
well-behaved   expectation μ   :   =   E(x)   and variance σ   2   :   =   Var(x). Let x1,   ⋯   ,xn:   Ω   →   ℝ   be a sequence of independent copies   of   x. Then   for   all   E   >   0,

You may want to begin by looking   up the   Chebyshev’s   inequality:   For   any   random   variable z   with finite   expectation E(z)   and variance Var(z), we have ℙ(|z   − E(z)|   ≥   t)   ≤   Var(z)/t2   for any given number   t   >   0.
(Comparing   the   weak   law   of   large   numbers   with   Hoeffding’s   inequality):   Below is   some further information about   Hoeffding’s inequality.   Hoeffding’s   inequality   is the following important   result:
Theorem   (Hoeffding).   Let x:   Ω   →   [0,1]   be a bounded   random variable with a well-   behaved   expectation μ   :   =   E(x).   Let x1,   ⋯   ,xn:   Ω   →   ℝ   be a sequence   of independent         copies of   x. Then   for   all   E   >   0,

Please note that in the   Hoeffding Theorem we   additionally   assume x   to be   bounded.
We   can view   Hoeffding’s inequality as a variant   of   the law   of large   numbers.
However,   Hoeffding’s inequality gives   us information about the   rate   of   convergence.   In particular, the   sample   average for bounded random variables   converges exponentially   fast to its   expectation.
Hoeffding’s   inequality is a precursor to Vapnik-Chervonekis theory   which   serves   as   a foundation for the theory   of Statistical   Machine   Learning.




   





         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
