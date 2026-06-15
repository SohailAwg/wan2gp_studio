# Plugin User Guide: Character And Environment Consistency

This guide explains how to use the **Character Consistency Studio** plugin to keep a character, outfit, visual style, and environment stable across multiple WanGP shots.

The plugin is available in the **Characters** tab after it is enabled. It creates reusable character packs and exports WanGP settings JSON files under `character_packs/`.

Environment consistency does not currently use a separate Environment tab. Use the same plugin by writing a locked world/style prompt, using location references when the selected model supports references, and repeating the same environment anchor in every shot.

## What This Plugin Does

The plugin helps you build a repeatable generation recipe:

- A character name.
- A locked identity prompt.
- A negative prompt against identity drift.
- An optional locked style/world prompt.
- One or more reference images.
- One or more shot prompts.
- A model-specific WanGP settings manifest.

Use it when you want the same character to appear in several shots without changing face, age, body shape, clothing, props, or overall visual world.

## Step 1: Enable The Plugin

1. Start WanGP.
2. Open the **Plugins** tab.
3. Find **Character Consistency Studio**.
4. Check the plugin checkbox.
5. Click **Save and Restart**.
6. Wait for WanGP to restart.
7. Refresh the browser tab.
8. Confirm that a **Characters** tab is visible.

On Kaggle, the public URL may briefly show a restart page or Bad Gateway while the backend restarts. Wait about 30 seconds, then refresh the same Cloudflare URL. Do not rerun the stop cell.

## Step 2: Choose The Right Consistency Mode

Open the **Characters** tab and choose **WanGP consistency mode**.

Use **Bernini-R 14B - multi-reference ingredients** for the normal character plus environment workflow. This is the best first choice when you have several reference images and want the plugin to preserve visual ingredients.

Use **Bernini-R 1.3B - low VRAM ingredients** on Kaggle or smaller GPUs if the 14B mode is too heavy. Start here when VRAM is tight.

Use **VACE Stand-In 14B - face identity + control** when you need face identity plus a control workflow. Put body/outfit references first and the close-up face reference last.

Use **Stand-In 14B - face identity** when you only need one close-up face reference. Extra references are ignored in this mode.

Use **SCAIL-2 14B - animate from reference/control video** when the main need is motion transfer from a control video.

Use **JoyAI-Echo 22B - multi-shot memory story** for memory-style story prompting. This mode does not use image references in the exported settings.

## Step 3: Prepare Character References

Create a small, clean reference set before filling the plugin.

Recommended character reference set:

1. Front face or upper-body portrait.
2. Three-quarter face or profile view.
3. Full-body or waist-up outfit view.
4. Optional prop or signature accessory reference.

Good references are clear, well-lit, not heavily filtered, and show the same age, hairstyle, outfit, and body type you want to preserve.

Avoid references that mix different outfits, ages, haircuts, art styles, face shapes, or lighting unless those differences are intentional and described in the identity prompt.

For Kaggle, keep files in a stable temp or working path that WanGP can read. Example:

```text
/kaggle/working/refs/character_front.png
/kaggle/working/refs/character_body.png
/kaggle/working/refs/character_profile.png
```

## Step 4: Prepare Environment References

For environment consistency, collect references for the recurring place or world.

Recommended environment reference set:

1. Wide establishing image of the location.
2. Close detail image showing materials, colors, props, or signage.
3. Optional lighting reference, such as day, night, neon, fog, sunset, or studio light.

Use these mostly with Bernini modes, because they are reference-friendly. If you mix character and environment references, keep the set small and high quality.

Recommended order for Bernini references:

1. Character face.
2. Character outfit/body.
3. Character side/profile.
4. Environment establishing image.
5. Environment detail image.

If identity starts drifting, remove some environment references and keep only the strongest character references. Then put environment details into the locked style/world prompt instead.

## Step 5: Fill The Character Name

In **Character name**, enter a stable, simple name.

Good examples:

