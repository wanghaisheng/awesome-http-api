#%RAML 0.8
---
#===============================================================
#  Products API - RAML example
#  References:
#    - RAML Specification - http://raml.org/spec.html
#    - RAML Projects - http://raml.org/projects.html
#    - RAML Tools  - http://www.apihub.com/raml-tools
#===============================================================
title: Products API
version: v0.1
#baseUri: http://products.api.apievangelist.com
baseUri: http://mocksvc.mulesoft.com/mocks/a86239e0-d3af-48c6-9fd5-f8edc7c35d69
#List of media type to support
mediaType:  application/json
#List of protocols to support for baseUri
protocols: [ HTTP, HTTPS ]

#===============================================================
#  API documentation
#===============================================================
documentation:
  - title: Home
    content: | #This is a prototype product API.
  - title: Getting Started
    content: TODO

#===============================================================
# API resource definitions
#===============================================================

/products:
  uriParameters:
  displayName: Products
  description: A collection of products
  post:
    description: Create a product
    #Post body media type support
    #text/xml: !!null  # media type text, xml support
    #application/json: !!null  #media type json support
    body:
      application/json:
        schema: |
          {
            "$schema": "http://json-schema.org/draft-03/schema",
            "product": {
                "name": {
                    "required": true,
                    "type": "string"
                },
                "description": {
                    "required": true,
                    "type": "string"
                },
                "url": {
                    "required": true,
                    "type": "string"
                },
                "image": {
                    "required": true,
                    "type": "string"
                },
                "thumbnailUrl": {
                    "required": true,
                    "type": "string"
                },
                "keywords": {
                    "required": true,
                    "type": "string"
                },
                "brand": {
                    "required": false,
                    "type": "string"
                },
                "color": {
                    "required": false,
                    "type": "string"
                },
                "itemCondition": {
                    "required": false,
                    "type": "string"
                },
                "manufacturer": {
                    "required": false,
                    "type": "string"
                },
                "model": {
                    "required": false,
                    "type": "string"
                },
                "sku": {
                    "required": false,
                    "type": "string"
                },
                "weight": {
                    "required": false,
                    "type": "string"
                },
                "width": {
                    "required": false,
                    "type": "string"
                },
                "height": {
                    "required": false,
                    "type": "string"
                },
                "depth": {
                    "required": false,
                    "type": "string"
                }
            },
            "required": true,
            "type": "object"
          }
        example: |
          {
            "product": {
              "id": "1",
              "name": "Product One",
              "description": "This is the full description of the product.",
              "url": "http://example.com",
              "image": "http://example.com/image.jpg",
              "thumbnailUrl": "http://example.com/image-thumb.jpg",
              "keywords": "western, cowboy",
              "brand": "Brand Name",
              "color": "Black",
              "itemCondition": "New",
              "manufacturer": "Manufacturer Name",
              "model": "Black",
              "sku": "SKU #",
              "weight": "12 pounds",
              "width": "12 inches",
              "height": "12 inches",
              "depth": "12 inches"
            }
          }
  get:
    description: Get a list of products
    queryParameters:
      q:
        description: Search phrase to look for products
        type: string
        required: false
    responses:
      200:
        body:
          application/json:
            #example: !include schema/product-list.json

  #---------------------------------------------------------------
  # Nested resource representing a  single product - name parameter as part of the path.
  #---------------------------------------------------------------
  /{productId}:
    description: | # Retrieve a specific product using its ID.
    uriParameters:
     productId:
       displayName: Product ID
       type: integer
    get:
      description: Get a single product
      queryParameters:
        productId:
          description: The ID of the product
          type: integer
          required: true
      responses:
        200:
          body:
            application/json:
              #example: !include schema/product-list.json
    put:
      description: Updates a single product
      queryParameters:
        productId:
          description: The ID of the product
          type: integer
          required: true
      body:
        application/json:
          schema: |
            {
              "$schema": "http://json-schema.org/draft-03/schema",
              "product": {
                  "name": {
                      "required": true,
                      "type": "string"
                  },
                  "description": {
                      "required": true,
                      "type": "string"
                  },
                  "url": {
                      "required": true,
                      "type": "string"
                  },
                  "image": {
                      "required": true,
                      "type": "string"
                  },
                  "thumbnailUrl": {
                      "required": true,
                      "type": "string"
                  },
                  "keywords": {
                      "required": true,
                      "type": "string"
                  },
                  "brand": {
                      "required": false,
                      "type": "string"
                  },
                  "color": {
                      "required": false,
                      "type": "string"
                  },
                  "itemCondition": {
                      "required": false,
                      "type": "string"
                  },
                  "manufacturer": {
                      "required": false,
                      "type": "string"
                  },
                  "model": {
                      "required": false,
                      "type": "string"
                  },
                  "sku": {
                      "required": false,
                      "type": "string"
                  },
                  "weight": {
                      "required": false,
                      "type": "string"
                  },
                  "width": {
                      "required": false,
                      "type": "string"
                  },
                  "height": {
                      "required": false,
                      "type": "string"
                  },
                  "depth": {
                      "required": false,
                      "type": "string"
                  }
              },
              "required": true,
              "type": "object"
            }
          example: |
            {
              "product": {
                "id": "1",
                "name": "Product One",
                "description": "This is the full description of the product.",
                "url": "http://example.com",
                "image": "http://example.com/image.jpg",
                "thumbnailUrl": "http://example.com/image-thumb.jpg",
                "keywords": "western, cowboy",
                "brand": "Brand Name",
                "color": "Black",
                "itemCondition": "New",
                "manufacturer": "Manufacturer Name",
                "model": "Black",
                "sku": "SKU #",
                "weight": "12 pounds",
                "width": "12 inches",
                "height": "12 inches",
                "depth": "12 inches"
              }
            }
      responses:
        200:
          body:
            application/json:
              #example: !include schema/product-list.json  
    delete:
      description: Delete a single product
      queryParameters:
        productId:
          description: The ID of the product
          type: integer
          required: true
      responses:
        200:
          body:
            application/json:
              #example: !include schema/product-list.json                          
