# What is HTTP? (HyperText Transfer Protocol)

Bir web sitesini görüntülemek istediğinizde o web sitesindeki html, resim ve video gibi çeşitli içeriklerin web clientına transferini sağlamakla görevli olan protokol HTTP protokolüdür.

## What is HTTPS? (HyperText Transfer Protocol Secure)

HTTPS, HTTP protokolünün güvenli olan versiyonudur. HTTPS, sadece web client ve web server arasındaki verileri şifrelemekle kalmaz bunun yanında o web serverını taklit eden bir şeyle konuşmadığınıza dair güvence de sağlar.

# What is a URL? (Uniform Resource Locator)

URL tarayıcımıza, hedef serverda gidilmek istenilen kaynağın nerede bulunduğunu tarif eder. Aşağıdaki gösterimde URL'in tüm özelliklerini görebilirsiniz. (Her aramada URL'in tüm özelliklerini kullanmayız.)

![Image](images/url.png)

## Scheme

Kaynağa erişmek için hangi protokolün kullanıldığını gösterir. (Örneğin HTTP, HTTPS, FTP olabilir.)

## User

Bazı servisler kimlik doğrulama gerektirir ve bu yüzden url'in bu kısmına kullanıcı adı ve parola girmeniz gerekir.

## Host

Erişmek istediğiniz web serverının domain name'i ya da IP adresidir

##  Port

Bağlanacağınız portu ifade eder. HTTP için -> 80 portu, HTTPS için -> 443 portu kullanılır ama bunun haricinde 1 - 65535 arasında herhangi portu içerebilir.

## Path

Erişmek istediğin kaynağın bulunduğu konumu daha doğrusu dosya yolunu ifade eder.

## Query String

Erişilmek istenilen yola ek olarak gönderilebilecek ekstra bitleri içerir. Bu ekstra bitler filtreleme, sıralama ve arama gibi çeşitli işlevlere yarayabilir. 

Örneğin, /blog? id=1 ifadesi blog path'ine "1" ID'sine sahip blog makalesini almayı söyler.

## Fragment

İstekte bulunan kaynağın içerisindeki sayfanın belirli bir parçasına erişmeye olanak tanır. Örneğin uzun bir sayfa olduğunu varsayarsak, o sayfanın sadece belirli bir kısmına erişmek isteyebiliriz.

# Making a Request

GET / HTTP/1.1 sadece bu ifadeyi yazarak bir web serverına istekte bulunabiliriz. Ama genelde bu çok yetersiz olacağından bir isteği ekstra bilgiler içeren "Header"ların içinde göndeririz. (Header konusuna sonra bakacağız.)

## BİR İSTEK ÖRNEĞİ OLARAK;

![IMAGE](images/asdf.png)

verebiliriz.

Şimdi bu isteği daha yakından inceleyelim.

## Line 1

Bu istek web serverından bilgi almak için "GET" methodunu kullanıyor, ana sayfayı "/" ile istiyor ve web serverına HTTP protokolünün 1.1 sürümünü kullandığımızı söylüyor.

## Line 2

Web sunucusuna tryhackme.com web sitesini istediğimizi belirtiyoruz.

## Line 3

Web serverına kullandığımız tarayıcının ismini ve versiyonunu söylüyoruz.

## Line 4

Web serverına bizi buraya yönlendiren web sayfasının ne olduğunu söylüyoruz.

## Line 5

HTTP istekleri, isteğin bittiğini web serverına bildirmek için her zaman boş bir satırla biter.

## CEVAP İSE ŞU ŞEKİLDE OLABİLİR;

![Image](images/qwe.png)

## Line 1

HTTP 1.1 serverın kullandığı HTTP protokolünün sürümüdür, ardından gelen "200 OK" ifadesi HTTP durum kodudur ve isteğin başarıyla tamamlandığını belirtir.

## Line 2

Bu satır bize web serverında çalışan web server yazılımını ve onun sürümünü ifade eder.

## Line 3

Web serverının geçerli tarihi, saati ve saat dilimini söyler.

## Line 4

Content-Type header'ı, clienta HTML, resim, video, pdf veya XML gibi ne tür bilgilerin gönderileceğini söyler.

## Line 5

Content-Lenght header'ı, clienta yanıtın ne kadar uzun olduğunu söyler ve böylece hiçbir verinin eksik olmadığı doğrulanabilir.

## Line 6

Aynı istekte de olduğu gibi yanıtın sonunu doğrulamak için de boş bir satır kullanılır.

## Line 7-14

