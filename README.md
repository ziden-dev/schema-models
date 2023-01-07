This repository contain some example of the json for Ziden schema with some related context . 
# Name
- To define the name of the schema or context we use **"name"** tag.
# Context
- To define the contexts or the conditions of one or multiple data type in the schema, we use **"@context"** tag.
- This contain an array of URI of predefined contexts or schemas that user want to use in their schema. 
# ID
- To specify the position of a property in a claim, we use the tag **"@id"**
## Standard position vocab
| Notation       | Slot index |
| -------------- |:----------:|
| std-pos: idx-1 |     2      |
| std-pos: idx-2 |     3      |
| std-pos: val-1 |     6      |
| std-pos: val-2 |     7      |

# Type
- The type of a property is defined by the **"type"** tag.
## Standard data type
- The standard data type have the id notation of *std* 
| Notation   | Type    | Description                                                |
| ---------- | ------- | ---------------------------------------------------------- |
| std:str    | String  | Standard string data type                                  |
| std:int64  | Integer | Standard 64-bit integer type                               |
| std:double | Double  | Standard 64-bit double type                                |
| std:obj    | Object  | Nesting of one or many child property                      |
| std:bool   | Boolean | Standard boolean data type                                 |
| std:date   | Date    | Date in YYYYMMDD format (no space or delimiter in between) |

## Custom data type
- The custom data type is *the stardard data type* which have *extra condition or value range*.
- The custom data type can only be defined in context.
- Declaring a new data type is the same as declare a property in a schema.

Example: 
``` json
{
"@type": "context",
"name":"US Identity Document",
"@id":"udi"
...
"gender":{
	"type": "std:string",
	"values": ["male", "female", "other"]
	}
}

{
"@type":"schema",
"name": "KYC form",
"@id": "12ab-34cd-56ef",
"@context":[
"raw.githubusercontent.com/ziden/schema-models/us-identity-document",
...
]
...
"gender":{
	"@id":"std-pos: val-1",
	"type":"udi:gender",
}
""
}

```
**Updating ...**