# ML_final_project
This is a competition on kaggle (https://www.kaggle.com/competitions/tabular-playground-series-aug-2022). The task is a binary classification problem, you need to find out if a product will fail after some destruction. Please see more detail in the link.

## Environment
- Windows 11 64bit, wsl2
- Python 3.8.10
- autogluon 0.6.1
- kuma_utils
    - from github : https://github.com/analokmaus/kuma_utils
    - git clone https://github.com/analokmaus/kuma_utils.git
 
## Usage
0. check the environment (I wrote git clone 'kuma_utils' and pip install autogluon.tabular for you in my code)
1. download dataset from competition here : https://www.kaggle.com/competitions/tabular-playground-series-aug-2022/data . 
2. git clone my code
3. download my saved model here : https://drive.google.com/drive/folders/18dfo1v3agAFcpg-Iq6gciRTgxe1C1hJu?usp=share_link, put my saved model to correct path 
4. update the dataset path on your own or follow the directory tree bellow
5. run train.ipynb first to train your own model, after training, please **restart and change saved model path first**, then run inference.ipynb to predict. (more about this below!!)

### preventing 'list' object is not callable
For more clear code, I change data type of 'all_attribute' while rin time, **so please do 'restart' before every 'run all'**

### How autogluon save its model?
- You can see 'predictor.save()' in the last line of train.ipynb, it will create a dir 'AutogluonModels' where .ipynb are (if not exist).  
- Every time you call this function it will generate a dir name like 'ag-20230107_133316' in dir 'AutogluonModels' , it means every predictor.fit() will generate a new dir for this model.  
- That's the reason why you should change the saved model path in inference.ipynb after every training, you will find predictor.save() output something like "TabularPredictor saved. To load, use: predictor = TabularPredictor.load("AutogluonModels/ag-20230107_133316/")",just copy this line and replace in inference.ipynb

### directory tree
- your project dir
  - AutogluonModels (saved model)
    - ag-20230107_133316 
    - ... (some similar dir name)
  - train.ipynb
  - inference.ipynb
  - tabular-playground-series-aug-2022 (dataset you download from kaggle)
  - kuma_utils (Package you git clone from github link above, I'll do this in my code.)
  - submission.csv (after you run inference.ipynb, the predict result will save in this file)
  
## Result
1. got 0.59175 on private dateset in the competition (the 1st place while competition got 0.59128)
![image](https://user-images.githubusercontent.com/71379735/211155420-c9d29667-f4be-4362-86e3-f26b3c051e4d.png)
2. you can find my saved model here : https://drive.google.com/drive/folders/18dfo1v3agAFcpg-Iq6gciRTgxe1C1hJu?usp=share_link  

## Reference
- https://www.kaggle.com/code/qqzzxxdd/private-score-0-59168-simple-fe-autogluon/notebook
- https://www.kaggle.com/code/ambrosm/tpsaug22-eda-which-makes-sense
- https://github.com/analokmaus/kuma_utils
