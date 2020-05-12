# Visual Analysis of Movie Images<br>Walt Disney Animation Studio VS. Studio Ghibli

DSC160 Data Science and the Arts - Midterm Project Repository - Spring 2020

Project Team Members: 
- Jou-Ying Lee, jol067@ucsd.edu
- Yunlin Tang, yut085@ucsd.edu
- Yupei Zhou, yuz522@ucsd.edu
- Sizhu Chen, sic100@ucsd.edu
- Yuanbo Shi, yus263@ucsd.edu

## Abstract

(10 points) 

Rooted in our group members' common interest in watching animation movies, and after revision of Professor's comments, we decided to take this Midterm Project as an opportunity to explore critically the intersection between digital films (animations) and the arts. 
Movie photos or movie screenshots are one of the very first impressions movie viewers have on each film. Often times, qualities of these images would directly influence viewers' decision on whether to proceed with watching or whether to turn to other options. Inspired by this understanding, our group hopes to compare two of the greatest animation production bases: America and Japan's animation movie photos, for studies on how Western and Eastern animation movies differ in their illustration approaches. In particular, we would be looking at two of the most prominent animation studios from the two nations -- Walt Disney Animation Studios (America) and Studio Ghibli (Japan) -- and inspect how image statistics from their movie productions differ.
<p align="center"> 
<img src="https://upload.wikimedia.org/wikipedia/en/c/c8/Walt_Disney_Animation_Studios_logo.svg">
</p>

The world-famous Walt Disnet Animation Studios has produced countless number of celebrated animated feature films including:
- Snow White and the Seven Dwarfs
- Pinocchio
- Frozen
- etc.

<p align="center"> 
<img  width=360px height=290px src =https://upload.wikimedia.org/wikipedia/en/c/ca/Studio_Ghibli_logo.svg>
</p>

The noteable Studio Ghibli, on the other hand, has produced many award-winning animation films, as well as many of the most highest-grossing anime films worldwide. These include:
- Castle in the Sky
- Spirited Away
- Howl's Moving Castle
- etc.

Derived from our group members' background understanding on the two production studios' animes, our hypotheses are based on these workshops' movie images, and are formulated as followed:
1. Hypothesis1
2. Hypothesis2
3. Hypothesis3

Besides primary image features discussed above, we would also look into reflecting movie images' feature statistics on each movie's "Plot Keywords." Most mentioned plot keywords would be illustrated by word-clouds with colors associated to results of image processing. Building upon topics covered in class, our analyses would be primarily based on Python. We are expecting to deploy popular image-processing libraries including skimage, OpenCV, Pillow along with Bokeh for interactive visualizations. Results would later be presented in a variety of forms including images and graphs for summary of significant findings, word-clouds for displays of plot keywords results, and interactive charts enabled for better understandings of our project.  

## Data

(10 points) 

This section will describe your data and its origins. Each item should contain a name of the data source, a link to the source, and any necessary background information such as:
- What is your cultural data source? 
- When was it made? 
- Who created the works? 
- Is it digital native, or is it some kind of scan, recording, photo, etc., of an analog form? 

## Code

(20 points)

Please follow the click on links for directions to each different section's coded ipynb files.
- [Data Scraping](code/scrape-image.ipynb): ipynb file for data acquisition and scraping
- [Data Analysis](code/data_analysis.ipynb): ipynb file for feature extraction and data processing
- [Modelling](code/modelling.ipynb): ipynb file for feature engineering, model fitting, and model evaluation
- [Data Visualization](code/visualization.ipynb): ipynb file for data visualization 

## Results

(30 points) 

This section will contain links to documentation of your results. This can include figures, sound files, videos, bitmaps, as appropriate to your domain of analysis. Each result should include a brief textual description, and all should be listed below: 

- image files (`.jpg`, `.png` or whatever else is appropriate)
- audio files (`.wav`, `.mp3`)
- written text as `.pdf`

#### Modelling:
- In an attempt to classify Disney's movie photos from those of Ghibli's, several classification models -- including Support Vector Machine, Random Forest Classifier, AdaBoost Classifier, Gaussian Mixture Model, Decision Tree Classifier, and K-Nearest Neighbors -- were trained and tested on our image dataset.
- Our best classification result is based on a Support Vector Machine with a highest accuracy score of 0.818. While this result can not be referenced as particularly high, we do believe there is a high probability it might be due to our lack of training data. With more training instances, we are confident in seeing a possibly higher classification accuracy score. Disregarding of this limitation, a score of 0.818 does tell us that there are discernable and un-ignorable differences in terms of image stats between the famous Western Animation studio and the prominent Eastern Studio Gilbli.
- Each model are fitted to a GridSearch with numerous hyperparamters for tuning, as well as a 5-fold cross validation to address the problem of overfitting. Results are then selected as the best accuracy_score among each model's 5 produced score.
- Not very surprising, Support Vector Machine (SVM) won the first place in terms of classification, with a highest accuracy score of 0.818. However, what we found surprising is a SVM model with a hyperparamter set of an 'rbf' kernel, and gamma of 'scale', produced equally high accuracy_score as a linear SVC with penalty term of l2. This says that a Support Vector Machine with two different kernel functions gave exactly the same result, which we believe is pretty rare to see.
- Except for the few classifiers that gave unreasonable outcomes (e.g. K-Nearest Neighbors with )

#### Visualization
We are concered with five image features (mean_hue, mean_saturation, mean_value, mean_entropy, edge_sum) in this project, and a boxplot showing distributions of these five features in both studios is given below.
<p align="center">
  <img src="https://github.com/ucsd-dsc-arts/dsc160-midterm-group9/blob/master/results/Boxplots%20of%20Image%20Features.jpg" width="720">
</p>

