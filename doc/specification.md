## The Perun Language specification


All grammar in this specification is defined in [Antl4](http://www.antlr.org/).


```
compilationUnit:  ( class | function )* ;

class: IDENTIFIER '{' field* method* '}' ;
field: variable ';' ;
method: function ';' ;

function: (IDENTIFIER)? functionType '{' statement* '}' ;
functionType: '(' parameterList? ')' type
parameterList: variable (',' variable)* ;

statement: ( assignment | declaration | expression ) ';' ;

assignment: assignmentLeft '=' assignmentRight ;
assignmentLeft: variable | variableName ;
assignmentRight: declaration | expression ;

declaration: function | class ;

expression: ( callable | expression ) call ;
callable: function | qualifiedIdentifier ;
call: '(' argumentList ')' ;
argumentList: expression ( ',' expression )*

variable: variableName type ;
variableName: identifier ;
type: classType | functionType ;
classType: qualifiedIdentifier ;


// TODO handle comments

qualifiedIdentifier: IDENTIFIER ( ':' IDENTIFIER )* ;

IDENTIFIER: FIRST_CHAR ( FIRST_CHAR | OTHER_CHAR )* ;
fragment FIRST_CHAR: 'a'..'z' | 'A'..'Z' | '_' ;
fragment OTHER_CHAR: '0'..'9' | '_' | ;

```



