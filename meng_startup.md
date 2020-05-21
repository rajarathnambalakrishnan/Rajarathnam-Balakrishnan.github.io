## Start-up Success Prediction
*(4 member team)*

### Problem Statement:
<p style="text-align: justify;">
Hundreds of startups are born everyday, out of which only few survive. The ability to predict whether or not a startup succeeds is thus of important value to many stakeholders such as the founders, investors and the public. However the definition of success varies largely between these stakeholders. For instance, for a startup founder, success could mean the founding vision being fulfilled, the amount of personal happiness or the amount of power they retain in the company. For customers, success would mean the ability of a startup to deliver its promises. While most of these measures complement each other, some of them could be conflicting such as the ability of the founder to retain power vs. revenue generated for investors. Moreover, not all these definitions of success can be quantified. Hence we narrowed our stakeholder as the investors and decided to predict whether a startup succeeds from an investor’s perspective. 
<br><br>
Investors' decision of whether or not to invest in a startup is based on the profit they gain from the investment. Currently investors largely depend on their intuition and experience to pick the right startup from the numerous startups being pitched to them everyday. Our objective for this project is to build this intuition into a machine using a data driven approach. We believe that this can become a useful tool for new investors to make right choices and for experienced ones to use as a filtering tool.
<br><br>
Before we define success for our project, we need to understand the typical funding process. It is shown below:
<br><br>
<p align='center'>
    <img src="images/startup2.png?raw=true" width="600" height="300"/>
</p>
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
<br><br>
- acquisitions.csv file contains data about startups that have been acquired,<br>
- IPO.csv contains information about startups that IPOed, <br>
- funding_rounds.csv and funds.csv contains funding information pertaining to different startups,<br>
- investments.csv holds the information about venture capitalists involved in the funding, <br>
- milestones.csv contains the timeline of milestones achieved by each startup with clear descriptions,<br>
- offices.csv contains the information about the startups’ offices and their locations, <br>
- people.csv and degrees.csv contains data regarding education, personal information for all the personnel related to the startups from CEOs to staff, <br>
- relationships.csv contains data about different connections of personnel and startups. <br>
-objects.csv acts as a master table which contains some additional information about all the startups that were mentioned in the remaining 10 csvs. <br><br><br>
</p>


