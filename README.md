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
1. Pictures with higher mean saturation are more likely to be from Disney Studio.
2. Pictures with lower mean entropy are more likely to be from Studio Ghibli.
3. Pictures with higher mean hue are more likely to be from Disney studio.

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

Please click on the following links for directions to each different section's coded ipynb files.
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

The two animation studios (Disney Animation Studios and Ghibli Studios) we chose in this project are two of the most prominent production companies in animation movies. They occupied extremely significant positions in the movie art-making world as milestones in several decades. Since the 20th century, Disney had employed Technicolor and Cels animation technique in their animation making process. Many animated companies also made use of the Disney technical and aesthetic model into their own films. Ghibli Studio, as an example, also made reference to the Disney model but further extended its movie productions into a distinct and unique style in order to differ from others. Our results from extracting several basic and advanced image statistics on multiple frames in movies have shown the general difference between Disney and Ghibli styles. On the multiple boxplots of image features provided in the data visualization part (shown below), each boxplot for different features generally reflects the average stats between these two companies. The plot includes the average value for HSV color (illustrated below), entropy, and edge measurements. It is clear that the mean hue and saturation between the two groups are approximately close; however, the boxplots also indicate that the 25/75 percentiles (Q1 and Q3) are more spread in Disney movies compared to Ghibli. In addition, the mean value in Ghibli movies is slightly higher than Disney’s. This observation concludes that both studios have similar characteristics in light and shadow, bright and dark contrast, and tint color contrast. However, Ghibli is more consistent in color harmony and lightness (value) of general color elements in movies, while Disney has a stronger complementary color and hue contrast. In addition, the mean entropy in Ghibli movies is also slightly higher than in Disney, which demonstrates that Disney tends to use plain color in several frames while Ghibli does not. These differences lead to a relatively good and acceptable performance for several machine learning models to classify the labels for each frame in our datasets while we use the image features.

<div align='center'>
	<img src='https://github.com/ucsd-dsc-arts/dsc160-midterm-group9/blob/master/results/Boxplots%20of%20Image%20Features.jpg' width=512>
	<img src='https://ptgmedia.pearsoncmg.com/images/art_krause2_colortips/elementLinks/krause1_fig01_alt.jpg' width=512>
</div>

The difference found in the numbers of frames in movies between Disney and Ghibli can be related to cultural factors, such as the distinct animations styles between American and Japanese art productions. While portraying the human characters, American animation attempts to depict in comic-book-style realism that most characters are grossly exaggerated or comically cartoonish. For the Japanese side, it emphasizes in angles, flowing, and attenuated lines such as detailed eyes and face shapes, but minimal lines in depicting noses and mouths. In choosing the color elements, American animation focuses more on solid block colors while the Japanese pay more attention to variants and shading of hues. These discrepancies can be applied to our case as well. As shown below, two frames which respectively extracted from Disney and Ghibli movies can precisely reflect the visual differences of style in depicting characters between these two cultures. 

<div align='center'>
	<img src='https://d13ezvd6yrslxm.cloudfront.net/wp/wp-content/images/Alice-in-Wonderland-1-700x300.jpg' width=500>
	<img src='//cdn.onebauer.media/one/media/5e31/aba8/fa58/9980/efc1/507b/spirited-away-main.jpg?quality=50&width=1800&ratio=16-9&resizeStyle=aspectfill&format=jpg' width=500>
</div>

Notice that both studios anthropomorphized the nonliving objects or animals in animations. However, similar to the styles of human characters, Disney used exaggerated features to emphasize the characteristics of the objects such as solid color blocks and strong hue contrast; and Ghibli used detailed line elements and tint color contrast to portray the nonexisting dragon character. These obvious variations in two distinct animation styles can be correlated with the different audiences and targeted consumer groups in the United States and Japan. In American culture, animation movies are more considered as a medium for young-aged children thus using exaggerations and simplification in depicting the characters would attract more potential consumers. In contrast, Japanese culture considers animation movies are also for teenagers and adults; therefore the style of detailed realism would be more appropriate for the targeted users’ group.

