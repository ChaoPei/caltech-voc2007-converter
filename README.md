# Caltech Pedestrian Dataset Converter to Pascal VOC 2007 format for Faster R-CNN

## Requirements

- OpenCV 2.4.13
- Python 3.4+,
- NumPy 1.10+
- SciPy 0.16+

## Usage (Caltech Pedestrian Dataset Example)

### 1. Prepare dataset

Download caltech dataset, pick up images and annotations from videos.

```
$ ./scripts/caltech-dataset-download.sh
$ ./caltech-parser/parse_annotations.py
$ ./caltech-parser/parse_seqs.py
```

Each `.seq` video is separated into `.png` images. Each image's filename is consisted of `{set**}_{V***}_{frame_num}.png`. According to [the official site](http://www.vision.caltech.edu/Image_Datasets/CaltechPedestrians/), `set06`~`set10` are for test dataset, while the rest are for training dataset.

(Number of objects: 346621)

### 2. Draw and Test

You can draw bounding boxes in the images and get a video for checking.

```
$ ./scripts/test_plot_annotations.py
```

### 3. Create VOC2007 format dataset

Convert images to VOC2007 format dataset.

```
$ ./converter/converter.py --anno [annotations.json path] --images [images path] --dst [voc save path] --dataset [dataset type]
```

* config your properties for VOC2007 annotations and train and test sets in `config.py`.
* make voc_path dir empty is better.

### 4. Complete VOC2007 dataset

Copy other dir from VOC2007 like: `local`, `results`...

## Notice

`./converter/config.py` is a configure file for different dataset.
`./converter/filter.py` can add yourself filter for different interesting objects.
