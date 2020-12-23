# Requisitos previos para comenzar


## Glosario

Sabemos que algunos términos son nuevos. Antes de empezar, te los dejamos a mano.

Término | Descripción
------------ | -------------
_Preferencia (preference)_ | Es la **información del producto o servicio que se quiere ofrecer.** Entre los atributos más importantes de una preferencia se definen: la descripción, el monto y los items. Al generarla se obtiene la URL para iniciar el flujo de pago.
_Credenciales (credentials)_ | Tus credenciales son las **claves que te proporcionamos para que puedas configurar tus integraciones.**<br/><br/>**Public key**. Clave pública de la aplicación para conocer, por ejemplo, los medios de pago y cifrar datos de tarjeta. Debes usarla solo para tus integraciones.<br/>**Access token**. Clave privada de la aplicación para generar pagos. Debes usarla solo para tus integraciones.<br/><br/>Para poder encontrarlas, ve a tus <a href="[FAKER][CREDENTIALS][URL]" target="_blank"> credenciales </a> y selecciona las productivas.<br/><br/>
_Punto de inicio (init_point)_ | **Es la URL que se obtiene al momento de generar la preferencia** y que da inicio al flujo de pago del Checkout Pro.
_Ítem (ítem)_ | Hace referencia al producto o servicio que se quiere ofrecer. Puede ser uno o una lista.
_Aplicación (application)_ | Las aplicaciones sirven para procesar los pagos del vendedor. **Cada aplicación identifica a una integración en particular**, ya que cada una tiene sus <a href="[FAKER][CREDENTIALS][URL]" target="_blank"> credenciales </a>propias. Una cuenta de Mercado Pago puede tener múltiples aplicaciones.<br/><br/>Puedes encontrar la información de cada una en credenciales. Al ingresar, se creará una automáticamente o puedes <a href="https://applications.mercadopago.com/" target="_blank"> crear una aplicación</a> cada vez que lo necesites.

## Requisitos previos

Para continuar, verifica los requisitos previos necesarios:

### 1. Acceso a cuenta de Mercado Pago o Mercado Libre
Para poder comenzar la integración, es necesario **contar con una cuenta de Mercado Pago o Mercado Libre**.
----[mla]----
Si aún no tienes una, puedes <a href="https://www.mercadopago.com.ar/" target="_blank"> crear una cuenta de Mercado Pago</a> cuando quieras.
------------
----[mlm]----
Si aún no tienes una, puedes <a href="https://www.mercadopago.com.mx/" target="_blank"> crear una cuenta de Mercado Pago</a> cuando quieras.
------------
----[mlb]----
Si aún no tienes una, puedes <a href="https://www.mercadopago.com.br/" target="_blank"> crear una cuenta de Mercado Pago</a> cuando quieras.
------------
----[mlu]----
Si aún no tienes una, puedes <a href="https://www.mercadopago.com.uy/" target="_blank"> crear una cuenta de Mercado Pago</a> cuando quieras.
------------
----[mlc]----
Si aún no tienes una, puedes <a href="https://www.mercadopago.cl/" target="_blank"> crear una cuenta de Mercado Pago</a> cuando quieras.
------------
----[mco]----
Si aún no tienes una, puedes <a href="https://www.mercadopago.com.co/" target="_blank"> crear una cuenta de Mercado Pago</a> cuando quieras.
------------
----[mpe]----
Si aún no tienes una, puedes <a href="https://www.mercadopago.com.pe/" target="_blank"> crear una cuenta de Mercado Pago</a> cuando quieras.
------------

### 2. Instalación de SDK de Mercado Pago
**Instala el SDK oficial** para simplificar tu interacción con nuestras APIs.

[[[
```php
===
<a href="https://getcomposer.org/download" target="_blank"> Instala Composer</a> para usar el SDK.

Luego ejecuta el siguiente código en la línea de comandos:
===
php composer.phar require "mercadopago/dx-php"
```
```node
===
Para instalar el SDK debes ejecutar el siguiente código en la línea de comandos de tu terminal usando <a href="https://www.npmjs.com/get-npm" target="_blank">npm</a>:
===
npm install mercadopago
```
```java
===
Para instalar el SDK en tu proyecto <a href="http://maven.apache.org/install.html" target="_blank"> Maven </a> agrega la siguiente dependencia en tu archivo pom.xml y luego ejecuta 'maven install'.
===
<dependency>
            <groupId> com.mercadopago </groupId>
            <artifactId> dx-java </artifactId>
            <version> 1.0.33 </version>
</dependency>
```
```ruby
===
El SDK de Mercado Pago está disponible como <a href="https://rubygems.org/gems/mercadopago-sdk" target="_blank"> gema</a>, para instalarla debes ejecutar el siguiente código en la línea de comandos:
===
gem install mercadopago-sdk
```
```csharp
===
----[mlb]----
Usa <a href="https://docs.microsoft.com/pt-pt/nuget/install-nuget-client-tools" target="_blank"> NuGet</a> para instalar el SDK .NET de Mercado Pago.
------------
----[mla, mlm, mco, mlc, mlu, mpe]----
Usa <a href="https://docs.microsoft.com/es-es/nuget/install-nuget-client-tools" target="_blank"> NuGet</a> para instalar el SDK .NET de Mercado Pago.
------------
Para hacerlo ejecuta el siguiente comando en la consola del NuGet Package Manager:
===
PM> Install-Package mercadopago-sdk -Version 1.0.57
```
]]]

---

### Próximos pasos

> LEFT_BUTTON_REQUIRED_ES
>
> Integra Checkout Pro
>
> Sigue el paso a paso para comenzar a recibir pagos en tu sitio.
>
> [Integra](https://www.mercadopago.com.ar/developers/es/guides/online-payments/checkout-pro/integration)

> RIGHT_BUTTON_RECOMMENDED_ES
>
> Prueba tu integración
>
> Revisa que esté todo bien en tu integración con los usuarios de prueba.
>
> [Prueba](https://www.mercadopago.com.ar/developers/es/guides/online-payments/checkout-pro/test-integration)
