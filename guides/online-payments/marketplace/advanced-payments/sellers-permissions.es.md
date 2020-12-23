---
  indexable: false
---

# Obtención de permisos y datos de los Vendedores

El Marketplace que desee integrarse, debe solicitar permisos a sus Vendedores para poder operar y realizar pagos en su nombre. Para ello, debe seguir los pasos de [Mercado Pago Connect](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/es/guides/online-payments/marketplace/checkout-api/create-marketplace).

Al seguir estos pasos, el Marketplace podrá obtener el `user_id` que lo debe utilizar como `collector_id` en cada `disbursement` que desee crear en el Advanced Payment. Es importante guardar el `user_id` del Vendedor para poder identificar el propietario de la cuenta de Mercado Pago en caso que haga falta.
