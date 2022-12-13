---
layout: fixture
title: Canvases with thumbnail property with level0 image service (Most optimised option)
description: This is an efficient way of advertising various sizes for a thumbnail and allows a producer to cache copies of thumbnails to make them fast to retrieve.
author: Glen Robson
tags: thumb
version: 2
---

A client should inspect the `thumbnail` property to see if it is the correct size:

```
{
    "@id": "https://example.com/titlepage1_verso/full/679,/0/default.jpg",
    "@type": "dctypes:Image",
    "height": 904,
    "width": 679,
    "service": {
        ...
    }
}
```

If it is then it can use that version. If it is too small then it should inspect the service element to see if it can find a size bigger than it wants and select that. Note For IIIF Presentation API version 2 the conical request for a size is to drop the height so the request for the smallest image would be:

```
https://example.com/titlepage1_verso/full/170,/0/default.jpg
```

In version 3  the conical URL requires you to specify the width and height for the image you want. The different sizes available can be seen in the sizes array of the image:

```
"serivce": {
    "sizes": [
        {
            "width": 170,
            "height": 226
        },
        {
            "width": 340,
            "height": 452
        },
        {
            "width": 679,
            "height": 904
        },
        {
            "width": 1357,
            "height": 1808
        },
        {
            "width": 2714,
            "height": 3615
        },
        {
            "width": 5428,
            "height": 7230
        }
    ],
}
```