The boxplot shows that the distributions seem similar with minor differences. Additionally, we look at pairplots of these five features in both studios.
<p align="center">
  <img src="https://github.com/ucsd-dsc-arts/dsc160-midterm-group9/blob/master/results/Pairplots%20of%20Image%20Features.jpg" width="720">
</p>

The [pairplot](https://seaborn.pydata.org/generated/seaborn.pairplot.html) function in the [Seaborn](https://seaborn.pydata.org/index.html) library carries out a linear regression and plots the result on non-diagonal plots. It shows the linear relationship between every pair of features in both studios. We notice that for the following pairs of features, linear regression suggests an opposite relationship.
- mean_hue vs. mean_entropy
- mean_value vs. mean_entropy
- mean_value vs. edge_sum

Interactive plots of these three pairs of features in greater detail can be found at the "Make Interactive Plots" section of the [visualization notebook](code/visualization.ipynb). And Bitmap plots of these three pairs of features for both studios can be found in the [bitmaps](results/bitmaps) folder.

We also look at wordclouds generated by plots of movies produced by the two studios. 
<p align="center">
  <img src="https://github.com/ucsd-dsc-arts/dsc160-midterm-group9/blob/master/results/Ghibli%20Movie%20Plot%20Keywords.jpg" width="512">
  <img src="https://github.com/ucsd-dsc-arts/dsc160-midterm-group9/blob/master/results/Disney%20Movie%20Plot%20Keywords.jpg" width="512">
</p>

We can see that both studios feature movies marked by "young" and "life". Yet there are differences in terms of specific plots. For example, "girl" stands out in Ghibli studio's movies as they make more movies featuring stories of girls. Such distinction also leads to differences in image features.

## Discussion

(30 points, three to five paragraphs)

The first paragraph should be a short summary describing your results.

The subsequent paragraphs could address questions including:
- Why is this culturally relevant?
- How does your computational approach differ from the traditional art historical, musicological, manuel/subjective approach to analyzing your cultural subject? 
- How do you think the original artists/musicians would respond to this type of analysis? Would it change/inform their practice in some way?
- How do your results relate to broader social, cultural, economic political, etc., issues? 
- In what future directions could you expand this work?

The two animation studios (Disney Animation Studios and Ghibli Studios) we chose in this project are two of the most prominent production companies in animation movies. They occupied extremely significant positions in the movie art-making world as milestones in several decades. Since the 20th century, Disney had employed Technicolor and Cels animation technique in their animation making process. Many animated companies also made use of the Disney technical and aesthetic model into their own films. Ghibli Studio, as an example, also made reference to the Disney model but further extended its movie productions into a distinct and unique style in order to differ from others. Our results from extracting several basic and advanced image statistics on multiple frames in movies have shown the general difference between Disney and Ghibli styles. On the multiple boxplots of image features provided in the data visualization part (shown below), each boxplot for different features generally reflects the average stats between these two companies. The plot includes the average value for HSV color, entropy, and edge measurements. It is clear that the mean hue and saturation between the two groups are approximately close; however, the boxplots also indicate that the 25/75 percentiles (Q1 and Q3) are more spread in Disney movies compared to Ghibli. In addition, the mean value in Ghibli movies is slightly higher than Disney’s. This observation concludes that both studios have similar characteristics in light and shadow, bright and dark contrast, and tint color contrast. However, Ghibli is more consistent in color harmony and lightness (value) of general color elements in movies, while Disney has a stronger complementary color and hue contrast. These differences lead to a relatively good and acceptable performance for several machine learning models to classify the labels for each frame in our datasets while we use the image features. 
![](https://github.com/ucsd-dsc-arts/dsc160-midterm-group9/blob/master/results/Boxplots%20of%20Image%20Features.jpg)
<div align='center'><img src='https://ptgmedia.pearsoncmg.com/images/art_krause2_colortips/elementLinks/krause1_fig01_alt.jpg'></div>

## Team Roles

Provide an account of individual members and their efforts/contributions to the specific tasks you accomplished.
- Sizhu Chen: scraped data (images and text) from two different website. (scrape-images-hayao/disney.ipynb)
- Jou-Ying Lee: wrote Abstract, completed model fitting (modelling.ipynb), drafted the "Modelling" portion of "Results" and finished Technical Notes and Dependencies.
- Yupei Zhou: completed visualization (visualization.ipynb) and drafted "Visualization" portion of "Results".
- Yunlin Tang: wrote discussion, integrated results part. 
- Yuanbo Shi: data preprocesscing, feature extraction, feature analyzing (data_analysis.ipynb)

## Technical Notes and Dependencies

Our codes are solely based on Python programming language, with common image processing libraries addressed in the Introduction. Except for deployment of Pandas -- a powerful data analysis and manipulation library, and Numpy -- a core library for scientific computing. We use the [wordcloud](https://amueller.github.io/word_cloud/) library to make wordclouds of movie plot keywords. Other implemented libraries are mostly introduced in class, and therefore we do not anticipate needs for additional installation of pip packages or softwares. Each ipynb file contains each of its needed imports within the documents itself, therefore by running the codes entirely, one should be able to have necessary imports ready for codes to be running.

## Reference

References to any papers, techniques, repositories you used:
- Papers
- Repositories:
	- https://github.com/roberttwomey/dsc160-code
- Blog posts
- Sites
	- https://en.wikipedia.org/wiki/Studio_Ghibli
	- https://en.wikipedia.org/wiki/Walt_Disney_Animation_Studios
	- https://seaborn.pydata.org/index.html
	- https://seaborn.pydata.org/generated/seaborn.pairplot.html
	- https://seaborn.pydata.org/generated/seaborn.regplot.html
	- https://amueller.github.io/word_cloud/
