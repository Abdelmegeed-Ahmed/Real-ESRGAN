<br>
<br>

---

### 📖 Real-ESRGAN .

> [[Paper](https://arxiv.org/abs/2107.10833)] &emsp; [[YouTube Video](https://www.youtube.com/watch?v=fxHWoDSSvSc)] &emsp;[[PPT slides](https://docs.google.com/presentation/d/1QtW6Iy8rm8rGLsJ0Ldti6kP-7Qyzy6XL/edit?usp=sharing&ouid=109799856763657548160&rtpof=true&sd=true)]<br>

---



### Installation

1. Clone repo
   
    ```bash
    git clone https://github.com/xinntao/Real-ESRGAN.git
    cd Real-ESRGAN
    ```

1. Install dependent packages

    ```bash
    # Install basicsr - https://github.com/xinntao/BasicSR
    # We use BasicSR for both training and inference
    pip install basicsr
    # facexlib and gfpgan are for face enhancement
    pip install facexlib
    pip install gfpgan
    pip install -r requirements.txt
    python setup.py develop
    ```

---

## ⚡ Quick Inference

### Online inference
   1. You can try in our website: [ARC Demo](https://arc.tencent.com/en/ai-demos/imgRestore) (RealESRGAN_x4plus_anime_6B)
   2. Online Replicate demo: [![Replicate](https://img.shields.io/static/v1?label=Demo&message=Replicate&color=blue)](https://replicate.com/xinntao/realesrgan)
   3. Online Colab demo for Real-ESRGAN: [![Colab](https://img.shields.io/static/v1?label=Demo&message=Colab&color=orange)](https://colab.research.google.com/drive/1k2Zod6kSHEvraybHl50Lys0LerhyTMCo?usp=sharing)
   4. Online Colab demo for for Real-ESRGAN (**anime videos**): [![Colab](https://img.shields.io/static/v1?label=Demo&message=Colab&color=orange)](https://colab.research.google.com/drive/1yNl9ORUxxlL4N0keJa2SEPB61imPQd1B?usp=sharing)

---
## ⚡ Python script


```console
Usage: python inference_realesrgan.py -n RealESRGAN_x4plus -i infile -o outfile [options]...

A common command: python inference_realesrgan.py -n RealESRGAN_x4plus -i infile --outscale 3.5 --face_enhance

  -h                          show this help
  -i --input                  Input image or folder. Default: 'inputs' 
  -o --output                 Output folder. Default: 'results' 
  -n --model_name             Model name. Default: 'RealESRGAN_x4plus' 
         (Model names: RealESRGAN_x4plus | RealESRNet_x4plus | RealESRGAN_x4plus_anime_6B | RealESRGAN_x2plus | realesr-animevideov3 | realesr-general-x4v3) 
  -s, --outscale              The final upsampling scale of the image. Default: 4 
  --suffix                    Suffix of the restored image. Default: out 
  -t, --tile                  Tile size, 0 for no tile during testing. Default: 0 
  --face_enhance              Whether to use GFPGAN to enhance face. Default: False 
  --fp32                      Use fp32 precision during inference. Default: '--fp32'
  --ext                       Image extension. Options: auto | jpg | png, auto means using the same extension as inputs. Default: auto 
  -dn, --denoise_strength     Denoise strength. 0 for weak denoise (keep noise), 1 for strong denoise ability, 'Only used for the realesr-general-x4v3 model' 
  --alpha_upsampler           The upsampler for the alpha channels. Options: realesrgan | bicubic . Default: 'realesrgan' 
  -g, --gpu-id                gpu device to use. Default=None. can be 0,1,2 for multi-gpu 
```

#### Inference general images

---
Inference!
```bash
python inference_realesrgan.py -n RealESRGAN_x4plus -i inputs --face_enhance
```

```
  The most straightforward way of improving model performance is to fine-tune on some specific datasets.
```
---
##  Notes

-  Add the **realesr-general-x4v3** model - a tiny small model for general scenes. It also supports the **-dn** option to balance the noise (avoiding over-smooth results). **-dn** is short for denoising strength.
-  [The inference code](inference_realesrgan.py) supports: 1) **tile** options; 2) images with **alpha channel**; 3) **gray** images; 4) **16-bit** images.
-  The training codes have been released. A detailed guide can be found in [Training.md](docs/Training.md).

---

