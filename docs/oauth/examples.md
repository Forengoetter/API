Für diese Schnittstelle kann man keine _richtigen_ Beispiele zur verfügung stellen. Wir haben unter dem Punk **Erhalt der Nutzerdaten** Beispielantworten der API aufgezeigt, hier soll es darum gehen wir man die Verifikation des _tokens_ exemplarisch mit verschiedenen Sprachen löst.

### PHP
```
[author=Kuschel_Swein]
// the token provided by the user via GET
$token = $_GET['token'];

// your application id
$applicationID = 1;

// your secret key
$secretKey = "mysupersecretkey";

// your public key
$publicKey = "mypublickey";

// the wanted userdata, needed for the link
$scopes = ['username', 'email', 'avatar', 'minecraft_uuid', 'minecraft_uuid'];

// the redirect url, probably this script, must match the url that your provided in your application
$redirectURL = 'https://mydomain.com/index.php';

// create a stream, to add our headers
$opts = [
   "http" => [
      "method" => "GET",
      "header" => "Accept-language: en\r\n".
	  "X-Token: ".$token."\r\n".
	  "X-ApplicationId: ".$applicationID."\r\n".
	  "X-SecretKey: ".$secretKey."\r\n"
   ]
];

// create a stream context from our options
$context = stream_context_create($opts);

// make our request to the API
$data = file_get_contents('https://api.forengoetter.org/oauth', false, $context);

// decode the json data
$json = json_decode($data);

// check if the token is valid
if ($json->type == 'success') {
	// store the userdata we got from the api
  	$userData = $json->userData;
} else {
	// handle invalid token
   	echo 'got invalid api response: '.$json->message.' with code '.$json->code;
}

// this is optional, its just a link to the authentication for the user
echo '<a href="https://forengoetter.org/oauth/?applicationID='.$applicationID.'&client_id='.urlencode($publicKey).'&redirectURL='.urlencode($redirectURL).'&scope='.urlencode(implode(',', $scopes).'">Login mit Forengötter Account</a>';
```

### Node.js
```
[author=DerJP]
// We're using the `node-fetch` library to make HTTP requests in this example,
// but you're free to use any library you like, of course.
const fetch = require('node-fetch');

// Static configuration variables
// Note: In a real application, most of these should be
// contained inside of environment variables.

// Your application id
const APPLICATION_ID = 1;

// Your public key
const PUBLIC_KEY = 'mypublickey';

// Your secret key
const SECRET_KEY = 'mysupersecretkey';

// User data you want to request from the FOG API
const SCOPES = [
	'username',
	'email',
	'avatar',
	'minecraft_uuid',
	'minecraft_uuid',
];

// The URL where the user should be sent back to upon completing authentication.
// The FOG API will redirect the user to this URL with a token.
const REDIRECT_URL = 'https://mydomain.com/auth/fog/callback';

// Redirect the user to the FOG OAuth portal
function initOAuth() {
	// Note: Redirection would normally take place in the front-end (e.g. through an anchor tag)
	// or using redirection methods provided by frameworks like Express or Koa.
	// We're using a dummy function for demonstration.
	redirectUser(`https://forengoetter.org/oauth/?applicationID=${APPLICATION_ID}&client_id=${PUBLIC_KEY}&redirectURL=${REDIRECT_URL}&scope=${SCOPES.join(',')}`);
}

// Function used to validate a token against the FOG API and get the user data
// This function should be used in the redirect route's handler after extracting the token.
async function validateToken(t) {
	// Populate a `Headers` object with the needed parameters
	const params = {
		'X-Token': t,
		'X-Application': APPLICATION_ID,
		'X-SecretKey': SECRET_KEY,
	};
	const headers = new fetch.Headers(params);

	// Perform the request
	const response = await fetch('https://api.forengoetter.org/oauth', {
		method: 'GET',
		headers: headers,
	});
  	const json = await response.json();

  	if (json.type === 'success') {
    	// Do something with the user data...
  	} else {
    	// Handle invalid token
  	}
}
```
