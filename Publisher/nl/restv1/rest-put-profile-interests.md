# REST API: PUT profile interests

Waarschuwing: Je bekijkt nu het overzicht voor de oude versie van onze 
API. Wij raden aan om [versie 2](../restv2/rest-api.md) van de API te gebruiken.

Om de interesses van een profiel te overschrijven, kun je een HTTP PUT
request sturen naar de volgende URL:

`https://api.copernica.com/v1/profile/$id/interests?access_token=xxxx`

De code **$id** moet je vervangen door de numerieke identifier van het profiel 
waarvan je de interesses wilt veranderen. De nieuwe interesses van het profiel
kun je in de body van het bericht plaatsen.


## Body data

Je kunt op twee manieren body data aan dit request meesturen, en de wijze waarop
je dit doet is van invloed op de manier waarop de methode werkt.

Als je een array van interessenamen meestuurt, dan worden _alle_ interesses
van het profiel overschreven. Alle huidige interesses worden uitgeschakeld,
en alleen de interesses die in het array zijn opgenomen worden geactiveerd.

Je kunt ook een object sturen als body data. De keys van het object zijn dan
de interessenamen, en de velden boolean waardes om te bepalen of de interesse
aan of uit wordt geschakeld. Eventuele interesses die je _niet_ in het object
opneemt, worden automatisch uitgeschakeld.


## Voorbeeld

Het volgende PHP script demonstreert hoe je de API methode kunt aanroepen.
In de API call worden de interesses van een profiel met ID 4567 aangepast.
Voor profiel 1234 worden de interesses "tennis" en "hockey" geactiveerd, en
alle andere interesses (zelfs de interesses die niet expliciet zijn vermeld) 
uitgeschakeld (tweede methode). Daarna wordt voor profiel 1235 de interesse 'football' geactiveerd en alle andere interesses uitgeschakeld (eerste methode).

```php
    // vereiste scripts
    require_once('copernica_rest_api.php');
    
    // verander dit naar je access token
    $api = new CopernicaRestApi("your-access-token");

    // data voor de methode
    $data = array(
        'football'  =>  0,
        'tennis'    =>  1,
        'hockey'    =>  1
    );
    
    // voer het verzoek uit
    $api->put("profile/1234/interests", $parameters, $data);

    // data voor het tweede verzoek
    $data = array('football');
    
    // voer het verzoek uit
    $api->put("profile/1235/interests", $parameters, $data);
```

Dit voorbeeld vereist de [REST API class](rest-php).

    
## Meer informatie

* [Overzicht van alle API calls](rest-api)
* [Interesses toevoegen aan een profiel](rest-post-profile-interests)
* [Opvragen van profieldata](rest-get-profile)
* [Alle profiel bijwerken](rest-put-profile)
* [Profiel verwijderen](rest-delete-profile)
