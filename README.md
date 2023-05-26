# Faster R-CNN

## Setup

```bash
$ pip install -r requirements.txt
$ cd lib
$ python setup.py build develop
```

## Data Preparation

Download the training, validation, test data and VOCdevkit
```bash
$ wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCtrainval_06-Nov-2007.tar
$ wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCtest_06-Nov-2007.tar
$ wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCdevkit_08-Jun-2007.tar
```
Extract all of these tars into one directory named ```VOCdevkit```

```bash
$ tar xvf VOCtrainval_06-Nov-2007.tar
$ tar xvf VOCtest_06-Nov-2007.tar
$ tar xvf VOCdevkit_08-Jun-2007.tar
```

It should have this basic structure

```bash
$VOCdevkit/                           # development kit
$VOCdevkit/VOCcode/                   # VOC utility code
$VOCdevkit/VOC2007                    # image sets, annotations, etc.
# ... and several other directories ...
```
Follow similar steps to get PASCAL VOC 2012. Now we have 
```bash
$VOCdevkit/                           # development kit
$VOCdevkit/VOCcode/                   # VOC utility code
$VOCdevkit/VOC2007                    # image sets, annotations, etc.
$VOCdevkit/VOC2012                    # image sets, annotations, etc.
# ... and several other directories ...
```

## Train

```bash
$ CUDA_VISIBLE_DEVICES=$GPU_ID python trainval_net.py \
                   --dataset pascal_voc_0712 --net res50 \
                   --bs $BATCH_SIZE --nw $WORKER_NUMBER \
                   --lr $LEARNING_RATE --lr_decay_step $DECAY_STEP \
                   --cuda --use_tfb
```

## Test

```bash
$ python test_net.py --dataset pascal_voc_0712 --net res50 \
                   --checksession $SESSION --checkepoch $EPOCH --checkpoint $CHECKPOINT \
                   --cuda --use_tfb
```

## Detection

```bash
$ python demo.py --net res50 \
               --checksession $SESSION --checkepoch $EPOCH --checkpoint $CHECKPOINT \
               --cuda --load_dir path/to/model/directoy
```

## Model

Link：https://pan.baidu.com/s/1ZmKgk_Cro_p6ma13SmVVNA 
Key：58g0 
