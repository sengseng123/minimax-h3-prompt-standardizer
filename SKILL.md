---
name: h3-realistic-closeup-dialogue
description: Create concise bilingual MiniMax H3 production prompts for photorealistic facial close-ups with a short spoken line and optional character reference image. Use for intimate selfie, bedroom, vlog, confession, reaction, or micro-expression shots where face identity, eyes, eyelashes, skin texture, lip sync, and natural performance matter more than complex action. Do not use for multi-scene stories, action sequences, animation, or prompt analysis.
---

# H3 Realistic Close-up Dialogue

Return only these two sections:

```text
[中文 H3 生产 Prompt]
<Chinese prompt>

[English H3 Production Prompt]
<English prompt>
```

Do not add analysis, explanations, options, checklists, or next steps.

## Build the micro-scene

Treat the request as one complete facial-performance beat:

```text
Starting pose → eye contact and micro-expression → short spoken line → visible emotional aftertaste
```

- Use one continuous shot unless the user explicitly requests a cut.
- Use the requested duration. For one short line, default to 5 seconds when duration is omitted.
- Keep movement minimal and observable: breathing, one blink, slight finger relaxation, a small gaze adjustment, natural lip movement, and a restrained final smile or reaction.
- Prioritize the face. State the opening shot size, camera height, subject orientation, supporting-hand position if present, slow push-in only when useful, and stable final-frame state.
- Describe natural light, realistic pores, fine facial hair, iris texture, pupils, individual eyelashes, lip texture, and minor skin variation. Do not demand impossible simultaneous macro sharpness across the entire face; keep both eyes and eyelashes as the focus plane.

## Reference handling

When an image is provided, begin the Chinese prompt with `图1作为人物参考。` and the English prompt with `Picture 1 as the character reference.` Use the image only to preserve visible identity: exact face, eye shape and color, hairstyle, hair color, facial proportions, body proportions, and overall appearance. Ignore source background, pose, watermark, interface text, and compression artifacts unless the user explicitly wants them.

Never claim to see an unavailable image. If the user refers to a missing reference image, return exactly:

```text
NEEDS_INPUT: 请上传人物参考原图。
```

## Required production content

Keep both language versions semantically aligned and include, in this order:

1. Reference definition when applicable.
2. Video specifications: duration, ratio, resolution when provided, photorealistic live action, continuous shot.
3. Character blocking before the shot description.
4. One numbered close-up shot describing pose, face, micro-actions, spoken dialogue, lip sync, and final state.
5. Voice profile, `overall_soundscape`, and `non_diegetic_music: N/A` unless music is explicitly requested.
6. Visual requirements and prohibitions.
7. Mandatory identity-stability declaration when a character reference is supplied.

Keep user-provided dialogue unchanged in both versions. In the English prompt, wrap the spoken line as `<d>[Chinese] 用户原话</d>` when the line is Chinese. Do not translate dialogue.

## Stability constraints

Always prohibit subtitles, captions, dialogue text, other screen text, logos, and watermarks. All dialogue must be spoken naturally.

When a character image is supplied, prohibit face replacement, identity drift, eye-shape change, pupil drift, crossed eyes, hairstyle change, face-shape change, body-proportion change, malformed hands, extra fingers, lip deformation, and lip-sync errors.

For realism, prohibit beauty smoothing, plastic skin, excessive sharpening, exaggerated catchlights, artificial giant eyes, commercial glamour lighting, theatrical acting, and strong camera shake. Preserve natural skin texture without making blemishes grotesque.

Use quiet diegetic ambience appropriate to the location, plus breathing, subtle fabric or hair movement, and the character's voice. Set `non_diegetic_music: N/A` by default.
