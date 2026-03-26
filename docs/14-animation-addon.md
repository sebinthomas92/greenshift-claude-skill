# Animation Addon Blocks

The Animation addon provides GSAP-powered animation blocks for modern web animations. Uses the premium GSAP library bundled with Greenshift.

## Block Types

| Block Name | Namespace | Use Case |
|-----------|-----------|----------|
| Animation Container | `greenshift-blocks/animation-container` | Wrap any block with GSAP animations |
| Pin Scroll | `greenshift-blocks/pinscroll` | Pin element while scrolling |
| Lottie/DotLottie | `greenshift-blocks/lottie` | Lottie file animations |
| RIVE App | `greenshift-blocks/rive` | Rive app interactive files |
| Filterable Content | `greenshift-blocks/filterablecontent` | Animated content filtering |
| Image Sequencer | `greenshift-blocks/imagesequencer` | Apple-style image sequence on scroll |
| Video Scroller | `greenshift-blocks/videoscroller` | Apple-style video effect from video file |
| Flip State | `greenshift-blocks/flipstate` | Floating panels, smooth transitions |
| Page Transition | `greenshift-blocks/pagetransition` | Animated transitions between pages |
| Reveal Slide | `greenshift-blocks/revealslide` | Sliding reveal effect |
| Custom Cursor | `greenshift-blocks/customcursor` | Custom cursor following mouse |
| Mouse Follow | `greenshift-blocks/mousefollow` | Elements follow mouse movement |
| Parallax Effect | `greenshift-blocks/parallaxeffect` | Parallax on any block or text |
| Background Parallax | `greenshift-blocks/bgparallax` | Container with background parallax |
| Page Navigation | `greenshift-blocks/pagenavigation` | Section navigation dots |
| Horizontal Scroll | `greenshift-blocks/horizontalscroll` | Horizontal scroll sections |
| Smooth Scroll | `greenshift-blocks/smoothscroll` | Smooth scroll + effect classes |
| Blob Maker | `greenshift-blocks/blobmaker` | Floating gradient blobs |
| Before/After | `greenshift-blocks/beforeafter` | Image comparison slider |
| Effects Preset Kit | `greenshift-blocks/effectskit` | Ready-made motion classes |
| Dynamic 3D | `greenshift-blocks/dynamic3d` | 3D model with dynamic data |

---

## Animation Container (`greenshift-blocks/animation-container`)

The primary animation block. Wraps any content and applies GSAP animations.

### Trigger Types

| Trigger | Value | Description |
|---------|-------|-------------|
| On Load | `"load"` | Plays when page loads |
| On Scroll | `"scroll"` | Plays when scrolled into view (default) |
| On Hover | `"hover"` | Plays on mouse hover |
| On Click | `"click"` | Plays on click |

### Core JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "x": 0,
  "y": 50,
  "s": 0.8,
  "r": 0,
  "rx": 0,
  "ry": 0,
  "o": 0,
  "origin": "center center",
  "custom_origin": false,
  "ease": "power1-inOut",
  "duration": 1,
  "yoyo": false,
  "loop": false,
  "triggertype": "scroll",
  "triggerstart": "top 80%",
  "triggerend": "+=350",
  "triggerscrub": 1,
  "set_from": true,
  "pinReparent": false
}
```

### Transform Properties

| Parameter | Type | Description |
|-----------|------|-------------|
| `x` | number | Horizontal translation (pixels) |
| `y` | number | Vertical translation (pixels) |
| `s` | number | Scale (0.5 = half, 2 = double) |
| `r` | number | Rotation in degrees |
| `rx` | number | Rotation X (3D tilt forward/back) |
| `ry` | number | Rotation Y (3D tilt left/right) |
| `o` | string | Opacity ("0" to "1") |
| `origin` | string | Transform origin (e.g., "center center", "top left") |

### Easing Values

```
"none", "power1-in", "power1-out", "power1-inOut",
"power2-in", "power2-out", "power2-inOut",
"power3-in", "power3-out", "power3-inOut",
"power4-in", "power4-out", "power4-inOut",
"back-in", "back-out", "back-inOut",
"elastic-in", "elastic-out", "elastic-inOut",
"bounce-in", "bounce-out", "bounce-inOut",
"circ-in", "circ-out", "circ-inOut",
"expo-in", "expo-out", "expo-inOut",
"sine-in", "sine-out", "sine-inOut"
```

### HTML Structure

```html
<div id="gspb_gsap-{id}">
  <div id="{id}" class="gs-gsap-wrap"
    data-{param}="{value}"
    data-triggertype="{type}"
    data-duration="{seconds}"
    data-from="yes"
    data-prehidden="1">
    <!-- Inner blocks -->
  </div>
