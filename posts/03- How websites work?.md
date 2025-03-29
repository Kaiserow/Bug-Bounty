# How websites work?

Bir web sitesini oluşturan iki bileşen vardır;

## Front-end (Client Side)

Tarayıcınızın web sitesini görüntüleme şeklidir.

## Back-end (Server Side)

Talebinizi işleyen ve bir cevap döndüren sunucunun sürecidir.

# HTML

HTML, web sitelerini inşa etmek için ve onların genel yapılarını tanımlamak için kullanılır.

CSS, web sitelerinin daha iyi gözükmesi için çeşitli stil seçenekleri eklenmesine olanak tanır.

JavaScript ise daha kompleks özelliklerin uygulanmasında ve sayfaların interaksiyonunu arttırmakta kullanılır.

HyperText Markup Language (HTML), web sitelerinin yazıldığı dildir. Elementler (ya da tags) HTML sayfalarının bloklar halinde inşa edilmesine olanak tanır ve browsera içeriğin ne şekilde gösterilmesi gerektiğini söyler. Bu yapıya F12'ye basarak "Elements" kısmından ulaşabilirsiniz. HTML yapısını daha yakından incelemek gerekirse;

#### <!DOCTYPE html>

Sayfanın HTML5 dökümanı olduğunu tanımlar. Bu sayede farklı tarayıcılar arasında standartizasyon sağlanır. Yani aslında tarayıcıya sayfayı doğru şekilde görüntüleyebilmesi için HTML5 kullanmasını söyler.

#### <html>

Bu element, HTML sayfasının kök yani temel elementidir. Diğer tüm elementler bundan sonra gelmelidir.

#### <head>

Sayfa hakkında bilgileri içerir. (Örneğin sayfanın başlığı head elementi içinde yazılır.)

#### <body>

Bu element ise HTML dökümanının gövdesini oluşturur. sadece <body> elementi içinde yazılan içerikler tarayıcıda gösterilir.

#### <h1>

Büyük bir başlık vermek için kullanılır.

#### <p>

Paragrafı tanımlar.

Bunlar gibi daha bir çok tag bulunur.

Ayrıca bu tagler onlara daha fazla özellik kazandıran ve "attribute" adı verilen niteliklere sahip olabilir. Örneğin, <p class="bold-text"> şeklinde "class" niteliği paragraftaki metinin daha kalın olmasını sağlar. Bunun yanında <img src="img/cat.jpg"> ise img elementine ek olarak bir kaynağın yolunu belirtir. Böylece resim bu kaynaktan temin edilebilir.

class niteliği birden fazla element için kullanılabilir ama bunun yanında "id" attribute'u gibi (<p id="example">) tek bir element için kullanılması gereken nitelikler de mevcuttur. Bunlar genelde JavaScript ile belirli bir elemente hızlıca ve doğrudan erişmek için ya da CSS'te tek bir elemente özel bir stil vermek için tercih edilebilir.

# JavaScript (JS)

HTML web sitesinin yapısını ve içeriğini oluşturmak için kullanılırken JS, web sayfalarının işlevselliğini kontrol etmek için kullanılır. JS olmadan bir web sitesinin sayfaları etkileşimli öğelere sahip olamaz. Bu da sayfaları statik yaparak daha yavan bir görüntü sunardı. JS, sayfaların dinamik olmasını sağlayarak sayfanın güncel kalmasını sağlayabilir. Örneğin bir kullanıcı bir düğmeye bastığında sayfa değişebilir veya bunun yanında çeşitli hareketli animasyonları görüntüleme işlevselliği sağlayabilir.

JS, sayfa kaynak koduna (page source code) eklenir ve <script> etiketi içinde yüklenebilir ya da src attribute'u ile uzaktan eklenebilir. Örneğin;

<script src="/location/of/javascript_file.js"></script> gibi.

# Sensitive Data Exposure

Bir web sitesinin clear-text (yani açık metin) bilgilerini end-user'a karşı düzgün bir şekilde koruyamaması ya da kaldıramaması durumunda hassas veriler açığa çıkabilir. Bu bilgiler genellikle bir sitenin front-end source code'unda bulunur.

Artık web sitelerinin HTML elementleri kullanılarak oluşturulduğunu ve bunları da o sitenin kaynak kodunu (page source) görüntüleyerek görebileceğimizi öğrendik. Bir web site geliştiricisi bu kaynak kodunun içinde çeşitli kimlik bilgilerini, web sitesinin özel kısımlarına ait gizli linkleri ya da HTML-JS gibi kodların içinde bulunan hassas veriyi kaldırmayı unutabilir. Bu tür hassas veriler kötü niyetli bir aktör tarafından çeşitli saldırılar için kullanılabilir. Hatta daha kötüsü, saldırgan bazen bazı bilgiler aracılığı ile sitenin back-end bileşenlerine bile erişebilir. Bu yüzden bir web uygulamasının güvenliği incelenirken ilk olarak kaynak kodu incelenerek çeşitli hassas verilerin olup olmadığı gözden geçirilmelidir.

# HTML Injection

HTML injection, filtrelenmemiş kullanıcı girdisinin (input) sayfada görüntülenmesi durumunda oluşan bir güvenlik açığıdır Bu girdi filtrelenmezse (yani herhangi bir kullanıcının web sitesine girdiği kötü amaçlı metinleri filtreleyememekten bahsediyoruz.) ve bu girdi sayfada kullanılırsa, bir salgırdan bu siteye istediği html kodunu enjekte edebilir. Böylece bu saldırgan sayfanın görünümünü ve JS kodları ile de işlevselliğini kontrol edebilir.

Burada temel kural asla kullanıcı girdisine güvenmemektir. Bu kötü amaçlı girdileri önlemek için bir geliştirici, "Sanitization" adı verilen girdi temizleme işlemini gerçekleştirmelidir. Mesela bu girdi temizleme işini HTML elementlerini kaldırarak yapabilir.


