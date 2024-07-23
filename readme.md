


JMeter ile Performans Testi Örnekleri

Bu projede, ExpressJS ile geliştirdiğim basit bir API'yi çeşitli ücretsiz uygulama sunucularına yükleyerek performanslarını karşılaştırmayı amaçlıyorum.

API şu anda Render platformunda dağıtılmış durumda. Render üzerinde, API'nin belirli bir süre kullanılmadığında pasif hale geçtiğini gözlemledim. Bu durum, API'yi tekrar kullanmak istediğimde ilk isteğin gelme süresinin 1-2 dakikayı bulmasına neden oluyordu. Yapacağım karşılaştırma sonucunda, uygulamamı performans açısından en iyi ücretsiz sunucuya taşımayı planlıyorum.

Geliştirdiğim API, verilen IMDB ID parametresine sahip filmin çekim lokasyonlarını yanıt olarak döner. Örnek bir istek ve yanıt aşağıda verilmiştir:

    İstek: https://imdb-server-ljf3.onrender.com/imdbid/tt0111161
    Yanıt:

json

[
    "Mansfield Reformatory - 100 Reformatory Road, Mansfield, Ohio, USA",
    "Butler, Ohio, USA",
    "Sandy Point, St. Croix, U.S. Virgin Islands",
    "Malabar Farm State Park - 4050 Bromfield Road, Lucas, Ohio, USA",
    "127A Smithfield Road, Frederiksted, Virgin Islands",
    "Wyandot County Courthouse, Upper Sandusky, Ohio, USA",
    "Ashland, Ohio, USA",
    "193 North Main Street, Mansfield, Ohio, USA",
    "Snyder Road and Hagerman Road, Bellville, Ohio, USA",
    "Mansfield, Ohio, USA",
    "Upper Sandusky, Ohio, USA",
    "Rod Bay, St Croix, USVI",
    "301 E 5th Street, Mansfield, Ohio, USA",
    "Yuma, Arizona, USA",
    "Bellville, Ohio, USA",
    "Sandusky, Ohio, USA",
    "Ohio, USA",
    "Mansfield, Shelby, Ohio, USA",
    "Arizona, USA",
    "USA"
]

Karşılaştırmaları yaparken aynı sayıda thread kullanarak Load, Stress ve Spike testleri gerçekleştireceğim. Performans testlerini gerçekleştireceğim uygulama sunucuları şunlardır:

    Render
    Vercel
    Railway
    AWS
    
### Number of Threads / Ramp Up / Loop 
###  500 / 5 / 5
| Platform|Samples|Average|Min|Max|Std|Error|Throughput|Total Sec |
|---|---|---|---|---|---|---|---|---|
| Vercel  |   5000   | 385  |  0 | 3311  | 472.21  |  0 | 521.5  | 9|
| AWS     |  5000    | 1200 | 0  | 2176  |  435.21 |  0 | 303.3  | 16|
| Railway |   5000   |1585|0|5709|974.31|0|228.1| 21|
| Render  |  5000    |14658|0|62880|14778.35|0|33.1|150|

### 1000 / 10 / 2
| Platform|Samples|Average|Min|Max|Std|Error|Throughput|Total Sec |
|---|---|---|---|---|---|---|---|---|
| Vercel  |   4000   | 220  |  0 | 1344  | 101.85  |  0 | 370| 11|
| AWS     |  4000    | 1257 | 0  | 2596  |  562.22 |  0 | 277.7  | 14|
| Railway |   4000   |1755|0|3418|639.5|0|227.8| 17|
| Render  |  4000    |17652|0|25622|4764.96|0|49.6|81|

### 750 / 10 / 20
| Platform|Samples|Average|Min|Max|Std|Error|Throughput|Total Sec |
|---|---|---|---|---|---|---|---|---|
| Vercel  |   30000   | 329  |  0 | 8527  | 319.35  |  0 | 992.6| 30|
| AWS     |  30000    | 2169 | 0  | 3009  |  452.88 |  0 | 311.4  | 96|
| Railway |   30000   |5823|0|10916|2686.66|0.02|116.4| 258|
| Render  |  30000    |12351|0|30471|1322.05|0.02|59.6|503|









Notes:


you can run them from your terminal with the following command: jmeter -n -t /location of script/NameOfYourScript.jmx 

 -   (-n): tells JMeter to run in Non-GUI mode
 -   (-t): name of .JMX with test plan
 -   (-l): name of JTL file for results
 -   (-j): Jmeter run log file
