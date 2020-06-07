# Assignment 2: Clustering and Visualization

To run the notebook: `jupyter lab`

Try to run the above models on a dataset with cropped face images, as done [here](https://stackoverflow.com/questions/13211745/detect-face-then-autocrop-pictures) 

---

### Description

In this assignment, you will analyze static image-based data. You will be given a dataset representing “Phoebe Buffay" reactions from the famous TV show F.r.i.e.n.d.s.

#### Dataset

Download the dataset here. Credit: This dataset was curated by Bita Azari, a graduate student in the Rosie Lab, specifically for this assignment. AU data was extracted using OpenFace. Please do not distribute or post outside this course.

This data contains 53 videos (~5000 images) of Phoebe in a context, and two corresponding .csv files of extracted AUs for each image. OpenFace's single-person AU detector was used:

single_person_au_presence: This set of .csv files represents the presence of the AUs (0,1)
single_person_au_intensity: This set of .csv files represents the intensity of AUs (0-5).
The .csv files contain 3 other columns, other than AUs:

timestamp: the timestamp of the data, which can be used to correlate images from videos
confidence: the confidence of extracted AUs 
success: if the confidence of AUs is lower than a threshold, the success field will show 0. 
You are also provided the complete raw data extracted using OpenFace's multi-person detector (all_features_multiperson), if you wish to use it.

Check this link (Links to an external site.) out for further information about AUs.

Hints:

You may need to use tools such as FFMPEG (Links to an external site.) to extract frames of a given video.
Prune your data through any type of pre-processing that you wish, e.g. remove frames with low confidence or success equal to 0
Aggregate all .csv files into one data structure. You’ll need to label each row with its corresponding video. 
Tasks

Gaussian Mixture Model and Visualization. The first goal here is to use AUs to "soft-cluster" and visualize the distribution of expressions portrayed by Phoebe using Gaussian Mixture Models. You will need to optimize the number of components using Bayesian Information Criterion (BIC), and report how many components you find best fits the data. What is the responsibility for each component? Once you find the optimal number of components, give each Gaussian mean a unique name which represents how you perceive it. Hint: Inspect the images closest to each mean. 
Dimensionality Reduction. Apply UMAP (Links to an external site.) to the original data, and perform a visualization. Apply the GMM from (1) again to the data, in this reduced feature space, again optimizing the number of components using BIC. Describe each resulting Gaussian component in terms of the features, in layperson's terms.
Soft Classification. Finally, you will use your trained model(s) to soft-classify the 3 test videos (~100 images) provided. For each image, your code should find the most similar component and have it provide your selected name(s) from (1).  Select a likelihood threshold such that images can be classified as "unknown" if they are not well classified.
What to Submit

This is a solo assignment. You will submit a Jupyter Notebook in Python (.ipynb) containing your code and explanations. The text of the notebook should include:

Your proposed components and qualitative descriptions
Examples of best and worst classifications from the test set
A discussion on context and examples of where classification using AUs alone may fail. What extra features might we need to extract?
Discussion on sub-emotions. Did all smiles fall into one cluster when applying UMAP? If not, elaborate on different smile clusters.
Briefly discuss the dataset for this assignment. If we used the above-trained GMM to classify other people's facial expressions, in what ways might the results be limited or biased?
Use of External Libraries

You are allowed to use external libraries such as numpy, scipy, sklearn and UMAP, but you must note this in the header comments of your code (i.e. place links).

#### Grading

This a typical research project, where we are not looking for a "right answer". Your grade will depend on the quality of your analysis given the tools provided, and discussion of limitations.

Academic Integrity

As usual, you must submit your own work. The TAs will use MOSS to check for similarities of code.
