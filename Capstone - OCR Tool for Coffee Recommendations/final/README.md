# Scan My Coffee - OCR Tool for Coffee Recommendations

### Introduction

In recent years, specialty coffee consumers are becoming more interested in their cup of brew. Behind every coffee they drink or brew, there is a wealth of information such as the the coffee bean's country/region of production, tasting notes, and processing method. Such information is often found on the coffee bean packaging, but unless the consumer manually googles that information from the packaging label, there is no way to efficiently find out more about the coffee. From a retailer perspective, more retailers would also want to be able to access what coffee consumers prefer, their likes or dislikes (i.e. what are they googling for).

This gap forms the primary motivation for embarking on this capstone project, and the aims of this project are summarised in the 'Problem Statement' below.

The notebooks should be read in this order: 
<br>
**Part 1**: [OCR_Bulk_vFinal.ipynb](https://github.com/benpoh90/Projects/blob/master/Capstone%20-%20OCR%20Tool%20for%20Coffee%20Recommendations/final/code/OCR_Bulk%20vFinal.ipynb)
<br>
**Part 2**: [Recommender_System_vFinal.ipynb](https://github.com/benpoh90/Projects/blob/master/Capstone%20-%20OCR%20Tool%20for%20Coffee%20Recommendations/final/code/Recommender_System_vFinal.ipynb)
<br>
**Appendix**: [Web_Scrape_vFinal.ipynb](https://github.com/benpoh90/Projects/blob/master/Capstone%20-%20OCR%20Tool%20for%20Coffee%20Recommendations/final/code/Web_Scrape_vFinal.ipynb)

---

### Problem Statement

There are two main goals for the project:
   - **Part 1**: Create a proof-of-concept for an optical character recognition (OCR) tool to capture text data from single-origin coffee bean packaging labels
   - **Part 2**: Deploy NLP techniques to accurately recommend coffees from a online store (sweetmarias.com) by leveraging the text data in Part 1

To narrow down the scope of the project, I will be focussing only on single origin coffee beans.

---

### Datasets

#### OCR
   - 300 images of coffee labels scraped from Instagram and Google Search 

#### Recommender System
   - Data of 350 coffees (country, description, variety etc.) scraped from [Sweet Marias](https://www.sweetmarias.com/)
   
*All image rights reserved to the copyright owners.*

---

### Methodology and Findings

An overview of the architecture is illustrated below:

<img src="https://i.imgur.com/JdPa21d.png"
     alt="architecture"
     style="float: left; margin-right: 10px;" />

**Part 1: OCR**

For text detection, I have chosen to use the EAST (Efficient and Accurate Scene Text) detector which is considered as one of the state-of-the-art deep learning architectures for text dectection. I have chosen to use EAST because it is trained on natural images and is fast (without compromising on accuracy) compared to other text detectors (e.g. YOLO).

For text recognition, I have chosen to use Tesseract OCR. EAST is only a text detection architecture and only creates bounding boxes of text it identifies. Therefore, Tesseract will be deployed to 'recognise' the text in these bounding boxes and generate a best guess of what the text is. There are a few parameters that I have tuned to help improve the accuracy of the results from Tesseract - these will be explained further later.

**Part 2: Recommender System**

The aim is to leverage the text data from the OCR tool to generate recommendations of related coffees to buy from Sweet Marias. For example, if the OCR tool generates these words ['plum, berry, caturra, washed'], we should ideally get recommendations on 5 coffees with very similar descriptions from Sweet Marias.

There are a few different NLP/deep-learning methods that I will try out in this section. These are a baseline TF-IDF model, a feed-forward neural network auto-encoder, a Word2Vec model and a BERT transformer.

This will be a content-based recommender system and recommendations are ranked based on the cosine distance of the word vectors generated from the 'query' (OCR text) and each coffee description from Sweet Marias.

**Findings**

Overall, 
the TF-IDF model satisifes the main aims of the recommender system purely because the input from the OCR tool are single words. In the context of the current project, it is the fastest and works well because it is performing just a keyword search. 

However, in future developments, an advanced model such as BERT is probably more fit for purpose especially if we want to build semantic association in our search. For example, if we have words such as 'grapefruit, lemon, bergamot', the recommendations will be for coffees with high acidity.
  
---

### Acknowledgements

There are the resources which I have found helpful in building this project.

**OCR**
<br>
[EAST Github](https://github.com/argman/EAST)
<br>
[OpenCV Github (for implementation of EAST in Python)](https://github.com/opencv/opencv/tree/4.x/samples/dnn)
<br>
Other Resources:
<br>
[Helpful guide from pyimagesearch on how to implement EAST](https://www.pyimagesearch.com/2018/08/20/opencv-text-detection-east-text-detector/?_ga=2.123146509.781830900.1634551481-1925401864.1633847684)
<br>
[Nanonets guide on OCR with Tesseract](https://nanonets.com/blog/ocr-with-tesseract/)
<br>
[Nanonets guide on OCR with Tesseract](https://nanonets.com/blog/deep-learning-ocr/#text-detection)
<br>
[Pyimagesearch resource on using Tesseract](https://www.pyimagesearch.com/2018/09/17/opencv-ocr-and-text-recognition-with-tesseract/)


**Recommender System**
<br>
[HuggingFace/SentenceTransformers of BERT](https://huggingface.co/sentence-transformers/paraphrase-MiniLM-L6-v2)
<br>
[Gensim's Word2Vec Implementation](https://www.analyticsvidhya.com/blog/2020/08/top-4-sentence-embedding-techniques-using-python/)
<br>
Building Recommender Systems:
<br>
[Analytics Vidya article](https://medium.com/analytics-vidhya/movie-recommender-system-using-content-based-and-collaborative-filtering-84a98b9bd98e)
<br>
[Towards Data Science article](https://towardsdatascience.com/build-a-text-recommendation-system-with-python-e8b95d9f251c)
<br>
Other Resources:
<br>
[Auto-encoders guide by Jeremy Jordan](https://www.jeremyjordan.me/autoencoders/)
<br>
[Helpful article on transformer architectures](https://neptune.ai/blog/bert-and-the-transformer-architecture-reshaping-the-ai-landscape)

---
