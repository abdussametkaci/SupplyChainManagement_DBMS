# SupplyChainManagement_DBMS
## Varlık Tablolarının Amaçları
1) Supliers: Tedarikçilerin kayıtlarının tutulduğu tablodur. Bu tabloda tüm tedarikçilere ait bilgilerin saklanması amacıyla oluşturulmuştur. (ad, soyad, email, vs.)
2) Products: Tüm ürünlerin saklandığı tablodur. Ürünlerin fiyatı ve onlara ait açıklamalar bulunmaktadır.
3) Supliers_Product: Hangi tedarikçinin hangi ürünlere sahip olduğunu ve bu ürünlerden kaç adet bulunduğunu tutan tablodur.
4) Product_Type: Ürünlerin türlerini tutan tablodur. Örneğin: meyve, sebze, süt ürünü.
5) Addresses: Tedarikçilerin bulundukları adresi tutmaktadır.
6) Locations: Bir adresten yapılan tedariğin hangi bölgeye ulaştırıldığını tutmak amacıyla oluşturulmuştur.
7) Customers: Bir tedarikçiden ürün siparişi veren müşterilerin bilgilerini tutmaktadır.
8) Customer_Shipments: Müşterilerin sipariş verdikleri tedarikleri içeren tablodur. Bu tabloda hangi tedarikçiden hangi üründen kaç adet sipariş verildiği, ayrıca siparişin hangi yöntem ile getirilmesi istendiği ve siparişin durumları gibi bilgileri de içermektedir.  
9) Shipment_Type: Sipariş verilen tedariğin hangi yöntem ile taşınacağını içeren tablodur. Burada çeşitli taşıma yöntemlerini içermektedir. Örneğin havadan, karadan, denizden.
10) Shipment_State: Sipariş verilen tedariğin durumunu tutmaktadır. Örneğin bir tedarik hala tedarikçide mi yoksa yolda mı, gümrükte mi veya müşteriye vardı mı gibi bilgileri içermektedir.
11) Shipement_Item: Bir müşerinin hangi tedarikçiden hangi ürünün alındığı ve bu üründen kaç adet söylendiği bilgisini içermektedir.
12) Shipment_Locations: Sipariş verilen tedariklerin hangi bölgelere sipariş verildiği bilgisini tutmaktadır.
13) Payments: Müşterilerin verdikleri sipariş için ne kadarlık ödeme yaptıklarının bilgisini tutan tablodur. Hangi tarihte ödeme yapıldığı ve ödemenin hangi yöntem ile gerçekleştirildiği bilgisi tutulmaktadır.
14) Payment_Type: Müşterilerin yapmış olduğu ödemelerin türlerini içeren tablodur. Örneğin peşin ödme, taksitli ödeme, kredi ile ödeme vs.
15) Bills: Tedarikçilerin siparişi verilen ürünlerinin faturalarının tutulduğu tablodur. Bu fatura hangi tedarikçiye ait olduğu, hangi ürün için faturalandırıldığı ve bu fatura müşterinin hangi ödemesi için kesildiği bilgileri tutulmaktadır.

## İlişkisel Veri Modeli Kuralları
1)	Bir müşteri tek seferde (yani aynı tarihte) bir tedarikçinin bir ürününden 1.000’den fazla ürün siparişi veremez.
2)	Bir müşterinin süt ürünlerini sadece kara yolu ile sipariş vermesine izin verilebilir. Diğer tüm yöntenlere izin verilmez.
3)	Bir tedarikçinin bir adresinde 100’den fazla lokasyona tedarik sağlamasına izin verilemez.
4)	Bir tedarikçinin bir üründen 10.000’den fazla bulundurması yasaktır.
5)	Bir müşteri taksitli ödeme yapabilmesi için 20.000 ₺ üzerinde sipariş vermesi gerekmektedir.
6)	Bir müşterinin sipariş verdiği ürün yolda veya tedarikçisinde ise aynı tedarikçiden aynı üründen sipariş veremez.

