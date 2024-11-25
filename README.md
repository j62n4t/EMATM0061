java c
Assignment 3 
EMATM0061: Statistical   Computing and   Empirical   Methods, TB1,   2024
Introduction 
Create an R Markdown for the assignment 
First, it is recommended that you   create a   single   R   Markdown   document   to   include         your solutions, with headings   created by heading   codes   such as   “##   1.1   (Q1)”,   “##   3   (Q1)”,   etc.
It is a good practice to   use   R   Markdown to   organise   your   code   and   results.   For example,you   can   start   with   the   template   called   Assignment02_TEMPLATE.Rmd   which can be downloaded via   Blackboard.
You can   optionally hand in this assignment   by   13:00   Monday   7   October.   This will help us understand your work but will not   count towards your   final   grade.   If   you want to hand in the assignment, please   upload   a   PDF   file   containing   your   answers   to   Blackboards   (click on the “Assignment 03” under the   assignment tab).   There   is   no requirement on how the   PDF file is   generated.   One   example   is to   choose   the   output         of R-markdown as   PDF   (which may require   LaTex to be   installed   in your   computer).   Another example is to choose a   html   output   at   R-markdown   and   convert   the   html file into a   PDF file.   If   you have multiple   PDF   files,   please   combine   them   into   a   single   PDF file before the   submission. 
Load packages 
We need to load two packages, namely   “Stat2Data”   and   “tidyverse”,   before answering the questions.   If   they haven’t been installed   on your   computer,   please   use   “install.packages()” to   install   them   first. 
1.                Load the tidyverse package:
library(tidyverse)
2.                Load the   Stat2Data package and then the   dataset   Hawks:
library(Stat2Data)
data("Hawks")
1. Visualisation 
This part is mainly about visualisation using   ggplot2.   It   covers   mainly   Lecture   7.   We are going to use the “Hawks”   dataset   that   was   used   last   week.
(Q1) After the dataset Stat2Data was loaded   sucesfully,   create   a   smaller   dataset   with the code   below.
hawksSmall<-
drop_na(select(Hawks,Age,Day,Month,Year,CaptureTime,Species,Wing,Weight   ,Tail))Use the dim() function to check   how   many   rows   and   how   many   columns   in   hawksSmall. Then use the head() function to   display the   first   5   rows   of   the   hawksSmal. The result should   look like   this:
## 
Age 
Day 
Month 
Year 
CaptureTime 
Species 
Wing 
Weight Tail 
## 1 
I 
19 
9 
1992 
13:30 
RT 
385 
920 219 
## 2 
I 
22 
9 
1992 
10:30 
RT 
376 
930 221 
## 3 
I 
23 
9 
1992 
12:45 
RT 
381 
990 235 
## 4 
I 
23 
9 
1992 
10:50 
CH 
265 
470 220 
## 5 
I 
27 
9 
1992 
11:15 
SS 
205 
170 157 
(Q2) Use acombination of   the functions   “ggplot()” and   “geom_histogram”   to   create a histogram plot of   the weights of Hawks within   the   hawksSmall   data   frame   with   bin   widths of 10. Your result should look   something   like   the   following.

(Q3) Similar to   (Q2),use the “geom_density()” function to create   two   density   plots   of   the tail lengths of Hawks within the hawksSmall   data frame,   with   parameters “adjust=0.5” and “adjust=2”, respectively. Your results   should   look like   this:

Can you explain the difference between the two   plots?   How   many   modes   does   the   distribution   of Hawk tail lengths have in   each of   the plots.
(Q4) Based   on the answer from   (Q3),   can you   create the following   plot?

(Q5) Violin plot:
Use the ggplot and geom_violin() functions to   create the   following   violin   plot   for   the   three species.

(Q6) Scatter plot
Generate a plot similar to the following   plot   using   the   ggplot()   and   geom_point()   functions.
1.                How many aesthetics are present within the   following   plot?
2.               What are the glyphs within this   plot?
3.             What   are the   visual   cues   being   used   within   this   plot?

