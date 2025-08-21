# Ashtech-store
my api key: lygosapp-32fb14b1-6d3e-463b-a39f-98496e646c26
information sur l'api

Présentation globale

Lygos est une solution de paiement pour entrepreneurs et entreprises en Afrique francophone. Elle permet d’intégrer facilement des fonctionnalités de paiement dans vos applications et sites web. Nous simplifions les paiements afin de vous permettre de vous concentrer sur votre coeur de métier. Lygos automatise pour vous la gestion des paiements et les suivi de vos transactions à travers une seule interface de manière sécurisée.
​
Lygos Pay

Aujourd’hui c’est plus de 8,000 entreprises et entrepreneurs qui nous font confiance pour vendre localement et à l’international.
Pour commencer à utiliser l’API vous devez obligatoirement créer un compte sur Lygos Pay. Vous devez aussi fournir vos informations personelles (CNI ou permis) et des informations concernant votre business.
​
Endpoints API

Voici les differentes catégories d’API mises à disposition pour nos utilisateurs et partenaires.
Nos API

Nos API reposent sur les principes REST, une architecture qui garantit des services fiables, flexibles et faciles à intégrer. Elles utilisent les méthodes HTTP classiques comme GET, POST, PUT et DELETE pour interagir avec les ressources. Les réponses sont toujours au format JSON, ce qui les rend simples à comprendre et à utiliser avec les outils de développement modernes. Que vous construisiez une application, connectiez des systèmes ou enrichissiez votre plateforme, nos API sont là pour vous offrir une expérience fluide et agréable.
En apprendre davantage sur REST
View the OpenAPI specification file
​
Réponses et erreurs

Voici la liste des erreurs et des réponses associées que vous pourrez rencontrer durant la mise en place des API dans votre application. Lygos maintient un formattage clair et comprehensible pour vous faciliter l’intégration.
Code Statut	Catégorie	Description	Exemple
200	Succès	La requête a réussi, et le serveur a renvoyé les données attendues.	GET /users renvoie une liste d’utilisateurs.
201	Créé	La ressource a été créée avec succès.	POST /users renvoie les détails du nouvel utilisateur.
204	Aucun Contenu	La requête a réussi, mais aucune donnée n’est retournée.	DELETE /users/{id} après suppression réussie d’un utilisateur.
400	Requête Incorrecte	Le serveur n’a pas compris la requête en raison d’une syntaxe invalide.	Champs obligatoires manquants dans une requête POST.
401	Non Autorisé	Une authentification est requise ou a échoué.	Jeton API manquant ou invalide.
403	Interdit	Le client n’a pas les permissions nécessaires pour accéder à la ressource.	Tentative d’accès à des données restreintes.
404	Non Trouvé	La ressource demandée est introuvable.	GET /users/{id} pour un utilisateur inexistant.
409	Conflit	La requête entre en conflit avec l’état actuel du serveur.	Tentative de création d’une ressource en double.
422	Entité Non Traitée	La requête est bien formée mais contient des données invalides.	Données invalides pour la création d’une ressource.
500	Erreur Serveur Interne	Le serveur a rencontré une condition inattendue.	Erreurs générales ou exceptions inattendues du serveur.
502	Mauvaise Passerelle	Le serveur a reçu une réponse invalide d’un serveur en amont.	Problème temporaire avec les services en amont.
503	Service Indisponible	Le serveur est temporairement incapable de traiter la requête (surcharge ou maintenance).	Panne planifiée ou surcharge du serveur.
504	Délai d’Attente	Le serveur n’a pas reçu de réponse à temps d’un serveur en amont.	Requêtes longues causant des délais d’attente.
​
Authentification

Pour comprendre comment gérer l’authentification, vous pouvez vous réferrer à la section Authentification du guide.
Environnements et URLs
Informations concernant nos URLs et environnements.
​
Environnements disponibles

Actuellement, nous disposons uniquement d’un environnement de production. D’autres environnements (staging, développement) pourront être ajoutés ultérieurement en fonction des besoins.
​
Production

API Backend : https://api.lygosapp.com/v1/
​
Accès et Sécurité

