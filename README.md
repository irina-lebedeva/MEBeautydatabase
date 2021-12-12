# Facial beauty assessment on multi-ethnic MEBeauty dataset

2550 images of Black, Asian, Caucasian, Hispanic, Indian, Mideastern female and male faces.

Scores collection (AWS SageMaker), data preprocessing, face cropping and alignment, <br />
train and validation with different base models by using PyTorch.

## Usage

Clone this repo.
```bash
git clone https://github.com/irina-lebedeva/MEBeautydatabase
cd MEBeautydatabase/
```
### Train the model with one of the pretrained base model

```bash
python train_val.py train.py --base_model [choosen base model] --train_augmentation [augmented train set or not]
                                 --batch_size [batch size] --epochs [number of epochs]
```
Please note that data augmentation is time-consuming.

Possible base models: densenet, mobilenet, alexnet, vgg16 (default)

### Prediction

```bash
 python predict.py  --image_path [path to the image for prediction] --model_path [pretrained model filename]
    
```
Default image  - `/inference_samples/girl.jpg`

Default model `/models/model.pht`

### Face cropping and alignment

Crop all the files in the folder and its subfolders and save it to a new folder with the same structure.<br />
Based on DeepFace https://github.com/serengil/deepface

Options: opencv (haar cascade + Adaboost), dlib (HOG + linear SVM), mtsnn, retinaface (RetinaNet)

```bash
 python face_crop_align.py  --images_path [path to the folder with images] 
 --results_path [folder where the cropped images should be saved] 
 --method [one of the backends mentioned above]
    
```
Default folder  - `/images/`

Default backend `opencv`

## Citation
If you use this code for your research, please cite our paper.
```
@article{lebedeva2021mebeauty,
  title={MEBeauty: a multi-ethnic facial beauty dataset in-the-wild},
  author={Lebedeva, Irina and Guo, Yi and Ying, Fangli},
  journal={Neural Computing and Applications},
  pages={1--15},
  year={2021},
  publisher={Springer}
}
```

Note: The MEBeauty can be only used for non-commercial research purpose.

For any questions about this database please contact the authors by sending email to irina.val.lebedeva@gmail.com
