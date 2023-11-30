# E-TicaretDatabase Diyagram ve Açıklamaları

![E-TicaretDatabase](https://github.com/berrekucuk/E-TicaretDatabase/assets/139650041/478501f0-fb2c-4315-9319-cbdd4aad7335)

+ **Categories** : Ürün kategorilerini temsil eden tablodur.
+ **CategoryEquivalents** : Kategori eşdeğerlerini belirten bir tablodur. Örneğin, bir ürünün birden fazla kategoriye ait olması durumunda, bu eşdeğerler bu tabloda tutulabilir.
+ **CategoryFields** : Kategori alanlarını tanımlar. Her bir kategori alanı, bir kategori ile ilişkilendirilmiş özel özellikleri veya bilgileri içerir.
+ **CommentImageUrls** : Yorumlara ait resim URL'lerini saklar. Bir yorumun resimlerini içeren bu tablo, yorumlara dair görsel içerikleri yönetir.
+ **CommentLikes** : Yorumlara yapılan beğenileri izler. Hangi kullanıcının hangi yorumu beğendiğini belirten ilişkisel bir tablodur.
+ **Comments** : Ürünler veya satıcılar hakkında yapılan kullanıcı yorumlarını içeren tablodur.
+ **Invoices** : Satın alımların faturalara bilgilerini temsil eder.
+ **Orders** : Müşteri siparişlerini temsil eder.
+ **OrderStatuses** : Sipariş durumlarını yönetir. Bir siparişin hangi aşamada olduğunu belirten durumları içerir (örneğin, bekliyor, kargoya verildi, teslim edildi).
+ **PaymentDetails** : Ödeme detaylarını temsil eden  tablodur.
+ **ProductFieldCategoryFields** : Ürün alanları ile kategori alanlarını ilişkilendiren bir ara tablodur.
+ **ProductFieldImageUrls** : Ürün alanlarına ait resim URL'lerini saklar.
+ **ProductFields** : Ürün özelliklerini tanımlar. Her ürün alanı, bir ürünle ilişkilendirilmiş özel özellikleri içerir.
+ **Product** : Satılabilir ürünleri temsil eder.
+ **ProductSelections** : Ürün seçeneklerini yönetmek ve bu seçeneklerin hiyerarşisini tanımlamak için kullanılan tablodur.
+ **Sellers** : Satıcıları temsil eden tablodur.
+ **SellerTitles** : Satıcı unvanlarını içerir. Örneğin, "Altın Satıcı" gibi özel satıcı unvanlarını yönetir.
+ **ShoppingCarts** : Kullanıcıların alışveriş sepetlerini temsil eder.
+ **TaxDepartments** : Vergi departmanlarını temsil eder. 
+ **TicketsDetails** : Müşteri destek taleplerinin detaylarını içerir.
+ **Tickets** : Müşteri destek taleplerini temsil eder. 
+ **UserAddresses** : Kullanıcı adreslerini içerir. 
+ **User** : Kullanıcıları temsil eder. 