(Q7) Trend lines and   facet   wraps:
Generate the following plot using the ggplot(),   geom_point(),   geom_smooth()   and   facet_wrap() functions.   Note that in the facet plot, the   three   panels   use   different            scales.
1.             What   are the   visual   cues   being   used   within   this   plot?
2.                Based   on the plot below, what can we say   about   the   relationship   between   the   weight of   the hawks and their   tail   lengths?

(Q8) Adding annotations
First,   compute the “Weight” and the “Tail”   of   the   heaviest   hawk   in the   dataset.   You   can use filter() and select()   function to   select   proper   data.
Second, reuse the code that you create   from   Q(3),   adding   anarrow   and   an annotation to indicate the heaviest hawk. Your result   should   look   similar   to   this:

2. Finite probability spaces 
Now, let’s move on to consider   probability   on   finite   sample   spaces,   which   is   covered   in   Lecture   8.
2.1 Sampling with replacement 
Recall that for positive integers n   and k,  gives   the   number   of subsets   of   size k   from a   set   of n   objects.You can   compute this number straightforwardly within   “R” via the   choose   function “choose()” .   For example, if   we want to compute the   number   of different   subsets   of      size   3 from a collection of size   8 we   would   compute:
choose(8,3)
##   [1]   56
Suppose we have a bag containing   10   spheres. This   includes   3   red   spheres   and   7   blue spheres.
Let’s suppose that we draw a   sphere   at   random   from the   bag   (all   spheres   have   equal probability of   being drawn). We record its   colour   and   then   return   the   sphere   to   the   bag. This process is repeated   22 times.   This   is   an   example   of sampling with replacement since the spheres are replaced   after   each   draw.
(Q1) Write down a mathematical expression   for   the   probability   that   Z   out   of   the   22   selections were red   spheres   (here Z    ∈   {0,   1, ⋯ ,22}).
You can try writing down your mathematical   expression   using   “LaTex”   code   in your   R markdown file, making use   of   the   LaTex functions   “binom{”{}}   and   “frac{”{}}.   For         information about writing mathematical formulae in   Rmarkdown   documents,   find            illustrative examples in “Assignment_R
MarkdownMathformulasandSymbolsExamples.rmd”   (under the resource list tab on   blackboard   course webpage) or visit:
https://bookdown.org/yihui/bookdown/markdown-extensions-by- bookdown.html#equations 
(Q2) Next write an   R function called   “prob_red_spheres()” which takes   Z   as   an argument and   computes the probability that Z   out of a total   of   the   22 balls   selected   are   red.
Test your function as   follows:
prob_red_spheres(10)
##   [1] 0.05285129
(Q3) Generate a data frame. called   “prob_by_num_reds” with   two   columns “num_reds” and   “prob”   . The “num_reds”   column should   contain   numbers   1 through   22 and the “prob”   column should give   the   associated   probability   of selecting that many reds out of a total   number   of 22   selections.   Display the first   3 rows   of   your   data   frame.:
prob_by_num_reds %>% head(3)
##         num_reds                        prob
## 1                        1   0.003686403
##   2                        2 0.016588812
##   3                        3 0.047396606(Q4) Now use the “geom_line()” function within the   “ggplot2”   library,   in   conjunction   with your data frame. to   display a plot   of   the   probability   as   a   function   of   the   number         of reds.
Your plot should look   as   follows:

