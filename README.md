# Arabic Image Captioning using Pre-training of Deep Bidirectional Transformers
## Introduction
## Datasets
[jontooy/Flickr8k-Image-Features](https://huggingface.co/datasets/jontooy/Flickr8k-Image-Features)
## Models
| Model               | B1 | B2 | B3 | B4 | ROUGLE-L | METEOR | CIDEr | MUSE |
|---------------------|----|----|----|----|----------|--------|-------|------|
| [AraBERT32-Flick8k](https://huggingface.co/jontooy/AraBERT32-Flickr8k)   |**0.391**|**0.264**|0.150|0.092|0.331|0.314|0.415|**0.671**|
| [AraBERT32-COCO](https://huggingface.co/jontooy/AraBERT32-COCO)      |0.365|0.221|0.129|0.0715|0.310|**0.317**|0.36|0.669|
| [AraBERT256-Flickr8k](https://huggingface.co/jontooy/AraBERT256-Flickr8k) |0.387|0.244|**0.151**|**0.093**|**0.334**|0.312|**0.428**|0.66|
| [GigaBERT32-Flickr8k](https://huggingface.co/jontooy/GigaBERT32-Flickr8k) |0.386|0.241|0.144|0.0827|0.331|0.315|0.403|0.669|
| [GigaBERT32-COCO](https://huggingface.co/jontooy/GigaBERT32-COCO)     |0.36|0.215|0.124|0.0708|0.308|0.311|0.344|0.668|
## Citations
Please consider citing this paper if you use the code:
```
@mastersthesis{emami2022aracap,
   author = {Jonathan Emami},
   title = {Arabic Image Captioning using Pre-training of Deep Bidirectional Transformers},
   school = {Lund University},
   year = 2022
}
```