İstenilen bilgiyi içerir. Yukarıdaki örnekte istenilen bilgi ana sayfa olduğundan yanıtta da html kodlarıyla bu web sayfasını istemciye yollamış.

# HTTP Methods

HTTP methodları, HTTP isteği yapılırken bu istekte amaçlanan eylemi ifade etmeye yarar. Bir sürü HTTP methodu olmakla birlikte biz en yaygın olanlara bakacağız.

## GET Request

Web serverından bilgi almak için "GET" methodu kullanılır.

## POST Request

Web serverına bilgi vermek için ve potansiyel olarak yeni kayıtlar (record) oluşturmak için kullanılır.

## PUT Request

Web serverında olan bir bilgiyi güncellemek amacıyla veri göndermek için kullanılır.

## DELETE Request

Web serverından bir bilgi ya da kayıt silmek için kullanılır.

# HTTP Status Codes

Yukarıda bahsettiğimiz gibi HTTP response yani yanıtlarının ilk satırı daima requestlerin sonucunu ve nasıl işleneceğini HTTP status code'ları ile bildirir.

#### 100-199 - Information Response

Bu aralıktaki durum kodları clienta requestin ilk parçasının geldiğini ve geri kalanının da gönderilmesi gerektiğini söyler. Bu kodlar artık çok yaygın değildir.

#### 200-299 - Success

Bu durum kodları clienta taleplerinin başarıyla gerçekleştiğini bildirir.

#### 300-399 - Redirection

Bunlar ise clientın isteğini başka bir kaynağa yönlendirmek için kullanılır. Bu kaynak bir web sayfası, hatta başka bir web sitesi bile olabilir.

#### 400-499 - Client Errors	

Yapılan istekte hata oluştuğunu clienta bildirmek için kullanılır.

#### 500-599 - Server Errors	

Bunlar ise server kaynaklı hataları bildirir. Bu durum kodları genelde isteği işleyen server tarafında oldukça büyük bir sorun olduğuna işaret eder.

# Common HTTP Status Codes:

### 200 - OK	

Talebin başarıyla tamamlandığını söyler.

### 201 - Created	

Kaynağın oluşturulduğunu söyler. (kaynak, yeni bir kullanıcı eklenmesi ya da yeni bir blog oluşturulması olabilir.)

### 301 - Moved Permanently

Client'in browserına bu kaynağın kalıcı olarak başka bir yere taşındığını söyler ya da oraya yönlendirir.

### 302 - Found	(Moved Temporarily)

Yukarıdakine benzerdir fakat farkı geçici olarak taşınmış olmasıdır ve yakın gelecekte tekrar taşınabilir. Aynı zamanda "302 Moved Temporarily" olarak da bilinir ama bu daha eskide kalmış bir kullanımdır.

### 400 - Bad Request

Clientın gönderdiği istekte bir şeylerin eksik ya da yanlış olduğunu ifade etmek için kullanılır. Bazen clientın gönderdiği talep web serverının istediği belirli bir parametre de gelmediği için böyle bir hatayla karşılaşılabilir.

### 401 - Not Authorised

Yetkili olmayan bir client kaynağa erişmek istediğinde bu hatayı alacaktır. Bu yetkilendirme işlemi genelde username ve password vererek sağlanabilir.

### 403 - Forbidden	

Giriş yapıp yapmadığınızdan bağımsız her türlü bu kaynağı görüntüleme izniniz olmadığında alacağınız hata mesajıdır.

### 405 - Method Not Allowed

Kaynağın bu methoda izin vermediğini belirtir. Örneğin, /create-account kaynağındasınız ve sunucu tarafı bir POST isteği ile yeni bir bilgi girmenizi bekliyor ama siz GET isteği gönderiyorsanız bu hatayı alırsınız.


### 404 - Page Not Found	

Clieantın talepte bulunduğu kaynak ya da sayfa aslında yoksa bu mesajı alırsınız.

### 500 - Internal Service Error

Bu hata mesajı, serverın beklenmeyen bir durumla karşılaştığını ve talebi yerine getiremediniği belirtir. Yani aslında sunucu tarafında bir problem olduğunu ama problemin tam olarak ne olduğu bilinmediğinden verilen hata mesajıdır. Bu hata bir yazılım hatası veya sunucu yapılandırma problemi gibi bir sorun olabilir.

### 503 - Service Unavailable	

Server aşırı yüklendiğinden ya da bakımda olduğundan clientın talebini karşılayamaz ve bu hata mesajı gösterilir.

# Headers

