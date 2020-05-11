# Project Title

DSC160 Data Science and the Arts - Midterm Project Repository - Spring 2020

Project Team Members: 
- Jou-Ying Lee, jol067@ucsd.edu
- Yunlin Tang, yut085@ucsd.edu
- Yupei Zhou, yuz522@ucsd.edu
- Sizhu Chen, sic100@ucsd.edu
- Yuanbo Shi, yus263@ucsd.edu

## Abstract

(10 points) 

Rooted in our group members' common interest in watching movies, and after revision of Professor's comments, we decided to take this Midterm Project as an opportunity to explore critically the intersection between digital films and the arts. 
Movie photos or movie screenshots are one of the very first impressions movie viewers have on each movie. Often times, 
designs of these images would influence viewers' perceptions of movie contents and therefore secondarily affect their evaluations on the movies overall. With these ideas in mind, our group seeks to find out underlying associations between viewers' voted ratings for each film and image statistics/features of each movie poster. We would base our analyses on data including movie posters and movie details both available from IMDB website. Specifically, we would be looking at movies of the particular sci-fi genre. This category is chosen upon reflection on how sci-fi movies most closely resembles "the future" -- and therefore, via assay on these movie covers, we hope to consider these findings as cultural resemblences of pertaining social forms. Believing that the general public would prefer a more "uplifting and wholesome future," we address this subject by comparing what the movie posters tell (image features) by their acquired ratings. That is, based on common perceptions of image data, we hypothesize that
- The more variety of hues a sci-fi movie poster has, the higher its rating will be.
- The brighter a sci-fi movie poster is, the higher its rating will be.
- The more saturated a sci-fi movie poster is, the higher its rating will be.

Besides primary image features discussed above, we would also look into reflecting movie posters' image statistics on each movie's "Plot Keywords." Most mentioned plot keywords would be illustrated by word-clouds with colors associated to results of image processing. Building upon topics covered in class, our analyses would be primarily based on Python. We are expecting to deploy popular image-processing libraries including skimage, OpenCV, Pillow along with Bokeh for interactive visualizations. Results would later be presented in a variety of forms including images and graphs for summary of significant findings, word-clouds for displays of plot keywords results, and interactive charts enabled for better understandings of our project.  

## Data

(10 points) 

This section will describe your data and its origins. Each item should contain a name of the data source, a link to the source, and any necessary background information such as:
- What is your cultural data source? 
- When was it made? 
- Who created the works? 
- Is it digital native, or is it some kind of scan, recording, photo, etc., of an analog form? 

## Code

(20 points)

This section will link to the various code for your project (stored within this repository). Your code should be executable on datahub, should we choose to replicate your result. This includes code for: 

- data acquisition/scraping
- cleaning
- analysis
- generating results. 
- [Modelling](code/modelling.ipynb): ipynb file for feature engineering, model fitting, and model evaluation

Link each of your notebooks or .py files within this section, and provide a brief explanation of what the code does. Reading this section we should have a sense of how to run your code.

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

## Discussion

(30 points, three to five paragraphs)

The first paragraph should be a short summary describing your results.

The subsequent paragraphs could address questions including:
- Why is this culturally relevant?
- How does your computational approach differ from the traditional art historical, musicological, manuel/subjective approach to analyzing your cultural subject? 
- How do you think the original artists/musicians would respond to this type of analysis? Would it change/inform their practice in some way?
- How do your results relate to broader social, cultural, economic political, etc., issues? 
- In what future directions could you expand this work?

## Team Roles

Provide an account of individual members and their efforts/contributions to the specific tasks you accomplished.
- Jou-Ying Lee: wrote Abstract, completed model fitting (modelling.ipynb), and drafted the "Modelling" portion of "Results".

## Technical Notes and Dependencies

Any implementation details or notes we need to repeat your work. 
- Additional libraries you are using for this project
- Does this code require other pip packages, software, etc?
- Does this code need to run on some other (non-datahub) platform? (CoLab, etc.)

## Reference

References to any papers, techniques, repositories you used:
- Papers
- Repositories
- Blog posts
