# laionide 

Shout out to stability.ai for donating the compute to [laion](https://discord.gg/8pSACZJk) needed for this to be possible.

## Laionide (v3)

Comparison:

OpenAI `glide-base-filtered` (top) and `laionide-v3` (bottom).

![](/compare.png)

> "People are walking with umbrellas in the rain" 

Files:
- [laionide-v3-base.pt](https://github.com/afiaka87/laionide/releases/download/Checkpoints/laionide-v3-base.pt)

Inference:
- [replicate](https://replicate.com/laion-ai/laionide-v3)
- [colab](https://gist.github.com/laion-ai/8655b15c94bf0e80f586ce54cfe39ab5#file-laionide-v3-ipynb)
- [locally](https://github.com/laion-ai/pyglide)

Results:
- [comparison to openai W&B report](https://wandb.ai/afiaka87/laionide-v3-glide/reports/Laionide-Version-3-Benchmark--VmlldzoxNjE0MTE3)

Notes:
- You can use `laionide-v2-sr.pt` to upscale the outputs from `laionide-v3-base.pt`.
- There are watermarks in some outputs. You can try to prompt engineer this away, but it isn't always possible. `royalty free` seems to work well. 

Training details:
- finetuned `laionide-v2-base.pt` for 9 epochs on a subset of CC12M (~1.5 million pairs), COCO (~100K pairs), virtual genome (~100K pairs), and open images localized annotations (~800K pairs). 
- 20% of unconditional/empty token, per the paper.

## Laionide (v2)

Files:
- [laionide-v2-base.pt](https://github.com/afiaka87/laionide/releases/download/Checkpoints/laionide-v2-base.pt)
- [laionide-v2-sr.pt](https://github.com/afiaka87/laionide/releases/download/Checkpoints/laionide-v2-sr.pt)

Inference:
- [replicate](https://replicate.com/laion-ai/laionide-v2)

Training details:
- Data was removed from training given any of the following:
- Value of 'NSFW' or 'LIKELY' in the nsfw column from LAION's metadata (better than nothing)
- Images which originally had an aspect ratio greater than 1.3 (or) less than 0.8
- The original width or original height is less than 256 pixels.
- Captions were checked against a list of slurs. If a slur is in the caption, it is removed. I won't be publishing the slurs.


## Laionide (v1)

Files (Links currently broken)
- https://www.dropbox.com/s/mchzd28p9ees0db/laionide-base.pt
- https://www.dropbox.com/s/7cxn0gelotpocun/laionide-upsample.pt

Training details

- GLIDE finetune on laion over both the base model 
- 1M captions seen for 2 epochs with 20% chance of unconditional token
- Upsample model sees 200K samples.

Inference
- [colab](https://gist.github.com/afiaka87/5f64e4de49b50554270a0a6ece243014#file-laionide-ipynb)
- [replicate](https://replicate.com/laion-ai/laionide)
