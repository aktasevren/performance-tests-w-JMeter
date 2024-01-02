


### JMeter ile Performans Test Örnekleri

Bu projede ExpressJS ile yapmış olduğum basit bir API'yi ücretsiz uygulama sunucularına yükleyerek serverları karşılaştıracağım.

Yapmış olduğum API şu an https://render.com/ üzerine deploy edildi. Render üstünde API belli bir süre kullanılmadığında pasif'e alındığını fark ettim. Daha sonra kullanmak istediğimde bir requestin gelme süresi 1-2 dakikayı bulabiliyordu. Karşılaştırma sonucunda uygulamamı ücretsiz sunuculardan en iyi olanına taşıyacağım.


API basit bir şekilde verilen IMDB ID parametresine sahip filmin sahneleri nerede çekildiyse lokasyonlarını cevap olarak dönüyor.


Örnek request ve response ;


*Request* : https://imdb-server-ljf3.onrender.com/imdbid/tt0111161

*Response* : ["Mansfield Reformatory - 100 Reformatory Road, Mansfield, Ohio, USA","Butler, Ohio, USA","Sandy Point, St. Croix, U.S. Virgin Islands","Malabar Farm State Park - 4050 Bromfield Road, Lucas, Ohio, USA","127A Smithfield Road, Frederiksted, Virgin Islands","Wyandot County Courthouse, Upper Sandusky, Ohio, USA","Ashland, Ohio, USA","193 North Main Street, Mansfield, Ohio, USA","Snyder Road and Hagerman Road, Bellville, Ohio, USA","Mansfield, Ohio, USA","Upper Sandusky, Ohio, USA","Rod Bay, St Croix, USVI","301 E 5th Street, Mansfield, Ohio, USA","Yuma, Arizona, USA","Bellville, Ohio, USA","Sandusky, Ohio, USA","Ohio, USA","Mansfield, Shelby, Ohio, USA","Arizona, USA","USA"]

Karşılaştırmaları yaparken aynı thread sayılarını kullanarak Load, Stress, Spike testleri yapacağım.

#### Karşılaştırma yapacağım uygulama sunucuları
- Render
- Vercel
- AWS