L’accès à l’API nécessite une authentification via clé API ou OAuth selon les endpoints.
Toutes les communications passent par HTTPS pour garantir la sécurité des échanges.
Pour accéder aux endpoints de l’environnement ci-dessus, utilisez la base d’URL suivante :
https://api.lygosapp.com/v1/

List Payment Gateways
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.lygosapp.com/v1/gateway",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => [
    "api-key: <api-key>"
  ],
]);

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}



200->
[
  {
    "id": "3c90c3cc-0d44-4b50-8888-8dd25736052a",
    "amount": 123,
    "currency": "<string>",
    "shop_name": "<string>",
    "message": "<string>",
    "user_id": "3c90c3cc-0d44-4b50-8888-8dd25736052a",
    "creation_date": "2023-11-07T05:31:56Z",
    "link": "<string>",
    "order_id": "<string>",
    "success_url": "<string>",
    "failure_url": "<string>"
  }
]

401->
{
  "detail": {
    "message": "No API Key.",
    "type": "NO_API_KEY_PROVIDED"
  }
}


404->

{
  "detail": {
    "message": "API Key not found",
    "type": "API_KEY_NOT_FOUND"
  }
}

402->
{
  "detail": [
    {
      "loc": [
        "<string>"
      ],
      "msg": "<string>",
      "type": "<string>"
    }
  ]
}


Headers
​
api-key
string | nullrequired
Response
200

application/json
Successful Response
​
id
string<uuid>required
​
amount
integerrequired
​
currency
stringrequired
​
shop_name
stringrequired
​
user_id
string<uuid>required
​
creation_date
string<date-time>required
​
link
stringrequired
​
message
string | nulldefault:""
​
order_id
string | nulldefault:""
​
success_url
string | nulldefault:""
​
failure_url
string | nulldefault:""

<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.lygosapp.com/v1/gateway",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => json_encode([
    'amount' => 123,
    'shop_name' => '<string>',
    'message' => '<string>',
    'success_url' => '<string>',
    'failure_url' => '<string>',
    'order_id' => '<string>'
  ]),
  CURLOPT_HTTPHEADER => [
    "Content-Type: application/json",
    "api-key: <api-key>"
  ],
]);

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}

200->

{
  "id": "3c90c3cc-0d44-4b50-8888-8dd25736052a",
  "amount": 123,
  "currency": "<string>",
  "shop_name": "<string>",
  "message": "<string>",
  "user_id": "3c90c3cc-0d44-4b50-8888-8dd25736052a",
  "creation_date": "2023-11-07T05:31:56Z",
  "link": "<string>",
  "order_id": "<string>",
  "success_url": "<string>",
  "failure_url": "<string>"
}
401->
{
  "detail": {
    "message": "No API Key.",
    "type": "NO_API_KEY_PROVIDED"
  }
}

404->
{
  "detail": {
    "message": "API Key not found",
    "type": "API_KEY_NOT_FOUND"
  }
}

422->

{
  "detail": [
    {
      "loc": [
        "<string>"
      ],
      "msg": "<string>",
      "type": "<string>"
    }
  ]
}

Headers
​
api-key
string | nullrequired
Body
application/json
​
amount
integerrequired
​
shop_name
stringrequired
​
order_id
stringrequired
​
message
string | nulldefault:""
​
success_url
string | nulldefault:""
​
failure_url
string | nulldefault:""
Response
200

application/json
Successful Response
​
id
string<uuid>required
​
amount
integerrequired
​
currency
stringrequired
​
shop_name
stringrequired
​
user_id
string<uuid>required
​
creation_date
string<date-time>required
​
link
stringrequired
​
message
string | nulldefault:""
​
order_id
string | nulldefault:""
​
success_url
string | nulldefault:""
​
failure_url
string | nulldefault:""

<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.lygosapp.com/v1/gateway/{gateway_id}",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
]);

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}

200-> 
{
  "id": "3c90c3cc-0d44-4b50-8888-8dd25736052a",
  "amount": 123,
  "currency": "<string>",
  "shop_name": "<string>",
  "message": "<string>",
  "user_country": {
    "name": "Cameroon",
    "iso_code": "CMR"
  },
  "creation_date": "2023-11-07T05:31:56Z",
  "link": "<string>",
  "order_id": "<string>",
  "success_url": "<string>",
  "failure_url": "<string>"
}


