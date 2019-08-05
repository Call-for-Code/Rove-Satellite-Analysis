# Satellite Imagery Analysis

Analyze satellite imagery for road and building damage. 

### Folders

#### classify

##### `use_dd_classifier`

Use a [pretrained model](https://github.com/qcao10/DamageDetection.git) to classify square image tiles generated by `crop_images`. If an image tile is classified as "damaged," calculate its coordinate bounding box and return it.

##### `use_ibm_api`

Use IBM Watson Visual Recognition custom-trained model API to classify images and return a JSON.

#### preprocess

##### `crop_images`

Use `gdal_warp` to crop GeoTIFFs into square tiles, centered at features of a given Shapefile (in our case, the Shapefile contains building polygons). Also, generate a text file containing classification data for each building.

In `cell [6]`, customize these variables:

- `images_dir`: PATH to directory containing source GeoTIFFs to crop.
- `shapefile_name`: PATH to Shapefile containing features
- `RESULT_DIR`: directory to dump cropped images
- `OFFSET`: coordinate distance from center of cropped square to its edges
- `DIM`:  cropped images are `DIM*DIM` pixels.

#### train

##### building_damage

Use Keras to train a custom model to classify cropped building tiles based on damage level (no damage, affected, minor, major, destroyed).

