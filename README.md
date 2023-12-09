# AINA
Team KNS project for INF 385T: Deep Learning and Multimodal Systems

### Prerequisite:
Our datasets are all maintained under the folder path `/content/drive/MyDrive/Colab Notebooks/DL Project/` in Google Drive. We run our notebook on Google Colab with Drive mounted. Please make sure to edit file/folder paths across the notebook to point to the correct locations within your environment before you run any Notebook cells.

## `embeddings.ipynb`
### Contents:
- An exploration of CLIP, ISC21, and ResNet50 embedding models in the context of image similarity where we generate embeddings, calculate cosine similarity for a group of images and compare median aggregations
- Exploration of how low cosine similarity scores can be for look-alikes (in an attempt to determine a suitable threshold value)
- Dataset pre-processing: We apply 18 transformations to a subset of 346 images from the Instagram Images (Kaggle) dataset as described below

### Dataset pre-processing
**Dataset:** [Instagram Images - 1,211,625 posts](https://www.kaggle.com/datasets/shmalex/instagram-images)

**Prerequisite:** Adjust `base` and `save_to` values as needed if you desire to process more images.

We apply the following operations, and for each operation (and sub-operation), there will be a new folder in the `save_to` path for the processed images:

#### 1. Borders: white, black
Given an image of size `width x height`, we identify the bigger dimension as `side` and add borders to the image so that the resultant picture has `side x side` dimensions. However, if `width=height`, we just add borders of width 70px on all sides.  
We use #fff and #000 color borders and this behavior can be customized using `border_colors`.

#### 2. Filters: inkwell, lofi, aden
The supported filters are listed in the [pilgram documentation](https://github.com/akiomik/pilgram). We only use `inkwell`, `lofi`, and `aden`. (`inkwell` is a kind of black and white filter.)

#### 3. Crop to:
The following `position`s are accepted:
- center
- left_half
- right_half
- upper_half
- lower_half
- upperleft_quarter
- upperright_quarter
- lowerleft_quarter
- lowerright_quarter

#### 4. Mirror:
Flips image horizontally (left to right)

#### 5. Rotate: 45°, 90°, 180°
Returns a rotated copy of this image, rotated the given number of degrees counter clockwise around its centre. We rotate by 45°, 90°, and 180° and this behavior can be customized using `angles`.

