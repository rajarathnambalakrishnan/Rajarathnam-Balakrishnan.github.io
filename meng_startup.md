## Start-up Success Prediction
*(4 member team)*

### Problem Statement:
<p style="text-align: justify;">
Hundreds of startups are born everyday, out of which only few survive. The ability to predict whether or not a startup succeeds is thus of important value to many stakeholders such as the founders, investors and the public. However the definition of success varies largely between these stakeholders. For instance, for a startup founder, success could mean the founding vision being fulfilled, the amount of personal happiness or the amount of power they retain in the company. For customers, success would mean the ability of a startup to deliver its promises. While most of these measures complement each other, some of them could be conflicting such as the ability of the founder to retain power vs. revenue generated for investors. Moreover, not all these definitions of success can be quantified. Hence we narrowed our stakeholder as the investors and decided to predict whether a startup succeeds from an investor’s perspective. 
<br><br>
Investors' decision of whether or not to invest in a startup is based on the profit they gain from the investment. Currently investors largely depend on their intuition and experience to pick the right startup from the numerous startups being pitched to them everyday. Our objective for this project is to build this intuition into a machine using a data driven approach. We believe that this can become a useful tool for new investors to make right choices and for experienced ones to use as a filtering tool.
<br><br>
Before we define success for our project, we need to understand the typical funding process. It is shown below:
<br><br></p>

<p align='center'>
    <img src="images/startup2.png?raw=true" width="600" height="300"/>
</p>

<p style="text-align: justify;">
<br><br>
With this in mind, we came up with two measures of success which are described below:
<br><br>
1. Securing Series A or above funding: A startup is defined to be successful if it secures a Series A funding or above. Prior to series A funding, a startup usually is funded by angel investors. If a startup secures series A funding, the angel investors would be able to cash out and earn profit. Thus this metric would serve as a basis for angel investors to decide which startups deserve their seed investment. We want to predict during the seed round if the startup will raise Series A funding.
<br><br>
2. Undergoing Major Liquidity Event: A startup is defined to be successful if it undergoes a major liquidity event such as Initial Public Offering (IPO) or Mergers and Acquisitions (M&A). These are the common opportunities for venture capitalists to cash out and earn returns on their investment. Thus this metric would serve as a basis for venture capitalists to decide which startups to invest in. To be specific, we want to predict during Series B if the startup makes it to a liquidity event.
</p>

### Dataset:
<p style="text-align: justify;">
We obtained the raw data for this project from Kaggle. Specifically, the datasets were provided from Crunchbase on Kaggle. The datasets were part of the 2013 Snapshot by Crunchbase about the startup world involving all the necessary information across 11 CSV files. These CSV files had information about acquisitions, IPOs, funding rounds, investors, personnels, milestones, office locations, people associated with these startups, funds. The total number of rows when all the CSV files were considered, amounted to 0.5 Million rows of data. On a thorough note, the different CSV files are described as follows:
<br></p>

* **acquisitions.csv** file contains data about startups that have been acquired
* **IPO.csv** contains information about startups that IPOed
* **funding_rounds.csv** and funds.csv contains funding information pertaining to different startups
* **investments.csv** holds the information about venture capitalists involved in the funding
* **milestones.csv** contains the timeline of milestones achieved by each startup with clear descriptions
* **offices.csv** contains the information about the startups’ offices and their locations
* **people.csv** and **degrees.csv** contains data regarding education, personal information for all the personnel related to the startups from CEOs to staff
* **relationships.csv** contains data about different connections of personnel and startups
* **objects.csv** acts as a master table which contains some additional information about all the startups that were mentioned in the remaining 10 csvs

<p style="text-align: justify;">
The most challenging part of the data preparation was the many to many and one to many relationships across the tables. Pivot, groupby and merge from Pandas package was extensively used, converting necessary details to counts while maintaining unique IDs for each startup in order to create a single final table. Filters were further applied to narrow down the relevant parts of the excess information for effective analysis. For the Series-A criteria in our problem statement, those startups and their related information from all the 11 tables were selected based on the availability of their Series A funding information. Similarly, for major liquidity events (IPO, M&A) based criteria, those startups and their related information from the 11 tables were selected only if they had information about IPO or acquisition. Then the information for the two separate criterias were further cleaned based on other features’ availability. Any features that had missing values resulted in complete removal of the rows since these cannot be imputed. Finally the information according to the two separate criteria were filtered for USA based startups. 
<br><br></p>

### Analysis:

**1. Series A Prediction:** <p style="text-align: justify;">
For our models, we define the company as a success when it moves to series A funding or above from seed funding. 
<br><br>
After exploring our dataset, we found out that most of the startups did not make it to Series A funding. Thus, for our baseline model, we decided to predict all startups fail to reach Series-A. We tried Four different machine learning models, which are Logistic, LDA, Vanilla bagging, and CART model. The accuracy for those models are shown in the following table:
<br></p>

| Model              | Accuracy | TPR   | 
| --------------|:--------:| -----:|
| **Baseline**       | 0.634    | 0     |
| **Logistic**       | 0.622    | 0.65  |
| **LDA**            | 0.652    | 0.25  |
| **Vanilla bagging**| 0.618    | 0.42  |
| **CART**           | 0.664    | 0.27  |

<p style="text-align: justify;">
From the table we can see that the LDA and CART model had better performance than the baseline model, with accuracy 0.652 and 0.664 accordingly. Based on the accuracy, we decided to choose CART as our final model. 
<br><br></p>

**2. Major Liquidity Event Prediction:** <p style="text-align: justify;">
The success criteria was encoded as 1 for IPO and M&A and 0 for closed startups. Startups which are still operating under VC funding (neither IPOed or M&A nor closed) were left out to improve the accuracy. An assumption was made that a successful startup returns 5x the investment and a failed one loses 1x the investment. Assuming that there is limited money available to invest and each startup gets the same amount of investment, a function was defined to measure the profit to investment ratio:
<br><br></p>

```
ProfitX = ( 5 * (Number of true positives) - 1 * (number of false positives) ) / (Number of total predicted positives)
```
<p style="text-align: justify;">
The comparison of performance of different models are given below:
<br></p>

| Model              | Accuracy | ProfitX  | 
| --------------|:--------:| -----:|
| **Baseline**       | 0.55    | 2.31     |
| **Logistic**       | 0.68    | **3.18**  |
| **Random Forest**  | 0.64    | 2.91  |
| **XG Boost**| 0.67    | 3.19  |

<p style="text-align: justify;">
The baseline model was a naive prediction, claiming that all startups must be funded since the majority (55%) of startups in the list were successful.  
<br><br>
It was found that Logistic Regression and XGBoost Classifier performed the best. Random forest tended to overfit the training data. Although XGB produced a slightly better ProfitX, Logistic Regression has almost equal training and test accuracy, showing that it is a robust model. It is also highly interpretable, so that is an additional bonus. Also, its ProfitX competes closely with XGB. Hence, we choose the Logistic Regression as our preferred model.
<br><br>
Not only are we interested in the success of startups but we want to know what leads to this success. When we examined the feature importances of the Logistic Regression model, we found that the top features under each category of features are:
<br><br></p>

| Schools | Field | State in USA |Previous Experience|
| --------------|:--------:| --------:| ---------:|
| **Stanford** | Software | CA | Google |
| **Berkeley** | Analytics    | MA| Amazon|
| **MIT**  | Mobile | TX| LinkedIn|









