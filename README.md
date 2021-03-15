# Mobiiliohjelmointi lopputyö, "reseptinhaku" 

Ohjelma tehty React Nativella.

## Ohjelmalla voi

- Hakea reseptejä Recipepuppy palvelusta, ja avata alkuperäiset reseptit selaimeen
- Tallentaa omia reseptejä muistio-tyyppisesti
- Ottaa kuvat annoksista
- Voit listata lähimmät ravintolat, sekä avata ulkoisen karttaohjelman osoitteen löytämistä varten

## Toteutus

- Yhtenäinen käyttöliittymä käyttäen Stack Navigatoria ja yhteneväistä ikoni- ja värimaailmaa
- Kamera tehty käyttäen expo-camera:a, ja varsinaisen kuvan ottaminen captureScreen kirjastolla. Tämä sen takia että kuviin saadaan teeman mukaiset kehykset.
- Lähimmät ravintolat listataan käyttäen Googlen nearby-search komentoa, sijainti haetaan automaattisesti käytettävän laitteen gps:n avulla (expo-location)

## Rajapinnat, tekniikkaa ym

- Reseptihaussa recipepuppy API
- Ravintolahaussa Google maps nearbysearch API
- Kamera Expo-Camera, käyttäjälupa pyydetään kameralle sekä laitteen sisäisen muistin käytölle
- Karttahaussa Google Maps API sekä ravintolatiedot open-api.myhelsinki (https://hri.fi/data/dataset/myhelsinki-open-api-paikat-tapahtumat-ja-aktiviteetit). Käytetty eri API lähteitä, jolla saatu erilaisia hakuja tehtyä koodiin. Open-api antaa myös helposti käytettävää dataa karttapalvelua varten.
- Muistio käyttää SQLite open databasea
- Ohjelmassa käytetty erilaisia tapoja toteuttaa painikkeet ja muut käyttäjävalinnat, Button, TouchableOpacity, suoraan text-komponenttiin liitetty onPress

## Osiot

- Pohjalla on Stack Navigator - komponentti, sekä varsinainen käyttäjälle näkyvä valikko on luotu Bottom Tab Navigator - komponentilla
- Reseptihaku on toteutettu Recipepuppy palvelun kautta, jolla haetaan käyttäjälle reseptin nimi, kuva, peruslista aineista. Tämän lisäksi käyttäjälle annetaan mahdollisuus avata resepti kokonaisuudessaan selaimeen, kopioida nimi/osoite leikepöydälle sekä lähettää nimi/osoite sähköpostilla eteenpäin
- Kamera on toteutettu expo camera sekä react native view shot - palveluilla. Expo cameralla saadaan kuvattava kohde näkymään ruudulla, view shot palvelusta käytetään captureScreen - komponenttia, jolla ruudusta otetaan screenshot. Tämä kuva tallentuu ohjelman luomaan sisäiseen välimuistiin. Screenshot otetaan siksi, että kuvaan saadaan mukaan kehykset
- Ravintolalista käyttää laitteen paikannusominaisuutta, selvittää sen hetkisen sijainnin ja listaa Google Nearbysearch-palvelulla viiden kilometrin etäisyydellä olevat ravintolat, listaa ne nimellä ja osoitteella varustettuna. Sen jälkeen käyttäjä voi osoitetta napauttamalla avata karttaohjelman ko. osoitteeseen
- Omat reseptit käyttää SQLite tietokanta-ominaisuutta, tähän käyttäjä voi kirjata omat reseptinsä
- Kartta käyttää Google Maps - palvelua kartan luomiseen, ja Helsingin alueen ravintolat tarkempine tietoinen tarjoaa My Helsinki open-api. Tällä apilla saa käyttöön Helsingn alueelta monta eri palvelua, ja niiden tiedot. Palvelu on maksuton.
