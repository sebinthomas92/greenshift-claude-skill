# Query Dynamic Addon Blocks

The Query addon provides server-side rendered dynamic blocks for post listings, grids, directories, and user interactions. All blocks render on the server with proper WordPress queries.

## Block Types

| Block Name | Namespace | Use Case |
|-----------|-----------|----------|
| Query Builder | `greenshift-blocks/querygrid` | Post grids, listings with filters |
| Repeater Builder | `greenshift-blocks/repeater` | Custom repeatable field rendering |
| Slider Query | `greenshift-blocks/sliderquery` | Slider from query results |
| Filter Block | `greenshift-blocks/filter` | Dynamic filters for query builder |
| API Connector | `greenshift-blocks/apiconnector` | Connect to external APIs/JSON |
| Dynamic Chart | `greenshift-blocks/dynamicchart` | Chart from dynamic data |
| Dynamic Fields | `greenshift-blocks/dynamicfields` | Display any dynamic data |
| Dynamic Attributes | `greenshift-blocks/dynamicattributes` | Dynamic HTML attributes |
| Dynamic Styles | `greenshift-blocks/dynamicstyles` | Dynamic CSS styles |
| Dynamic FAQ | `greenshift-blocks/dynamicfaq` | FAQ from meta/taxonomy data |
| Placeholders | `greenshift-blocks/placeholders` | Dynamic value placeholders |
| Dynamic Search | `greenshift-blocks/dynamicsearch` | Advanced AJAX search |
| Taxonomy Archive | `greenshift-blocks/taxonomyarchive` | Category/term grid display |
| Thumbs/Hot Counter | `greenshift-blocks/thumbscounter` | Like/vote counter |
| Taxonomy Repeater | `greenshift-blocks/taxonomyrepeater` | Custom taxonomy term lists |
| User List Builder | `greenshift-blocks/userlist` | User directory listings |
| Comment Query | `greenshift-blocks/commentquery` | Custom comment displays |
| Wishlist | `greenshift-blocks/wishlist` | User wishlist functionality |
| Meta Getter | `greenshift-blocks/metagetter` | Retrieve any meta value |
| Visibility Condition | `greenshift-blocks/visibility` | Conditional block display |
| Login Popup | `greenshift-blocks/loginpopup` | AJAX login form |
| Template Builder | `greenshift-blocks/templatebuilder` | Custom post type templates |
| Dynamic Switcher | `greenshift-blocks/dynamicswitcher` | User preference switcher |
| Parent-child List | `greenshift-blocks/parentchild` | Hierarchical categorizer |
| Breadcrumbs | `greenshift-blocks/breadcrumbs` | Breadcrumb navigation |
| Dynamic Gallery | `greenshift-blocks/dynamicgallery` | Gallery from custom fields |
| Gallery Block | `greenshift-blocks/galleryblock` | Upload-based gallery |
| 360 Gallery | `greenshift-blocks/gallery360` | Circular gallery view |
| Dynamic Map | `greenshift-blocks/dynamicmap` | Map from custom fields |
| Advanced Listing | `greenshift-blocks/advancedlisting` | Post/product listing builder |

---

## Query Builder (`greenshift-blocks/querygrid`)

The most powerful block. Renders any post type in customizable grid/list layouts.

### Core JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "postType": "post",
  "postsToShow": 6,
  "columns": [3, 2, 2, 1],
  "orderBy": "date",
  "order": "desc",
  "enablePagination": false,
  "paginationType": "simple",
  "enableFilters": false,
  "enableCarousel": false,
  "enableAds": false,
  "containerLink": false,
  "gap": ["20px"],
  "align": "wide"
}
```

### Query Sources

| Source | Description |
|--------|-------------|
| Default | Latest posts of selected post type |
| Custom taxonomy | Filter by taxonomy terms |
| Manual select | Pick specific posts by ID |
| Related items | Posts sharing same taxonomy |
| Child/sister items | Hierarchical page children |
| Ids relationship | ACF relationship field |
| MetaBox relationship | MetaBox plugin relations |
| Wishlist | User's saved items |

### Order Options

```
"date", "title", "ID", "rand", "modified",
"meta_value", "meta_value_num", "comment_count"
```

### Pagination Types

| Type | Value | Description |
|------|-------|-------------|
| Simple | `"simple"` | Standard page numbers |
| Infinite | `"infinite"` | Load more on scroll |
| Load More | `"loadmore"` | Button to load more |

### Meta Query Conditions

Add conditional queries using meta fields:

```json
{
  "metaQuery": [
    {
      "key": "price",
      "value": "100",
      "compare": ">=",
      "type": "NUMERIC"
    }
  ]
}
```

### Placeholders for Meta Query

| Placeholder | Description |
|-------------|-------------|
| `{POST_ID}` | Current post ID |
| `{AUTHOR_ID}` | Current author ID |
| `{CUSTOM:field_name}` | Value from meta field |
| `{TIMESTRING:+1 month}` | Dynamic date calculation |
| `{GET:param}` | URL parameter value |

### Conversion to Carousel

Query grid supports conversion to slider/carousel mode via the `enableCarousel` option.

### Grid Item Classes Hook

```php
add_filter('gspbgrid_item_class', 'gs_item_class', 10, 3);
function gs_item_class($class, $postid, $block_instance) {
    $classnew = get_post_class('', $postid);
    return $class . ' ' . implode(' ', $classnew);
}
```

### Modifying Query Args

```php
// Global - all query blocks
add_filter('gspb_module_args_query', function($args) {
    if (!is_admin()) {
        $args['custom_param'] = 'value';
    }
    return $args;
});

