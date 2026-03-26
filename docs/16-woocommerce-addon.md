# WooCommerce Addon Blocks

The WooCommerce addon provides FSE (Full Site Editing) blocks for product templates and e-shop tools. These blocks are used in WooCommerce product templates and shop pages.

## Block Types

| Block Name | Namespace | Use Case |
|-----------|-----------|----------|
| Woo Query Builder | `greenshift-blocks/wooquerygrid` | Product loop/grid with custom design |
| Product Comparison | `greenshift-blocks/productcomparison` | Dynamic product comparison page |
| Product Gallery | `greenshift-blocks/productgallery` | Product image gallery with video |
| Variation Gallery | `greenshift-blocks/variationgallery` | Multiple images per variation |
| 360 Product Viewer | `greenshift-blocks/product360` | 360-degree product view |
| 3D/Video Viewer | `greenshift-blocks/product3dviewer` | 3D model and video in gallery |
| Product Tabs | `greenshift-blocks/producttabs` | Customizable product tabs |
| Product Quick View | `greenshift-blocks/productquickview` | Quick view popup button |
| Attribute Groups | `greenshift-blocks/attributegroups` | Better attribute management |
| Sliding Cart Button | `greenshift-blocks/slidingcart` | Header cart counter + panel |
| Product Swatches | `greenshift-blocks/productswatches` | Color/image swatches for variations |
| Product Bundles | `greenshift-blocks/productbundles` | Bundle products together |
| Product Combos | `greenshift-blocks/productcombos` | Product combo deals |
| Classic Filters | `greenshift-blocks/classicfilters` | Traditional product filters |
| Product Button | `greenshift-blocks/productbutton` | Custom add to cart button |
| Quick Buy Button | `greenshift-blocks/quickbuy` | One-click buy button |
| Stock Bar | `greenshift-blocks/stockbar` | Stock progress indicator |
| Free Shipping Bar | `greenshift-blocks/freeshippingbar` | Free shipping threshold bar |
| Product Price | `greenshift-blocks/productprice` | Customizable price display |
| Product Rating | `greenshift-blocks/productrating` | Customizable star rating |
| Product Hooks | `greenshift-blocks/producthooks` | WooCommerce hooks in FSE |
| My Account Hooks | `greenshift-blocks/myaccounthooks` | Custom my account page |
| Product Availability | `greenshift-blocks/productavailability` | In/out of stock display |
| Product Discount | `greenshift-blocks/productdiscount` | Auto-calculated discount badge |
| Product SKU | `greenshift-blocks/productsku` | SKU field display |
| Product Taxonomy | `greenshift-blocks/producttaxonomy` | Category/tag display |

---

## WooCommerce Query Builder (`greenshift-blocks/wooquerygrid`)

A variation of Query Builder specifically for WooCommerce products. Requires Query addon to be installed.

### Features

