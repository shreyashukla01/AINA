# AINA: An Image Nearness Analysis

This project is an academic project created for the course INF 385T: Deep Learning and Multimodal Systems

Team KNS (Shreya Shukla - https://github.com/shreyashukla01, Krishna Sri Somepalli - https://github.com/krishnasriSomepalli)

### Motivation
Image similarity is important in tasks like content-based information retrieval, detecting duplicate images, assessing similar images for medical ailments and making recommendations to consumers based on queried images. In the social media realm, it can have multifold benefits in **detecting and flagging inappropriate images**, identifying misinformation and preventing upload of violent and vulgar content. In this project we did a **comprehensive analysis of image similarity detection** where we delve into different models, embeddings, visualizations and more.

### Dataset
We used a subset of Instagram images dataset available on Kaggle.

### Our analysis had different phases as explained below -

**1. Comparison of similarity scores from different models -**
In our analysis, we initially conducted various operations on the images, including cropping, applying Instagram filters, mirroring, and rotating (18 modifications). Subsequently, leveraging models like CLIP and ISC21 (available at https://sites.google.com/view/isc2021), we computed **image similarity scores for the modified images** and averaged them. By utilizing the average similarity score across the different images, we assessed and compared the performance of different models in detecting similarities.

**2. Siamese Network -** Next we created a Siamese network, using ResNet50 as the embedding generator and  a fully connected CNN network for the Dense Layers. 

  <img width="554" alt="Screenshot 2024-02-19 at 6 29 09 PM" src="https://github.com/shreyashukla01/AINA/assets/30028998/08bde2d1-6618-476c-9ede-b2c8f5c26a13">

**3. Embedding Visualizations -** Given the high-dimensional nature of the embeddings (e.g., 50 dimensions for ResNet 50, 512 for CLIP, and 256 for ISC21), we used **dimensionality reduction techniques like t-SNE and UMAP to visualize embeddings** that helped us understand how images are positioned in relation to each other and how far apart they are from one another within the reduced-dimensional space.

Our data for below visualization consists of 4 image categories (Dog, Kid, Party, Skiing). For each category we visualize embeddings of 19 images (1 original and 18 modified).

  <img width="474" alt="Screenshot 2024-02-19 at 6 33 26 PM" src="https://github.com/shreyashukla01/AINA/assets/30028998/b5326820-7125-43d3-afd5-e0f9753928b3">

**4. Evaluation of Cosine Similarity for different embeddings -** This includes the evaluation of cosine similarity using a subset comprising four image categories (Dog, Kid, Party, Skiing), each category includes embeddings for 19 images (1 original and 18 modified). The process involves **normalizing the image embeddings and subsequently calculating the cosine similarity matrices**. This is achieved by taking the dot product of image embeddings and their transpose. Below is the cosine matrix for CLIP model

  <img width="268" alt="Screenshot 2024-02-19 at 9 16 11 PM" src="https://github.com/shreyashukla01/AINA/assets/30028998/f8535ddc-93e0-47d4-8775-4fe131164cfc">

**5. Explainable AI for Object Detection -** In our analysis, a consistent observation emerged: when images undergo cropping, the similarity scores decrease, implying that these algorithms may classify cropped images as dissimilar even if they originate from the same source. This highlights a scenario where **not only image similarity but also object detection becomes crucial**. To delve into this aspect, we leverage the **explainable AI tool GradCAM** (Grad-CAM, 2023) to **visualize the objects detected by both ResNet50 and CLIP models**. 

  <img width="591" alt="Screenshot 2024-02-19 at 6 38 47 PM" src="https://github.com/shreyashukla01/AINA/assets/30028998/ea6e24c8-0b73-4a6f-a58d-e791583bed73">

  <img width="591" alt="Screenshot 2024-02-19 at 6 39 04 PM" src="https://github.com/shreyashukla01/AINA/assets/30028998/80f44186-a458-4247-a7aa-58d7076d66ea">

It's noteworthy that ResNet50, acknowledged for its robust performance in object detection, exhibits the recognition of a singular object correctly, while CLIP, renowned for its prowess in image similarity recognition, identifies both a bus and a girl **under the label "Person."**







