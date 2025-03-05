## LEDiT: Your Length-Extrapolatable Diffusion Transformer without Positional Encoding<br><sub>Official PyTorch Implementation</sub>

### [Paper](https://arxiv.org/abs/2311.17528) | [Project Page](https://shenzhang2145.github.io/ledit/)

![LEDiT samples](visuals/image_gallery.jpg)

This repo contains PyTorch model definitions, pre-trained weights and training/sampling code for our paper exploring 
length-extrapolatable diffusion transformer(LEDiT). You can find more visualizations on our [project page](https://shenzhang2145.github.io/ledit/).

> [**Your Length-Extrapolatable Diffusion Transformer without Positional Encoding**](https://shenzhang2145.github.io/ledit/)<br>
> Shen Zhang<sup>1</sup>*, Yaning Tan<sup>2</sup>*, Siyuan Liang<sup>1</sup>*, Zhaowei Chen<sup>1</sup>, Linze Li<sup>1</sup>, Ge Wu<sup>3</sup>, Yuhao Chen<sup>1</sup>, Shuheng Li<sup>1</sup>, Zhenyu Zhao<sup>1</sup>, Caihua Chen<sup>2</sup>, Jiajun Liang<sup>1</sup>†, Yao Tang<sup>1</sup>†
> <br><sup>1</sup>JIIOV Technology, <sup>2</sup>Nanjing University, <sup>3</sup>Nankai University<br>

Diffusion transformers (DiTs) struggle to generate images at resolutions higher than their training resolutions. The primary  obstacle is that the explicit positional encodings(PE), such as RoPE, need extrapolation which degrades performance when the inference resolution
differs from training. 

In this paper, we propose a Length-Extrapolatable Diffusion Transformer(LEDiT), a simple yet powerful architecture to overcome this limitation.  LEDiT needs no explicit PEs, thereby avoiding extrapolation. The key innovations of LEDiT are introducing causal attention to implicitly impart global positional information to tokens, while enhancing locality to precisely distinguish adjacent tokens. Experiments on 256x256 and 512x512 ImageNet show that LEDiT can scale the inference resolution to 512x512 and 1024x1024, respectively, while achieving better image quality compared to current state-of-the-art 
  length extrapolation methods(NTK-aware, YaRN).  Moreover, LEDiT achieves strong extrapolation performance with just 100k steps of fine-tuning on a pretrained DiT, demonstrating its potential for integration into existing text-to-image DiTs.

This repository contains:

* 🪐 A simple PyTorch [implementation](models.py) of LEDiT
* ⚡️ Pre-trained class-conditional LEDiT models trained on ImageNet (512x512 and 256x256)
* 🛸 A LEDiT [training script](train.py) using accelerate