- Pre-installed WooCommerce block layout
- All Query Builder features (grid, carousel, filters, pagination)
- Product-specific query options (on sale, featured, by category)
- Wholesale pattern support
- Custom ad areas between products

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "postType": "product",
  "postsToShow": 12,
  "columns": [4, 3, 2, 1],
  "orderBy": "date",
  "order": "desc",
  "gap": ["20px"],
  "align": "wide",
  "enablePagination": true,
  "enableFilters": false,
  "enableCarousel": false,
  "taxonomyFilter": {
    "taxonomy": "product_cat",
    "terms": []
  },
  "metaQuery": [
    {
      "key": "_sale_price",
      "value": "",
      "compare": "!=",
      "type": "CHAR"
    }
  ]
}
```

### Built-in Inner Blocks

The WooCommerce Query Builder comes pre-configured with these dynamic inner blocks:

- Product image (from featured image)
- Product title (linked to product)
- Product price
- Product rating
- Add to cart button

### Example: Product Grid

```html
<!-- wp:greenshift-blocks/wooquerygrid {"id":"gsbp-woo001","postType":"product","postsToShow":8,"columns":[4,3,2,1],"orderBy":"date","order":"desc","gap":["20px"],"align":"wide"} -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-wimg01","tag":"img","localId":"gsbp-wimg01","dynamictext":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"current_item","dynamicPostData":"featured_image"},"styleAttributes":{"width":["100%"],"aspectRatio":["1/1"],"objectFit":["cover"],"borderRadius":["var(--wp--custom--border-radius--small, 10px)"]}} -->
<img class="gsbp-wimg01" loading="lazy"/>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-wtitle01","textContent":"<dynamictext></dynamictext>","tag":"h3","dynamictext":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"current_item","dynamicPostData":"post_title"},"localId":"gsbp-wtitle01","styleAttributes":{"marginTop":["var(--wp--preset--spacing--40)"],"marginBottom":["0.5rem"]}} -->
<h3 class="gsbp-wtitle01"><dynamictext></dynamictext></h3>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-wprice01","textContent":"<dynamictext></dynamictext>","dynamictext":{"dynamicEnable":true,"dynamicType":"customfield","dynamicFieldKey":"_price","dynamicFieldBefore":"₹"},"localId":"gsbp-wprice01","styleAttributes":{"fontWeight":["700"],"color":["var(--wp--preset--color--primary, #000)"]}} -->
<div class="gsbp-wprice01"><dynamictext></dynamictext></div>
<!-- /wp:greenshift-blocks/element -->

<!-- /wp:greenshift-blocks/wooquerygrid -->
```

---

## Product Gallery (`greenshift-blocks/productgallery`)

FSE block for single product template. Shows product image with gallery slider.

### Features

- Swiper-based slider (replaces default Flexslider)
- SimpleLightbox (replaces PhotoSwipe)
- Video support (inline self-hosted or YouTube/Vimeo lightbox)
- Responsive width/height controls
- Thumbnail position: side or bottom
- Image scaling: cover or contain

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "thumbPosition": "bottom",
  "thumbWidth": [80],
  "thumbHeight": [80],
  "imageScale": "cover",
  "enableLightbox": true,
  "enableVideo": true
}
```

### Performance Note

When using this block, disable default WooCommerce gallery scripts in:
**WooCommerce → Settings → Greenshift Tools**

This removes:
- Flexslider JS
- PhotoSwipe JS + CSS
- Unnecessary WooCommerce gallery styles

---

## Product Tabs (`greenshift-blocks/producttabs`)

Customizable product information tabs.

### Tab Designs

| Design | Description |
|--------|-------------|
| Tabs | Traditional tabbed interface |
| Toggles | Compact accordion-style tabs |
| Sections | Unstacked visible sections (no JS) |
| Section with links | Tabs at top, all content visible, scrolls to section |
| Separate section | Show individual tab section anywhere on page |

### Custom Tabs

Add custom tabs via **WooCommerce → Settings → Greenshift Tools**:
- Title and HTML content per tab
- Supports shortcodes (including reusable template shortcodes)
- Dynamic field content via Query addon reusable templates

---

## Product Swatches (`greenshift-blocks/productswatches`)

Custom attribute types for variations: color swatches, image swatches, label swatches.

### Swatch Types

| Type | Description |
|------|-------------|
| Color | Solid color circles |
| Image | Small product images |
| Label | Text labels with styling |

Works in both product pages and product loop/grid (via WooCommerce Query Builder).

---

## Sliding Cart Button (`greenshift-blocks/slidingcart`)

Header cart icon with item counter badge and sliding cart panel.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "iconType": "cart",
  "showCount": true,
  "panelPosition": "right",
  "panelWidth": ["400px"]
}
```

---

## Stock Bar (`greenshift-blocks/stockbar`)

Visual stock level indicator. Supports real stock data or configurable fake urgency.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "type": "real",
  "barColor": "#00d084",
  "bgColor": "#e0e0e0",
  "showText": true,
  "text": "{stock} items left",
  "fakeTotal": 100,
  "fakeRemaining": 12
}
```

