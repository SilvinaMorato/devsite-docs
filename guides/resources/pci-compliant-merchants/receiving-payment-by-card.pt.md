# Receba pagamentos sendo PCI Compliant

O Mercado Pago permite aos vendedores que cumprem com a regulamentação PCI que tokenizem cartões por backend.

> WARNING
>
> Pré-requisitos
>
> * Implementar o [processamento de pagamentos por API](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/pt/guides/online-payments/checkout-api/receiving-payment-by-card).
> * Possuir o documento AOC (Declaração de Compliance) assinado por um consultor QSA.

É necessário criar um `card_token`, que é a representação segura do cartão:

[[[
```php
<?php  
    require ('mercadopago.php');

    $mp = new MP('ACCESS_TOKEN');

    $card_token_data = array(
        "card_number" => "450995xxxxxx3704",
        "security_code" => "123",
        "expiration_month" => 6,
        "expiration_year" => 2018,
        "cardholder" => array(
            "name" => "APRO",
            "identification" => array(
                "number" => "12345678",
                "type" => "DNI"
            )
        )
    );

    $card_token = $mp->post("/v1/card_tokens", $card_token_data);
  ?>
```
```java
import com.mercadopago.MP;
import org.codehaus.jettison.json.JSONObject;

MP mp = new MP ("ACCESS_TOKEN");

JSONObject payment = mp.post("/v1/card_tokens", "{"+
    "'card_number': '450995xxxxxx3704',"+
    "'security_code': '123',"+
    "'expiration_month': 6,"+
    "'expiration_year': 2018,"+
    "'cardholder': {"+
        "'name': 'APRO',"+
        "'identification': {"+
            "'number': '12345678',"+
            "'type': 'DNI',"+
        "}"+
    "}"+
"}");
```
```csharp
using mercadopago;
using System;
using System.Collections;

MP mp = new MP("ACCESS_TOKEN");

Hashtable card_token = mp.post("/v1/card_tokens", "{"+
            "'card_number': '450995xxxxxx3704',"+
            "'security_code': '123',"+
            "'expiration_month': 6,"+
            "'expiration_year': 2018,"+
            "'cardholder': {"+
                "'name': 'APRO',"+
                "'identification': {"+
                    "'number': '12345678',"+
                    "'type': 'DNI'"+
                "}"+
            "}"+
        "}");
```
```javascript
var MP = require ("mercadopago");
var mp = new MP ("ACCESS_TOKEN");

var doCardToken = mp.post ("/v1/card_tokens",
    "card_number": "450995xxxxxx3704",
    "security_code": "123",
    "expiration_month": 6,
    "expiration_year": 2018,
    "cardholder": {
        "name": "APRO",
        "identification": {
            "number": "12345678",
            "type": "DNI"
        }
    });

doCardToken.then (
    function (payment) {
        console.log (payment);
    },
    function (error){
        console.log (error);
    });
```
```ruby
require 'mercadopago.rb'
$mp = MercadoPago.new('ACCESS_TOKEN')

cardTokenData = Hash[
    "card_number" => "450995xxxxxx3704",
    "security_code" => "123",
    "expiration_month" => 6,
    "expiration_year" => 2018,
    "cardholder" => Hash[
        "name" => "APRO",
        "identification" => Hash[
            "number" => "12345678",
            "type" => "DNI"
        ]
    ]

card_token = $mp.post("/v1/card_tokens", cardTokenData);

puts card_token
```
```python
import mercadopago
mp = mercadopago.MP("ACCESS_TOKEN")

card_token = mp.post("/v1/card_tokens", {
    "card_number": "450995xxxxxx3704",
    "security_code": "123",
    "expiration_month": 6,
    "expiration_year": 2018,
    "cardholder": {
        "name": "APRO",
        "identification": {
            "number": "12345678",
            "type": "DNI"
        }
    }
});

print(json.dumps(card_token, indent=4))
```
]]]

**Resposta**

```json
{
    "id": "ff8080814cbd77a8014cc",
    "public_key": null,
    "card_id": null,
    "luhn_validation": true,
    "status": "active",
    "date_used": null,
    "card_number_length": 16,
    "date_created": "2015-04-16T13:06:25.525-04:00",
    "first_six_digits": "450995",
    "last_four_digits": "3704",
    "security_code_length": 3,
    "expiration_month": 6,
    "expiration_year": 2018,
    "date_last_updated": "2015-04-16T13:06:25.525-04:00",
    "date_due": "2015-04-24T13:06:25.531-04:00",
    "live_mode": false,
    "cardholder": {
        "identification": {
            "number": "12345678",
            "type": "type"
        },
        "name": "name"
    }
}
```

Após obter o card_token, você pode [criar o pagamento](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/pt/guides/online-payments/checkout-api/receiving-payment-by-card).

## Obtenha aprovação mais rápida enviando o device fingerprint

O Mercado Pago possui suas próprias ferramentas de prevenção de fraudes. Sempre que possível, recomendamos que envie informações sobre o comportamento do cliente para detectar movimentos incomuns e evitar transações fraudulentas. Não se preocupe, cuidamos dos dados de seus clientes e não os compartilhamos com ninguém.