</div>
```

### Data Attributes Mapping

| JSON param | HTML data attr |
|-----------|---------------|
| `x` | `data-x` |
| `y` | `data-y` |
| `s` | `data-s` |
| `r` | `data-r` |
| `rx` | `data-rx` |
| `ry` | `data-ry` |
| `o` | `data-o` |
| `origin` | `data-origin` |
| `ease` | `data-ease` |
| `duration` | `data-duration` |
| `yoyo` | `data-yoyo="yes"` |
| `loop` | `data-loop="yes"` |
| `triggertype` | `data-triggertype` |
| `triggerend` | `data-triggerend` |
| `triggerscrub` | `data-triggerscrub` |
| `set_from` | `data-from="yes"` |
| `prehidden` | `data-prehidden="1"` |

### Example: Scroll-triggered Fade Up

```html
<!-- wp:greenshift-blocks/animation-container {"id":"gsbp-anim01","y":50,"s":0.8,"o":"0","triggerend":"+=350","triggerscrub":1,"set_from":false} -->
<div id="gspb_gsap-gsbp-anim01"><div id="gsbp-anim01" class="gs-gsap-wrap" data-y="50" data-s="0.8" data-o="0" data-duration="1" data-triggertype="scroll" data-triggerend="+=350" data-triggerscrub="1" data-from="yes" data-prehidden="1">
<!-- wp:greenshift-blocks/element {"id":"gsbp-txt01","textContent":"Animated Content","tag":"h2","localId":"gsbp-txt01"} -->
<h2 class="gsbp-txt01">Animated Content</h2>
<!-- /wp:greenshift-blocks/element -->
</div></div>
<!-- /wp:greenshift-blocks/animation-container -->
```

### Example: Hover Animation with Chain

```html
<!-- wp:greenshift-blocks/animation-container {"id":"gsbp-hover01","s":0.9,"duration":0.1,"triggertype":"hover","multiple_animation":"[{\"_id\":\"chain01\",\"y\":20,\"r\":15,\"duration\":0.3}]"} -->
<div id="gspb_gsap-gsbp-hover01"><div id="gsbp-hover01" class="gs-gsap-wrap" data-s="0.9" data-duration="0.1" data-triggertype="hover" data-multianimations="[{\"_id\":\"chain01\",\"y\":20,\"r\":15,\"duration\":0.3}]" data-from="yes">
<!-- Inner blocks -->
</div></div>
<!-- /wp:greenshift-blocks/animation-container -->
```

### Multiple Animation Chain

Use `multiple_animation` for chained/parallel animations:

```json
"multiple_animation": "[{\"_id\":\"step1\",\"y\":50,\"r\":90,\"ease\":\"power1-inOut\",\"duration\":0.6},{\"_id\":\"step2\",\"x\":100,\"r\":180,\"ease\":\"back-inOut\",\"duration\":0.8,\"time\":\">-0.5\"},{\"_id\":\"step3\",\"s\":0.5,\"o\":\"0\"}]"
```

Chain item properties:
- All transform properties (`x`, `y`, `s`, `r`, `rx`, `ry`, `o`)
- `ease` — easing for this step
- `duration` — seconds for this step
- `time` — GSAP position parameter (`">-0.5"` = overlap previous by 0.5s)
- `obj` — CSS selector to animate different element (e.g., `".my-class"`)

### Custom Object Targeting

Animate a different element by CSS class:

```json
"multiple_animation": "[{\"_id\":\"target1\",\"obj\":\".target-element\",\"y\":100,\"r\":90,\"duration\":0.6}]"
```

---

## Pin Scroll (`greenshift-blocks/pinscroll`)

Pins content in viewport while scrolling. Combine with Animation Container for scroll-driven effects.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "triggerstart": "top top",
  "triggerend": "+=700"
}
```

### HTML Structure

```html
<!-- wp:greenshift-blocks/pinscroll {"id":"gsbp-pin01","triggerstart":"top top","triggerend":"+=700"} -->
<div class="wp-block-greenshift-blocks-pinscroll gspb_pinscroll_wrap">
  <div id="gspb_gsapin-gsbp-pin01" class="gs-pin-wrap gs-gsap-wrap"
    data-triggertype="scroll"
    data-triggerstart="top top"
    data-triggerend="+=700"
    data-ease="none"
    data-pinned="yes"
    data-pinforce="yes"
    style="display:flex">
    <!-- Animation container or inner blocks -->
  </div>
</div>
<!-- /wp:greenshift-blocks/pinscroll -->
```

