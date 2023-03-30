# Especificaciones del API

A continuación se detallan los distintos mensajes que tiene el API StockistPhoenix. Consta de los siguientes mensajes: 

* PhoenixHotelConfigurationRequest/ PhoenixHotelConfigurationResponse<br/>
Mensaje dedicado a recuperar las habitaciones y tarifas de un hotel del cliente. 

* PhoenixBroadcastRateRequest / PhoenixBroadcastRateResponse<br/>
Mensaje dedicado a la publicación de precio e inventario 

* PhoenixBookingNotificationRequest/ PhoenixBookingNotificationResponse<br/>
Mensaje dedicado a la recuperación de reservas. Aqui el cliente envía la Request y Hotetec realizará la Response. 

Es importante destacar que en cualquiera de las respuestas de estos mensajes podría indicarse que se ha producido un error al tratar la request. Los errores siempre se informarán siempre siguiendo el elemento Error (4.4.8 Error). En el anexo final podrá observar algunos ejemplos. 