## Model
![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/model.png)

## SQL Sorguları
1)	ISTANBUL adresindeki tedarikçilerin hava yoluyla taşıdıkları ürünlerin adedini bulunuz

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/sorgu1.PNG)

2)	Tedarikçisinden mal isteyip malları hala tedarikçisinde olan müşterilerin ürünlerini ve fiyatlarını bulunuz

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/sorgu2.PNG)

3)	Peşin ödeme ile 10.000 TL üzerinde faturaya sahip tedarikçileri bulunuz

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/sorgu3.PNG)

## PL SQL Fonksiyonu
Müşterinin belli bir siparişinde toplam tutarı döndüren fonksiyonu yazınız

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/sorgu4.PNG)

## PL SQL Tablo Trigger
Bir müşteri bir tedarikçiden belli sayıda mal sipariş verdiğinde otomatik olarak tedarikçinin mal sayısı sipariş edilen kadar düşürelecektir. Eğer elinde bulunan maldan fazla sipariş verilirse hata dönderilecektir

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/sorgu5.PNG)

# Normalizasyon
![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/tablo1.PNG)

## Fonksiyonel Bağımlılıklar
suplier_id -> name, surname, email

product_id -> p_name,description, cost, product_type_id, type

product_type_id -> type

suplier_id, product_id -> name, surname, email, p_name,description, cost, product_type_id, type, quantity

## Birinci Normal Form (1NF)
Bir tablonun 1. Normal Formda olması için bir kayıttaki tüm alanlar bir anlama sahip veri içermelidir. Yukarıdaki tabloda product_id, p_name, ve cost sütunlarında birden fazla veri tutulduğundan dolayı bu 1. Normal forma aykırıdır. Bunu 1. Normal forma uygun hale getirmek için de satır sayısı artırılmalıdır ve bu sayede her bir sütunda sadece 1 adet veri saklanması sağlanır. Bunu gerçekleştirerek tablonun yeni hali aşağıdaki gibi görünmektedir.

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/tablo2.PNG)

## İkinci Normal Form (2NF)
Bir tablonun 2NF’da olması için, 1NF şartlarına ek olarak aday anahtar harici tüm alanlar tüm aday anahtarla tam fonksiyonel bağımlı olmalıdır. Verilen fonksiyonel bağımlılıklara göre tablonun şu anki hali 2. Normal forma aykırıdır. Çünkü suplier_id ve product_id gibi anahtarlarım {suplier_id, product_id} aday anahtarımdaki alt kümelere erişebilmektedir. 

suplier_id -> name, surname, email

product_id -> p_name,description, cost, product_type_id, type

product_type_id -> type

suplier_id, product_id -> quantity

Yeni ilişkiler bu şekilde olmaktadır ve tablolarımı da aşağıdaki gibi bölmekteyim.

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/tablo3.PNG)

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/tablo4.PNG)

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/tablo5.PNG)

## Üçüncü Normal Form (3NF)
Bir tablonun 3NF’da olması için, 2NF şartlarına ek olarak ilişkisel tabloda tüm alanlar birincil anahtara doğrudan fonksiyonel bağımlı olmalıdır. Birincil anahtar haricindeki alanlar arasında hiç bir fonksiyonel bağımlılık olmamalıdır. Benim belirttiğim ilişkilerde 3. Normal forma ayrıkırı bir durum içermektedir. Çünkü product_type_id doğrudan type sütununa erişebilmektedir. Bu durumda yine tabloları bölmek gerekmektedir.

suplier_id -> name, surname, email

product_id -> p_name,description, cost, product_type_id

product_type_id -> type

suplier_id, product_id -> quantity

Yeni ilişkier yukarıda verildiği gibi olmalıdır ve yeni tablolar aşağıdaki gibidir.

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/tablo6.PNG)

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/tablo7.PNG)

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/tablo8.PNG)

![](https://abdussametkaci.github.io/SupplyChainManagement_DBMS/img/tablo9.PNG)
