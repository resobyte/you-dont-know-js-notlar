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