```text
Maya_Red_Jacket
Detective_Arman
Nova_Pilot
```

Avoid changing the name between shots. The exported files use this name, and the generated prompts also benefit from a stable character label.

## Step 6: Write The Locked Identity Prompt

The **Locked identity prompt** is the main identity anchor. Describe only details that must stay the same.

Include:

- Age range.
- Face shape.
- Hair color, hair length, and hairstyle.
- Skin tone.
- Body type and height impression.
- Outfit.
- Signature colors.
- Persistent accessories or props.

Example:

```text
Maya is a 28-year-old woman with an oval face, warm brown skin, dark almond eyes, shoulder-length black wavy hair, and a calm focused expression. She has a slim athletic build and always wears a fitted red leather jacket over a black shirt, dark jeans, small silver hoop earrings, and a worn brass compass necklace.
```

Do not put changing actions here. Keep actions inside the shot prompts.

## Step 7: Write The Negative Identity Drift Prompt

Use **Negative identity drift prompt** to reject common failures.

Good starting prompt:

```text
different person, face drift, changed hairstyle, changed age, inconsistent outfit, different jacket, different body shape, missing necklace, distorted hands, extra fingers, broken anatomy, duplicate face, low quality
```

Add specific negatives when you see a repeated problem.

Examples:

```text
blonde hair, blue jacket, child face, elderly face
```

Do not make the negative prompt so broad that it fights your actual shot. If your scene is dark, do not add `dark lighting` as a negative.

## Step 8: Write The Locked Style/World Prompt

Use **Optional locked style/world prompt** for environment consistency.

This field should describe the recurring world, location, lighting, camera style, color palette, props, and material details that should remain stable.

Example:

```text
The story takes place in the same rain-soaked neon street market at night, with teal and magenta shop signs, wet reflective pavement, steam from food stalls, dense hanging cables, worn metal shutters, and cinematic handheld camera movement. Keep the environment grounded, detailed, and consistent across every shot.
```

For interiors:

```text
All shots are inside the same compact spaceship cockpit with matte white panels, blue instrument lights, scratched transparent displays, black rubber floor mats, and a circular front window showing stars. Keep the layout and lighting consistent.
```

For product or brand worlds:

```text
Use the same clean premium studio environment: softbox reflections, pale gray seamless background, brushed metal table, subtle blue rim light, and minimal luxury advertising style.
```

## Step 9: Add Shot Prompts

Use **Shot prompts (blank line separates shots)**.

Write one shot per paragraph. Separate shots with a blank line.

Each shot should include:

- The same character name.
- The action.
- The camera framing.
- The same environment anchor.
- Any movement or emotion.

Example:

```text
Medium close-up of Maya in the rain-soaked neon street market, standing under a teal sign, looking toward camera with a calm focused expression. Her red leather jacket and brass compass necklace are clearly visible. Slow cinematic push-in.

Wide shot of Maya walking through the same rain-soaked neon street market, wet pavement reflecting magenta and teal signs, steam rising from food stalls. She keeps the same red leather jacket, black shirt, dark jeans, and compass necklace. Smooth tracking shot.

Over-the-shoulder shot of Maya examining a glowing map at the same neon street market stall, the same hanging cables and metal shutters behind her. Her face, hairstyle, outfit, and necklace remain unchanged. Subtle handheld camera motion.
```

Do not ask for a completely different outfit, age, hairstyle, or art style in later shots unless you intentionally want identity drift.

## Step 10: Add Reference Images

You can add references in either of two ways.

Use **Reference image uploads** when you are working interactively in the browser.

Use **Reference image paths (one per line)** when files already exist on disk.

Example:

```text
/kaggle/working/refs/maya_face.png
/kaggle/working/refs/maya_body.png
/kaggle/working/refs/maya_profile.png
/kaggle/working/refs/neon_market_wide.png
/kaggle/working/refs/neon_market_detail.png
```

