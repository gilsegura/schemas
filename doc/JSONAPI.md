{JSON:API} SCHEMA SPECIFICATIONS
========

## Specifications

| Specification | Version |                                     Schema                                      |
|:-------------:|:-------:|:-------------------------------------------------------------------------------:|
|   json:api    |   1.1   | [schema](./../jsonapi/v1.1/schema.json) / [datum](./../jsonapi/v1.1/datum.json) |
|    openapi    |  3.0.3  |                       [schema](./../jsonapi/openapi.json)                       |

## Usage

```
{
    "paths": {
        "/articles": {
            "$ref": "./openapi.min.json#/paths/~1resources"
        },
        "/articles/{id}": {
            "$ref": "./openapi.min.json#/paths/~1resources~1{id}"
        },
        "/articles/{id}/relationships/author": {
            "$ref": "./openapi.min.json#/paths/~1resources~1{id}~1relationships~1{related}"
        },
        "/articles/{id}/relationships/tags": {
            "$ref": "./openapi.min.json#/paths/~1resources~1{id}~1relationships~1{related}"
        }
    }
}
```

```
{
    "paths": {
        "/articles": {
            "get": {
                "$ref": "./openapi.min.json#/paths/~1resources/get"
            },
            "post": {
                "$ref": "./openapi.min.json#/paths/~1resources/post"
            }
        }
    }
}
```

```
{
    "paths: {
        "/articles": {
            "post": {
                "parameters": [
                    {
                        "$ref": "./openapi.min.json#/components/parameters/content-type"
                    },
                    {
                        "$ref": "./openapi.min.json#/components/parameters/accept"
                    }
                ],
                "requestBody": {
                    "required": true,
                    "content": {
                        "application/vnd.api+json": {
                            "schema": {
                                "type": "object",
                                "required": [
                                    "data"
                                ],
                                "properties": {
                                    "data": {
                                        "type": "object",
                                        "required": [
                                            "type",
                                            "id"
                                        ],
                                        "properties": {
                                            "type": {
                                                "const": "articles"
                                            },
                                            "id": {
                                                "type": "string",
                                                "format": "uuid"
                                            }
                                        },
                                         "additionalProperties": false
                                    }
                                },
                                "additionalProperties": false
                            }
                        }
                    }
                },
                "responses": {
                    "201": {
                        "$ref": "./openapi.min.json#/paths/~1resources/post/responses/201"
                    }
                }
            }
        }
    }
}
```