Traditionally, to compare and contrast the similarities and differences between two groups of frames in animation movies respectively from two different production studios will be based on human inspection. Related back to the 20th century, the techniques in filmmaking are progressively improving. The most popular method in the process of making animation movies was Cels. It is an important innovation to the traditional animation since it allows some parts of each frame to be repeated in other frames, which provides the studio industries opportunities to create more vivid animation and saving labor compared to other traditional methods. However, this method became expensive since the 2000s because of the emergence of computer animation. One of the major differences in styles between Disney and Ghibli is also related to the use of cels and CG. Since 1995, computer animation grew into the dominant animation technique in the US. Many animation movies produced by Disney studios in the 21st century are employed by CG techniques; in contrast, although some of the Ghibli movies are made digitally, the majority of them are the hybrid products which are mixtures of traditional animation methods such as hand-paint cels and computer animation (illustrations are listed below). This difference in filmmaking methods can also account for the distinct characteristics of these two cultures mentioned above. To analyze the image statistics and artistic elements in these movies, the traditional way would be similar to the making process. Inspecting the frames one by one using human labor is slow and expensive although this method would also take care of the details in each frame. Our computational approach to compare and contrast these frames is much faster and convenient. It pays more attention to the general performance and average statistics for each group than the details. Based on this method, it provides broader information and comparisons which are applicable and appropriate to use in our case.

<div align='center'>
	<img src='https://i0.hdslb.com/bfs/article/9f6675b21ac0eaecd9100e32616def17d207524b.jpg' width=500>
	<img src='https://i0.hdslb.com/bfs/article/f0edeefa3dd5705cf13773c79ddc1b797f92f573.jpg' width=500>
	<img src='https://i0.hdslb.com/bfs/article/e276a0eb4f305220b9c662c9a30db0b21b2025ef.jpg' width=500>
</div>

In our project, we also provide the word clouds for Disney animation studio and Ghibli studios respectively. It is significant to make reference to the context in each movie for further cultural analysis as well. In the word cloud, we have scraped the brief introduction for each movie in our dataset then compute the plot for two companies respectively. The most prominent words in Disney movies are life, young, and home. These phrases actually represent the American cultural and social value in the mainstream, which emphasize the significance of the family unit as a sense of belonging and the individual existentialism. The idea of conformity in social life was popular during the 1960s in the United States, which significantly strengthened the idea of being part of a family. Furthermore, the popularity of existentialism in the 20th century also profoundly influenced American society which emphasizes the individual reasonings and subjective experience. These cultural elements are reflected in the Disney animation movies as well, where our word cloud also includes words such as “adventure” and “family”. In contrast, the word cloud of Ghibli movies has different prominent words, such as “girl”, “young”, “forest” and “find”. These words are related to the recurring and consistent themes in the Ghibli movies: feminism, environmentalism, and growth/maturing from youth. Most of the Ghibli movies which were directed by Miyazaki Hayao were more concerned about the issues in Japanese culture and society. We notice that American animation movies are more imaginative and creative which construct an ideal artistic world for the audience; on the other hand, most of the Japanese animation movies reveal the imperfection of the society and provide an opportunity for consumers to reflect on themselves. In conclusion, stylistic art productions from both Disney and Ghibli are not only artistically important but also culturally representative. The artworks from these two studios respectively reflect the general trend in animation movies and art flavors of the targeted audience among years in Western and Eastern culture. In the future, we can use more techniques in analyzing the advanced image statistics in order to perform better cultural analysis on art.

<div align='center'>
	<p>Word Cloud for Disney</p>
	<img src='https://raw.githubusercontent.com/ucsd-dsc-arts/dsc160-midterm-group9/master/results/Disney%20Movie%20Plot%20Keywords.jpg' width=500>
	<br/>
	<p>Word Cloud for Ghibli</p>
	<img src='https://raw.githubusercontent.com/ucsd-dsc-arts/dsc160-midterm-group9/master/results/Ghibli%20Movie%20Plot%20Keywords.jpg' width=500>
</div>


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
