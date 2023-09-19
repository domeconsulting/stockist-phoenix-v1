# Tipos Complejos
Aqui se describen algunos de los tipos complejos definidos en los mensajes de este documento

````xml
<credentials>
	<system>TEST</system>
	<vendorCode>VENDORTEST</vendorCode>
	<user>USERTEST</user>
	<password>SECRETPASSWORD</password>
</credentials> 
````

## Credentials
Indica las credenciales de acceso para la plataforma. 
 
Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
system | *String* | No | Sistema de acceso a la plataforma
vendorCode | *String* | No | Código de proveedor
user | *String* | Sí | Código de usuario
password | *String* | Sí | Password del usuario

````xml
<hotelConfig code="1234" name="Hotel Test">
	<roomConfig code="2542" name="Doble Vista Mar">
		<occupationConfig adults="2" children=" 0" babies="0"/>
		<occupationConfig adults="2" children="1" babies="0"/>
		<rateConfig code="1234" name="Hotel Test">
			<mealPlanConfig code="RO" name=" Solo Alojamiento"/>
			<mealPlanConfig code="AI" name=" Todo Incluido"/>
			<property code="NRE"/>
		</rateConfig>
	</roomConfig>
</hotelConfig>

````

## HotelConfig
Información de la configuración de un hotel 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@code | *String* | Sí | Código del hotel 
@name | *String* | Sí | Nombre del hotel
roomConfig | [**RoomConfig**](#RoomConfig) [ 1..N ] | Sí | Información de habitaciones

````xml
<roomConfig code="2542" name="Doble Vista Mar">
	<occupationConfig adults="2" children="0" babies="0"/>
	<occupationConfig adults="2" children="1" babies="0"/>
	<rateConfig code="1234" name="Hotel Test">
		<mealPlanConfig code="RO" name="Solo Alojamiento"/>
		<mealPlanConfig code="AI" name="Todo Incluido"/>
		<property code="NRE"/>
	</rateConfig>
</roomConfig> 

````
## RoomConfig
Información de la configuración de una habitación

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@code | *String* | Sí | Código de la habitación
@name | *String* | Sí | Nombre de la habitación
occupationConfig | [**OccupationConfig**](#OccupationConfig) [ 1..N ] | Sí | Información de las ocupaciones permitidas por la habitación
rateConfig | [**RateConfig**](#RateConfig) [ 1..N ] | Sí | Información de las tarifas de esta habitación

````xml
	<occupationConfig adults="2” children="0” babies="0”/>
````

## OccupationConfig

Información de la configuración de una ocupación para una habitación 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@adults | *Integer* | Sí | Número de adultos de la ocupación
@children | *Integer* | Sí | Número de niños de la ocupación
@babies | *Integer* | Sí | Número de bebés de la ocupación

````xml
<rateConfig code="1234" name="Hotel Test">
	<mealPlanConfig code="RO" name="Solo Alojamiento"/>
	<mealPlanConfig code="AI" name="Todo Incluido"/>
	<property code="NRE"/>		
</rateConfig>

````
## RateConfig

Información de la configuración de una tarifa 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@code | *String* | Sí | Código de la tarifa
@name | *String* | Sí | Nombre de la tarifa
mealPlanConfig | [**MealPlanConfig**](#MealPlanConfig) [ 1..N ] | Sí | Información de los regimenes alimenticios para la tarifa
property | [**Property**](#Property) [ 1..N ] | No | Información de las propiedades de las tarifas

````xml
	<mealPlanConfig code="RO” name="Solo Alojamiento”/> 
````

## MealPlanConfig

Información de la configuración de un régimen alimenticio 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@code | *String* | Sí | Código del régimen alimenticio
@name | *String* | Sí | Nombre del régimen alimenticio

````xml
	<property code="MED” value="55”/>
````

## Property

Información de una propiedad de tarifa 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@code | *String* | Sí | Código de la propiedad
@value | *String* | No | Valor de la propiedad

````xml
	<error code="PHX-3” message="Error al recuperar la tarifa”/>
````

## Error

Información de un error. 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@code | *String* | Sí | Código de error
@message | *String* | No | Mensaje de error

````xml
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
				<occupation adults="1" children="0" babies="0" status="Open" amount="512.0" `/>
			</mealPlan>
		</applicableDates>
	</room>
</rate>
````

## Rate

Información de actualización de precio e inventario de una tarifa 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@code | *String* | Sí | Código de tarifa
room | [**Room**](#Room) [ 1..N ] | Sí | Información de la habitación

````xml
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
````

## Room

Información de actualización de precio e inventario de una habitación 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@code | *String* | Sí | Código de la habitación
applicableDates | [**ApplicableDates**](#ApplicableDates) [ 1..N ] | Sí | Fechas de aplicación


````xml
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

````
## ApplicableDates

Información del rango de fechas de la actualización

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@dateFrom | *Date* | Sí | Fecha de inicio en formato dd/MM/yyyy
@dateTo | *Date* | Sí | Fecha de fin en formato dd/MM/yyyy
availableQuota | *Integer* | Sí | Habitaciones disponibles (cupo disponible)
release | *Integer* | No | Días de release
minimumStay | *Integer* | No | Días de estancia mínima
maximumStay | *Integer* | No | Días de estancia máxima
checkinRestriction | *String* | No | Indica si el dia de checkin tiene restringida la entrada<br/>Valores Open, Closed
checkoutRestriction | *String* | No | Indica si el dia de checkout tiene restringida la salida<br/>Valores Open, Closed
mealPlan | [**MealPlan**](#MealPlan) [ 1..N ] | Sí | Información de actualización de régimen.

````xml
<mealPlan code="RO">
	<occupation adults="1" children="0" babies="0" status="Open" amount="512.0"/>
</mealPlan>
````
## MealPlan

Información de actualización de un régimen alimenticio 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@code | *String* | Sí | Código de regimen alimenticio
occupation | [**Occupation**](#Occupation) [ 1..N ] | Sí | Información de actualización de ocupación

````xml
	<occupation adults="1" children="0" babies="0" statuss="0pen" amount="512.0" /> 
````
## Occupation

Información de actualización de una ocupación 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@adults | *Integer* | Sí | Número de adultos
@children | *Integer* | Sí | Número de niños
@babies | *Integer* | Sí | Número de bebes
@status | *String* | Sí | Indica el estado para la ocupación<br/>Valores Open, Closed
@amount | *Double* | Sí | Indica el importe diario para la ocupación

````xml
<booking>
	<reference>A00123</reference>
	<externReference>PMI01254</externReference>
	<createDateTime>01/06/2020 12:00:00</createDateTime>
	<checkinDate>01/08/2020</checkinDate>
	<checkoutDate>05/08/2020</checkoutDate>
	<agencyCode>TST</agencyCode>
	<externAgency>Extern Agency</externAgency>
	<vendorCode>ABC</vendorCode>
	<hotelCode>30625</hotelCode>
	<amount>1650.40</amount>
	<contactPerson name="TEST" surname="TEST" email="test@test.com" telephone="test@test.com"/>
	<bookingRoom id="1">
		<status>Confirmed</status>
		<checkinDate>01/08/2020</checkinDate>
		<checkoutDate>05/08/2020</checkoutDate>
		<roomCode>DBL</roomCode>
		<mealPlan>RO</mealPlan>
		<amount>1650.40</amount>
		<rateDay day="01/08/2020" rateCode="1234" amount="412.60"/>
		<rateDay day="02/08/2020" rateCode="1234" amount="412.60"/>
		<rateDay day="03/08/2020" rateCode="1234" amount="412.60"/>
		<rateDay day="04/08/2020" rateCode="1234" amount="412.60"/>
		<guest id="1" name="Guest name" amount="825.25" age="33" birthDate="01/04/1987"/>
		<guest id="2" name="Guest name 2" amount="825.25" age="35" birthDate="01/04/1985"/>
		<arrivalFlight dateTime="01/01/2021 00:00:00" flightNumber="abc1234"/>
		<departureFlight dateTime=" 06 01 2021 00:00:00" flightNumber="xyz9876"/>
		<remark text=" Non smoking room please"/>
	</bookingRoom>
	<remark text="Nice room please"/>
	<paymentCardDetail holder="Guest name" number="4111111111111111" expiryDate="01/04/2025" securityCode="123"/>
</booking>

````
## Booking
Información de una reserva. Se aceptan reservas sin valorar (sin nodo amount), pero aparecerán como amount 0. 
<b>NOTA !! Siempre deben indicarse TODOS los bookingRoom de una reserva </b>

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
reference | *String* | Sí | Localizador de la reserva
externReference | *String* | No | Localizador de la agencia / terceros
createDateTime | *Date* | Sí | dia y hora de la creacion de la reserva.<br/>Formato dd/MM/yyyy HH:mm:ss
checkinDate | *Date* | Sí | Dia de entrada (más reciente de las habitaciones).<br/>Formato dd/MM/yyyy
checkoutDate | *Date* | Sí | Dia de salida (más tarde de las habitaciones).<br/>Formato dd/MM/yyyy
agencyCode | *String* | Sí | Código de agencia (Proporcionado por Hotetec)
externAgency | *String* | No | Nombre de agencia final / terceros. Es la agencia final que realiza la reserva, si el cliente tiene agencias que se conecten a él.<br/>Hotetec <-> Cliente <-> Agencia final
vendorCode | *String* | No | Código de proveedor. Proveedor de Hotetec sobre el cual se realiza la reserva.(Proporcionado por hotetec)
hotelCode | *String* | Sí | Código de hotel

````xml
	<contactPerson name="TEST" surname="TEST" email="test@test.com" telephone="test@test.com"/> 
````
## ContactPerson
Información de la persona de contacto de la reserva. 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@name | *String* | Sí | Nombre de la persona de contacto
@surname | *String* | Sí | Apellidos de la persona de contacto
@email | *String* | No | Email de la persona de contacto
@telephone | *String* | No | Número de telefono

````xml
<bookingRoom id="1">
	<status>Confirmed</status>
	<checkinDate>01/08/2020</checkinDate>
	<checkoutDate>05/08/2020</checkoutDate>
	<roomCode>DBL</roomCode>
	<mealPlan>RO</mealPlan>
	<amount>1650.40</amount>
	<rateDay day="01/08/2020" rateCode="1234" amount="412.60"/>
	<rateDay day="02/08/2020" rateCode="1234" amount="412.60"/>
	<rateDay day="03/08/2020" rateCode="1234" amount="412.60"/>
	<rateDay day="04/08/2020" rateCode="1234" amount="412.60"/>
	<guest id="1" name="Guest name" amount="825.25" age="33" birthDate="01/04/1987"/>
	<guest id="2" name="Guest name 2" amount="825.25" age="35" birthDate="01/04/1985"/>
	<arrivalFlight dateTime="01/01/2021 00:00:00" flightNumber="abc1234"/>
	<departureFlight dateTime=" 06 01 2021 00:00:00" flightNumber="xyz9876"/>
	<remark text=" Non smoking room please"/>
</bookingRoom> 

````
## BookingRoom
Información de una habitación de la reserva. Se permiten habitaciones sin valorar (sin nodo amount) pero aparecerán con amount 0. El nodo rateDay también es opcional si son reservas sin valorar o no se dispone de la información de contrato. 
<b>NOTA !! Siempre deben indicarse TODOS los bookingRoom de una reserva</b>

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@id | *String* | Sí | Código identificativo de la habitación
status | *String* | Sí | Estado de la habitación reserva.<br/>Valores Confirmed / Cancelled
checkinDate | *Date* | Sí | Dia de entrada.<br/>Formato dd/MM/yyyy
checkoutDate | *Date* | Sí | Dia de salida.<br/>Formato dd/MM/yyyy
roomCode | *String* | Sí | Código de habitación
mealPlan | *String* | Sí | Código de régimen alimenticio
amount | *Double* | No | Importe de la habitación
rateDay | [**RateDay**](#RateDay) [ 0..N ] | No | Desglose por día de la tarifa
guest | [**Guest**](#Guest) [ 1..N ] | Sí | Pasajeros de la reserva
arrivalFlight | [**FlightInformation**](#FlightInformation) | No | Información del vuelo de llegada
departureFlight | [**FlightInformation**](#FlightInformation) | No | Información del vuelo de salida
remark | [**Remark**](#Remark) [ 0 .. N ]| No | Notas para la habitación

````xml
	<rateDay day="01/08/2020" rateCode="1234" amount="412.60" /> 
````
## RateDay

Desglose de tarifas por día 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@day | *Date* | Sí | Dia de aplicacion del elemento.<br/>Formato dd/MM/yyyy
@rateCode | *String* | Sí | Código de tarifa
@amount | *Double* | Sí | Importe del día

````xml
	<guest id="1" name="Guest name" amount="825.25" age="33" birthDate="01/04/1987"/>
````
## Guest

Información de un pasajero de la reserva 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@id | *String* | Sí | Identificador de pasajero
@name | *String* | Sí | Nombre de pasajero
@amount | *Double* | No | Importe del pasajero
@age | *String* | No | Edad del pasajero
@birthDate | *Date* | Si | Fecha de nacimiento del pasajero.<br/>Formato dd/MM/yyyy

`````xml
	<remark text="nice room please"/> 
````
## Remark

Información de las notas de una reserva 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@text | *String* | Sí | Texto del nota

````xml
<paymentCardDetail holder="Guest name" number="4111111111111111" expiryDate="01/04/2025" securityCode="123"/> 
````

## PaymentCardDetail

Información de pago por tarjeta de una reserva 


Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@holder | *String* | Sí | Nombre del titular de la tarjeta
@number | *String* | Sí | Número de la tarjeta
@expiryDate | *Date* | Sí | Fecha de caducidad de la tarjeta.<br/>Formato dd/MM/yyyy
@securityCode | *String* | Sí | CVC código de seguridad

````xml
	<arrivalFlight dateTime="01/01/2021 00:00:00" flightNumber="abc1234" />
````
## FlightInformation

Información de un vuelo de la reserva 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
@dateTime | *Date* | Sí | Información del día y hora del vuelo.<br/>Formato dd/MM/yyyy HH:mm:ss
@flightNumber | *String* | Sí | Número de vuelo
