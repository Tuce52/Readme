1. Proje Tanımı

Bu proje, bir metin dosyasını analiz ederek metne ait temel istatistiksel bilgileri elde etmeyi amaçlamaktadır. Program; kelime sayısı, cümle sayısı, satır sayısı ve harf sayısı gibi verileri hesaplamakta, ayrıca metinde en sık geçen, en uzun ve en kısa kelimeleri belirlemektedir.

Proje, metin analizi ve dosya işlemleri konularına giriş seviyesinde örnek bir uygulama sunmakta ve temel doğal dil işleme mantığını öğretmeyi hedeflemektedir.

2. Çalışma Mantığı

Programın çalışma mantığı aşağıdaki adımlardan oluşmaktadır:

Metin dosyası UTF-8 formatında okunur.
```cs
string metin = File.ReadAllText("metin.txt", Encoding.UTF8);
```
Metin içerisindeki noktalama işaretleri ve özel karakterler temizlenir.
```cs
 string temizMetin = Regex.Replace(
     metin,
     @"[^\p{L}\s]",
     ""
)
```
Metin, Türkçe dil kurallarına uygun şekilde küçük harfe dönüştürülür.
```cs
.ToLower(new CultureInfo("tr-TR"));
```

Metin kelimelere ayrılır.
```cs
 temizMetin = Regex.Replace(temizMetin, @"\s+", " ");

 string[] kelimeler = temizMetin
     .Split(new[] { ' ' }, StringSplitOptions.RemoveEmptyEntries);

```


Kelime, cümle, satır ve harf sayıları hesaplanır.

Kelime frekans analizi yapılarak en sık geçen kelime belirlenir.

Kelime uzunluklarına göre en uzun ve en kısa kelimeler tespit edilir.

Elde edilen sonuçlar kullanıcıya ekranda gösterilir.

3. Kullanılan Teknolojiler

Programlama Dili: C#

Kullanılan Kütüphaneler / Namespace’ler:

System

System.IO

System.Linq

System.Text

System.Text.RegularExpressions

System.Globalization

4. Sistem Gereksinimleri

İşletim Sistemi: Windows 10 veya üzeri

Gerekli Yazılımlar:

.NET Framework 4.7 veya üzeri / .NET 6+

Visual Studio 2022 (önerilen)

Girdi Dosyası: UTF-8 formatında .txt uzantılı metin dosyası

5. Lisans Bilgisi

Bu proje MIT Lisansı kapsamında sunulmaktadır.

MIT Lisansı tercih edilmiştir çünkü:

Açık kaynak kullanımına uygundur.

Akademik ve ticari çalışmalarda serbestçe kullanılabilir.

Kodun paylaşılmasına ve geliştirilmesine izin verir.

Basit ve anlaşılır bir lisans yapısına sahiptir.

Bu lisans sayesinde proje eğitim amaçlı olarak özgürce kullanılabilir ve geliştirilebilir.
