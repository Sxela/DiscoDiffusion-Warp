# Disco Diffusion v5.2 - WarpFusion

[![Disco Diffusion v5.2 - Warp](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Sxela/DiscoDiffusion-Warp/blob/main/Disco_Diffusion_v5_2_Warp.ipynb)
![visitors](https://visitor-badge.glitch.me/badge?page_id=sxela_ddwarp_repo)

[Discuss on Discord](https://linktr.ee/devdef) (keeping it on linktree now so it's always an active link)

# About
This version improves video init. You can now generate optical flow maps from input videos, and use those to:
- warp init frames for consistent style 
- warp processed frames for less noise in final video

## Init warping
The feature works like this: we take the 1st frame, diffuse it as usual as an image input with fixed skip steps. Then we warp in with its flow map into the 2nd frame and blend it with the original raw video 2nd frame. This way we get the style from heavily stylized 1st frame (warped accordingly) and content from 2nd frame (to reduce warping artifacts and prevent overexposure)

# Changelog

### 27.05.2022
- Add existing flow check, now generate only if no flow found
- Add comprehensive error reporting for missing video_init, video frames, flow files
- Fix non alphanumeric batch names not working 
- Fix frames not being sorted before creating output video
- Fix incorrect RAFT root foder on local machines 
- Add storing RAFT on gdrive

### 23.05.2022
- Add [colab](https://github.com/Sxela/DiscoDiffusion-Warp/blob/main/image_morphing_3d.ipynb) for 3d animation only 

### 22.05.2022:
- Add saving frames and flow to google drive (suggested by Chris the Wizard#8082)
- Add back consistency checking

### 18.05.2022
- Update 512x512 and secondary model urls

### 17.05.2022
- Remove consistency checking for stability

### 15.05.2022
- Add 256x256 comis faces model

### 22.04.2022:
- Add ViT-L/14@336px
### 21.04.2022: 
- Add warp parameteres to saved settings
### 16.04.2022:
- Use width_height size instead of input video size
- Bring back adabins and 2d/3d anim modes
- Install RAFT only when video input animation mode is selected
- Generate optical flow maps only for video input animation mode even with flow_warp unchecked, so you can still save an obtical flow blended video later
- Install AdaBins for 3d mode only (should do the same for midas)
- Add animation mode check to create video tab 
### 15.04.2022: Init

### Settings: 
(Located in animation settings tab)

Video Optical Flow Settings:
- flow_warp - check to warp
- flow_blend: 0 - you get raw input, 1 - you get warped diffused previous frame 
- check_consistency: check forward-backward flow consistency (uncheck unless getting too many warping artifacts)

## Output warping
This feature is plain simple - we just take any frame, warp in to the next frame, blend with real next frame, get smooth noise-free result.

### Settings: 
(located in create video tab)
blend_mode: 
- none: just mash frames together in a video
- optical flow: take frame, warp, blend with the next frame
- check_consistency: use consistency maps (may prevent warping artfacts)
- blend: 0 - you get raw 2nd frame, 1 - you get warped 1st frame

## TODO: add automatic flow map management (i.e. create only when needed)

This is a variation of the awesome [DiscoDiffusion colab](https://colab.research.google.com/github/alembics/disco-diffusion/blob/main/Disco_Diffusion.ipynb#scrollTo=Changelog)

If you like what I'm doing you can check my linktree
- follow me on [twitter](https://twitter.com/devdef)
- tip me on [patreon](https://www.patreon.com/sxela) 

Thank you for being awesome!
