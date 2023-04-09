# Animinoic

Welcome to Animinoic - a latent diffusion model for weebs. This model is intended to generate high quality and detailed anime style with just a few prompts. Like other anime-style Stable Diffusion models, it also supports danbooru tags to generate images.

e.g. **_girl, cat ears, blonde hair, brown hoodie, smile, blush, cat girl, cat tails, close mouth_**

## 🧨 Diffusers

This model can be used just like any other Stable Diffusion model. For more information,
please have a look at the [Stable Diffusion](https://huggingface.co/docs/diffusers/stable_diffusion).

```python
from diffusers import DiffusionPipeline, DPMSolverMultistepScheduler
import torch

repo_id = "YoruAkio/Animinoic"

pipe = DiffusionPipeline.from_pretrained(repo_id, torch_dtype=torch.float16)
pipe.scheduler = DPMSolverMultistepScheduler.from_config(pipe.scheduler.config)
pipe = pipe.to("cuda")

prompt = "girl, cat ears, blonde hair, brown hoodie, smile, blush, cat girl, cat tails, close mouth"

image = pipe(prompt, num_inference_steps=25).images[0]
image.save("girl.png")
```

## Google Colab

Using [Google Colab](https://colab.research.google.com) to run Animinoic:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YoruAkio/Animinoic/blob/main/Animinoic.ipynb)

## License

This model is open access and available to all, with a CreativeML OpenRAIL-M license further specifying rights and usage.
The CreativeML OpenRAIL License specifies:

1. You can't use the model to deliberately produce nor share illegal or harmful outputs or content
2. The authors claims no rights on the outputs you generate, you are free to use them and are accountable for their use which must not go against the provisions set in the license
3. You may re-distribute the weights and use the model commercially and/or as a service. If you do, please be aware you have to include the same use restrictions as the ones in the license and share a copy of the CreativeML OpenRAIL-M to all your users (please read the license entirely and carefully)
   [Please read the full license here](https://huggingface.co/spaces/CompVis/stable-diffusion-license)
