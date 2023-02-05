# Arabic Image Captioning using Pre-training of Deep Bidirectional Transformers

## Introduction
This repository contains source code necessary to reproduce the results presented in the paper. It also contains a python notebook

## Datasets
+ **Flickr8k:** Image features, object tag labels (English and Arabic)  and captions available on [Huggingface](https://huggingface.co/datasets/jontooy/Flickr8k-Image-Features)
+ **MS COCO:** Image features and object tag labels are available on the [OSCAR repo](https://github.com/microsoft/Oscar). Arabic captions are available on the [Arabic-COCO repo](https://github.com/canesee-project/Arabic-COCO).

## Models
All of our models are named after the scheme *modelBatchSize-dataset*, where model is our initialization model, *BatchSize* is the training batch size and *dataset* is the dataset trained on. For example, one of our best performing models was initialized on [AraBERT (bert-base-arabertv02)](https://huggingface.co/aubmindlab/bert-base-arabertv02) and trained with a batch size of 32 on [Flickr8k](https://huggingface.co/datasets/jontooy/Flickr8k-Image-Features). 

The table below presents the final test scores (BLEU-1,2,3,4, ROUGE-L, METEOR, 546 CIDEr and MUSE) of a selection of our models.

| Model               | B1 | B2 | B3 | B4 | ROUGLE-L | METEOR | CIDEr | MUSE |
|---------------------|----|----|----|----|----------|--------|-------|------|
| [AraBERT32-Flickr8k](https://huggingface.co/jontooy/AraBERT32-Flickr8k)   |**0.391**|**0.264**|0.150|0.092|0.331|0.314|0.415|**0.671**|
| [AraBERT32-COCO](https://huggingface.co/jontooy/AraBERT32-COCO)      |0.365|0.221|0.129|0.0715|0.310|**0.317**|0.36|0.669|
| [AraBERT256-Flickr8k](https://huggingface.co/jontooy/AraBERT256-Flickr8k) |0.387|0.244|**0.151**|**0.093**|**0.334**|0.312|**0.428**|0.66|
| [GigaBERT32-Flickr8k](https://huggingface.co/jontooy/GigaBERT32-Flickr8k) |0.386|0.241|0.144|0.0827|0.331|0.315|0.403|0.669|
| [GigaBERT32-COCO](https://huggingface.co/jontooy/GigaBERT32-COCO)     |0.36|0.215|0.124|0.0708|0.308|0.311|0.344|0.668|

## Supplementary Materials

### Software

The supplementary software files are the following:
-  **testrun_captioning.py**
	- Modified version of the file **oscar/run_captioning.py** originially provided in the [OSCAR github](https://github.com/microsoft/Oscar)
	- Use tag `--evaluate_during_training` together with tag `--val_yaml path/to/val.yaml ` to output validation loss and accuracy during training on validation dataset specified in `val.yaml`
	- Use tag `--save_steps n` to save model checkpoint every *n* epochs

### Data

The supplementary data files are the following:
- **object_tags_dict.json**
	- 1,144 English object tags detected in the Flickr8k dataset using VinVL
	- 1,144 Arabic object tags translations using the Google Translate API
	- All object tag indices are chosen to match the label map provided by VinVL ([Download link](https://penzhanwu2.blob.core.windows.net/sgg/sgg_benchmark/vinvl_model_zoo/VG-SGG-dicts-vgoi6-clipped.json))
- **object_tags_annot.csv**
	- Validation of 112 (10% sample of total) object tags translation provided in **object_tags_dict.json**, by two Arabic experts
	- Inter-Annotator Agreement (IAA) between the two Arabic experts
	- All object tags are validated on a scale 1-3 (1: incorrect, 2: partly correct, 3 : correct)
- **human_eval_annot.csv**
	- Human annotation on a sample of predictions from AraBERT32-COCO on the Flickr8k test-split
	- The sample contains 30 image-caption pairs in total. The top 10, median 10 and bottom 10 image-caption pairs sorted by MUSE similarity with any reference caption
	- All scores are made by two Arabic experts using the guidelines of THUMB

## Citations

Please consider citing this paper if you use the models:
```
@inproceedings{emami-etal-2022-arabic,
    title = "{A}rabic Image Captioning using Pre-training of Deep Bidirectional Transformers",
    author = "Emami, Jonathan  and
      Nugues, Pierre  and
      Elnagar, Ashraf  and
      Afyouni, Imad",
    booktitle = "Proceedings of the 15th International Conference on Natural Language Generation",
    month = jul,
    year = "2022",
    address = "Waterville, Maine, USA and virtual meeting",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.inlg-main.4",
    pages = "40--51",
    abstract = "",
}
```
Or cite the original masterthesis:

```
@mastersthesis{emami2022aracap,
   author = {Jonathan Emami},
   title = {Arabic Image Captioning using Pre-training of Deep Bidirectional Transformers},
   school = {Lund University},
   year = 2022
}
```