### Implementação de dispositivo na web

Para implementar a geração do dispositivo em seu site, adicione o seguinte código em seu plataforma de pagos:

```html
<script src="https://www.mercadopago.com/v2/security.js" view="checkout"></script>
```

É importante que você envie o `device_id` gerado por esse código ao seu servidor e que, ao criar o pagamento, adicione o seguinte header à request:

```http
X-meli-session-id: device_id
```
**Você pode obter o `device_id` de duas formas:**

Uma variável global de javascript é criada automaticamente com o nome `MP_DEVICE_SESSION_ID`, cujo o valor é o `device_id`. Se você preferir atribuí-lo a outra variável, indique o nome adicionando o atributo `output`.

```html
<script src="https://www.mercadopago.com/v2/security.js" view="checkout" output="deviceId"></script>
````

Você também pode adicionar uma tag HTML no seu site com o identificador `id="deviceId"`, e o código atribuirá automaticamente o valor `device_id`.

```html
<input type="hidden" id="deviceId">
```


### Implementação do device em aplicações móveis nativas

Se você possui uma aplicação nativa, pode capturar a informação do dispositivo com nosso SDK e enviar no momento de criar o token.

#### 1. Adicione a dependência

[[[

```ios
===
Adicionar o seguinte código no arquivo **Podfile**.
===
use_frameworks!
pod ‘MercadoPagoDevicesSDK’
```
```android
===
Adicionar o seguinte código no arquivo **build.gradle**.
===
dependencies {
   implementation 'com.mercadolibre.android.device:sdk:1.0.0'
}
```

]]]

#### 2. Inicialize o módulo

[[[

```swift
===
Recomendamos realizar a inicialização no envento didFinishLaunchingWithOptions do AppDelegate.
===
import MercadoPagoDevicesSDK
...
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        ...        
        MercadoPagoDevicesSDK.shared.execute()
        ...
}
```
```objective-c
===
Recomendamos realizar a inicialização no envento didFinishLaunchingWithOptions do AppDelegate.
===
@import ‘MercadoPagoDevicesSDK’;
...
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    ...
    [[MercadoPagoDevicesSDK shared] execute];
    ...
}
```
```java
===
Recomendamos realizar a inicialização na classe MainApplication.
===
import com.mercadolibre.android.devices.sdk.DeviceSDK;


DeviceSDK.getInstance().execute(this);
```

]]]

#### 3. Capture a informação

Execute alguma das funções abaixo para obter a informação no formato que precisar.

[[[

```swift
MercadoPagoDevicesSDK.shared.getInfo() // Devolve um objeto Device que é Codificável
MercadoPagoDevicesSDK.shared.getInfoAsJson() // Devolve um objeto em JSON
MercadoPagoDevicesSDK.shared.getInfoAsJsonString() // Devolve o JSON em formato de String
MercadoPagoDevicesSDK.shared.getInfoAsDictionary() // Devolve um objeto Dictionary<String,Any>
```
```objective-c
[[[MercadoPagoDevicesSDK] shared] getInfoAsJson] // Devolve um objeto em JSON
[[[MercadoPagoDevicesSDK] shared] getInfoAsJsonString] // Devolve o JSON em formato de String
[[[MercadoPagoDevicesSDK] shared] getInfoAsDictionary] // Deolve um objeto Dictionary<String,Any>
```
```java
Device device = DeviceSDK.getInstance().getInfo() // Devolve um objeto Device, que é serializável
Map deviceMap = DeviceSDK.getInstance().getInfoAsMap()  // Devolve um Map<String, Object>
String jsonString = DeviceSDK.getInstance().getInfoAsJsonString() // Devolve uma String no formato JSON
```

]]]

#### 4. Envie a informação

Por último, envie a informação obtida no campo `device` ao criar o `card_token`.

```
{
	...,
	 "device":{
	  "fingerprint":{
	     "os":"iOS",
	     "system_version":"8.3",
	     "ram":18446744071562067968,
	     "disk_space":498876809216,
	     "model":"MacBookPro9,2",
	     "free_disk_space":328918237184,
	     "vendor_ids":[
	        {
	           "name":"vendor_id",
	           "value":"C2508642-79CF-44E4-A205-284A4F4DE04C"
	        },
	        {
	           "name":"uuid",
	           "value":"AB28738B-8DC2-4EC2-B514-3ACF330482B6"
	        }
	     ],
	     "vendor_specific_attributes":{
	        "feature_flash":false,
	        "can_make_phone_calls":false,
	        "can_send_sms":false,
	        "video_camera_available":true,
	        "cpu_count":4,
	        "simulator":true,
	        "device_languaje":"en",
	        "device_idiom":"Phone",
	        "platform":"x86_64",
	        "device_name":"iPhone Simulator",
	        "device_family":4,
	        "retina_display_capable":true,
	        "feature_camera":false,
	        "device_model":"iPhone Simulator",
	        "feature_front_camera":false
	     },
	     "resolution":"375x667"
	  }
}
```
