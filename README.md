# Amazon_Vine_Analysis

## Overview

For this project, we are tasked with analyzing Amazon reviews written by members of the paid Amazon Vine program.  This program allows manufacturers and publishers to receive reviews for their products.  These comapnies, such as the SellBy company, pay a fee for this service to Amazon.  The companies also provide products to Amazon Vine members, who are then required to publish a review of the product they received.  The purpose of this analysis is to determine whether this service provides good value for the expenses incurred by the companies (such as SellBy), as well as whether reviews written by paid Amazon Vine members may be biased.  The following steps were taken to prepare the dataset using ETL (extract, transform, load):

1. Create Google Colab Notebook and import dependencies <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/Colab.png"/>
2. Extract Amazon Review dataset as a DataFrame <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/dataset.png"/>
3. Transform dataset into 4 dataframes:

  <p float="left">
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/cust_df.png" alt="Customers DataFrame" style="height: 400px; width:400px;"/>
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/prod_df.png" alt="Products DataFrame" style="height: 400px; width:400px;"/> 
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/review_id_df.png" alt="Review ID DataFrame" style="height: 400px; width:400px;"/> 
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/vine_df.png" alt="Vine DataFrame" style="height: 400px; width:400px;"/>   
    <p/>  
4. Load all four dataframes into pgAdmin

 <p float="left">
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/customers_table.png" alt="Customers Table" />
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/products_table.png" alt="Products Table" /> 
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/review_id_table.png" alt="Review ID Table" /> 
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/Vine_table.png" alt="Vine Table" />   
    <p/>  
  
## Resources

* Software: Amazon Web Services (AWS), Google Colaboratory (Colab) Notebooks, Python 3.7.6, PySpark 3.0.3, pgAmdin4, PostgresSQL 13.6 
* Data Source: amazon-reviews-pds/tsv/amazon_reviews_us_Video_Games_v1_00.tsv.gz
* Codes for used for ETL rpocess [here](https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Amazon_Reviews_ETL.ipynb) and [here](https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Vine_Review_Analysis.ipynb).

## Amazon Vine Reviews Analysis (Results)

In order to perform bias testing on the Amazon Vine reviews, we first filtered our [Vine DataFrame](https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Vine_Review_Analysis.ipynb) to include only results where there were 20 more total votes, and at least 50% of their total votes were determined as "helpful" by other consumers reading the reviews:

```
> new_vine_df = vine_df.filter("total_votes>=20")
> helpful_df = new_vine_df.filter("helpful_votes / total_votes >= 0.5")
> helpful_df.show()

```
We then created two new dataframes from the filtered dataset to separate reviews from Vine members and non-Vine members to begin our comparison:
 <p float="left">
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/Vine_reviews.png" alt=" Vine Reviews" style="height: 400px; width:400px;"/>
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/non_Vine_reviews.png" alt="Non-Members Reviews" style="height: 400px; width:400px;" /> 
 <p/>  

With our newly created dataframes, we were ready to begin our bias testing. All calculations were performed on the Vine and non-Vine member dataframes separately, but for reliability, the same procedures were peformed for both.  The following information was returned:

* There were a total of 94 helpful reviews for Vine members, and 40,471 for non-Vine members.
* Of the 94 reviews for Vine members, 48 of them were 5-star reviews.  Of the 40,471 reviews for non-Vine members, 15,663 were 5-star reviews.
* These results indicate that 51% of the reivews from Vine members were 5-star ratings, compared to 39% for non-Vine members.

```
< vine_reviews = y_count / y_ratings
< print("{:.0%}".format(vine_reviews))
< non_vine_reviews = n_count / n_ratings
< print("{:.0%}".format(non_vine_reviews))
```



