# PhoenixBookingNotification
````xml
<PhoenixBookingNotificationRequest>
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
</PhoenixBookingNotificationRequest>
````

Cuando se realice una reserva en el cliente, éste deberá mandar una notificación con la reserva a la plataforma de Hotetec mediante el mensaje <b>PhoenixBookingNotificationRequest</b>. Hotetec responderá esta notificación mediante la respuesta <b>PhoenixBookingNotificationResponse</b>. 

<aside class="warning">
<b>NOTA IMPORTANTE:</b>: Cuando se notifique una reserva a Hotetec, la reserva <b>SIEMPRE DEBERÁ CONTENER TODAS LAS HABITACIONES</b>, tanto las que se hayan cancelado, como las que se hayan modificado o creado nuevas.
</aside>

Como indica el recuadro superior si por ejemplo se notifica una reserva de dos habitaciones y posteriormente se cancela una habitación, deberán indicarse las DOS habitaciones, una con el estado CONFIRMADO y la otra con el estado CANCELADO.

## PhoenixBookingNotificationRequest

Mensaje de notificación de reserva que debe enviar el cliente a Hotetec.

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
booking | [**Booking**](##Booking) | Sí | Notificación de reserva

````xml
<PhoenixBookingNotificationResponse> 
   <status>OK</status> 
</PhoenixBookingNotificationResponse> 
````

## PhoenixBookingNotificationResponse

Mensaje de respuesta de notificación de reserva. 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
status | *String* | Sí |Indica si se ha procesado correctamente la petición o no.<br/>Valores OK / KO. 
error | [**Error**](##Error) | No | Indica si ha habido algun error.

