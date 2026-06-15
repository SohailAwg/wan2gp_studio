# Example 02: Aram In The Orbital Greenhouse

Use this when you want character, environment, and controlled walking motion.

## Character name

```text
Dr_Aram_Orbital_Greenhouse
```

## WanGP consistency mode

```text
VACE Stand-In 14B - face identity + control
```

## Locked identity prompt

```text
Dr. Aram is a 42-year-old man with a narrow angular face, medium olive skin, deep-set hazel eyes, thick dark eyebrows, short salt-and-pepper curly hair, a neatly trimmed short beard, and a lean tall build. He always wears a white quilted space-agronomy jacket with green shoulder panels, dark utility trousers, black gloves, a transparent wrist display on his left arm, and a small circular greenhouse badge on his chest. Keep his face, beard, hair, age, build, white and green jacket, gloves, wrist display, and circular badge identical in every shot.
```

## Negative identity drift prompt

```text
different person, face drift, clean shaven, long hair, blonde hair, changed beard, changed age, young face, elderly face, inconsistent jacket, missing green shoulder panels, missing badge, missing wrist display, different body shape, distorted hands, extra fingers, broken anatomy, duplicate person, low quality, blurry face
```

## Optional locked style/world prompt

```text
All shots take place inside the same orbital greenhouse corridor. The environment has curved glass walls showing Earth below, rows of hydroponic plants, white ceramic floor panels, soft green grow lights, silver irrigation pipes, condensation on the glass, floating dust motes, and a calm science-fiction documentary camera style. Keep the greenhouse layout, curved glass walls, Earth view, hydroponic rows, green lighting, white panels, and silver pipes consistent across every shot.
```

## Shot prompts

```text
Medium shot of Dr. Aram walking slowly through the same orbital greenhouse corridor, following the motion from the control video. He looks at the hydroponic plants with a focused expression. His white quilted jacket with green shoulder panels, black gloves, left wrist display, and circular greenhouse badge remain clearly visible. Curved glass walls show Earth below, with soft green grow lights and silver irrigation pipes around him.

Side tracking shot of Dr. Aram continuing the same controlled walking motion through the same orbital greenhouse corridor. He gently touches a hydroponic leaf with his black glove while keeping the same face, short salt-and-pepper curly hair, trimmed beard, white and green jacket, dark utility trousers, left wrist display, and circular badge. The same curved glass walls, Earth view, white floor panels, green lights, and silver pipes remain consistent.

Close-up of Dr. Aram stopping beside the same hydroponic plant row, lifting his left wrist display while following the final pause from the control video. His face, beard, hairstyle, age, jacket, gloves, badge, and wrist display remain unchanged. Condensation on the curved glass, Earth below, green grow lights, and silver irrigation pipes stay in the same orbital greenhouse style.
```

## Reference image paths

```text
/kaggle/working/refs/aram_body_white_green_jacket.png
/kaggle/working/refs/aram_orbital_greenhouse_pose.png
/kaggle/working/refs/aram_close_face_beard.png
/kaggle/working/refs/orbital_greenhouse_corridor.png
```

## Optional control video path for SCAIL/VACE-style workflows

```text
/kaggle/working/controls/slow_walk_turn_pause.mp4
```

## Resolution

```text
832x480
```

## Frames

```text
121
```

## Seed

```text
24680
```

## Best first test

Click **Preview Settings**, then **Queue First Shot**. Watch the main WanGP queue, logs, downloads, and gallery for progress. For VACE Stand-In, keep the close-up face reference last in the reference list. If the motion dominates too much and the face drifts, use a shorter control video and a cleaner face reference.
