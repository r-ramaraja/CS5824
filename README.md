# CS5824

Course project for VT CS5824 Spring '23



## Setup

- Clone the repository: `git clone https://github.com/r-ramaraja/CS5824.git`
- Data collection: Run the [data_collection](https://github.com/r-ramaraja/CS5824/blob/main/data-collection.ipynb) Jupyter notebook to download the image data from Google Open Images and segregate them into their respective catgeories.
- Data preprocessing: Run the [data_preprocessing](https://github.com/r-ramaraja/CS5824/blob/main/data-preprocessing.ipynb) Jupyter notebook to preprocess the data and prepare the images and its associated masks for inpainting model inference

## LaMa Inpainting Inference

- Clone the LaMa repository: `git clone https://github.com/advimman/lama.git`
- Setup the environment with the required dependencies mentioned [here](https://github.com/advimman/lama#environment-setup)
- Change `.png` to `.jpg` in the config file given [here](https://github.com/advimman/lama/blob/main/configs/prediction/default.yaml#L10)
- Run the inference as per the steps given [here](https://github.com/advimman/lama#inference-) for each category. Example: `python predict.py --config configs/prediction/default.yaml --input_dir /home/ram/CS5824/images_and_masks/validation/food --output_dir /home/ram/CS5824/output/lama/validation/food`

## Deepfill v2 Inference

- Clone the Deepfill v2 repository: `git clone https://github.com/JiahuiYu/generative_inpainting.git`
- Setup the environment with the required dependencies mentioned [here](https://github.com/JiahuiYu/generative_inpainting#run)
- Run the inference as per the steps given [here](https://github.com/JiahuiYu/generative_inpainting#run) for each category. Example: `python test.py --image /home/ram/CS5824/images_and_masks/validation/food/000000000139.jpg --mask /home/ram/CS5824/images_and_masks/validation/food/000000000139_mask001.png --output /home/ram/CS5824/output/deepfill/validation/food/000000000139_mask001.png --checkpoint pretrained/states_tf_places2.pth`

## Evaluation

- Go to the clone LaMa repository
- Change `.png` to `.jpg` in the config file given [here](https://github.com/advimman/lama/blob/main/configs/eval2_gpu.yaml#L5)
- Run the evaluation script given [here](https://github.com/advimman/lama/blob/main/bin/evaluate_predicts.py) for the inputs and outputs to get the LPIPS, FID, and SSIM metrics. Example: `python bin/evaluate_predicts.py configs/eval2_gpu.yaml /home/ram/CS5824/images_and_masks/validation/food /home/ram/CS5824/output/lama/validation/food /home/ram/CS5824/output/lama/food.csv`
- You can repeat the above steps by using the same LaMa evaluation script for the deepfill v2 outputs as well.
- You can also find the results from the evaluation done for the reports can be found [here](https://github.com/r-ramaraja/CS5824/tree/main/results)
- Run the [results_visualization](https://github.com/r-ramaraja/CS5824/blob/main/results_visualization.ipynb) Jupyter notebook to visualize the results of the inpainting models.
- Please note that the metrics may vary slightly from the ones reported in the report due to the different GPU configuration and also the fact that the report used a downsized version of the dataset (1500 images per category) for the evaluation.