(Q5) 
Next we shall explore the “sample()”   function within   R.   Let’s   suppose we   want   to   simulate a random experiment in which we   sample   with   replacement   from   a
collection of 10   objects, and repeat this   process   22   times.
We   can   do this by   calling:
sample(10, 22,   replace=TRUE)
##      [1]      5    8      6   10      4      5      3      1      6      5   10      9      4      5      7      6      7      7   10      1      5
5
Try this out for yourself. The output   should   be   a vector   of length   22   consisting entirely of numbers between   1 and   10.   Since this is   sampling with   replacements   and   the number of samples exceeds the number   of   elements, there代 写EMATM0061: Statistical Computing and Empirical Methods, TB1, 2024 Assignment 3Processing
代做程序编程语言   will   be   repetitions. 
Try rerunning the function. You probably get   a   different   sample.   This   is to   be expected, and   even desirable, since the   function simulates   a   random   sample.
However, the fact that we get a different   answer   everytime   we   run   the   code   is problematic from the perspective of   reproducibility. To avoid   this   process   we   can   set a random seed via the function   set.seed().   By   doing   so   we   should   get   the   same   output   everytime. Try   the   following   out   for   yourself:
## case 1: Setting the random seed just once
set.seed(0)
for(i in 1:5){
print(sample(100,5,replace=FALSE))
# The result may well differ every time
}
## case 2: Resetting the random seed every time
set.seed(1)
print(sample(100,5,replace=FALSE)) set.seed(1)
print(sample(100,5,replace=FALSE)) set.seed(1)
print(sample(100,5,replace=FALSE))
# The result should not change 
## case 3: reproducing case 1 if we set a random seed at the beginning.
set.seed(0)
for(i in 1:5){
print(sample(100,5,replace=FALSE))
} # The result will be 5 samples exactly the same as in case 1 (why?).
Next, try to understand what the following code   does
itermap <- function(.x,   .f)   {   result   <- list()
for (item in .x)   {
result <- c(result, list(.f(item)))   }
return(result)   }
itermap( c(1,2,3), function(x){ return(c(x,x^2))   }   )
##   [[1]]
##   [1]   1   1   ##
##   [[2]]
##   [1]   2   4   ##
##   [[3]]
##   [1]   3   9
itermap_dbl <- function(.x,   .f)   {   result <- numeric(length(.x))
for (i in 1:length(.x))   {
result[i] <- .f(.x[[i]])   }
return(result)   }
itermap_dbl( c(1,2,3), function(x){ return(x^3)   }   )
##   [1]      1      8   27
The function “itermap” and   “itermap_dbl” defined   above   are   similar to the   “map()”   and   “map_dbl” functions in   R that will be introduced   next week.
We shall now use the “sample()”   to   construct   a   simulation   study   to   explore   the
probability   of selecting z red balls from a bag   of size   10,   with   3   red   and   7   blue   balls,   when sampling   22 balls with replacement.
First set a random seed.   Then   create   a   data   frame   called
“sampling_with_replacement_simulation”   consisting   of   two   columns. The   first   is called   “trial” and   contains numbers   1 through   1000. The second   is   called
“sample_balls” and   corresponds to random samples of size   22   from   a bag   of size   10,   with replacement. We can   do this   as   follows:
num_trials<-1000 # set the number of trials set.seed(0) # set the random seed
sampling_with_replacement_simulation<-data.frame(trial=1:num_trials) %>%
mutate(sample_balls = itermap(.x=trial, function(x){sample(10,22,   replace =   TRUE)}))
# generate collection of num_trials simulations
Now add a new column   called   “num_reds”   such that,   for   each   row,   “num_reds”
contains an integer which gives the number   of items within   the   sample   for that   row   (i.e., the sample represented by the   entry of   the   “sample_balls”   column)   which   are
less than   or equal to three   (assuming that the three   red balls   are   labelled   by   {1,2,3}).   For example, suppose that for some   row   of   the   data   frame,   the   “sample_balls”
column contains a   entry which is the   following   list:
4   10   4   10   8   3   5   5   5   5   10   7   1   2   1   10   5   6   5   7   1   10
Then the corresponding row of   the   “num_reds”   column should   contain   the   number         5, since   5 of   these values are less than   equal   to   3.   You   may   want   to   use   the   functions “mutate()”, “itermap_dbl” and “sum()”. After performing this step,   the   data   frame.	
“sampling_with_replacement_simulation” should contain a new   column   called “num_reds”   .
(Q6) 
Next we shall add a new   column   called   “predicted_prob” to   our   existing   data   frame. “prob_by_num_reds” which gives the number of times (that we   observed the
corresponding number of reds within our simulation)   divided by   the   total   number   of observations. This aims to estimate the probability   of   the   event   that   Z   out   of a
total   of   the   22 balls selected are red   (for Z    =    1,2, ⋯   ,22). We   can   do this as   follows:
num_reds_in_simulation<-sampling_with_replacement_simulation %>% pull(num_reds)
# we extract a vector corresponding to the number of reds in each trial
prob_by_num_reds<-prob_by_num_reds %>%
mutate(predicted_prob=itermap_dbl(.x=num_reds, function(.x)
sum(num_reds_in_simulation==.x))/num_trials)
# add a column which gives the number of trials with a given number of reds
Here “prob_by_num_reds” was initially defined in   (Q3).
(Q7) Finally,   create a plot which compares the results   of   your   simulation   with   your   probability formula.
Your result should look something like   the   plot   below.   Of course,   since this   is   a   random simulation, your result   may well look   slightly   different.
prob_by_num_reds %>%
rename(TheoreticalProbability=prob,
EstimatedProbability=predicted_prob) %>%
ggplot() + geom_line(aes(x=num_reds, y=TheoreticalProbability)) +
geom_line(aes(x=num_reds, y=EstimatedProbability), linetype='dashed')
+
geom_point(aes(x=num_reds, y=EstimatedProbability)) +
theme_bw() + xlab("Number of reds") + ylab("Probabilities")