400->
{
  "detail": {
    "message": "User not found or inactive",
    "type": "GATEWAY_USER_NOT_FOUND"
  }
}

401->
{
  "detail": {
    "message": "No API Key.",
    "type": "NO_API_KEY_PROVIDED"
  }
}

404-> 

  {
  "detail": {
    "message": "Payment Gateway Not found",
    "type": "GATEWAY_NOT_FOUND"
  }
}

422->
{
  "detail": [
    {
      "loc": [
        "<string>"
      ],
      "msg": "<string>",
      "type": "<string>"
    }
  ]
}

Path Parameters
​
gateway_id
string<uuid>required
Response
200

application/json
Successful Response
​
id
string<uuid>required
​
amount
integerrequired
​
currency
stringrequired
​
shop_name
stringrequired
​
message
stringrequired
​
user_country
objectrequired
Show child attributes
​
creation_date
string<date-time>required
​
link
stringrequired
​
success_url
stringrequired
​
failure_url
stringrequired
​
order_id
string | nulldefault:""


<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.lygosapp.com/v1/gateway/{gateway_id}",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "PUT",
  CURLOPT_POSTFIELDS => json_encode([
    'amount' => 123,
    'shop_name' => '<string>',
    'message' => '<string>',
    'success_url' => '<string>',
    'failure_url' => '<string>'
  ]),
  CURLOPT_HTTPHEADER => [
    "Content-Type: application/json",
    "api-key: <api-key>"
  ],
]);

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}

200->
"<any>"

401->
{
  "detail": {
    "message": "No API Key.",
    "type": "NO_API_KEY_PROVIDED"
  }
}

404->
{
  "detail": {
    "message": "Payment Gateway Not found",
    "type": "GATEWAY_NOT_FOUND"
  }
}
422->
{
  "detail": [
    {
      "loc": [
        "<string>"
      ],
      "msg": "<string>",
      "type": "<string>"
    }
  ]
}


Headers
​
api-key
string | nullrequired
Path Parameters
​
gateway_id
string<uuid>required
Body
application/json
​
amount
integer
​
shop_name
string
​
message
string
​
success_url
string
​
failure_url
string
Response
422

application/json
Validation Error
​
detail
ValidationError · object[]

<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.lygosapp.com/v1/gateway/{gateway_id}",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "DELETE",
  CURLOPT_HTTPHEADER => [
    "api-key: <api-key>"
  ],
]);

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
200->
"<any>"
401->
{
  "detail": {
    "message": "No API Key.",
    "type": "NO_API_KEY_PROVIDED"
  }
}
404->

{
  "detail": {
    "message": "Payment Gateway Not found",
    "type": "GATEWAY_NOT_FOUND"
  }
}
422->
{
  "detail": [
    {
      "loc": [
        "<string>"
      ],
      "msg": "<string>",
      "type": "<string>"
    }
  ]
}
Headers
​
api-key
string | nullrequired
Path Parameters
​
gateway_id
string<uuid>required
Response
200

application/json
Successful Response
The response is of type any.

<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.lygosapp.com/v1/gateway/payin/{order_id}",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => [
    "api-key: <api-key>"
  ],
]);

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
200->
{
  "order_id": "<string>",
  "status": "<string>"
}
404->
{
  "detail": {
    "message": "No API Key.",
    "type": "NO_API_KEY_PROVIDED"
  }
}
422->
{
  "detail": [
    {
      "loc": [
        "<string>"
      ],
      "msg": "<string>",
      "type": "<string>"
    }
  ]
}

Headers
​
api-key
string | nullrequired
Path Parameters
​
order_id
stringrequired
Response
200

application/json
Successful Response
​
status
stringrequired
​
order_id
string | nulldefault:""

les pays et les operateurs sue lygos prend en charge
benin mtn et moov
cameroun Mtn
Burkina moov
congo MTN
RDC orange money, vodacom, airtel
cote d'hivoir mtn, orange money, wave
gabon airtel
kenya Mpesa
Rwanda MTN, airtel
senegal free, orange money, wave
Tanzani airtel, tigo, halotel
zambi aitel, mtn