// Specific block by ID
add_filter('gspb_module_args_query_id', function($args, $id) {
    if ($id == 'gsbp-XXXXXXX') {
        $args['ignore_sticky_posts'] = 1;
    }
    return $args;
}, 10, 2);
```

### Example

```html
<!-- wp:greenshift-blocks/querygrid {"id":"gsbp-qry001","postType":"product","postsToShow":6,"columns":[3,2,2,1],"orderBy":"date","order":"desc","gap":["20px"],"align":"wide"} -->
<!-- wp:greenshift-blocks/element {"id":"gsbp-qimg01","tag":"img","localId":"gsbp-qimg01","dynamictext":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"current_item","dynamicPostData":"featured_image"},"styleAttributes":{"width":["100%"],"aspectRatio":["16/9"],"objectFit":["cover"],"borderRadius":["var(--wp--custom--border-radius--small, 10px)"]}} -->
<img class="gsbp-qimg01" loading="lazy"/>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-qtitle01","textContent":"<dynamictext></dynamictext>","tag":"h3","dynamictext":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"current_item","dynamicPostData":"post_title"},"localId":"gsbp-qtitle01","styleAttributes":{"marginTop":["var(--wp--preset--spacing--40, 1rem)"]}} -->
<h3 class="gsbp-qtitle01"><dynamictext></dynamictext></h3>
<!-- /wp:greenshift-blocks/element -->
<!-- /wp:greenshift-blocks/querygrid -->
```

---

## Filter Block (`greenshift-blocks/filter`)

Adds dynamic filters to Query Builder. Supports taxonomy, meta, search, and price range.

### Filter Types

| Type | Description |
|------|-------------|
| Taxonomy | Filter by categories, tags, custom taxonomies |
| Meta field | Filter by custom field values |
| Search | Text search within query |
| Price range | Numeric range slider |
| Date | Date-based filtering |

Connect to Query Builder via the Filter Connection ID (format: `gspb_filterid_gsbp-XXXXXXX`).

---

## Dynamic Fields (`greenshift-blocks/dynamicfields`)

Display any WordPress data dynamically. For use inside Query Builder or templates.

### Dynamic Types

| Type | Value | Description |
|------|-------|-------------|
| Post data | `"postdata"` | Title, date, excerpt, content, etc. |
| Custom field | `"customfield"` | Any post meta value |
| Taxonomy | `"taxonomy"` | Category, tag names |
| User data | `"userdata"` | Author name, avatar, etc. |
| Site data | `"sitedata"` | Site title, URL, etc. |

### Post Data Sources

```
"post_title", "post_date", "post_excerpt", "post_content",
"post_author", "featured_image", "post_permalink",
"comment_count", "post_id"
```

---

## Meta Getter (`greenshift-blocks/metagetter`)

Retrieve and display any meta value, attribute, or user meta.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "metaKey": "custom_field_name",
  "metaType": "post",
  "before": "Price: ",
  "after": " USD",
  "fallback": "N/A"
}
```

---

## Visibility Condition (`greenshift-blocks/visibility`)

Conditionally show/hide blocks based on:
- User logged in/out status
- User role
- Device type
- Date/time range
- Custom field value
- URL parameter
- Cookie value

---

## Wishlist (`greenshift-blocks/wishlist`)

Adds wishlist/bookmark buttons to posts. Works with Query Builder for wishlist archive pages.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "type": "heart",
  "enableCount": true,
  "enableText": true,
  "addText": "Add to Wishlist",
  "removeText": "Remove from Wishlist"
}
```

---

## Thumbs/Hot Counter (`greenshift-blocks/thumbscounter`)

Add like/vote functionality to posts or loops.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "type": "thumbs",
  "enableCount": true,
  "enableDownvote": false
}
```

---

## Login Popup (`greenshift-blocks/loginpopup`)

Custom AJAX login form with popup display.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "buttonText": "Login",
  "redirectUrl": "/dashboard",
  "enableRegister": true,
  "enableForgot": true
}
```

---

## Breadcrumbs (`greenshift-blocks/breadcrumbs`)

SEO-friendly breadcrumb navigation.

### JSON Parameters

```json
{
  "id": "gsbp-XXXXXXX",
  "separator": "›",
  "homeText": "Home"
}
```

---

## Template Builder (`greenshift-blocks/templatebuilder`)

Create custom templates for categories, users, and custom post types. Used in FSE (Full Site Editing) context.

---

## Key Concepts

### Dynamic Text Pattern

All dynamic content uses the `dynamictext` parameter:

```json
{
  "textContent": "<dynamictext></dynamictext>",
  "dynamictext": {
    "dynamicEnable": true,
    "dynamicType": "postdata",
    "dynamicSource": "current_item",
    "dynamicPostData": "post_title"
  }
}
```

HTML uses `<dynamictext></dynamictext>` as placeholder, replaced server-side.

### Server-Side Rendering

Query addon blocks render on the server. The HTML in the editor is a template — actual content is generated at page load via `WP_Query`. This means:

1. Block HTML in code editor is the **template** structure
2. Dynamic placeholders get replaced with real data
3. No JavaScript needed for content rendering
4. SEO-friendly — content is in the initial HTML

### Filter Connection

To connect Filter and Query blocks:
1. Set a unique Filter ID in Query Builder settings
2. Reference that ID in the Filter block
3. Format: `gspb_filterid_gsbp-XXXXXXX`
