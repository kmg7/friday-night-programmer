# Use Cases

Burada sezon boyunca üzerinde durulabilecek örnek senaryolara ait detaylar yer almaktadır. Senaryolar UC kodları ile işaretlenmiştir.

## UC00 : Çağrı Merkezi Çözümleri için SDK

Bir çağrı merkezinin işleyişini düşünelim. Operatörlerin kullandığı uygulamanın ilk sürümü geliştiriliyor. Tarihler milenyuma bir kalayı göstermekte. Çağrı merkezindeki operatörler windows işletim sistemi için yazılmış bir masaüstü uygulama kullanıyorlar. Müşteri verileri farklı firmalardan farklı zaman dilimlerinde ve farklı depolama cihazları üzerinden geliyorlar. Örneğin müşteri portföyü nispeten küçük olan bir sigorta firması verisini diskete alıp mektupla gönderiyor ve bunu ayda bir gerçekleştiriyor. Bir başka finans kurumu ise yüksek müşteri portföyünü ayda bir olmak suretiyle CD ile yolluyor. Hatta farklı bir firma nispeten ilk sisteme aktarılan müşterilerinde gerçekleşen güncellemeleri içeren bir e-postayı firmaya gönderiyor. Her kurumsal müşterinin yolladığı bilgiler farklı formatlarda ve farklı şema yapılarına sahip. Program ilk yıllarında büyük müşteri verilerini dBase, Paradox ve benzeri veri tabanlarında yönetebiliyor ancak zamanla sisteme yeni kurumsal müşteriler dahil oluyor ve kullanılacak veri boyutu giderek büyüyor. Sonuçta Oracle veri tabanına geçilmesine karar veriliyor. Bu senaryoyu 1999 yılı itibariyle aşağıdaki gibi hayal edelim.

![1999 Senaroysu](../images/Scenario1999.png)

Sistem migration planlarından sonra birkaç yıl daha sorunsuz çalışıyor. Çağrı merkezindeki operatör sayısı üç katına çıkıyor ancak tüm sistem aynı kattaki bir network üzerinden yürümeye devam ediyor. Ne yazık ki bir süre sonra korkunç salgın başlıyor ve pandemi ilan ediliyor. İnsanlar evlere kapanırken çağrı merkezi personelinin operasyonu evdeki bilgisayarlarından yürütmesi gerekiyor. Kısa süre içerisinde tüm uygulamanın web tabanlı bir sisteme geçmesine karar veriliyor. Çağrı merkezinin anlaşmalı olduğu kurumsal müşteriler modern teknolojilerden yararlanarak portföylerini artık servisler aracılığıyla iletebileceklerini belirtiyor ancak veri boyutları oldukça büyük ve bu nedenle sadece değişen ve yeni eklenen müşteri verilerinin çekileceği bir sisteme ihtiyaç var gibi duruyor. O vakitlerde firmalar bazı müşteri bilgilerini XML Web servisler ve hatta REST tabanlı api'ler araclığı ile de vermeye başlıyorlar. Arada yine işi farklı şekillerde çözen örneğin iki kurum arasında güvenli olarak kullanılabilen bir FTP sunucusuna dosya bırakanlar da var. Bu yeni duruma göre çağrı merkezinde müşteri verilerinin tutulmasına da gerek olmayabilir lakin bu birazda iş modelinin yürütülüşüne bağlı. Neyse ki biz bu detayları çok fazla kurcalamıyoruz ve senaryomuz aşağıdaki şekline bürünmeye başlıyor.

![2004 Sonrasi Senaryosu](../images/Scenario2004.png)

Zamanla uygulamadaki teknik borç yükünün arttığı fark ediliyor. Şirket oldukça şanslı ki kendilerine ürünü yenilemeleri için iyi bir bütçe ve kaynak ayrılıyor. Var olan sistemi günümüz teknolojileri ile yeniden yazmamız bekleniyor.

En başında itibaren yeni sürüme kadar çıkabilecek sadece ufak değişiklilerle yeni teknolojilere adapte edilebilecek bir çatı _(Framework)_ geliştirilebilir miydi? Müşteri verilerinin çağrı merkezi uygulaması tarafından ele alınmasında ne tür senaryolar ele alınabilirdi?

## UC01 : Üniversite Dönem Projelerinin Yönetimi için Uygulama

Üniversitede ders verdiğimizi düşünelim. Dönem boyunca öğrenciler belli konu başlıklarında projeler alıyor olsun. Projelerde konular belli ve eğitmen tarafından giriliyor. Öğrencilerin en az iki kişilik takımlar oluşturarak havuzdan bir proje seçmesi isteniyor. Projelerin github veya muadili bir kod reposunda tutulması isteniyor. Proje notu takımdaki tüm öğrenciler için geçerli. Proje notunun 100 üzerinden hesap edildiğini düşünürsek belli başlı kriterleri sağlaması bekleniyor. Örneğin mutlak bir kaynak kod reposunda tutulması, detaylı bir Readme dosyası içermesi, Clean Code kriterlerini sağlaması, seçilmiş olan dile göre belli prensipleri içermesi _(Örneğin C# ile ilgili bir proje ise OOP temellerini barındırması, SOLID ilkelerine uygun olması)_ iyi bir model tasarımına sahip olması ve benzer birçok kriter sayılabilir. Normalde aşağıdaki gibi bir Excel tablosu pekala bu iş için oldukça idealdir ki ben bunu kullanıyorum. İTÜ Matematik Mühendisliği bölümüne verdiğim C# ile Nesne Yönelimli Programlamanın temelleri konulu derse ait proje ödevlerinden birisini aşağıdaki Google Sheet tablosunda olduğu gibi tutmuştum.

![Project Score Card](../images/ProjectScoreCard.png)

Aslında Excel/Google Sheet bu tip çözümlerde son derece kullanışlı araçlar. Gerçekten başka hiçbir programa ihtiyaç duymadan her şeyi Excel gibi ürünlerde halletmek pekala mümkün olabilir :) Ancak biz bunun için bir program yazmaya çalışabiliriz. Senaryomuzu baz alarak proje, takım ve öğrenci girişlerinin yapılabildiği, proje takım eşleştirmelerinin gerçekleştirildiği, proje gelişim tarihçesinin izlenebildiği web tabanlı bir uygulama ele alınabilir. Başlangıçta proje içerisindeki enstrümanlara ait model yapısı aşağıdaki çizelgede olduğu gibi düşünülebilir ancak ihtiyaçlara göre bu zamanla değişebilir. Şimdilik senaryomuzda bu grafiği baz alarak hareket edelim.

![Use Case 02 Solution Model](../images/ProjectScoreCardModel.png)
