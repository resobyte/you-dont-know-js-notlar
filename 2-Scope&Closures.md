# you-dont-know-js-notlar

## Scopes & Closures

> Çeşitli dillerle etkileşim seviyenize bağlı olarak kendiliğinden anlaşılır olabilir veya şaşırtıcı olabilir, ancak JavaScript'in genel "dinamik" veya "yorumlanmış" diller kategorisine girmesine rağmen, aslında derlenmiş dil. Geleneksel olarak derlenmiş birçok dilde olduğu gibi, çeşitli dağıtılmış sistemler arasında taşınabilir derlemenin sonuçları da önceden derlenmemiştir. (Runtime Error)


Geleneksel derlenmiş dil işleminde, programınız kaynak kodun bir kısmı yürütülmeden önce kabaca "derleme" olarak adlandırılan genellikle üç adımdan geçecektir.

1. Tokenizing/Lexing
Aslında yazdığımız bir 

```javascript
var a = 2;
``` 
Anlamlı parçalara bölünür, 
- var
- a
- =
- 2
- ;

Buradaki aktör lexical analyzer, belirli kurallara göre karakterler okunup token’a dönüştürülür. Kod metninden aşağıdaki gibi bir token listesi üretilmiş oluyor.

```javascript
let count = 2; 
/* 
[
  {value: 'let', type: 'keyword'},
  {value: 'count', type: 'identifier'},
  ...
]
*/

```
Bu işlem sırasında kelimeleri ayrıştırmanın aslında basit bir mantığı var. Kod harf harf okunurken bir boşluk karakterine, operatör işaretine(== gibi) veya özel bir karaktere rastlandığında bir kelime tamamlanıp ayrıştırılır.

2. Parsing

Syntax analyzer diğer adıyla parser, bir önceki aşamada oluşturulmuş token serisini kurallı anlamlı bir yapıya(Abstract Syntax Tree) dönüştürür. Ayrıca dilin syntax’ına uygun olup olmadığı burada kontrol edilir ve buna göre varsa syntax hataları fırlatılır. 

Örnek KOD:
```javascript
let tips = [
  "Click on any AST node with a '+' to expand it",

  "Hovering over a node highlights the \
   corresponding part in the source code",

  "Shift click on an AST node expands the whole substree"
];

function printTips() {
  tips.forEach((tip, i) => console.log(`Tip ${i}:` + tip));
}
```

