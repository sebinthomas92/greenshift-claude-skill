# SEO & Marketing Addon Blocks

The Marketing addon provides high-conversion blocks for affiliate sites, product reviews, and SEO-optimized content. All blocks support SEO schema markup.

## Block Types

| Block Name | Namespace | Use Case |
|-----------|-----------|----------|
| Offer Box | `greenshift-blocks/offerbox` | Product offer with image, pricing, coupon, CTA button |
| Comparison Table | `greenshift-blocks/comparison-table` + `comparison-item` | Side-by-side product comparison |
| How To | `greenshift-blocks/howto` + `howto-item` | Step-by-step instructions with HowTo schema |
| Event Box | `greenshift-blocks/event` | Event listing with dates, location, tickets |
| Review Box | `greenshift-blocks/reviewbox` | Editor's review with score, criteria, pros/cons |
| Score Box | `greenshift-blocks/scorebox` | Product score card with pros/cons and CTA buttons |
| Compact Listing | `greenshift-blocks/offerlisting` | Compact product listing with scores and badges |
| Full Listing | `greenshift-blocks/offerlistingfull` | Full-width listing with expandable details |
| Popup Button | `greenshift-blocks/popupbutton` | Popup triggered by button click |
| Versus Pattern | `greenshift-blocks/versus` | Head-to-head product comparison |
| WooCommerce Box | `greenshift-blocks/woocommercebox` | Import WooCommerce products into posts |
| HotSpot | `greenshift-blocks/hotspot` | Clickable hotspots on images |
| Link Hidder | `greenshift-blocks/linkhidder` | Hide affiliate links from crawlers |
| Fast Image Slider | `greenshift-blocks/simpleslider` | Lightweight image slider |

---

## Offer Box (`greenshift-blocks/offerbox`)

Self-closing block. Product offer with image, pricing, coupon code, and CTA button.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "name": "Product Name",
  "description": "Product description text",
  "disclaimer": "Additional terms or info",
  "old_price": "$699.99",
  "sale_price": "$549.99",
  "coupon_code": "COUPON25",
  "rating": 5,
  "schemaenable": true,
  "button": {
    "text": "Buy Now",
    "url": "https://example.com/product",
    "newTab": true,
    "noFollow": true
  },
  "thumbnail": {
    "url": "https://placehold.co/525x879",
    "width": 525,
    "height": 879
  },
  "schemafields": {
    "mpn": "12345",
    "sku": "SKU001",
    "count": 15,
    "currency": "USD",
    "price": "549.99",
    "brand": "Brand Name",
    "valid": "2026-12-31T23:59:00",
    "author_review": true,
    "author_review_score": 5
  }
}
```

### Styling Options

| Parameter | Type | Description |
|-----------|------|-------------|
| `typographyContent` | object | Content text styling (`size`, `color`) |
| `typographyPrice` | object | Price text styling |
| `typographyButton` | object | Button text styling (`color`, `colorHover`) |
| `backgroundButton` | object | Button background (supports `gradient`) |
| `shadow` | object | Box shadow (`hoffset`, `voffset`, `blur`, `spread`, `color`) |
| `border` | object | Border styling (all sides) |
| `spacing` | object | Margin and padding |

### Example

```html
<!-- wp:greenshift-blocks/offerbox {"id":"gsbp-a1b2c3d","name":"Ceramic Pro 9H","description":"Professional-grade ceramic coating for vehicles","old_price":"$199.99","sale_price":"$149.99","coupon_code":"SCC20","rating":5,"schemaenable":true,"button":{"text":"Shop Now","url":"https://example.com","newTab":true,"noFollow":true},"thumbnail":{"url":"https://placehold.co/500x500","width":500,"height":500},"schemafields":{"sku":"CP9H","currency":"USD","price":"149.99","brand":"Ceramic Pro"}} /-->
```

---

## Comparison Table (`greenshift-blocks/comparison-table`)

Container block with `comparison-item` children. Best conversion rates on mobile.

### Table JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "enableBadges": true,
  "enableSpec": true,
  "enableCallout": true,
  "enableList": true,
  "enableNumbers": false,
  "responsiveView": "stacked",
  "align": "wide"
}
```

`responsiveView` options: `"stacked"` (default), `"slide"` (slider on mobile), `"overflow"` (horizontal scroll)