Header'lar bir talep yapılırken o talebin üstüne eklenen ek bitlerdir. Aslında HTTP request yapılırken header'a ihtiyaç olmamasına rağmen web sayfasını düzgün bir şekilde görüntüleyebilmek için gereklidir.

## Common Request Headers

Bu header'lar clientın (bu client genelde browser yani tarayıcıdır) servera talep gönderdiği esnada o talebin yanında ek olarak gönderdiği bitlerdir. Yani aslında o talep ek olarak bir headerla gider.

### Host

Web serverları çoğu zaman birden fazla web sitesine ev sahipliği yapar. Bu yüzden host header'ı ile beraber hangi web sitesine talepte bulunacağınızı belirtmeniz gerekir. Aksi takdirde web serverının varsayılan web sitesini alırsınız.

### User-Agent

Bu sizin browserınızı ve onun sürüm numarasını (versiyonunu) belirtir. Bu sayede web serverı, web sitesini sizin tarayıcınıza göre biçimlendirebilir. Ayrıca bazı HTML, JavaScript ve CSS öğelerinin yalnızca belirli tarayıcılarda kullanılabilir olduğunu da söyleyelim.

### Content-Length

Client, web serverına veri gönderirken o verinin içerik uzunluğunu söyleyerek, servera ne kadar veri beklemesi gerektiğini belirtir. Bu sayede server verilerin eksik gelip gelmediğinden emin olabilir.

### Accept-Encoding: 

Browser, web serverına hangi sıkıştırma yöntemlerini desteklediğini söyler. Böylece verilerin internet üzerinden daha rahat ve sorunsuz iletilmesi için daha küçük hale getirilmesi sağlanabilir.

### Cookie

Bunlar ise, bilgilerinizi hatırlamanıza yardımcı olmak için kullanılır. Client, önceki oturumlarda serverdan aldığı bu verileri tekrar servera gönderir. (Örneğin, daha önceden giriş yapmış bir kullanıcıyı hatırlama gibi)

## Common Response Headers

Bunlar, talepten sonra serverdan clieanta döndürülen yanıt başlıklarıdır.

### Set-Cookie

Request header'ının aksine bu sefer, web serverından clienta gönderilen çerezleri ifade eder. Tarayıcınıza çeşitli bilgileri kaydetmesini (depolamasını) söyler. (Bu da aynı şekilde oturum bilgisi vs. olabilir) Böylece tarayıcı ileride yapılacak requestlerde "cookie" header'ını kullanarak sunucunun kaydetmesini söylediği verileri tekrar sunucuya gönderebilecektir. Bunun sayesinde de çeşitli veriler sunucu tarafına hatırlatılabilir ve kullanıcı deneyimi iyileştirilebilir.

### Cache-Control

Response içeriğinin, tekrar request atmadan önce browserin belleğinde ne kadar süreyle saklanacağını belirtir.

### Content-Type

Daha önce de biraz bahsettiğimiz gibi Content-Type, yanıtın ne tür veriler içerdiğini ifade eder. Bu verilerin içeriği, HTML, CSS, JavaScript veya resim, PDF, video vb. şeyler olabilir. Browser, Content-Type'a bakarak bu verileri nasıl ve ne şekilde işlemesi gerektiğini bilir.

### Content-Encoding

Verilerin internet üzerinden gönderilirken daha küçük hale getirilmesi için kullandığı sıkıştırma yöntemini belirtir. Yukarıda da bahsedildiği üzere web serverı bu sıkıştırma yöntemini tarayıcının desteklediği sıkıştırma yöntemleri arasından belirler.

## Çerezler Hakkında;

Muhtemelen çerezleri daha önce duymuşsunuzdur, bunlar bilgisayarınızda depolanan küçük bir veri parçasıdır. Çerezler, bir web sunucusundan "Set-Cookie" header'ı aldığınızda kaydedilir. Daha sonra yaptığınız her istekte çerez verilerini web sunucusuna geri gönderirsiniz. HTTP "stateless" bir protokol olduğundan (önceki isteklerinizi takip etmez), çerezler web sunucusuna kim olduğunuzu, web sitesi için bazı kişisel ayarları veya daha önce web sitesine gidip gitmediğinizi hatırlatmak için kullanılabilir.

Çerezler birçok amaç için kullanılabilir ancak en yaygın olarak web sitesi kimlik doğrulaması için kullanılır. Çerez değeri genellikle parolayı görebileceğiniz açık metinli bir dize değil, bir belirteçtir (yani insan tarafından kolayca tahmin edilemeyen benzersiz gizli kod).













