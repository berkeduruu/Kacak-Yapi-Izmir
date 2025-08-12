# Kacak-Yapi-Izmir
A small project on detect new builded buildings by detect differences between two images at different years (dates) retvieved from overpass (openstreetmap) and QGIS


İlk adım: Overpass ile İzmir çapındaki ilçelerin 2022 ve 2025 temmuz ayındaki yapıları işaretleyen bir kod yardımıyla verileri çektim. Bunu selenium ile yaptım başka şekilde de muhtemelen indirebilirdim daha da rahat olurdu ama QGIS ten de aynı şekilde indirilebiliyor bir plugin yardımıyla lakin onda da geçmiş yıllarınkini bulamadığımdan bıraktım uğraşmayı garanti yolla devam ettim. Bazı ilçelerin geojson ı yok overpass te bazı ilçlerde memory konusunda hata çıkarıyordu açıkçası pek de uğraşmadım en kötü çözüm mahalle bazında toplayıp birleştirmek ama gerek duymadım.

İkinci adım: Bu geojson dosyalarını QGIS içinde açtım pyQGIS kullanrak ilçeleri 1:2000 ölçeğinde bölümlere ayırarak görselleirni çıkardım .pgw dosyalarıyla ileride tespit edilen binaların koordinatlarını almak için 1000x1000 çözünürlükte bu ayarları değiştirebilirsiniz ki zaten bir mantığa göre seçmedim.

<img width="738" height="412" alt="Picture" src="https://github.com/user-attachments/assets/705a912e-3343-4cea-a66f-5e8688c573b2" />
<img width="394" height="403" alt="Picture" src="https://github.com/user-attachments/assets/ab8d4c1d-ec9f-4fb9-8bcf-71d44439c0fe" />


Üçüncü adım: Bu görselleri tek tek 2022 ve 2025 yılındaki binaların görüntülerini kıyaslamak için görsellerdeki renkleri siyah veya beyaz olarak sınıflandırdım K-means kullandım kümelendirmek için aslında hiç de gerek yok da k-means e sadece yapmak için yaptım o kısmı. Bitişik binalarda bazı sıkıntılar oluyordu siyah beyaz mask ı çıkınca görselin aralarındaki siyah çizgi çok küçük kaldığından direkt çizgiyi göz ardı ediyordu ben de bundan geçiçi olarka kurtulmak için mask ta yer alan binaların rengini erezyona uğrattım 1 pixel ki işaretleme daha rahat yapılabilsin. Bu fark algılamayı açıkçası overpass da [diff: date1 , date2] dediğinizde size zaten veriyor aynı şekilde QGIS de size bunu rahatlıkla gösteriyor aslında ama koordinat kısmında nasıl binların koordinatını bulursunuz bilmem ki benim yaptığımdan daha kolay olacağı kesin.

<img width="1105" height="616" alt="image" src="https://github.com/user-attachments/assets/0332f692-96a7-43a0-abf8-db02a83e9a89" />

Dördüncü adım: TKGM - Parsel Sorgulama bulduğum bina imar izni gib bilgileri tutan en iyi site buna da selenium ile eriştim aslında ama kod bitmeden günlük sorgu sınırı olduğunu fark ettim o sebeple kod yarıda kalıyorburada ilerletmedim. Buradaki genel mantık işaretlenen binalardan gelecek koordinat bilgisiyle birlikte TKGM sitesi url sine koordinat yazdığınızda direkt sitede sorgu yapılan parsele ulaşıyorsunuz o sebeple eğer günlük sınır olmasaydı biraz daha kolaylaşıyordu kodun işi.


Burada görsel olarak küçük bir sunum yer alıyor sırasıyla yapılan işlemleri az da olsa anlatıyor.
[Yeni Microsoft PowerPoint Sunusu.pptx](https://github.com/user-attachments/files/21732395/Yeni.Microsoft.PowerPoint.Sunusu.pptx)