### Comparison Item JSON Parameters

```json
{
  "productBadge": "Best Value",
  "badgeColor": "#655ec7",
  "productTitle": "Product Name",
  "productSubtitle": "Short description",
  "numberValue": "1",
  "starRating": 4.5,
  "productImage": {
    "url": "https://placehold.co/525x879",
    "id": "",
    "width": 525,
    "height": 879
  },
  "bottomText": "Detailed description with <br> for line breaks",
  "prosText": "<mark class=\"has-inline-color has-vivid-green-cyan-color\">+</mark> Pro 1<br><br><mark class=\"has-inline-color has-vivid-green-cyan-color\">+</mark> Pro 2",
  "consText": "<mark class=\"has-inline-color has-vivid-red-color\">-</mark> Con 1",
  "specText": "<strong>Spec</strong><br>Value<br><br><strong>Spec 2</strong><br>Value 2",
  "buttonUrl": "https://example.com",
  "buttonText": "Buy Now",
  "buttonRel": true,
  "buttonTarget": true,
  "buttonColor": "#655ec7",
  "enableBadge": true,
  "enableBadges": true,
  "enableList": true,
  "enableSpec": true,
  "enableCallout": true,
  "listItems": [
    {"key": "Find on <a href=\"https://amazon.com\" target=\"_blank\" rel=\"noreferrer noopener\">Amazon</a>"},
    {"key": "Find on <a href=\"https://ebay.com\" target=\"_blank\" rel=\"noreferrer noopener\">eBay</a>"}
  ]
}
```

### Example

```html
<!-- wp:greenshift-blocks/comparison-table {"id":"gsbp-comp001","enableBadges":true,"enableSpec":true,"enableCallout":true,"align":"wide"} -->
<!-- wp:greenshift-blocks/comparison-item {"productBadge":"Editor's Pick","badgeColor":"#655ec7","productTitle":"Product A","productSubtitle":"Best overall","numberValue":"1","starRating":4.5,"productImage":{"url":"https://placehold.co/500x500"},"bottomText":"Excellent product for everyday use","prosText":"<mark class=\"has-inline-color has-vivid-green-cyan-color\">+</mark> Great quality","consText":"<mark class=\"has-inline-color has-vivid-red-color\">-</mark> Premium price","buttonUrl":"https://example.com","buttonText":"Check Price","buttonRel":true,"buttonTarget":true,"enableBadge":true,"enableBadges":true,"enableCallout":true} /-->
<!-- wp:greenshift-blocks/comparison-item {"productBadge":"Budget Pick","badgeColor":"#00d084","productTitle":"Product B","productSubtitle":"Best value","numberValue":"2","productImage":{"url":"https://placehold.co/500x500"},"bottomText":"Good product at lower price point","prosText":"<mark class=\"has-inline-color has-vivid-green-cyan-color\">+</mark> Affordable","consText":"<mark class=\"has-inline-color has-vivid-red-color\">-</mark> Fewer features","buttonUrl":"https://example.com","buttonText":"Check Price","buttonRel":true,"buttonTarget":true,"enableBadge":true,"enableBadges":true,"enableCallout":true} /-->
<!-- /wp:greenshift-blocks/comparison-table -->
```

---

## How To Block (`greenshift-blocks/howto`)

Container with `howto-item` children. Supports HowTo SEO schema for Google rich snippets.