---

## Free Shipping Bar (`greenshift-blocks/freeshippingbar`)

Progress bar showing how much more the customer needs to spend for free shipping.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "threshold": 50,
  "currency": "USD",
  "barColor": "#00d084",
  "reachedText": "You've earned free shipping!",
  "remainingText": "Add {amount} more for free shipping"
}
```

---

## Product Price (`greenshift-blocks/productprice`)

Customizable price field for FSE templates. More control than default WooCommerce price.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "priceColor": "#000",
  "salePriceColor": "#cf2e2e",
  "regularPriceStyle": "strikethrough",
  "fontSize": ["1.5rem"],
  "prefix": "",
  "suffix": ""
}
```

---

## Product Rating (`greenshift-blocks/productrating`)

Customizable star rating display for FSE templates.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "starColor": "#ffb900",
  "emptyColor": "#e0e0e0",
  "showCount": true,
  "showAverage": true,
  "size": ["20px"]
}
```

---

## Product Hooks (`greenshift-blocks/producthooks`)

Insert standard WooCommerce hooks inside FSE templates. Renders whatever plugins/theme attach to the hook.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "hook": "woocommerce_single_product_summary",
  "priority": 25
}
```

### Common Hooks

| Hook | Default Content |
|------|----------------|
| `woocommerce_single_product_summary` | Product summary area |
| `woocommerce_before_add_to_cart_form` | Before add to cart |
| `woocommerce_after_add_to_cart_form` | After add to cart |
| `woocommerce_product_meta_start` | Before product meta |
| `woocommerce_product_meta_end` | After product meta |
| `woocommerce_share` | Share buttons area |

---

## Product Discount (`greenshift-blocks/productdiscount`)

Auto-calculates and displays discount percentage from regular and sale prices.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "format": "-{percent}%",
  "backgroundColor": "#cf2e2e",
  "textColor": "#ffffff",
  "borderRadius": ["50%"],
  "position": "overlay"
}
```

---

## Product Button (`greenshift-blocks/productbutton`)

Custom add-to-cart button with full design control.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "text": "Add to Cart",
  "backgroundColor": "var(--wp--preset--color--primary)",
  "textColor": "#ffffff",
  "borderRadius": ["var(--wp--custom--border-radius--medium)"],
  "fullWidth": true,
  "showQuantity": true
}
```

---

## Quick Buy Button (`greenshift-blocks/quickbuy`)

One-click buy button that skips cart and goes directly to checkout.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "text": "Buy Now",
  "backgroundColor": "#00d084",
  "textColor": "#ffffff"
}
```

---

## Product Quick View (`greenshift-blocks/productquickview`)

Lightweight popup preview button for products in grid/loop context.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "buttonText": "Quick View",
  "iconOnly": false,
  "popupWidth": ["600px"]
}
```

---

## FSE Template Usage

WooCommerce addon blocks are designed for use in Full Site Editing templates:

1. **Single Product Template** — Use Product Gallery, Product Tabs, Product Price, Product Rating, Product Hooks, etc.
2. **Shop/Archive Template** — Use WooCommerce Query Builder, Classic Filters
3. **Cart/Checkout** — Use Sliding Cart, Free Shipping Bar

### Building a Custom Product Template

Combine blocks in the Site Editor (Appearance → Editor → Templates → Single Product):

```
Product Gallery (left column)
├── Product images
├── Video support
└── Variation gallery

Product Info (right column)
├── Product Title (dynamic field)
├── Product Rating
├── Product Price
├── Product Discount badge
├── Product Swatches
├── Product Button (add to cart)
├── Quick Buy Button
├── Stock Bar
├── Product SKU
├── Product Taxonomy (categories/tags)
└── Product Hooks (for plugin compatibility)

Full Width Below
├── Product Tabs (description, reviews, specs)
├── Product Comparison
└── Related Products (WooCommerce Query Builder)
```
