__oson.annotation__ Language      
==========      
      
Abstract      
--------     
__oson.annotation__ is a small language which is used in the language [__oson__](https://github.com/sstshenshutao/oson).   
      
>__oson__ is a micro-language to describe the schema of JSON. It allows you to write down the JSON and the schema of JSON inside only one file(with annotation). oson is a subset of JSON-Schema, so it can be compiled to JSON-schema, it is inspired by "orderly" and annotation.      
      
  
oson.annotation can be compiled to a [JSON](https://www.json.org/json-zh.html), which is also a part of JSON Schema with path: [JSON Pointer (#/properties/somekey)](https://tools.ietf.org/html/rfc6901).  
      
For more details, see [oson/doc.md](https://github.com/sstshenshutao/oson/blob/master/doc.md)  
  
A compiler can be found here:  
[oson.annotation.js](https://github.com/sstshenshutao/oson.annotation.js)

## ------------------- the grammar of OSON.ANNOTATION ---------------  
    annotationObject  
        '@' annotation  
          
    annotation  
        annotationType  
          
    annotationType  
        unionType  
        basicType  
          
    unionType  
        '(' basicType ')' '|' unionType  
        '(' basicType ')'  
          
    basicType  
        basicTypePrefix basicTypeSuffix  
          
    basicTypePrefix  
        INTEGER_TYPE optionalRange  
        NUMBER_TYPE optionalRange  
        BOOLEAN_TYPE  
        NULL_TYPE  
        ANY_TYPE  
        STRING_TYPE optionalRange optionalPerlRegex  
        JSON_TYPE optionalExtraProperties  
        '\*' optionalTypeTuple  
          
    optionalTypeTuple  
        unionType  
        #nothing  
          
    basicTypeSuffix  
        optionalEnumValues optionalDefaultValue  
          
    optionalEnumValues  
        '{' elements '}'  
        '{' '}'  
        #nothing  
          
    optionalDefaultValue  
        '=' json_value  
        #nothing  
          
    optionalRange  
        '[' json_number ',' json_number ']'  
        '[' json_number ',' ']'  
        '[' ',' json_number ']'  
        '[' ',' ']'  
        #nothing  
          
    optionalPerlRegex  
        REGEX  
        #nothing  
          
    optionalExtraProperties  
        '\`' json_object '\`'  
        #nothing  
          
## ------------------- the grammar of JSON ---------------  
      
      
    elements  
        json_value  
        json_value ',' elements  
          
    json_value  
        json_string  
        json_number  
        json_object  
        json_array  
        TRUE  
        FALSE  
        NULL  
          
    json_number  
        NUMBER_LIT  
          
    json_array  
        '[' ']'  
        '[' elements ']'  
          
    json_object  
        '{' '}'  
        '{' members '}'  
          
    members  
        pair  
        pair ',' members  
          
    pair  
        STRING_LIT ':' json_value  
          
    json_string  
        STRING_LIT  
        
