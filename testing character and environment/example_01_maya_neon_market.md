# Example 01: Maya In The Neon Market

Use this as a first Kaggle-friendly character and environment consistency test.

## Character name

```text
Maya_Red_Jacket_Neon_Market
```

## WanGP consistency mode

```text
Bernini-R 1.3B - low VRAM ingredients
```

## Locked identity prompt

```text
Maya is a 28-year-old woman with an oval face, warm brown skin, dark almond eyes, shoulder-length black wavy hair, and a slim athletic build. She always wears a fitted red leather jacket over a black shirt, dark jeans, small silver hoop earrings, black ankle boots, and a worn brass compass necklace. Her expression is calm, alert, and focused. Keep her face, age, hairstyle, body shape, red jacket, dark outfit, earrings, boots, and brass compass necklace identical in every shot.
```

## Negative identity drift prompt

```text
different person, face drift, changed face, changed hairstyle, changed hair color, changed age, child face, elderly face, inconsistent outfit, different jacket, blue jacket, missing necklace, missing earrings, different body shape, distorted hands, extra fingers, broken anatomy, duplicate face, low quality, blurry face
```

## Optional locked style/world prompt

```text
The story stays in the same rain-soaked neon street market at night. The environment has teal and magenta shop signs, wet reflective pavement, steam from food stalls, dense hanging cables, worn metal shutters, red paper lanterns, small puddles, and cinematic handheld camera movement. Keep the location, lighting, color palette, street props, wet pavement, and neon reflections consistent across every shot.
```

## Shot prompts

```text
Medium close-up of Maya standing under a teal shop sign in the same rain-soaked neon street market, looking toward camera with a calm focused expression. Her red leather jacket, black shirt, silver hoop earrings, and brass compass necklace are clearly visible. Steam rises behind her, wet pavement reflects magenta signs, and the camera slowly pushes in.

Wide tracking shot of Maya walking through the same rain-soaked neon street market, passing food stalls, hanging cables, red paper lanterns, and worn metal shutters. She keeps the exact same face, shoulder-length black wavy hair, red leather jacket, black shirt, dark jeans, black ankle boots, silver hoop earrings, and brass compass necklace. Wet pavement reflects teal and magenta neon lights.

Over-the-shoulder shot of Maya examining a glowing paper map at a small stall in the same rain-soaked neon street market. The same teal and magenta shop signs, steam, hanging cables, red lanterns, and wet reflective pavement remain visible around her. Her face, hairstyle, outfit, earrings, boots, and brass compass necklace remain unchanged.
```

## Reference image paths

```text
/kaggle/working/refs/maya_front_face.png
/kaggle/working/refs/maya_full_body_red_jacket.png
/kaggle/working/refs/maya_three_quarter_profile.png
/kaggle/working/refs/neon_market_establishing.png
/kaggle/working/refs/neon_market_detail_lanterns.png
```

## Optional control video path for SCAIL/VACE-style workflows

```text

```

## Resolution

```text
832x480
```

## Frames

```text
81
```

## Seed

```text
12345
```

## Best first test

Click **Preview Settings**, then **Queue First Shot**. Watch the main WanGP queue, logs, downloads, and gallery for progress. If Maya's face or outfit drifts, remove the two environment reference images and keep only the three Maya references, while keeping the locked style/world prompt unchanged.
