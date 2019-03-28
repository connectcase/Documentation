# REST API: GET destination deliveries (Marketing Suite)

Er worden statistieken bijgehouden over elke mailing die verstuurd wordt met 
Copernica om je meer inzicht te geven in de prestatie hiervan. Deliveries zijn 
een van de statistieken die worden bijgehouden. 
Je kan de deliveries voor een specifieke destination opvragen met een HTTP GET call naar de volgende URL:

`https://api.copernica.com/v2/ms/destination/{$destinationID}/deliveries?access_token=xxxx`

Deze methode ondersteunt ook het gebruik van de [fields parameter](./rest-fields-parameter) 
voor het **timestamp** veld.

## Teruggegeven velden

Deze methode geeft een JSON object terug met deliveries. Voor elke delivery 
is de volgende informatie beschikbaar:

* **ID**: De ID van de delivery.         
* **mailing**: De ID van de mailing.
* **timestamp**: Tijdstempel van de delivery.
* **attempts**: Aantal pogingen voor de delivery.
* **destination**: De ID van de destination voor de delivery.
* **profile**: De ID van het profiel voor de delivery.
* **subprofile**: De ID van het subprofiel voor de delivery.

## PHP voorbeeld

Dit script demonstreert hoe je de API methode kunt gebruiken:

```php
// vereiste scripts
require_once('copernica_rest_api.php');

// verander dit naar je access token 
$api = new CopernicaRestAPI("your-access-token", 2);

// voer het verzoek uit
print_r($api->get("ms/destination/{$destinationID}/deliveries"));
```

Dit voorbeeld vereist de [REST API klasse](./rest-php).

## Meer informatie

* [Overzicht van alle REST API calls](./rest-api)
* [Opvragen van alle deliveries](./rest-get-ms-deliveries)
* [Opvragen van destination abuses voor MS](./rest-get-ms-destination-abuses)
* [Opvragen van destination clicks voor MS](./rest-get-ms-destination-clicks)
* [Opvragen van destination errors voor MS](./rest-get-ms-destination-errors)
* [Opvragen van destination impressions voor MS](./rest-get-ms-destination-impressions)
* [Opvragen van destination unsubscribes voor MS](./rest-get-ms-destination-unsubscribes)