Keep the reference set focused. More references are not always better. For Bernini, 2-4 strong character references are usually more stable than 8 mixed images.

## Step 11: Add An Optional Control Video

Use **Optional control video path for SCAIL/VACE-style workflows** only when your selected mode needs motion or video control.

Use it for:

- SCAIL-2 animation from a driving video.
- VACE-style controlled motion or scene transfer.

Leave it blank for simple Bernini reference workflows.

Example:

```text
/kaggle/working/controls/walking_motion.mp4
```

The control video should match the action you want. If the control video has a very different body shape, camera angle, or motion, consistency can get worse.

## Step 12: Choose Resolution, Frames, And Seed

Use **Resolution** to set the output shape.

Start with:

```text
832x480
```

Use this for first tests because it is cheaper and faster.

Move to:

```text
1280x720
```

only after the character and environment are stable.

Use **Frames** to control clip length. Good first tests:

```text
81
```

or:

```text
121
```

Use **Seed** for repeatability.

Set:

```text
-1
```

for random tests.

Set a fixed number, such as:

```text
12345
```

when you want to compare prompt or reference changes more fairly.

## Step 13: Preview Settings

Click **Preview Settings** before generating.

Check **Validation** first.

If it says:

```text
Ready.
```

the plugin can build a settings manifest.

If it says:

```text
Add a locked identity prompt.
Add at least one shot prompt.
Add at least one reference image path or upload.
```

fill the missing fields and preview again.

Then inspect **WanGP settings preview**.

Confirm:

- `model_type` matches the mode you selected.
- `image_refs` contains your reference files, unless you selected JoyAI-Echo.
- `prompt` includes the locked identity, locked style/world prompt, and shot direction.
- `negative_prompt` includes your drift blockers.
- `resolution`, `video_length`, and `seed` are correct.

## Step 14: Save The Character Pack

Click **Save Character Pack**.

This saves a reusable pack under:

```text
character_packs/
```

The file contains the character name, mode, identity prompt, negative prompt, style/world prompt, reference images, control video path, and shot prompts.

Use this when you want to preserve the creative setup and edit or reuse it later.

## Step 15: Export WanGP Settings

Click **Export WanGP Settings**.

This saves a model-ready JSON file under:

```text
character_packs/
```

If you wrote one shot prompt, the exported JSON is a single settings object.

If you wrote multiple shot prompts, the exported JSON is a list of settings objects, one per shot.

Use this file for UI processing, API submission, notebook automation, or batch tests.

## Step 16: Queue The First Shot

Click **Queue First Shot**.

Use this as a smoke test before generating every shot.

The plugin queues the first shot in the main WanGP generation queue and returns immediately. Watch the main queue, logs, model downloads, and gallery for progress. The video output appears in the normal WanGP gallery, not inside the plugin panel.

Check:

- Same face.
- Same age.
- Same hairstyle.
- Same outfit.
- Same accessories.
- Same environment style.
- No major hand or anatomy problems.
- No accidental location change.

If the first shot fails, do not generate the whole batch yet. Fix references and prompts first.

## Step 17: Fix Character Drift

If the face changes:

1. Use fewer, clearer face references.
2. Put the best face reference first.
3. Strengthen the locked identity prompt.
4. Add specific negative terms for the wrong face.
5. Lower environment reference count if it competes with the character.

If the outfit changes:

1. Add exact clothing details to the locked identity prompt.
2. Use an outfit/body reference.
3. Repeat key outfit details in every shot prompt.
4. Add negatives for unwanted colors or clothes.

If age or body type changes:

1. State age range and build clearly.
2. Avoid references from different ages.
3. Add negative terms such as `child face`, `elderly face`, or `different body shape`.

## Step 18: Fix Environment Drift

If the location changes:

1. Put the location name and key details in the locked style/world prompt.
2. Repeat the same location phrase in every shot prompt.
3. Use one strong establishing environment reference.
4. Avoid asking for a new place unless it is meant to be a new scene.

