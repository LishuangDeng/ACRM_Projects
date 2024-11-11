**Churn model**

**Feature engineering part**

When we are working on feature engineering on the churn model, we mainly focus on the following four domains.

1\. Define the time window

2\. Define the active customers

3\. Define the churners

4\. Build up some useful features

1. **Define the time window**

**Why do we need the time window?**

\- In practice, we use the past data to build the model and get the predicted result to implement the market campaign for the future. Modeling and campaign are located in the different time periods.

\- Customer churn will not happen immediately. They also need time to evolve.

\- When we set a time window, we need to set an independent period and a dependent period. The dependent period is used to predict customer's churn rate during this period and the independent period is used to build up the features of all active customers.

In this project, we assume the churn marketing campaign will be implemented in the entire year(2025/01/01 - 2025/12/31)

We build up the model today(2024/10/30) and use the past data from 2006-12-08 to 2020-01-21.

**Purpose Model (Campaign)**

\----------INDEPENDENT-------------|xxxxGAPxxxxxx|----------DEPENDENT---------------|

(Modelling period) (Campaign period)

&nbsp;                      30/10/2024       01/01/2025                                  31/12/2025

**Model Building**

\------------INDEPENDENT----------|xxxxGAPxxxxxx|---------------DEPENDENT--------------|

&nbsp;                 30/10/2018     01/01/2019             31/12/2019

**Why we need to have two models?**

\- The model building uses the past data to build the churn model. Once we build up the best model, we can then update the data set on the best model to get the predicted results.

\- The implementing purpose model lets us know when we will implement the campaign in the future. However, we don't have the latest data yet, so we use the past data at the same period to match the future-purpose model.

**Why do we need a gap between independent and dependent periods?**

\- The gap is the period that we use to run the model and prepare the potential customers for the campaign. During this period, there are no new customers coming in the model and no churners.

1. **Define the active customers**

Keep in mind that not all the customers are active in the dataset. We just want to predict the active customers who still participate in the activities or still interact with the company. Sometimes, although the customers are active, we just want to predict the valuable customers’ churn rate.

1. **Define the churners**

The definition of churners is very important in the churn model. Different projects can have different definitions based on the specific business context.

Basically, we can classify two types of churners that are implicit and explicit according to the business models.

If the company charges a monthly subscription fee, e.g. telecommunication sector, customers have to inform the company that they will stop services. We call this type of churner an explicit churner. In most cases, customers will not inform the company they are leaving and switching to another company. We call this type of customer an implicit churner.

For different types of churners, we use different metrics to define the “churn” label in the model.

In this project, we will use the data from a fundraising company. It is a contractual company. Thus, we will define the churners based on whether the customers stop the service in the predefined period. In some cases, for the implicit churners, we can define “churn” when the customers have higher recency or lower frequency than normal(average) customers.

1. **Build up some useful features**

While building up independent variables for the model, firstly, we focus on the transaction table. RMF is a good indicator for the churn model. Then, we can extend the transaction table and seek some preference behaviors, like payment methods. Secondly, we can seek other interaction behaviors. In this project, we will explore some communication behaviors like communication methods, contact direction. Last but not least, we can explore some customer social demographics information and external data sources like social media data.

In the end, we merge all built features together to form a base table for modeling part.