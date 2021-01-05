# Amazon-apparel-Image-Classification-and-Product-Recommendation

## Abstract 
The aim of the project is to classify Amazon products and to make recommendations based on images, title and brand information. The images are based on 5 categories/types of apparel scraped from Amazon. The categories are hats, watches, tshirts, shoes and bags.

The first part of the project trains and tests an image classification model.

The second part of the project is divided into three subcategories of recommendation engine-

1) The first recommendation engine takes in images from the user and recommends products solely based on image similarity,

2) The second recommendation engines takes the product's title and recommendes products that has a high similarity score based on the title

3) The final recommendation engine takes into account the title and brand information and recommendes products that has a high similarity score based on the title and brand name.

The three recommendation engines are compared against each other and some conclusions are drawn.

## Introduction 
In the online marketplace world, companies make use of user history and product data to make recommendations to user. The data collected to make these recommendations are search terms, purchase history, product category, items in cart information and many more. Most commonly, recommendation engines make use of text based keyword matches to identify products that consumers may like. Another alternative and less widely used technique is to make use of images to compare product similarity. Images may be better representative of consumers interest than text. This is the comparison we will be making in this project.

In this project, we present a smart engine for on-line shopping that takes image as an input and then tries to understand the information about the features from the images. We first use neural network to classify the input image as one of the product categories. Then use neural network and memory based similarity methods to calulcate the similarity between product images and product description, which will be used to recommend other similar products from our database.

## Methodology 
This project is a complete end-to-end data science project, starting from data scraping to partial deployment. A high level overview of the steps is shown in figure 1.

![](https://github.com/divyar2630/Amazon-apparel-Image-Classification-and-Product-Recommendation/blob/main/images_note/end2end.png)

Figure 1: Overview of the project

The data collection process involes scraping data from Amazon and storing it in a CSV file. A further description of the data collection process and the data can be viewed in section IV. The scraped data has many missing values and discrepancies. An initial cleaning process was done in Excel and further cleaning is done in section V. The data cleaning is followed by exploratory data analysis where we try to understand the data a bit further. The exploratory data analysis is explained in section VI. Now we have our data ready for image classification and building a recommendation engine.

![](https://github.com/divyar2630/Amazon-apparel-Image-Classification-and-Product-Recommendation/blob/main/images_note/Image_classification.PNG)

## Recommendation Engine

The second part of the project deals with recommending the most suitable products to users based on the current selection and choice of the product. Our model relies on the fact that multiple features can be extracted from images and text and used for similarity computation.

![](https://github.com/divyar2630/Amazon-apparel-Image-Classification-and-Product-Recommendation/blob/main/images_note/output.png)

Figure 4: Recommendation engine flowchart

The above flowchart describes the steps involved in building the recommendation engine.

The recommendation engine we build in this project is a content based method. In a content based method, we look at the product features to recommend other similar products based on product attributes (figure 5).

![](https://github.com/divyar2630/Amazon-apparel-Image-Classification-and-Product-Recommendation/blob/main/images_note/content.png)

Figure 5: Content based filtering

We build two recommendation engines in this project. The first type is image based recommendatione engine and second type is text based recommendation engine.

In order to recommend products based on images, we calculate the cosine similarities between the image features extracted using a pre-trained model. Images were then recommended based on the computed cosine similarities ranked in descending order. The higher the cosine similarity, the more semantically similar the recommended image is to the input image.

In the text based recommendation system, the first method is to recommend products based on the product title and second method is to recommend products based on title and brand of the product.

![](https://github.com/divyar2630/Amazon-apparel-Image-Classification-and-Product-Recommendation/blob/main/images_note/cosine.png)

Figure 6: Cosine Similarity

In order to recommend products based on text, we calculate the cosine similarities(figure 6) between the text feature (title, title+brand) after getting the Bag of Words.In the product title and brand method, we calculate a cosine similarity score using the formula of weighted average (figure 7) which combines the individual cosine similarity scores along with the weights of each type. Products were then recommended based on the computed cosine similarities ranked in descending order. The higher the cosine similarity, the more semantically similar the recommended product title (or title+brand) is to the input title.


![](https://github.com/divyar2630/Amazon-apparel-Image-Classification-and-Product-Recommendation/blob/main/images_note/brand_title.png)
                                            Figure 7: Weight average 


## Data Collection 

The data was scraped from Amazon.com. A tool called parse hub was used for scraping the content. The 5 categories we decided are - hats, shoes, shirts, bags and watches. We scraped 10 pages for each of the outputs and the total number of results we got were 2800 rows. An initial cleaning in excel was performed and the data size reduced from 2800 to 2310

We scraped all the information available on the main page of a search (not the product page). A sample search of tshirts is shown below. The information includes the below:

* Product title
* Product brand
* Price
* Number of reviews
* Rating on a scale of 5
                                            
## Results 

In the final results section of the project, we printed results of the 3 recommendation engines and compared them side by side for easy reference. We took three product IDs and printed 5 recommended products ranked in order

![](https://github.com/divyar2630/Amazon-apparel-Image-Classification-and-Product-Recommendation/blob/main/images_note/PPT_shirt-1.png)
                                     
                     Picture 9: Results for Product ID:1000

![](https://github.com/divyar2630/Amazon-apparel-Image-Classification-and-Product-Recommendation/blob/main/images_note/PPT_bag-1.png)
                                           
                      Picture 10: Results for Product ID:200

![](https://github.com/divyar2630/Amazon-apparel-Image-Classification-and-Product-Recommendation/blob/main/images_note/PPT_watch-1.png)
                                            
                                            Picture 11: Results for Product ID:2000

### Observations :

* The products recommended for Product ID: 1000 (Picture : 9) gives good results for the image-based recommendation method with the highest similarity score of 0.86. The text based methods produce scores of around 0.63.
* The products recommended for Product ID: 200 (Picture : 10) gives good results for the title based recommendation method with the highest similarity score of 0.92.
* In the third picture, the score is highest for image based recommedation system compared to the text based recommendation system.
* In all the three pictures, the text based methods have many common results, whereas the image based is quite different.
* Apart from the above three results, several results were printed and compared. Based on the products in our database, image based recommendation system seems to give the best results, but with the information here we can not give conclusive results.

## Future Work 

In this section, we will discuss some work we were interested in trying in this project, but we were unable to implement due to time or knowledge constraint.

* We wanted to build a recommendation engine that incorporates both the image based and text based methods.
* We wanted to test other recommendation engine methods like collaborative filtering (Model Based in specific)
* We wanted to deploy the image classification and recommendation engine on a web app using Flask

## Conclusion 

We performed image classification and product recommendation based on images and text in our project. Although, the results produced from image based recommendation system yielded the best results here, we can not say for sure. A way to evaluate the three recommendation methods is experimentationn. Through A/B/n testing, we can make data driven decisions based on the click through rates or revenue from users in the test.
