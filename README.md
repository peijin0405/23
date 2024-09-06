# Gender Differences in Competitive Persistence: An Empirical Study Using Dutch Math Olympiad Data
### Replication: Do Women Give Up Competing More Easily? Evidence from the Lab and the Dutch Math Olympiad
Author of the paper: Thomas Buser & Huaiping Yuan
### Journal and link: 
American Economic Journal: Applied Economics 2019, 11(3): 225–252 
https://doi.org/10.1257/app.20170160 

### 1 Background
This paper mainly answers the question: Do women give up competing more easily? The authors use lab experiments and field data from the Dutch Math Olympiad to conduct this research. My replication focuses on the field study part. **In this part, the authors use the field data from the Dutch Math Olympiad to determine whether the gender difference in the reaction to losing carries over to the field**.

This paper takes the binary decision of whether to compete again one year later as the outcome measure. This study uses anonymized data for all participants in the 2010–2014 Olympiads, including their score, gender, and whether they participated again the year after. The data present a **sharp regression discontinuity design** because winning and losing depends on a strict cutoff (the threshold score). **Comparing the subsequent participation choices of individuals just below and just above the cutoff makes it possible to estimate the causal effect of losing versus winning on the likelihood of participating again one year later**. In particular, this paper is interested in the gender difference in this effect.

### 2 Replication and Results
#### 2.1 Regression results
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

According to the results, we could learn that in the non-clustered regression, the coefficient of our interest T is 0.143, which means that those girls who get a score higher than the threshold,  have a 14.3% higher possibility of participating in the competition in the following year. This difference between girls is statistically significant under the confidence level of 95%. In other words, **according to girls who score within 5 points of the cutoff, the effect of losing roughly translates to a 14.3 percent reduction in the likelihood of participating again**.

For boys, the influence of their score results on the following year’s participation is not significant. In regression (2), we could see that the gender difference in the reaction to losing is significant, with a confidence level of 90%. However, these differences are not significant with school fixed effects and standard errors clustered at the score level. 

#### Regression discontinuity graphs

![Panel_A_Regression_Discountinuity_Graphs(linear_fit)](https://user-images.githubusercontent.com/89746479/210925404-bb740938-d8b1-4577-8f9c-145a5c723eb8.png)

![Panel_B_Regression_Discountinuity_Graphs(quadratic_fit)](https://user-images.githubusercontent.com/89746479/210925423-caebe596-6245-4176-8b5b-2f6ead81d14d.png)

![Panel_C_Gender_difference_Linear](https://user-images.githubusercontent.com/89746479/210925019-2e9f5f63-3de3-459e-8b1d-87cb839f03ad.png)

According to Figures 3 and 4, regardless of the degree of the polynomial and the bandwidth used, the discontinuity estimates for the boys are always very close to zero. Unlike the paper's results, **I found the discontinuity estimates for the girl are more distant from zero but fail to reject the null hypothesis that the effect of losing is different between girls who pass the threshold and who do not**. In the estimation of gender difference in the effect of losing in Figure 3, we could see that with the bandwidth to be 7, we could reject the null hypothesis that there is no gender difference in the effect of losing. Even though we can not reach the conclusion that girls are sensitive to the effect of losing, we learn that losing exerts different effects on different genders. According to Figure 2 and the results of regression(2) and regression(3), we could conclude that girls react significantly more strongly to losing than boys.  

#### 3 Robustness Test

![Sensitivity_Analaysis_bandwidth(Linear)](https://user-images.githubusercontent.com/89746479/210925112-7c66eea0-e0d2-46b5-92f2-cf4c32a3b241.png)

![Sensitivity_Analaysis_bandwidth(Quadratic)](https://user-images.githubusercontent.com/89746479/210925130-6cfc466c-27a7-46ff-95db-02d57eddfecb.png)

![06bb6776f31fa769c87a7ebb58c4e3a](https://user-images.githubusercontent.com/89746479/215657969-19dc0e8e-8b8a-43cd-b8c7-27b983d87105.png)

#### 4 Parting Thoughts
In the replication of this paper, I found that the results were statistically significant when I applied non-cluster regression in replicating Figures 3 and 4. If I employ clustered regression, in many cases, I cannot reject the null hypothesis. In the replicated regression, I noticed that the significance of coefficients is diminished with clustered regression. This leads to the reflection of Clustering. In the paper-- *When Should You Adjust Standard Errors for Clustering?*( https://economics.mit.edu/files/13927), the authors discussed this condition of adjusting standard errors for Clustering. They proposed that **Clustering is in essence a design problem, either a sampling design or an experimental design issue**. It is a sampling design issue if sampling follows a two-stage process in which, in the first stage, a subset of clusters is randomly drawn from the population, and in the second stage, units are randomly drawn from the sampled clusters. In this case, the clustering adjustment is justified because there are clusters in the population that we do not see in the sample. And Clustering is an experimental design issue if the assignment is correlated within the clusters. 

In the case of studying the gender difference in losing effect, it is neither a sampling design nor an experimental design issue, since we cannot analogize a student achieving a certain score to a random assignment of scores, and there is no treatment effect in this case. **Therefore, the use of Clustering in this case may lead to underestimation of significance and commit the second type of error in statistical inference**. Last but not least, when I conducted the OLS estimates of the discontinuity for a range of score bandwidths around the cutoff using the linear and quadratic approaches without cluster on “Score”, I found the gender difference in losing effect is statistically significant and generated the conclusion that girls give up competing more easily than boys, as demonstrated by the fault at the threshold in Figure 2.


<big>References</big>

* Abadie, Alberto, et al. When Should You Adjust Standard Errors for Clustering? Oct. 2017.
* Buser, Thomas, et al. “Do Women Give Up Competing More Easily?  Evidence from the Lab and the Dutch Math Olympiad.” American Economic Journal: Applied Economics, 2019, pp. 225–52.







