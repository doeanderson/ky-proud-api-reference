# KY Proud API reference
Included in this repo is an example JSON block that contains the ideal data structure from our standpoint. Let us know if there are any questions.

## General structure of the data
- We expect any data within the results to be active. We will be wholesale replacing the data every time we pull from the API endpoint. Thus we have removed all `status` blocks from our example JSON.
- All business data should be un-nested, at the top-most level in the JSON object.
- All `addresses`, `categories`, `products`, `product_categories`, `programs`, `live_animals`, etc data should be an `array` of `objects` and live at the top-most level of the JSON object.
- We only need the top-most level of data within each seciton. IE) we only need the `product` data. We do not need that products' `product_category` or `product_category_type` as a child of that product
- If a business doesn't have a section, IE `live_animals` it should still contain that key with an empty array as it's value


## Formatting overview
- All keys should be in `snake_case`
- All keys should be wrapped in double quotes. IE) `"key_name_here": value`
- All empty values should be `null`
- `id` fields should be `integers`
- `longitude` & `latitude` should be `floats`
- boolean values should be represented by `true` and `false`. Please do not use strings as we utilize strict comparision.
