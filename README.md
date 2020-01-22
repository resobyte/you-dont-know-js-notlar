# you-dont-know-js-notlar

Up&Coming

Bir değişkene atanmadan kullanılan değerler, literal value olarak adlandırılır.

a = b * 5

5 burada literal değişken

Bir değişkene atanmayan genel ifadelere expression statement(ifade deyimi) denir.

b * 2

Javascript yorumlanan bir dil olarak kabul görmektedir zira yazdığınız kod her çalıştırdığınızda proses edilir. Fakat bu tam olarak doğru değildir. JavaScript motoru programı çalıştırır çalıştırmaz derler ve anında derlenmiş kodu çalıştırır.

Objeler, özellik adı verilen isimlendirimiş yerlerde değer tutma özelliğine sahip değerlerdir. obj.a gösterimi, obj adındaki obje değerinin a adındaki özelliği anlamına gelir. Bu gösterime alternatif olarak obj["a"] gösterimi de kullanılabilir.

Eğer number türünde bir değeriniz varsa ve bunu ekrana yazdırmak istiyorsanız bu değeri string türüne çevirmeniz gerekir. JavaScript'de bu dönüşüme "coercion" denir.

String türündeki "99.99" değerini number türündeki "99.99" ile karşılaştırdığımızda çoğu insan bu değerlerin birbirine eşit olduğunu düşünür. Fakat bunlar birbirlerinden oldukça farklı değerlerdir. Bu, aynı değerin farklı türlerdeki gösterimidir. Bunların daha serbest kurallar çerçevesinde eşit olduklarını söleyebiliriz, değil mi?

Böyle durumlarda size yardımcı olabilmek için JavaScript bazı durumlarda implicitly karşılaştırma yapmanızı sağlayacaktır.

İlk bölümde söylediğimiz gibi JavaScript typed(tipli) değerlere sahiptir; typed değişkenlere değil.

string
number
boolean
null and undefined
object
symbol (ES6'da yeni)

typeof null ilginç bir durum, çünkü beklediğimiz sonuç "null" iken yanlış bir şekilde "object" sonucunu veriyor.

Here's an example of explicit coercion:

var a = "42";

var b = Number( a );

a;				// "42"
b;				// 42 -- the number!

And here's an example of implicit coercion:

var a = "42";

var b = a * 1;	// "42" implicitly coerced to 42 here

a;				// "42"
b;				// 42 -- the number!

The specific list of "falsy" values in JavaScript is as follows:

"" (empty string)
0, -0, NaN (invalid number)
null, undefined
false

Any value that's not on this "falsy" list is "truthy." Here are some examples of those:

"hello"
42
true
[ ], [ 1, "2", 3 ] (arrays)
{ }, { a: 42 } (objects)
function foo() { .. } (functions)

To boil down a whole lot of details to a few simple takeaways, and help you know whether to use == or === in various situations, here are my simple rules:

If either value (aka side) in a comparison could be the true or false value, avoid == and use ===.
If either value in a comparison could be of these specific values (0, "", or [] -- empty array), avoid == and use ===.
In all other cases, you're safe to use ==. Not only is it safe, but in many cases it simplifies your code in a way that improves readability.

Hoisting

Mecazi olarak, bu davranış, bir varyant kavramsal olarak kapalı kapsamının üstüne "taşındığında" kaldırma olarak adlandırılır. Teknik olarak, bu işlem kodun nasıl derlendiğiyle daha doğru bir şekilde açıklanır, ancak şimdilik bu ayrıntıları atlayabiliriz.

var olarak tekrar tanımlanması..

Nested Scopes -> İlgili değişkenin fonksiyonda geçerliliğini, yönetmesi

ternary operator. -> var b = (a > 41) ? "hello" : "world";

"use strict"; Kodu katı moda çevirerek, var değişkenini vs kullanmanızı sağlar.