### Example: Pin + Scale Animation

```html
<!-- wp:greenshift-blocks/pinscroll {"id":"gsbp-pin01","triggerstart":"top top","triggerend":"+=700"} -->
<div class="wp-block-greenshift-blocks-pinscroll gspb_pinscroll_wrap"><div id="gspb_gsapin-gsbp-pin01" class="gs-pin-wrap gs-gsap-wrap" data-triggertype="scroll" data-triggerstart="top top" data-triggerend="+=700" data-ease="none" data-pinned="yes" data-pinforce="yes" style="display:flex">
<!-- wp:greenshift-blocks/animation-container {"id":"gsbp-pinanim01","s":0.8,"origin":"center 20%","custom_origin":true,"triggerstart":"top top","triggerend":"+=700","triggerscrub":1,"align":"full"} -->
<div id="gspb_gsap-gsbp-pinanim01" class="wp-block-greenshift-blocks-animation-container alignfull"><div id="gsbp-pinanim01" class="gs-gsap-wrap" data-s="0.8" data-origin="center 20%" data-duration="1" data-triggertype="scroll" data-triggerstart="top top" data-triggerend="+=700" data-triggerscrub="1">
<!-- wp:greenshift-blocks/element {"id":"gsbp-pinimg01","tag":"img","localId":"gsbp-pinimg01","src":"https://placehold.co/2000x1100","alt":"Pinned image","originalWidth":2000,"originalHeight":1100} -->
<img class="gsbp-pinimg01" src="https://placehold.co/2000x1100" alt="Pinned image" loading="lazy" width="2000" height="1100"/>
<!-- /wp:greenshift-blocks/element -->
</div></div>
<!-- /wp:greenshift-blocks/animation-container -->
</div></div>
<!-- /wp:greenshift-blocks/pinscroll -->
```

---

## Lottie/DotLottie (`greenshift-blocks/lottie`)

Render Lottie animations with full web vitals compliance. Supports scroll-linked playback.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "src": "https://example.com/animation.json",
  "width": [300],
  "height": [300],
  "loop": true,
  "autoplay": true,
  "triggertype": "scroll",
  "scrollSpeed": 0.5,
  "renderer": "svg"
}
```

---

## Before/After Block (`greenshift-blocks/beforeafter`)

Image comparison slider with drag handle.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "beforeImage": "https://placehold.co/800x600",
  "afterImage": "https://placehold.co/800x600",
  "beforeLabel": "Before",
  "afterLabel": "After",
  "orientation": "horizontal",
  "startPosition": 50
}
```

---

## SVG Animation (via Animation Section)

Any Greenshift block can use the built-in animation section for simple transforms without Animation Container.

### In-block Animation JSON

```json
"animation": {
  "duration": 700,
  "easing": "ease",
  "type": "custom",
  "y": 30,
  "rx": -60,
  "o": "0",
  "origin": "bottom center",
  "usegsap": true
}
```

### Data Attributes for In-block GSAP

```html
<div data-gsapinit="1"
     data-duration="0.7"
     data-y="30"
     data-rx="-60"
     data-o="0"
     data-origin="bottom center"
     data-from="yes"
     data-prehidden="1">
```

### When to Use Animation Container vs In-block Animation

| Feature | In-block Animation | Animation Container |
|---------|-------------------|-------------------|
| Simple reveals | ✅ Preferred | Works but overkill |
| Chained animations | ❌ | ✅ Required |
| Hover/click triggers | ❌ | ✅ Required |
| Scroll interpolation | ❌ | ✅ Required |
| Pin scroll | ❌ | ✅ Required |
| Custom object targeting | ❌ | ✅ Required |
| Performance | Lighter | Heavier (full GSAP) |

Use in-block animation for simple one-shot reveals. Use Animation Container for complex, interactive, or chained animations.

---

## SVG Draw Animation

Available on SVG Shape blocks. Animates stroke drawing.

### Enable on SVG Shape

```json
{
  "id": "gsbp-XXXXXXX",
  "animatesvg": true,
  "animatesvgduration": 3.9,
  "stroke": "#000000",
  "fillone": ""
}
```

The SVG must have `stroke` attributes on paths. Set `fillone` to empty to show stroke-only.

HTML adds:
```html
data-svgdraw="1" class="gs-gsap-wrap" data-from="yes" data-duration="3.9"
```