### HowTo JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "title": "How to Do Something",
  "description": "Brief overview of the tutorial",
  "seoschema": true,
  "borderColor": "#7000f4",
  "numberBgColor": "#7000f4",
  "numberColor": "#ffffff"
}
```

### HowTo Item JSON Parameters

```json
{
  "title": "Step Title",
  "seoschema": true
}
```

Each `howto-item` contains standard WordPress blocks (paragraphs, images, videos) as inner content.

### Example

```html
<!-- wp:greenshift-blocks/howto {"id":"gsbp-how001","title":"How to Apply Ceramic Coating","description":"Step-by-step guide to professional ceramic coating application","seoschema":true} -->
<!-- wp:greenshift-blocks/howto-item {"title":"Wash and decontaminate the surface"} -->
<!-- wp:paragraph -->
<p>Thoroughly wash the vehicle using a pH-neutral car shampoo. Clay bar the surface to remove embedded contaminants.</p>
<!-- /wp:paragraph -->
<!-- /wp:greenshift-blocks/howto-item -->
<!-- wp:greenshift-blocks/howto-item {"title":"Polish if needed"} -->
<!-- wp:paragraph -->
<p>Use a dual-action polisher to remove swirl marks and light scratches before coating.</p>
<!-- /wp:paragraph -->
<!-- /wp:greenshift-blocks/howto-item -->
<!-- wp:greenshift-blocks/howto-item {"title":"Apply the ceramic coating"} -->
<!-- wp:paragraph -->
<p>Apply coating to applicator pad, work in small sections using cross-hatch pattern.</p>
<!-- /wp:paragraph -->
<!-- /wp:greenshift-blocks/howto-item -->
<!-- /wp:greenshift-blocks/howto -->
```

---

## Review Box (`greenshift-blocks/reviewbox`)

Self-closing block. Shows editor's review with overall score, criteria bars, and pros/cons.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "score": 8.5,
  "enablecriterias": true,
  "enableproscons": true,
  "mainColor": "#7000f4",
  "textColor": "#fafbfd",
  "background": {"color": "#010101"},
  "criterias": [
    {"title": "Design", "value": 10},
    {"title": "Price", "value": 7.5},
    {"title": "Functionality", "value": 6.5},
    {"title": "Support", "value": 10}
  ],
  "prosTitle": "Positive Sides",
  "positives": [
    {"title": "Excellent build quality"},
    {"title": "Great feature set"}
  ],
  "consTitle": "Negative Sides",
  "negatives": [
    {"title": "Expensive"},
    {"title": "Steep learning curve"}
  ]
}
```

### Example

```html
<!-- wp:greenshift-blocks/reviewbox {"id":"gsbp-rev001","score":8.5,"enablecriterias":true,"enableproscons":true,"criterias":[{"title":"Quality","value":9},{"title":"Value","value":7.5},{"title":"Durability","value":9.5}],"prosTitle":"Pros","positives":[{"title":"Long-lasting protection"},{"title":"Deep gloss finish"}],"consTitle":"Cons","negatives":[{"title":"Requires professional application"}]} /-->
```

---

## Score Box (`greenshift-blocks/scorebox`)

