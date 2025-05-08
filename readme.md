
nvcc 12.9

```
conda create -n ViHGNN python=3.12 -y
```

## Requirements
```
pip install -r requirements.txt
```

## ViHGNN Code
Paper: [Vision HGNN: An Image is More than a Graph of Nodes](https://openaccess.thecvf.com/content/ICCV2023/papers/Han_Vision_HGNN_An_Image_is_More_than_a_Graph_of_ICCV_2023_paper.pdf)

## Training
- Training ViHGNN:
```
python train.py datasets/tiny-imagenet-200/ --output outputs/
python train.py datasets/tiny-imagenet-200/ --model vihg_ti_224_gelu --output outputs/ --sched cosine --epochs 300 --opt adamw -j 8 --warmup-lr 1e-6 --mixup .8 --cutmix 1.0 --model-ema --model-ema-decay 0.99996 --aa rand-m9-mstd0.5-inc1 --color-jitter 0.4 --warmup-epochs 20 --opt-eps 1e-8 --repeated-aug --remode pixel --reprob 0.25 --amp --lr 2e-3 --weight-decay .05 --drop 0 --drop-path .1 -b 16 
```
- Training Pyramid ViHGNN:
```
python train.py datasets/tiny-imagenet-200/ --model pvihg_ti_224_gelu --output outputs/ --sched cosine --epochs 300 --opt adamw -j 8 --warmup-lr 1e-6 --mixup .8 --cutmix 1.0 --model-ema --model-ema-decay 0.99996 --aa rand-m9-mstd0.5-inc1 --color-jitter 0.4 --warmup-epochs 20 --opt-eps 1e-8 --repeated-aug --remode pixel --reprob 0.25 --amp --lr 2e-3 --weight-decay .05 --drop 0 --drop-path .1 -b 16 
```