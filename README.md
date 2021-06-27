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
