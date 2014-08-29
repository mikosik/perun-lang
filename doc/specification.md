## The Perun Language specification


All grammar in this specification is defined in [Antl4](http://www.antlr.org/).


```
package: packageIdentifier '{' packageElement* '}'
packageElement: class | function

class: identifier '{' field* method* '}'
field: variableDeclaration ';'
method: function

function: functionName '(' parameterList? ')' result '{' statement* '}'
functionName: identifier
parameterList: parameter (',' parameter)*
parameter: variableDeclaration

statement: assignment | TODO


variableDeclaration: variableName variableType
variableName: identifier
variableType: identifier


IDENTIFIER: FIRST_CHAR ( FIRST_CHAR | OTHER_CHAR )* ;
fragment FIRST_CHAR: 'a'..'z' | 'A'..'Z' | '_' ;
fragment OTHER_CHAR: '0'..'9' | '_' | ;

```