AST:
```json
{
  "type": "Program",
  "start": 0,
  "end": 476,
  "body": [
    {
      "type": "VariableDeclaration",
      "start": 179,
      "end": 389,
      "declarations": [
        {
          "type": "VariableDeclarator",
          "start": 183,
          "end": 388,
          "id": {
            "type": "Identifier",
            "start": 183,
            "end": 187,
            "name": "tips"
          },
          "init": {
            "type": "ArrayExpression",
            "start": 190,
            "end": 388,
            "elements": [
              {
                "type": "Literal",
                "start": 194,
                "end": 241,
                "value": "Click on any AST node with a '+' to expand it",
                "raw": "\"Click on any AST node with a '+' to expand it\""
              },
              {
                "type": "Literal",
                "start": 246,
                "end": 326,
                "value": "Hovering over a node highlights the    corresponding part in the source code",
                "raw": "\"Hovering over a node highlights the \\\n   corresponding part in the source code\""
              },
              {
                "type": "Literal",
                "start": 331,
                "end": 386,
                "value": "Shift click on an AST node expands the whole substree",
                "raw": "\"Shift click on an AST node expands the whole substree\""
              }
            ]
          }
        }
      ],
      "kind": "let"
    },
    {
      "type": "FunctionDeclaration",
      "start": 391,
      "end": 475,
      "id": {
        "type": "Identifier",
        "start": 400,
        "end": 409,
        "name": "printTips"
      },
      "expression": false,
      "generator": false,
      "async": false,
      "params": [],
      "body": {
        "type": "BlockStatement",
        "start": 412,
        "end": 475,
        "body": [
          {
            "type": "ExpressionStatement",
            "start": 416,
            "end": 473,
            "expression": {
              "type": "CallExpression",
              "start": 416,
              "end": 472,
              "callee": {
                "type": "MemberExpression",
                "start": 416,
                "end": 428,
                "object": {
                  "type": "Identifier",
                  "start": 416,
                  "end": 420,
                  "name": "tips"
                },
                "property": {
                  "type": "Identifier",
                  "start": 421,
                  "end": 428,
                  "name": "forEach"
                },
                "computed": false
              },
              "arguments": [
                {
                  "type": "ArrowFunctionExpression",
                  "start": 429,
                  "end": 471,
                  "id": null,
                  "expression": true,
                  "generator": false,
                  "async": false,
                  "params": [
                    {
                      "type": "Identifier",
                      "start": 430,
                      "end": 433,
                      "name": "tip"
                    },
                    {
                      "type": "Identifier",
                      "start": 435,
                      "end": 436,
                      "name": "i"
                    }
                  ],
                  "body": {
                    "type": "CallExpression",
                    "start": 441,
                    "end": 471,
                    "callee": {
                      "type": "MemberExpression",
                      "start": 441,
                      "end": 452,
                      "object": {
                        "type": "Identifier",
                        "start": 441,
                        "end": 448,
                        "name": "console"
                      },
                      "property": {
                        "type": "Identifier",
                        "start": 449,
                        "end": 452,
                        "name": "log"
                      },
                      "computed": false
                    },
                    "arguments": [
                      {
                        "type": "BinaryExpression",
                        "start": 453,
                        "end": 470,
                        "left": {
                          "type": "TemplateLiteral",
                          "start": 453,
                          "end": 464,
                          "expressions": [
                            {
                              "type": "Identifier",
                              "start": 460,
                              "end": 461,
                              "name": "i"
                            }
                          ],
                          "quasis": [
                            {
                              "type": "TemplateElement",
                              "start": 454,
                              "end": 458,
                              "value": {
                                "raw": "Tip ",
                                "cooked": "Tip "
                              },
                              "tail": false
                            },
                            {
                              "type": "TemplateElement",
                              "start": 462,
                              "end": 463,
                              "value": {
                                "raw": ":",
                                "cooked": ":"
                              },
                              "tail": true
                            }
                          ]
                        },
                        "operator": "+",
                        "right": {
                          "type": "Identifier",
                          "start": 467,
                          "end": 470,
                          "name": "tip"
                        }
                      }
                    ]
                  }
                }
              ]
            }
          }
        ]
      }
    }
  ],
  "sourceType": "module"
}
```
3. Code-Generation:
Bu süreçte input olarak alınan AST, makine koduna dönüştürülür. Bu kod bir JS Engine(V8, SpiderMonkey…) tarafından execute edilir.

> JavaScript motoru, diğer birçok dil derleyicisinde olduğu gibi, bu üç adımdan çok daha karmaşıktır. Örneğin, ayrıştırma ve kod oluşturma sürecinde, gereksiz öğelerin daraltılması vb. Dahil olmak üzere yürütmenin performansını optimize etmek için kesinlikle adımlar vardır. Burada sadece geniş vuruşlarla resim yapıyorum. Ancak bence kısa bir süre içinde üstlendiğimiz bu ayrıntıların neden üst düzeyde alakalı olduğunu göreceksiniz. Birincisi, JavaScript motorları optimize etmek için yeterince zamana sahip olma lüksünü (diğer dil derleyicileri gibi) elde etmez, çünkü JavaScript derlemesi diğer dillerde olduğu gibi bir derleme adımında vaktinden önce gerçekleşmez. JavaScript için, derleme, çoğu durumda, kod yürütülmeden önce yalnızca mikrosaniye (veya daha az!) Olur. En hızlı performansı sağlamak için JS motorları, burada tartışmamızın "kapsamının" ötesinde olan her türlü hileyi (tembel derleme ve hatta sıcak yeniden derleme vb.) Kullanır. Basitçe söylemek gerekirse, herhangi bir JavaScript snippet'inin yürütülmeden önce (genellikle hemen önce!) Derlenmesi gerektiğini söyleyelim. Böylece, JS derleyicisi var var = 2; ve önce derleyin ve daha sonra hemen uygulamaya hazır hale getirmeye hazır olun.


