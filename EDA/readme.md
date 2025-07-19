# Key takeaways

<u>**Dataset properties**</u>:

- [No missing values](#missing-values-blank-check).
- Some numeric variables are not actually continous: 
    - [`yearc`](#yearc): represents the year of construction and only takes discrete year values.
    - [`rooms`](#rooms): indicates the number of rooms, which are integers ranging from 1 to 6.

<u>**Findings**</u>:

- [Most apartments are equipped with basic facilities, whereas high-end or upscale features are relatively uncommon.](#Categorical-variables)


    |Variable|Description|Yes rate (%)|
    |--|--|--|
    |cheating|Central heating available? |91.48|
    |wwater| Hot water supply available?| 96.49|
    |bathtile|Bathroom tiled?|81.49|
    |**bathextra**|High quality equipment in the bathroom?|**9.3**|
    |**upkitchen**|Upscale equipment in kitchen?|**7.31**|
    
- Top 10 districts by number of apartments:

    |Neuh-Nymp|177|
    |--|--|
    |Lud-Isar|161|
    |Au-Haid|139|
    |SchwWest|137|
    |Maxvor|132|
    |Laim|117|
    |Ram-Per |115|
    |Th-Ob-Fo-Fu-So|106|
    |Bogenh |98|
    |Ugies-Har |82|

- [Houses equipped with amenities tend to have a higher average `rent`](#rent-by-amenities), which is a reasonable trend in reality.

- [`location` clearly affects `rent`](#rent-by-location-and-district). Apartments in `good` and `top` locations tend to have higher average rents than those in `normal` areas, which aligns with real-world trends. However, [most apartments fall into the `normal` and `good` categories:](#rent-by-location-and-district)

    |`location`|count|
    |--|--|
    |normal|    1205|
    |good|       803|
    |top|         45|  

    and many of them still have very high rents (sometimes matching or exceeding those in the `top` group), suggesting that `location` is not the only factor influencing `rent`.
    
- [Finally, `area` and number of rooms (`rooms`) have a positive linear correlation with `rent`, meaning that `rent` tends to increase as these two variables increase. Meanwhile, the correlation between year of construction (`yearc`) and `rent` is quite weak](#corelation).
