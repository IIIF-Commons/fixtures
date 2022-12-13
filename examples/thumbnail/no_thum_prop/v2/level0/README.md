---
layout: fixture
title: Canvas with no thumbnail property - level0 image
description: This is a manifest where there is no thumbnail property but the thumbnail can be generated from the level 0 image service.
author: Glen Robson
tags: thumb
version: 2
---

With a level0 image server you can't request a custom size as the various sizes have been pre-generated. You must inspect the sizes array of the info.json to find a size bigger than you want:

```
{
    "sizes": [
        {
            "width": 126,
            "height": 95
        },
        {
            "width": 252,
            "height": 189
        },
        {
            "width": 504,
            "height": 378
        },
        {
            "width": 1008,
            "height": 756
        },
        {
            "width": 2016,
            "height": 1512
        },
        {
            "width": 4032,
            "height": 3024
        }
    ],
    "profile": "http://iiif.io/api/image/2/level0.json",
    "width": 4032,
    "@id": "https://example.com/iiif/image/tractor",
    "@context": "http://iiif.io/api/image/2/context.json",
    "height": 3024
}
```

With version 2 of the API the conical URL for a image is to only request the width and drop the height from the URL:

```
https://example.com/iiif/image/tractor/full/252,/0/default.jpg
```

You can check in the manifest to see if the image is a level0 image:

```
"service": {
    "@context": "http://iiif.io/api/image/2/context.json",
    "@id": "https://example.com/iiif/image/tractor",
    "profile": "http://iiif.io/api/image/2/level0.json"
}
```
