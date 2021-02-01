# Module16-Amazon_Vine_Analysis

## Purpose of Project

    <br>The purpose of this project is to analyzing Amazon reviews written by members of the paid Amazon Vine program. 
    The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. 
    Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish
    a review.

    <br>In this project, we had access to approximately 50 datasets. Each one contained reviews of a specific product, from clothing apparel
    to wireless products. I have picked "Amazon reviews_us_Electronics"

    
    using  PySpark (ETL process) 
    extracted the Electronics dataset, 
    transformed the data, 
    connected to an AWS RDS instance, and 
    loaded the transformed data into pgAdmin. 
    
    Next, using PySpark analysed the data to determine if there is any bias toward favorable reviews from Vine members in the dataset.

   ## Process:

   1- Perform ETL on Amazon Product Reviews
    
             [Amazon_Reviews_ETL.ipynb file](https://github.com/4renginy/Module16-Amazon_Vine_Analysis/blob/main/Amazon_Reviews_ETL.ipynb)


                I)Started with importing electronics data into colabotary 
                
                II)Turned the dataset into dataframe called review_id_df

                III) Created following tables to analyse;

                        a-customers_df
                        b-products_df
                        c-review_id_df
                        d-vine_df

                IV)Connected to AWS RDS and wrote each of those data frames to its table 

                At the end of this process we had all the tables at pgadmin sql database to be analysed.
               ![](https://github.com/4renginy/Module16-Amazon_Vine_Analysis/blob/main/sql.JPG)

    
    2- Determine Bias of Vine Reviews
    
    [Vine_Review_Analysis.ipynb] (https://github.com/4renginy/Module16-Amazon_Vine_Analysis/blob/main/Vine_Review_Analysis.ipynb)

               In this file we have uplaoded the electronics file into colaboratory, 

               created a dataframe from the full data

               created vine_df with 6 required colums for the analysis

                then filtered the data for
                                            1-"total_votes>=20 
                                            2-"helpful_votes/total_votes>=0.5"

                Now the preperations are over and we can start calculating
                                            
                    Total count of 5 star readings                      23497
                                         five star from nonvinemembers  23043
                                         five star from vinemembers       454

                    Total Count of nonvine club ratings                 49673
                     Count of wine club member ratings                   1080
                        
                    Five star percentage for nonvine club members      46.39 %
                    Five star percentage for wine club members         42.03 %

Conculution 1: Based on our calculations five star percentage from non wine club memebers is higher than wine 
club members, 
in addition when we  consider the count of nonvine members to vine members the cost is not worth the return. 

However we wanted to make sure the concution withdrow is accurate went one step ahead and run more calcuations by 
including verified purchases.

                Percentage of five star ratings for nonvine members with verified purchases:         48.06 %

                Percentage of five star for ratings for nonvine members with uverified purchases:    44.56 %

                Percentage of five star ratings for vinemembers with verified purchase:               100 % 

                Percentage of five star ratings for vinemembers with unverified purchases:           41.87 %

Concuclution 2: Percentage of nonvine members for verified and unverifed still higher than the unverifed members. 

    Yes the verified purcahse is 100 % but there are only 3 items in this calculation so still 100 % does not give 
    justifiable positif result.

## CONCULUTION:
Based on the number of members and nonmembers with 5 star ratings I beleive the amount of money we spend for 
vineclub does not have the necessary return.