If lighting changes:

1. Add exact lighting language to the locked style/world prompt.
2. Repeat lighting in each shot.
3. Remove conflicting words such as `sunny`, `night`, `studio`, or `outdoor` if they do not belong together.

If props disappear:

1. List persistent props in the locked style/world prompt.
2. Mention the important prop in each shot prompt.
3. Add a detail reference image if using Bernini.

## Step 19: Generate Multiple Shots

After the first shot is stable:

1. Add all final shots to **Shot prompts**.
2. Click **Preview Settings**.
3. Click **Export WanGP Settings**.
4. Run the exported settings through your normal WanGP workflow or notebook.

For best consistency, keep shots short and re-anchor identity and environment every shot.

Do not rely on a long prompt once at the top. Each shot should restate the important character and world anchors.

## Step 20: Recommended Kaggle Workflow

1. Reimport the latest notebook from GitHub.
2. Run all cells from top to bottom.
3. Open the Cloudflare public URL from Cell 8B.
4. Go to **Plugins**.
5. Enable **Character Consistency Studio** if it is not enabled.
6. Click **Save and Restart**.
7. Wait about 30 seconds.
8. Refresh the same Cloudflare URL.
9. Open **Characters**.
10. Build and preview your pack.
11. Queue only the first shot.
12. Export settings only after the first shot looks stable.

Do not stop the server while using the public URL. The URL works only while the Kaggle process and tunnel are alive.

## Example Complete Character And Environment Setup

Character name:

```text
Maya_Red_Jacket
```

Mode:

```text
Bernini-R 1.3B - low VRAM ingredients
```

Locked identity prompt:

```text
Maya is a 28-year-old woman with an oval face, warm brown skin, dark almond eyes, shoulder-length black wavy hair, and a slim athletic build. She always wears a fitted red leather jacket over a black shirt, dark jeans, small silver hoop earrings, and a worn brass compass necklace.
```

Negative identity drift prompt:

```text
different person, face drift, changed hairstyle, changed age, inconsistent outfit, different jacket, missing necklace, distorted hands, extra fingers, broken anatomy, low quality
```

Optional locked style/world prompt:

```text
The story stays in the same rain-soaked neon street market at night, with teal and magenta signs, wet reflective pavement, steam from food stalls, dense hanging cables, worn metal shutters, and cinematic handheld camera movement.
```

Shot prompts:

```text
Medium close-up of Maya under a teal shop sign in the same rain-soaked neon street market, looking toward camera with a calm focused expression. Her red leather jacket and brass compass necklace are clearly visible. Slow cinematic push-in.

Wide tracking shot of Maya walking through the same rain-soaked neon street market, wet pavement reflecting magenta and teal signs, steam rising behind her. She keeps the same red leather jacket, black shirt, dark jeans, and compass necklace.
```

Reference image paths:

```text
/kaggle/working/refs/maya_face.png
/kaggle/working/refs/maya_body.png
/kaggle/working/refs/neon_market_wide.png
```

Resolution:

```text
832x480
```

Frames:

```text
81
```

Seed:

```text
12345
```

## Quick Troubleshooting

**Characters tab is missing:** enable the plugin in **Plugins**, click **Save and Restart**, wait, then refresh.

**Public URL shows Bad Gateway after restart:** on Kaggle, wait about 30 seconds and refresh the same URL. If it still fails, rerun Cell 8 and Cell 8B.

**Validation says references are missing:** upload images or paste one image path per line in **Reference image paths**.

**Stand-In ignores references:** Stand-In face mode only uses the first close-up face reference.

**Environment is stable but face drifts:** reduce environment references and keep stronger character references.

**Face is stable but environment drifts:** strengthen the locked style/world prompt and repeat the environment anchor in each shot.

**Generation is too slow or runs out of VRAM:** use Bernini-R 1.3B, reduce resolution to `832x480`, reduce frames to `81`, and test one shot first.
