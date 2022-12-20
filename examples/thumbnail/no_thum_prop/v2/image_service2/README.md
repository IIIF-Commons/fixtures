---
layout: fixture
title: Canvas with no thumbnail property - ImageService
description: This is a manifest where there is no thumbnail property on either canvas but the thumbnail can be generated from the image service.
author: Glen Robson
tags: thumb
version: 2
---

With an image service you should inspect the `sizes` array and choose a size which is bigger than what you want. In almost all cases this will be more efficient than requiring the image server to generate a custom size for you. In the first image example the info.json shows:

```
{
  "@context": "http://iiif.io/api/image/2/context.json",
  "@id": "https://iiif.io/api/image/2.1/example/reference/918ecd18c2592080851777620de9bcb5-fountain",
  "height": 4032,
  "width": 3024
  "profile": [
    "http://iiif.io/api/image/2/level1.json",
    {
      "formats": [ "jpg", "png" ],
      "qualities": [ "default", "color", "gray" ]
    }
  ],
  "protocol": "http://iiif.io/api/image",
  "tiles": [
    {
      "height": 512,
      "width": 512
      "scaleFactors": [ 1, 2, 4 ],
    }
  ],
```

Which doesn't have a sizes array. It notes it is a level1 image server so you should feel free to request the size you would like.

The second canvas has the sizes specified in the service:

```
"service": {
    "@context": "http://iiif.io/api/image/2/context.json",
    "@id": "https://iiif.io/api/image/2.1/example/reference/918ecd18c2592080851777620de9bcb5-gottingen",
    "profile": "http://iiif.io/api/image/2/level2.json",
    "sizes": [
        { "width": 756, "height": 1008 },
        { "width": 1512, "height": 2016 },
        { "width": 3024, "height": 4032 }
    ]
}
```

so you should choose a size in the list and there is no need to retrieve the info.json for the image.
