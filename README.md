# KY Proud API reference
Included in this repo is an example JSON block that contains the ideal data structure for our frontend execution. Note that it is not valid JSON. We are utilizing `...` to indicate that additional entries would be here.

Ideally we will call 7 separate endpoints for all the needed data, ingesting that into a relational database on our side.

On this v2 version, we will have the following sections as headings/tabs on the website: `Business Category`, `Products`, `Product Categories`, `Programs`, `Live Animals`. We will build up the displayed data on the frontend as a direct correlation from the responses we get from the endpoint. We expect any data within the results to be active.

All data returned from the endpoint will be considered `active` and ready to be displayed on the website.  Thus we have removed all `status` blocks from our example JSON.

We will be wholesale replacing the data every time we pull from the API endpoint.

Let us know if there are any questions.

## General structure of the data
- All business data should be un-nested, at the top-most level in the JSON object.
- All `addresses`, `business_categories`, `products`, `product_categories`, `programs`, `live_animals`, `programs` data within the `businesses` endpoint should be an `array` of `integers` that represent the cooresponding ID of the associated entry.
- We only need the top-most level of data within each section. IE) we only need the `product` data. We do not need that products' `product_category` or `product_category_type` as a child of that product
- If a business doesn't have a section, IE) `live_animals` it should still contain that key with an empty array as it's value
- The individual entries from the `addresses`, `business_categories`, `products`, `product_categories`, `programs`, `live_animals`, `programs` endpoints should be an array of objects.


## Formatting overview
- All keys should be in `snake_case`
- All keys should be wrapped in double quotes. IE) `"key_name_here": value`
- All empty values should be `null`
- `id` fields should be `integers`
- `longitude` & `latitude` should be `floats`
- boolean values should be represented by `true` and `false`. Please do not use strings as we utilize strict comparision.

## Live animal requests
- Remove `(live)` from the JSON response on any entries related to live animals on `product_categories`. They will be in their own `Live Animals` section doing forward so that information is redundant to the end user.
- Please use the following formatting for `Live Animal` entries: `products.name` &mdash; `product_categories.name` &mdash; `products.type`. IE) `Breeding Stock` &mdash; `Sheep` &mdash; `Hamphire`.  If any of the entries after the `products.name` does not exist, please do not include the dash or entry. IE) `Breeding stock` &mdash; `Spanish Goats`

## Example pagination block
We included our ideal pagination block below if/when it's needed.
```
"pagination": {
        "total": 360,
        "count": 10,
        "per_page": 10,
        "current_page": 1,
        "total_pages": 36
    }
```
