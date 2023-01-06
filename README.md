# Replication: Do Women Give Up Competing More Easily? Evidence from the Lab and the Dutch Math Olympiad
##Author of the paper: Thomas Buser & Huaiping Yuan
##Journal and link: American Economic Journal: Applied Economics 2019, 11(3): 225–252 https://doi.org/10.1257/app.20170160 

This paper mainly answers the question: Do women give up competing more easily? The authors use lab experiments and field data from the Dutch Math Olympiad to conduct this research. My replication focuses on the field study part. **In this part, the authors use the field data from the Dutch Math Olympiad to determine whether the gender difference in the reaction to losing carries over to the field**.

This paper takes the binary decision of whether to compete again one year later as the outcome measure. This study uses anonymized data for all participants in the 2010–2014 Olympiads, including their score, gender, and whether they participated again the year after. The data present a **sharp regression discontinuity design** because winning and losing depends on a strict cutoff (the threshold score). **Comparing the subsequent participation choices of individuals just below and just above the cutoff makes it possible to estimate the causal effect of losing versus winning on the likelihood of participating again one year later**. In particular, this paper is interested in the gender difference in this effect.

####Regression results
In this thesis, I replicated the results of Figure 2,3,4 of the paper. Firstly, I conducted a set of estimates. I made subsets of boys and girls separately and estimate the following equation and present regression discontinuity results separately for each gender:

$$
Y_i = \alpha + \beta_1T_i + \beta_2NetScore_i +  \beta_3 NetScore_i \cdot T_i + \epsilon_i(1),
$$

where Y is a binary indicator for participating again a year later, T is a binary indicator for scoring above the cutoff (that is, making the second round). 

$$
Y_i = \alpha + \beta_1T_i + \beta_2 F_i + \beta_3NetScore_i +  \beta_4 NetScore_i \cdot T_i + \beta_5 F_i \cdot T_i + \beta_6 F_i \cdot NetScore_i + \epsilon_i(2),
$$
to learn the gender difference, I added F as a binary indicator for being female and an interaction variable of F and T, which estimates the gender difference in the reaction to loss. I also interacted the NetScore with the cutoff indicator T to allow for different slopes left and right of the cutoff. And the interaction of NetScore and T with F to allow for different slopes for each gender.

**To remove unobserved heterogeneity between students from different schools, I introduced school fixed effects, and I also clustered the standard errors at the score level to account for situations where observations within each score group are not independently and identically distributed**. In practice, I estimated the following equation:

$$
Y_i = \alpha + \beta_1T_i + \beta_2NetScore_i +  \beta_3 NetScore_i \cdot T_i + \gamma_s + \epsilon_i(3),
$$

$$
Y_i = \alpha + \beta_1T_i + \beta_2 F_i + \beta_3NetScore_i +  \beta_4 NetScore_i \cdot T_i + \beta_5 F_i \cdot T_i + \beta_6 F_i \cdot NetScore_i + \gamma_s + \epsilon_i(4).
$$
