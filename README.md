GameManager: Oyunun genel kontrolünü sağlayan sınıftır. Oyun durumu, seviyeler, yiyecek miktarı gibi işlevleri yönetir.

Bağımlılıklar:
BoardManager: Oyunun haritasını ve hücrelerini yönetir.
PlayerController: Oyuncunun hareketlerini ve etkileşimlerini kontrol eder.
TurnManager: Oyunun turlarını ve sırasını kontrol eder.
UIDocument: UI elemanlarıyla etkileşimi sağlar (örneğin, enerji göstergesi).
FoodObject, WallObject, Enemy, StaticEnemy, ExitCellObject: Haritada yer alan nesneleri yönetir.
------------------------------------------------------------------

BoardManager: Oyun alanını ve hücreleri yönetir. Hücrelerin dünyadaki konumları, içerikleri gibi işlemleri gerçekleştirir.

Kompozisyon (♦️):
CellData: Hücre bilgilerini tutar (örneğin, içerdiği nesne).
Grid: Hücrelerin dünyadaki yerlerini ve yapılarını belirler.

Bağımlılıklar:
FoodObject, WallObject, Enemy, StaticEnemy, ExitCellObject: Haritadaki nesneleri oluşturur ve bu nesnelerin işlevlerini yönetir.
İlişki: Tile: Hücreler farklı türde döşemeler içerir.
------------------------------------------------------------------

PlayerController
Açıklama: Oyuncunun hareketlerini ve durumunu kontrol eder. Hücreler arasında hareket eder, etkileşimlere girer ve oyunun ilerleyişini etkiler.

Bağımlılıklar:
BoardManager: Oyuncunun hareket edeceği hücreleri ve harita durumunu günceller.
GameManager: Oyuncunun enerjisini ve oyun durumunu kontrol eder.
------------------------------------------------------------------

TurnManager
Açıklama: Oyundaki sıraları ve turları yönetir. Her turda oyunun nasıl ilerleyeceği belirlenir.

Bağımlılıklar:
GameManager: Her turda GameManager'a bilgi gönderir ve oyunun genel durumunu günceller.
------------------------------------------------------------------

CellObject (Soyut Temel Sınıf)
Açıklama: Harita üzerindeki her nesne (örneğin, yiyecek, engel, düşman) bu sınıftan türetilir. Nesnelerin ortak özelliklerini ve işlevlerini tanımlar.

Kalıtım (▲):
Enemy, StaticEnemy, WallObject, FoodObject, ExitCellObject gibi nesneler CellObject sınıfından türetilir.
------------------------------------------------------------------

Enemy (CellObject'tan Türetilir)
Açıklama: Oyuncuya zarar verebilecek düşmanları temsil eder.

Kalıtım (▲):
StaticEnemy: Sabit duran bir düşman türüdür

Bağımlılıklar:
GameManager: Düşman etkileşimleri ve saldırılar hakkında bilgi verir.
------------------------------------------------------------------

WallObject (CellObject'tan Türetilir)
Açıklama: Oyuncunun geçemeyeceği engelleri temsil eder. Sağlık puanı vardır ve oyuncu etkileşimde bulunarak yok edebilir.

Kompozisyon (♦️):
Tile: Engelin görselliğini ve türünü belirler.

Bağımlılıklar:
GameManager: Oyuncu ile engel etkileşimde bulunulduğunda GameManager'a bilgi verir.
------------------------------------------------------------------

FoodObject (CellObject'tan Türetilir)
Açıklama: Oyuncuya enerji (yiyecek) veren nesneleri temsil eder.

Bağımlılıklar:
GameManager: Oyuncuya enerji ekler ve oyuncu yediğinde silinir.
------------------------------------------------------------------

ExitCellObject (CellObject'tan Türetilir)
Açıklama: Oyuncunun seviyeyi tamamlayıp yeni seviyeye geçmesini sağlayan nesneleri temsil eder.

Bağımlılıklar:
GameManager: Yeni seviyeye geçişi sağlar.
