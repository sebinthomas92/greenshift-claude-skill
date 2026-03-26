# Greenshift Claude Skill

A Claude skill for generating production-ready WordPress Gutenberg blocks using the [Greenshift](https://greenshiftwp.com/) block system — including all four premium addons.

## What It Does

Give Claude a content brief, and it outputs copy-paste-ready Gutenberg block HTML for the WordPress Code Editor. Works with the free Greenshift plugin **and** the premium addons.

## Supported Addons

| Addon | Blocks | Commands |
|-------|--------|----------|
| **Core** | 80+ core blocks (element, section, columns, slider, tabs, accordion, counter, charts, etc.) | `/greenshift-blocks:hero`, `:columns`, `:section`, etc. |
| **Marketing/SEO** | 14 blocks (offer box, comparison table, how-to, review box, score box, event, listing) | `/greenshift-blocks:offer`, `:comparison`, `:howto`, `:review`, `:listing`, `:event` |
| **Animation** | 21 blocks (GSAP animation container, pin scroll, lottie, SVG draw, parallax, chained animations) | `/greenshift-blocks:animate` |
| **Query** | 30 blocks (query builder, filters, dynamic fields, meta getter, wishlist, breadcrumbs, visibility) | — |
| **WooCommerce** | 26 blocks (woo query, product gallery/tabs/price/rating/hooks, sliding cart, swatches, stock bar) | `/greenshift-blocks:woo-grid` |

**Total: 91 premium block types documented.**

## Repository Structure

```
greenshift-claude-skill/
├── SKILL.md                    # Skill entry point (Claude reads this)
├── reference.md                # Quick attribute reference
├── plugin.json                 # Plugin metadata
├── docs/
│   ├── 00-index.md             # Navigation index
│   ├── 01-core-structure.md    # Block format, JSON parameters
│   ├── 02-attributes.md        # HTML attributes, links, images, icons
│   ├── 03-layouts.md           # Sections, columns, flexbox
│   ├── 04-styling-advanced.md  # Classes, gradients, background images
│   ├── 05-animations.md        # AOS animations, CSS keyframes
│   ├── 06-slider.md            # Swiper slider config
│   ├── 07-dynamic-content.md   # Dynamic text, query grids
│   ├── 08-variations.md        # Accordion, tabs, counter, countdown
│   ├── 09-css-variables.md     # All CSS variables
│   ├── 10-scripts.md           # Custom JS + GSAP
│   ├── 11-charts.md            # ApexCharts integration
│   ├── 12-migration-rules.md   # CRITICAL: typography, semantic headings
│   ├── 13-marketing-addon.md   # 🆕 Marketing/SEO premium addon
│   ├── 14-animation-addon.md   # 🆕 Animation premium addon
│   ├── 15-query-addon.md       # 🆕 Query premium addon
│   └── 16-woocommerce-addon.md # 🆕 WooCommerce premium addon
└── templates/
    ├── hero-section.html
    ├── two-columns.html
    ├── card-grid.html
    ├── cta-banner.html
    ├── faq-section.html
    ├── features-grid.html
    ├── footer.html
    ├── pricing-table.html
    ├── product-cards-grid.html
    ├── section-wrapper.html
    ├── stats-counters.html
    ├── testimonials-slider.html
    ├── offer-box.html          # 🆕 Marketing addon
    ├── comparison-table.html   # 🆕 Marketing addon
    ├── review-box.html         # 🆕 Marketing addon
    ├── score-box.html          # 🆕 Marketing addon
    ├── howto-steps.html        # 🆕 Marketing addon
    ├── listing-builder.html    # 🆕 Marketing addon
    ├── animation-container.html # 🆕 Animation addon
    └── woo-product-grid.html   # 🆕 WooCommerce addon
```

## Usage

### With vibe-tools (Claude Code / Claude Desktop)

Install via the [vibe-tools](https://github.com/vcode-sh/vibe-tools) marketplace:

```bash
vibe-tools install greenshift-blocks
```

Then in Claude:

```
/greenshift-blocks:hero Product name, tagline, CTA button text
/greenshift-blocks:offer Product name, price, discount, features
/greenshift-blocks:woo-grid Category: car care, 4 columns
/greenshift-blocks:animate Section with fade-in headline and staggered cards
```

### Manual Install

Copy `SKILL.md` and the `docs/` + `templates/` folders into your Claude project context or `.claude/skills/` directory.

## Output Format

All output is standard Gutenberg block HTML — paste directly into the WordPress **Code Editor** (⋮ menu → Code editor, or `Ctrl+Shift+Alt+M`).

Requires the **Greenshift** plugin active. Premium block types require the corresponding premium addon installed.

## Requirements

- WordPress 6.0+
- [Greenshift plugin](https://wordpress.org/plugins/greenshift-animation-and-page-builder-blocks/) (free)
- Premium addons for blocks in docs 13–16: Animation, Marketing, Query, WooCommerce

## Project

Built for [Motor Headz](https://shop.motorheadz.in) — premium car care products.  
Maintained by [Creative Sparks](https://creativesparks.in).

## Changelog

### 2026-03-26
- Added premium addon support: Marketing (14 blocks), Animation (21 blocks), Query (30 blocks), WooCommerce (26 blocks)
- Added 8 new templates: offer-box, comparison-table, review-box, score-box, howto-steps, listing-builder, animation-container, woo-product-grid
- Added 8 new commands: `:offer`, `:comparison`, `:howto`, `:review`, `:listing`, `:animate`, `:woo-grid`, `:event`
- Total blocks documented: 91 premium types across all 4 addons

### Initial Release
- Core Greenshift block documentation (12 doc files)
- 12 base templates
- Tested on WordPress 6.8.1 with Greenshift active