Container block. Product highlight card with score circle, image, pros/cons, and multiple CTA buttons.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "title": "Product Name",
  "label": "Editor's Choice",
  "labelicon": true,
  "score": 8,
  "schemaenable": true,
  "coverenable": false,
  "enableinner": true,
  "innerbottom": true,
  "scorebgColor": "#effaf6",
  "scorecircleColor": "#00d084",
  "scoretextColor": "#ffffff",
  "labelColor": "#cf2e2e",
  "prosColor": "#00d084",
  "consColor": "#de1414",
  "buttons": [
    {
      "btntitle": "Buy at Amazon",
      "url": "https://amazon.com/product",
      "newTab": true,
      "noFollow": true,
      "textcolor": "#ffffff",
      "bgcolor": "#cc0000",
      "radius": 3
    },
    {
      "btntitle": "Official Store",
      "url": "https://brand.com",
      "newTab": true,
      "noFollow": true,
      "textcolor": "#ffffff",
      "bggradient": "linear-gradient(135deg,rgba(252,185,0,1) 0%,rgba(255,105,0,1) 100%)",
      "radius": 3
    }
  ],
  "positives": [
    {"title": "Pro 1"},
    {"title": "Pro 2"}
  ],
  "negatives": [
    {"title": "Con 1"}
  ],
  "thumbnail": {
    "url": "https://placehold.co/500x500",
    "width": 500,
    "height": 500
  },
  "schemafields": {
    "mpn": "12345",
    "sku": "SKU001",
    "count": 5,
    "currency": "USD",
    "price": 149.99,
    "brand": "Brand"
  }
}
```

Inner content is standard WordPress blocks (paragraphs).

### Example

```html
<!-- wp:greenshift-blocks/scorebox {"id":"gsbp-scr001","title":"Ceramic Pro 9H","label":"Top Pick","labelicon":true,"score":9,"schemaenable":true,"scorebgColor":"#effaf6","scorecircleColor":"#00d084","buttons":[{"btntitle":"Shop Now","url":"https://example.com","newTab":true,"noFollow":true,"textcolor":"#ffffff","bgcolor":"#cc0000","radius":3}],"positives":[{"title":"10H hardness"},{"title":"Lifetime warranty"}],"negatives":[{"title":"Professional application only"}],"thumbnail":{"url":"https://placehold.co/500x500","width":500,"height":500},"schemafields":{"sku":"CP9H","currency":"USD","price":149.99,"brand":"Ceramic Pro"}} -->
<!-- wp:paragraph -->
<p>The gold standard in ceramic coatings for automotive protection.</p>
<!-- /wp:paragraph -->
<!-- /wp:greenshift-blocks/scorebox -->
```

---

## Event Box (`greenshift-blocks/event`)

Self-closing block. Event listing with dates, location, streaming links, and Event SEO schema.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "title": "Event Name",
  "content": "Event description",
  "startdate": "2026-10-30T15:59:00",
  "enddate": "2026-11-09T15:58:41",
  "schemaenable": true,
  "textColor": "#ffffff",
  "iconColor": "#7affeb",
  "highlightColor": "#00d084",
  "highlightPosition": "Top",
  "background": {
    "color": "#0e0e0e",
    "backgroundState": "Gradient",
    "gradient": "linear-gradient(324deg,rgb(77,46,138) 0%,rgb(155,81,224) 100%)"
  },
  "thumbnail": {
    "url": "https://placehold.co/200x200",
    "width": 200,
    "height": 200
  },
  "location": {
    "name": "Venue Name",
    "street": "123 Main St",
    "locality": "City",
    "region": "State",
    "postal": "12345",
    "country": "US",
    "stream": "https://youtube.com/watch?v=xxx",
    "maplabel": "Find on Google Maps",
    "streamlabel": "Watch Live"
  },
  "offer": {
    "url": "https://tickets.example.com",
    "price": "$49.99",
    "currency": "USD",
    "priceschema": "49.99"
  },
  "schemafields": {
    "name": "Organizer Name",
    "url": "https://organizer.com"
  }
}
```

---

## Compact Listing (`greenshift-blocks/offerlisting`)

Self-closing block. Compact product listing with multiple offers.

### Offer Item Structure

```json
{
  "score": 9,
  "enableBadge": true,
  "enableScore": true,
  "thumbnail": {
    "url": "https://placehold.co/600x289",
    "width": 600,
    "height": 289
  },
  "title": "Product Name",
  "copy": "Short description...",
  "customBadge": {
    "text": "Best Value",
    "textColor": "#ffffff",
    "backgroundColor": "#9b51e0"
  },
  "currentPrice": "$149.99",
  "oldPrice": "$199.99",
  "button": {
    "text": "Buy Now",
    "url": "https://example.com",
    "newTab": true,
    "noFollow": true
  },
  "couponCode": "SAVE20",
  "expirationDate": "2026-12-31T00:00:00",
  "disclaimer": "Use coupon for additional discount",
  "read": {
    "readMore": "Read full review",
    "readMoreUrl": "/review-page"
  }
}
```

---

## Full Listing Builder (`greenshift-blocks/offerlistingfull`)

Self-closing block. Full-width listing with expandable content, mobile-optimized layout.

### Key JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "titleTag": "h2",
  "readmorecolor": "#9b51e0",
  "enableexpand": true,
  "enableScoreIcon": true,
  "enableNumber": false,
  "colorScore": true,
  "pricecontent": true,
  "highlightcolor": "#cf2e2e",
  "numbercolor": "#892424",
  "numberbgssolor": "#ffb5b5",
  "reviewcolor": "#13c684",
  "align": "wide",
  "offers": []
}
```

Each offer in `offers[]` supports all fields from compact listing plus:
- `expandcontent` — HTML content shown when expanded
- `highlight` — boolean, highlights the item
- `moretext` — text below button (can contain links)
- `coupon` — coupon code to display with mask

---

## SEO Schema Support

These blocks support schema markup:

| Block | Schema Type |
|-------|-------------|
| Offer Box | Product with AggregateRating |
| How To | HowTo |
| Event Box | Event |
| Score Box | Product with AggregateRating |
| Review Box | Review |

Enable via `"schemaenable": true` in JSON parameters.
