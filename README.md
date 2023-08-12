![Python 3.6](https://img.shields.io/badge/python-3.6-green.svg)
>We will publish the code after the paper is published. Thank you for your attention.

>  This repository contains the official implementation code of the paper Deep modular Co-Attention Shifting Network for Multimodal Sentiment Analysis.
**Note:** We strongly recommend that you browse the overall structure of our code at first. If you have any question, feel free to contact us.



In this framework, we support the following methods:

|     Type    |   Model Name      |     From                |
|:-----------:|:----------------:|:------------------------:|
| Baselines |[TFN](models/singleTask/TFN.py)|[Tensor-Fusion-Network](https://github.com/A2Zadeh/TensorFusionNetwork)|
| Baselines |[MulT](models/singleTask/MulT.py)(without CTC) |[Multimodal-Transformer](https://github.com/yaohungt/Multimodal-Transformer)|
| Baselines |[MISA](models/singleTask/MISA.py) |[MISA](https://github.com/declare-lab/MISA)|
| Missing-Task  |[TFR-Net](models/missingTask/TFR_NET)|      [TFR-Net](https://github.com/Columbine21/TFR-Net)  |

#Data Preprocessing

1. Download datasets from the following links.

- MOSI
> download from [CMU-MultimodalSDK](http://immortal.multicomp.cs.cmu.edu/raw_datasets/processed_data/)

- SIMS
> download from [Baidu Yun Disk](https://pan.baidu.com/share/init?surl=XmobKHUqnXciAm7hfnj2gg) [code: `mfet`] or [Google Drive](https://drive.google.com/drive/folders/1A2S4pqCHryGmiqnNSPLv7rEg63WvjCSk)  
> **Notes:** Please download new features `unaligned_39.pkl` from [Baidu Yun Disk](https://pan.baidu.com/share/init?surl=XmobKHUqnXciAm7hfnj2gg) [code: `mfet`] or [Google Drive](https://drive.google.com/drive/folders/1A2S4pqCHryGmiqnNSPLv7rEg63WvjCSk), which is compatible with our new code structure. The `md5 code` is `a5b2ed3844200c7fb3b8ddc750b77feb`.

1. Download [Bert-Base, Chinese](https://storage.googleapis.com/bert_models/2018_11_03/chinese_L-12_H-768_A-12.zip) from [Google-Bert](https://github.com/google-research/bert).  

2. Convert Tensorflow into pytorch using [transformers-cli](https://huggingface.co/transformers/converting_tensorflow_models.html)  

3. Install python dependencies

4. Organize features and save them as pickle files with the following structure.

> **Notes:** `unaligned_39.pkl` is compatible with the following structure

###### Dataset Feature Structure

```python
{
    "train": {
        "raw_text": [],
        "audio": [],
        "vision": [],
        "id": [], # [video_id$_$clip_id, ..., ...]
        "text": [],
        "text_bert": [],
        "audio_lengths": [],
        "vision_lengths": [],
        "annotations": [],
        "classification_labels": [], # Negative(< 0), Neutral(0), Positive(> 0)
        "regression_labels": []
    },
    "valid": {***}, # same as the "train" 
    "test": {***}, # same as the "train"
}
```

5. Modify `config/config_regression.py` to update dataset pathes.

```
