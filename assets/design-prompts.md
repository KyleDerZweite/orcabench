# OrcaBench pod artwork

Both assets were generated on 2026-09-05 with the ImageGen skill's bundled API
fallback CLI, using `gpt-image-2` at high quality. The logo used the generation
endpoint. The banner used the image edit endpoint with the logo as a style
reference. The exact prompts are below.

The pod represents several agents moving toward a shared result. Keep each orca
recognizable as an animal. Coordination comes from spacing, shared direction,
and the sweep of the water.

## Compact logo

Requested canvas: 1024 × 1024. The API returned a 1254 × 1254 PNG with alpha.
The original is preserved at `output/imagegen/orca-pod-logo.png`. The README
version at `assets/orca-pod-logo.png` crops empty margins and places the mark
on a 1024 × 1024 pale background. The pod was checked at 64 and 128 pixels.

```text
Use case: logo-brand
Asset type: compact square logo for the OrcaBench orchestration benchmark
Primary request: an original, minimal logo of a coordinated pod of three stylized orcas swimming together.
Scene/backdrop: plain pale background, #FAFCFC.
Subject: three separate black-and-white orcas in a compact, staggered formation, swimming in the same direction. Each has a rounded orca head, tall dorsal fin, white eye patch, white underside, and clear tail flukes. Their bodies curve gently along the same course. Make all three animals visible and distinct.
Style/medium: crisp flat graphic illustration with broad shapes and clean edges. A finished brand mark, drawn with enough simplicity to remain readable at 64 pixels.
Composition/framing: one centered compact mark within a square, with generous even outer margin. Balanced negative space separates the animals. One restrained teal sweep beneath the pod suggests shared motion.
Color palette: near-black #101820, white #FFFFFF, restrained teal #086F73, pale background #FAFCFC.
Constraints: three orcas, recognizable silhouettes, no letters, no words, no watermark, no mockup. Keep white markings large enough to survive reduction.
Avoid: robot parts, circuit boards, network nodes, arrows, connection lines, fish schools, dolphins, sharks, excessive waves, tiny details, gradients, shadows, 3D effects.
```

## README banner

Requested canvas: 2304 × 768. The API returned a 1774 × 887 PNG. The original
is preserved at `output/imagegen/orca-pod-banner.png`. The README version at
`assets/orca-pod-banner.png` is cropped to 3:1 and resized to 1800 × 600.

```text
Input images: Image 1 is a style reference. Create a new wide banner using the same orca design and drawing style.
Use case: logo-brand
Asset type: wide 3:1 README banner for the OrcaBench orchestration benchmark
Primary request: a coordinated pod of five stylized orcas swimming together, conveying orchestration and several agents working toward one result.
Scene/backdrop: a pale #FAFCFC field above a quiet band of pale teal water #DDEEEF.
Subject: five distinct black-and-white orcas in a loose, staggered formation, swimming in the same direction along one gentle curve. Use rounded orca heads, tall dorsal fins, white eye patches, white undersides, and clear tail flukes. The animals share a course while retaining separate silhouettes.
Style/medium: crisp flat graphic illustration with broad shapes and clean edges, matching a minimal logo. Restrained and readable in an open-source research README.
Composition/framing: wide horizontal canvas. The whole pod forms one centered composition across the middle, with comfortable breathing room on every edge. Keep the animals large enough to read on a narrow page. A few restrained teal water strokes follow their shared course.
Color palette: near-black #101820, white #FFFFFF, teal #086F73, pale teal #DDEEEF, pale background #FAFCFC.
Constraints: five recognizable orcas, distinct bodies with no merged anatomy, no letters, no words, no watermark, no mockup.
Avoid: robot parts, circuit boards, network nodes, arrows, connection lines, fish schools, dolphins, sharks, decorative bubbles, dense ocean scenery, tiny details, gradients, shadows, 3D effects.
```

## README integration

The banner opens the README with the alt text "A pod of five black-and-white
orcas swimming together through teal water". The compact logo appears at 128
pixels in the design reference section, with the alt text "OrcaBench logo,
three orcas swimming as a pod".

The project name remains Markdown text. The pod is the visual reference for
orchestration. The existing color table, research scope, and human scoring policy
are unchanged. The original SVG remains as an earlier design reference.
