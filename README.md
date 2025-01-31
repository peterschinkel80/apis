# Free (customer/contact/crm) verification api's
Free apis for phone, email, url, webrank (site popularity), iban, postalcode and vat verification/enrichment.
Forever free (no auth, https/cors enabled) api's to check and standardise your data.
More details on [free.bedrijfsdata.nl](https://free.bedrijfsdata.nl/)

<h3 id="phone">Phone api</h3>
Checks if a phone number could exist (global).<br>
<pre>
Example request:
https://free.bedrijfsdata.nl/v1.1/phone?country_code=nl&phone=0207895050
https://free.bedrijfsdata.nl/v1.1/phone?phone=%2B31207895050

Example response:
{
    "status": "ok",
    "phone": {
        "int": "31207895050",
        "valid": 1,
        "international": "+31 20 789 5050",
        "national": "020 789 5050",
        "country": "NL",
        "region": "Amsterdam",
        "carrier": "",
        "ismobile": 0,
        "success": 1,
        "wrong_phone": 0
    }
}
</pre>

<h3 id="email">Email api</h3>
Checks if an Email address is a correct format and has an active mailserver (global).<br> 
<pre>
Example request:
https://free.bedrijfsdata.nl/v1.1/email?email=piet@bedrijfsdata.nl

Example response:
{
    "status": "ok",
    "email": {
        "email": "piet@bedrijfsdata.nl",
        "user": "piet",
        "domain": "bedrijfsdata.nl",
        "mx_host": "ASPMX5.GOOGLEMAIL.COM",
        "mx_ip": "74.125.200.26",
        "wrong_email": 0,
        "wrong_format": 0,
        "free": 0,
        "disposable": 0,
        "success": 1
    }
}
</pre>

<h3 id="url">Url api</h3>
Checks if a Url exists/redirects and returns the new url, top level domain (for deduplication) and ip (global).<br> 
<pre>
https://free.bedrijfsdata.nl/v1.1/url?url=http://www.bedrijfsdata.nl

Example response:
{
    "status": "ok",
    "url": {
        "url": "https:\/\/www.bedrijfsdata.nl\/",
        "domain": "bedrijfsdata.nl",
        "http_code": 200,
        "redirect_count": 1,
        "content_type": "text\/html; charset=UTF-8",
        "content_length": 100213,
        "ip": "45.82.189.100",
        "success": 1
    }
}
</pre>

<h3 id="webrank">Webrank api</h3>
There are a lot of website popularity rankings, like <a href="https://developer.chrome.com/docs/crux" target="_blank" rel="noindex">Google Crux rank</a>, <a href="https://tranco-list.eu/methodology" target="_blank" rel="noindex">Tranco rank</a>, <a href="https://www.domcop.com/openpagerank/what-is-openpagerank" target="_blank" rel="noindex">Domcop (page)rank</a> and many more, this api combines them all (global).<br> 
<pre>
Example request:
https://free.bedrijfsdata.nl/v1.1/webrank?domain=google.com

Example response:
{
    "status": "ok",
    "webrank": {
        "domain": "google.com",
        "webrank": "1",
        "tranco": "1",
        "domcop": "3",
        "hostio": "1",
        "commoncrawl": "1",
        "majestic": "1",
        "crux": "500",
        "cloudflare": "100",
        "umbrella": "1",
        "builtwith": null,
        "pagerank": "10.00"
    }
}
</pre>

<h3 id="iban">IBAN api</h3>
Checks if an IBAN account number is correct (global).
<pre>
Example request:
https://free.bedrijfsdata.nl/v1.1/iban?iban=NL17ADYB2017400505

Example response:
{
    "status": "ok",
    "iban": {
        "iban": "NL17ADYB2017400505",
        "iban_human": "NL17 ADYB 2017 4005 05",
        "country_code": "NL",
        "country": "Netherlands",
        "verified": true,
        "verified_checksum": true,
        "swift": 1,
        "sepa": 1,
        "success": 1
    }
}
</pre>

<h3 id="postalcode">Postalcode api (Zip)</h3>
Checks if a postalcode is in the right format (global). For NL postcode/address details see also the bag/geocoding api.
<pre>
Example request:
https://free.bedrijfsdata.nl/v1.1/postalcode?country_code=NL&postalcode=1013PN

Example response:
{
    "status": "ok",
    "postalcode": {
        "country_code": "NL",
        "postalcode": "1013PN",
        "success": 1,
        "wrong_postalcode": 0,
        "message": "good postalcode"
    }
}
</pre>

<h3 id="vat">VAT api (BTW), EU</h3>
Checks if a EU VAT number exists.
<pre>
Example request:
https://free.bedrijfsdata.nl/v1.1/vat?vat=NL001672022B01

Example response:
{
    "status": "ok",
    "vat": {
        "vat": "NL001672022B01",
        "country": "NL",
        "name": "HEINEKEN HOLDING N.V.",
        "response_date": "2025-01-29 09:33:59",
        "address": "TWEEDE WETERINGPLANTSOEN 5",
        "postcode": "1017ZD",
        "city": "AMSTERDAM",
        "active": 1
    }
}
</pre>

<h3 id="currency">Currency api (BTW), EU</h3>
Show the latest currency conversion rates.
<pre>
Example request:
https://free.bedrijfsdata.nl/v1.1/currency?currency=eur

Example response (with 5 from 339 currencies for readability):
{
    "status": "ok",
    "from_currency": "eur",
    "date": "2025-01-31",
    "found": 339,
    "currency": {
        "...": "..."
        "chf": 0.94546647,
        "doge": 3.13593387,        
        "eur": 1,
        "gbp": 0.83640947,
        "usd": 1.03911461,
        "...": "..."
    }
}
</pre>

<p><i>The api's underneath are for the Netherlands only:</i></p>

<h3 id="kvk">Kvk api (chamber of commerce), NL</h3>
Checks if a chamber of commerce number exists in the Netherlands.
<pre>
Example request:
https://free.bedrijfsdata.nl/v1.1/kvk?kvk=89395808

Example response:
{
    "status": "ok",
    "found": 1,
    "kvk": [
        {
            "id": "893958080000",
            "coc": "89395808",
            "vestiging": "000055191886",
            "name": "Bedrijfsdata.nl B.V.",
            "city": "Amsterdam",
            "type": "Hoofdvestiging",
            "active": 1
        }
    ]
}
</pre>

<h3 id="bag">BAG api (Address), NL</h3>
Checks if an address exists in the Netherlands by postcode, number and optional a suffix (the letter or addition). See the postcalcode api for other countries. 
<pre>
Example request:
https://free.bedrijfsdata.nl/v1.1/bag?postcode=1011PN&number=3
https://free.bedrijfsdata.nl/v1.1/bag?postcode=1013BC&number=71&suffix=a

Example response:
{
    "status": "ok",
    "found": 1,
    "bag": [
        {
            "number": "3",
            "letter": "",
            "addition": "",
            "postcode": "1011PN",
            "street": "Amstel",
            "city": "Amsterdam",
            "municipality": "Amsterdam",
            "province_code": "NH",
            "province": "Noord-Holland",
            "lat": "52.367560",
            "lon": "4.900388",
            "purpose": "bijeenkomstfunctie",
            "construction_year": "1985",
            "floor_area": "8217"
        }
    ]
}
</pre>

<h3 id="geocoding">Geocoding api (standardised address), NL</h3>
Translates a raw address into standardised fields.
<pre>
Example request:
https://free.bedrijfsdata.nl/v1.1/geocoding?q=Kalverstraat%201
https://free.bedrijfsdata.nl/v1.1/geocoding?q=Amstel+3,+1011PN+Amsterdam

Example response:
{
    "status": "ok",
    "found": 1,
    "geocoding": [
        {
            "number": 1,
            "letter": "",
            "addition": "",
            "postcode": "1012NX",
            "street": "Kalverstraat",
            "city": "Amsterdam",
            "municipality": "Amsterdam",
            "province_code": "NH",
            "province": "Noord-Holland",
            "freeformaddress": "Kalverstraat 1, 1012NX Amsterdam",
            "type": "adres",
            "lat": "52.37250408",
            "lon": "4.89214036"
        }
    ]
}
</pre>
<br>
More details on [free.bedrijfsdata.nl](https://free.bedrijfsdata.nl/)
<br><br><br>
<a href="https://www.bedrijfsdata.nl/">&copy; Bedrijfsdata.nl</a> -
<a href="https://www.bedrijfsdata.nl/bedrijfsdata-api/">Dutch Company api</a> - 
<a href="https://docs.bedrijfsdata.nl/">More docs</a> - 
<a href="https://zoeken.bedrijfsdata.nl/" rel="nofollow">Search a Dutch company</a> - 
<a href="https://bedrijfsherkenning.nl/">B2B visitor identification in NL</a> - 
<a href="https://www.prospectpro.nl/">B2B prospecting NL</a> 

<br>
<br>

