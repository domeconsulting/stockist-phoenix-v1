# PhoenixRoomRateUpdate
> Ejemplo PhoenixRoomRateUpdateRequest

````xml
<?xml version="1.0" encoding="UTF-8"?>
<PhoenixRoomRateUpdateRequest>
	<credentials>
		<system>PHX</system>
		<vendorCode>TESTDAVID</vendorCode>
		<user>YOUR_CHANNEL_USER</user>
		<password>YOUR_CHANNEL_PASSWORD</password>
	</credentials>
	<hotelCode>TEST</hotelCode>
	<rate code="AAA">
		<room code="1234">
			<applicableDates dateFrom="01/03/2020" dateTo="08/03/2020">
				<availableQuota>150</availableQuota>
				<release>10</release>
				<minimumStay>3</minimumStay>
				<maximumStay>20</maximumStay>
				<checkinRestriction>Open</checkinRestriction>
				<checkoutRestriction>Open</checkoutRestriction>
				<mealPlan code="RO">
					<occupation adults="1" children="0" babies="0" status="Open" amount="512.0"/>
				</mealPlan>
			</applicableDates>
		</room>
	</rate>
</PhoenixRoomRateUpdateRequest>
````

> Ejemplo PhoenixRoomRateUpdateResponse

````xml
<?xml version="1.0" encoding="utf-8"?>
<PhoenixRoomRateUpdateResponse> 
   <status>OK</status> 
</PhoenixRoomRateUpdateResponse> 

````


La actualización de precios e inventario se realizará mediante el mensaje <b>PhoenixRoomRateUpdateRequest</b> que enviará Hotetec al cliente y el cliente deberá responder con un mensaje <b>PhoenixRoomRateUpdateResponse</b>. 

## PhoenixRoomRateUpdateRequest

Mensaje de petición de actualización de precios e inventario 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
credentials | [**Credentials**](##Credentials) | Sí |Credenciales de autenticación del usuario. Las debe proporcionar el cliente a Hotetec 
hotelCode | *String* | Sí | Código de hotel
rate | [**Rate**] [ 1 .. N ](##Rate) | Sí | Información de tarifas


## PhoenixRoomRateUpdateResponse

Mensaje de respuesta de actualización de precios e inventario

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
status | *String* | Sí |Indica si se ha procesado correctamente la petición o no.<br/>Valores OK / KO. 
error | [**Error**](##Error) | No | Indica si ha habido algún error.