# Greenshift Block Documentation Index

This documentation is split into logical modules for easy reference. Each file covers a specific topic.

## Quick Navigation

| # | File | Topics Covered |
|---|------|----------------|
| 01 | [Core Structure](01-core-structure.md) | Block format, JSON parameters, content types, styleAttributes basics |
| 02 | [HTML Attributes](02-attributes.md) | Links, images, forms, dynamic attributes, icons |
| 03 | [Layouts](03-layouts.md) | Sections, columns, flexbox, content areas |
| 04 | [Advanced Styling](04-styling-advanced.md) | Local classes, gradients, background images, parallax |
| 05 | [Animations](05-animations.md) | AOS animations, keyframes, scroll animations |
| 06 | [Slider Blocks](06-slider.md) | Swiper configuration, slides, navigation |
| 07 | [Dynamic Content](07-dynamic-content.md) | Dynamic text, query grid, post data, taxonomies |
| 08 | [Block Variations](08-variations.md) | Accordion, tabs, counter, countdown, marquee, etc. |
| 09 | [CSS Variables](09-css-variables.md) | Font sizes, spacing, shadows, transitions, colors |
| 10 | [Scripts](10-scripts.md) | Custom JavaScript, GSAP integration |
| 11 | [Charts](11-charts.md) | ApexCharts integration |
| 12 | [Migration Rules](12-migration-rules.md) | Typography stripping, semantic headings, minimal intervention |
| 13 | [Marketing Addon](13-marketing-addon.md) | Offer box, comparison table, how-to, review, score box, listing builders, event box |
| 14 | [Animation Addon](14-animation-addon.md) | Animation container, pin scroll, lottie, GSAP chains, SVG draw |
| 15 | [Query Addon](15-query-addon.md) | Query builder, filters, dynamic fields, meta getter, wishlist, visibility |
| 16 | [WooCommerce Addon](16-woocommerce-addon.md) | Woo query builder, product gallery/tabs/price/rating, cart, FSE blocks |

## How to Use

1. **Start with Core Structure** (01) to understand block basics
2. **Reference specific topics** as needed
3. **Check CSS Variables** (09) for consistent theming
4. **See Block Variations** (08) for special components

## Critical Rules Summary

1. **IDs**: Every block needs unique `id` + matching `localId` (format: `gsbp-XXXXXXX`)
2. **No inline styles**: Always use `styleAttributes`, never `style="..."`
3. **Responsive arrays**: `["desktop", "tablet", "mobile_landscape", "mobile_portrait"]`
4. **Class requirement**: If `styleAttributes` exists, add `localId` to HTML `class`
5. **Images**: Always `loading="lazy"`, use `originalWidth`/`originalHeight` in JSON
6. **CSS Variables**: Prefer over hardcoded values

## File Output

Save all generated blocks as `.html` files (not `.md` or `.json`).
