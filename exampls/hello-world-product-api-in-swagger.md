{
    "apiVersion": "1.0",
    "swaggerVersion": "1.2",
    "basePath": "http://products.api.apievangelist.com/",
    "resourcePath": "/products",
    "produces": [
        "application/json"
    ],
    "apis": [
        {
            "path": "/products/",
            "operations": [
                {
                    "method": "GET",
                    "summary": "Pulls a listing of products",
                    "notes": "Returns a list of products, allowing you to filter by keyword query.",
                    "nickname": "getJobs",
                    "type": "products",
                    "parameters": [
                        {
                            "name": "query",
                            "description": "a text query to search across products",
                            "required": false,
                            "allowMultiple": false,
                            "dataType": "string",
                            "paramType": "query"
                        }
                    ],
                    "produces": [
                        "application/json"
                    ],
                    "responseMessages": [
                        {
                            "code": 404,
                            "message": "No Jobs To Return"
                        }
                    ]
                }
            ]
        },
        {
            "path": "/products/{id}",
            "operations": [
                {
                    "method": "GET",
                    "summary": "Retrieve an product using its ID",
                    "notes": "Returns a products detail",
                    "type": "people",
                    "nickname": "getJobs",
                    "produces": [
                        "application/json"
                    ],
                    "parameters": [
                        {
                            "name": "id",
                            "description": "id for the video, notice this is in the path, not a query variable",
                            "required": false,
                            "allowMultiple": false,
                            "dataType": "integer",
                            "paramType": "path"
                        }
                    ],
                    "responseMessages": [
                        {
                            "code": 400,
                            "message": "Invalid Application Information ID supplied"
                        },
                        {
                            "code": 404,
                            "message": "People not found"
                        }
                    ]
                }
            ]
        }
    ],
    "models": {
        "products": {
            "id": "products",
            "properties": {
                "id": {
                    "type": "integer"
                },
                "name": {
                    "type": "string"
                },
                "description": {
                    "type": "string"
                },
                "url": {
                    "type": "string"
                },
                "video": {
                    "type": "string"
                },
                "thumbnailUrl": {
                    "type": "string"
                },
                "keywords": {
                    "type": "string"
                },
                "inLanguage": {
                    "type": "string"
                },
                "creator": {
                    "type": "string"
                }
            }
        }
    }
}
