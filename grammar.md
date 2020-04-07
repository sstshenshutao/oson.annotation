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
    