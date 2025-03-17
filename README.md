# CSE150A-Group-Project

https://colab.research.google.com/drive/1SIrCfJj4YnumBDXQ1dHT_sR8NjnJsEVO?usp=sharing



Our AI agent is a utility-based agent that analyzes customer data from bank-full.csv and attempts to determine the likelihood of a customer subscribing to a term deposit based on various 6 features(age, job, education, marital status, account balance, housing). If the customer is rated to have a high probability of subscribing(over 50%), they will be emailed as part of the bank's marketing campaign. Features like age and account balance are partitioned into larger discrete intervals to make our calculations more streamlined. Age was divided into 4 intervals(young, middle-age,...,ect), balance was divided into 5 (debt, low, medium,..., etc). There are 11 different job categories(including things like retired and unemployed), and 3 marital status parameters(single, married, divorced). Housing is binary(yes/no), and education can take 3 values as well(primary, secondary, and tertiary schooling). Our outcome y(is the client predicted to subscribe to a term deposit?) is binary, being either ‘yes’ or ‘no’. 

We are measuring our agent's performance by looking at the values provided in the classification report, which includes measures such as precision, recall, f1-score, and support. The sensors of our agent read in the bank-full.csv file and this data becomes the environment that our agent operates in. Our performance measure would be the percentage of correct predictions. The actuators would be an automated system, which would send emails to customers based on these predictions. Our actuator is an email automation API utilizing SendGrid. For customers who are predicted to subscribe, we send them an automated email. 

We have set up our agent by importing the necessary data set that it needs to train our model and have made modifications to our dataset, such as encoding our categorical variables, scaling any numeric values, and handling missing data. Our agent serves a valuable purpose in probabilistic modeling due to it being a utility based agent because it aims to maximize potential clients. This agent would greatly benefit business owners who need the best possible outcomes when connecting with clients. The structure of our network would have a similar structure to a noisy-or model. There edges from each feature to our binary outcome Y(has the client subscribed a term deposit?). We are naively assuming that there are no edges between features. For some of our variables(age, account balance), we divide our data into larger discrete intervals. Unlike a noisy or model, all the parent nodes are not binary. We use libraries like pgmpy to calculate the CPTs. Ex: P(Age=a)=count(Age=a)/total samples, for root nodes. Ex: P(y=yes|Age=a,...)= count(y=yes and Age=a and …)/count(Age=a and …) for the child node y. 
The specifications regarding what is being done within imported functions(like pgmpy) is outlined within the notebook. We use polynomial transformations to generate new features, along with other basic preprocessing(like filling in missing values). 


Conclusion: 

Diagram of our model: 
![Digram](https://github.com/Nicole242/CSE150A-Group-Project/blob/Milestone3/150diagram2.png)

