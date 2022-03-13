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
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/customers_table.png" alt="Customers Table" style="height: 400px; width:400px;"/>
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/products_table.png" alt="Products Table" style="height: 400px; width:400px;"/> 
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/review_id_table.png" alt="Review ID Table" style="height: 400px; width:400px;"/> 
    <img src="https://github.com/crtallent/Amazon_Vine_Analysis/blob/main/Images/Vine_table.png" alt="Vine Table" style="height: 400px; width:400px;"/>   
    <p/>  
  




## Resources

* Software: Amazon Web Services (AWS), Google Colaboratory (Colab) Notebooks, Python 3.7.6, PySpark 3.0.3, pgAmdin4, PostgresSQL 13.6 

* Data Source: amazon-reviews-pds/tsv/amazon_reviews_us_Video_Games_v1_00.tsv.gz