Try to make sense   of each line   in the   above   code.
Notice the close relationship between probabilities   and long-run   frequency   behaviour. We shall explore this connection   over the   next   few   lectures.
2.2 Sampling without replacement 
This is a more challenging   question,   but the   ideas   from   the   last   question   are   useful   here.Let’s suppose we have a large bag   containing   100   spheres.   There   are   50   red   spheres,   30 blue spheres and   20 green spheres.   Suppose   that   we   sample   10   spheres   from   the      bag without replacement.
(Q1) What is the probability that one   or   more   colours   are   missing   from your
selection?   First aim to answer this question via   a   simulation   study using   ideas   from   the previous   question.
You may want to use the   following   steps:
1.                First set   a   random   seed;
2.                Next set a number   of   trials   (e.g.,   10 or   1000.   Try   this   initially with   a   small   number of simulations.   Increase your number of simulations to about a relatively large number to get a   more   accurate   answer,   once   everything seems to be working well), and a   sample   size   (10);
3.                Now use a combination of   the   functions   “sample()”,   “mutate()”   and
“itermap()” to generate your samples.   Here you are creating   a   sample   of size 10 from a collection of   100 balls   -   the   sampling   is   done without replacement;
4.                Now compute the number of “reds”,   “greens” and   “blues”   in   your   sample   using the “itermap_dbl()” and “mutate()”   functions.
5.             Compute   the   minimum   of   the   three   counts   using   the   “pmin()”   function.   When   this minimum is zero, thenone of   the   three   colours   is   missing.   It   is
recommended   that   you   lookup   the   difference   between “pmin()”   and   “min()”   here;
6.             Compute   the   proportion   of rows   for which   the   minimum   number   of   the   three   counts is   zero.
(Q2) (*Optional) This   question is optional   and   maybe   omitted   if   you   are   short   on   time.
Let’s derive a mathematical expression   for the   probability   that   we   considered   in
(Q1): You can try and use “combinations”   with   (k(n))   to   compute   the   probability
directly.   First aim to   compute the number of subsets   of size   10 from   100 which
either   entirely miss   out one   of   the subsets   Red   =   {1, ⋯ ,50},   Blues   =   {51, ⋯ ,80},
Greens   =   {81, ⋯   ,   100}. Then   compute the number   of subsets   of size   10 from   100
which miss   out two   of   the subsets   Red,   Blues,   Green.   Be careful not   to   double   count some of   these subsets! Once you have   computed   all   such   subsets,   combine   them   with the formula for the total number   of subsets   of size   10   from   a   set   of   100, to compute the probability of missing a   colour. 
Once you have the mathematical expression for   the   probability,   you   can   check   how   close the probability   computed in (Q1) to the   theoretical values.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
