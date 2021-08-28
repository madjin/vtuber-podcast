# vtuber-podcast
How to set up various vtuber productions


## Install Software

- **OBS: https://obsproject.com/**
- **VSeeFace: https://www.vseeface.icu/**
  - Best for web cam face tracking
- **VMagicMirror: https://malaybaku.github.io/VMagicMirror/en/index**
  - Best desktop mode support

## Acquire VRM avatar

Double check the terms of use and licenses that come with your avatar. 

- Purchase
  - https://booth.pm/
  - https://cryptoavatars.io/
- Create
  - https://vroid.com/en/studio
  - https://readyplayer.me/ (need to convert to VRM)
- Collect
  - https://hub.vroid.com/en/

## Configure VMagicMirror

1. Load the VRM into VMagicMirror, check "Load current VRM on next startup"
2. Open the Setting Window and go to Layout, check `Free Camera Mode` and move your character around (hold right click + drag / mouse wheel)
3. Position your avatar directly in the middle of the screen surrounded by green, then uncheck `Free Camera Mode` when done

**Tips**

If you want to record your avatar standing somewhere, position it to capture the entire body. If you want to be sitting behind a desk or podium, capture half the body.

4. Check `Free Layout` on Device and drag the arrows to position the mouse / keyboard for your character 

![image](https://user-images.githubusercontent.com/32600939/128775709-56081f30-f9cb-4820-a2db-3f29b1ebc3c9.png)

5. If its on, go to Effects and disable shadows
6. Make sure the right microphone is set by going to the Face tab and looking at LipSync

## Configure VSeeFace

VSeeFace works great with a webcam for face tracking while vtubing. Many great tutorials are listed here: https://www.vseeface.icu/#tutorials

When you're finished configuring, click this tiny x in the corner to hide the UI:

![image](https://user-images.githubusercontent.com/32600939/131228068-632aab5e-698a-4f8c-893c-ab51b7a99a39.png)

Note: You can load into OBS as a transparent video, no need for green screen filter.

## Configure OBS

1. Create a new scene, add a source for window capture with VMagicMirror selected.
2. Make sure the green covers the entire window without clipping the character
3. Make sure your microphone is picking up in the Audio Mixer
4. Go to Settings, Output, and Recording to see where videos get saved

## Recording

When your OBS looks like this, you are ready to record. Hop into a Discord call and start talking.

![image](https://user-images.githubusercontent.com/32600939/128776442-b2fc29c9-b8d3-4cea-94f5-3c01d7e4d7bb.png)

### Record with Screenshare

If using screenshare to present while vtubing, you can setup OBS like the picture below.

![image](https://user-images.githubusercontent.com/32600939/131227862-f06758bc-883c-4e74-bdc6-c2b11be2ee4d.png)

During post editing you'll be able to crop the window and the vtuber avatar into separate videos or UV map them in such a way to spatialize in a 3D scene.

![image](https://user-images.githubusercontent.com/32600939/131227932-53a1120e-aa5c-4238-9cdd-38bd5c7100b3.png)

Example ffmpeg command to split into 2 videos:

`ffmpeg -i test.mp4 -filter_complex "[0:v]crop=290:313:0:103[face];[0:v]crop=954:530:340:114[pres]" -map "[face]" -map 0:a face.mp4 "[pres]" -map 0:a pres.mp4`

#### To-do

- [x] VSeeFace setup
- [x] Avatar + Screen share recording setup
