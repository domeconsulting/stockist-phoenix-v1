# Ejemplos

````xml
<PhoenixHotelConfigurationResponse>
	<hotelConfig code="555" name="Playa del Mar">
		<roomConfig code="INV" name="Individual">
			<occupationConfig adults="1" children="0" babies="0"/>
			<rateConfig code="STD" name="Tarifa Estandard">
				<mealPlanConfig code="RO" name="Solo Alojamiento"/>
				<mealPlanConfig code="BB" name="Bed and breakfast"/>
				<mealPlanConfig code="AI" name="Todo Incluido"/>
			</rateConfig>
		</roomConfig>
		<roomConfig code="DBL" name="Doble">
			<occupationConfig adults=" 1" children="1" babies="0"/>
			<occupationConfig adults="2" children="0" babies="0"/>
			<occupationConfig adults="2" children="1" babies="0"/>
			<rateConfig code="STD" name="Tarifa Estandard">
				<mealPlanConfig code="RO" name="Solo Alojamiento"/>
				<mealPlanConfig code="BB" name="Bed and breakfast"/>
				<mealPlanConfig code="AI" name="Todo Incluido"/>
			</rateConfig>
			<rateConfig code="OFE" name="Tarifa Oferta">
				<mealPlanConfig code="AI" name="Todo Incluido"/>
				<property code="NRE"/>
			</rateConfig>
		</roomConfig>
		<roomConfig code="TPL" name="Triple">
			<occupationConfig adults="1" children="0" babies="0"/>
			<occupationConfig adults="1" children="1" babies="0"/>
			<occupationConfig adults="2" children="0" babies="0"/>
			<occupationConfig adults="2" children="2" babies="0"/>
			<occupationConfig adults="3" children="0" babies="0"/>
			<rateConfig code="STD" name="Tarifa Estandard">
				<mealPlanConfig code="RO" name="Solo Alojamiento"/>
				<mealPlanConfig code="BB" name="Bed and breakfast"/>
				<mealPlanConfig code="AI" name="Todo Incluido"/>
			</rateConfig>
		</roomConfig>
	</hotelConfig>
</PhoenixHotelConfigurationResponse>
````
## PhoenixHotelConfigurationResponse
Supongamos el hotel Playa del Mar con código 555. 
Este hotel tiene 3 habitaciones: Individual (código INV), Doble (código DBL) y Triple (código TPL).. La individual tiene solamente la ocupación para 1 Adulto. 
La Doble tiene las ocupaciones 1 Adulto + 1 Niño, 2 Adultos y 2 Adultos + 1 niño. Finalmente la Triple tiene las ocupaciones 1 Adulto, 1 Adulto + 1 niño, 2 Adultos, 2 Adultos + 1 niño, 2 Adultos + 2 niños y 3 Adultos. 
Las tarifas para este hotel son 2 la tarifa Estandard (código STD) y la tarifa Oferta (código OFE). La tarifa Estandard aplica a todas las habitaciones, mientras que la tarifa Premium solo aplica a la doble. La tarifa Estandard tiene disponibles los regímenes de Sólo Alojamiento (código RO), Bed and Breakfast (Código BB) y Todo incluido (Código AI). 
Mientras que la tarifa Oferta solamente está disponible con régimen Todo Incluido (AI). Esta tarifa es No reembolsable. 
El mensaje de petición de configuración del hotel quedaría de la siguiente manera: 

````xml
<PhoenixRoomRateUpdateRequest>
	<credentials>
		<system>PHX</system>
		<vendorCode>TESTDAVID</vendorCode>
		<user>YOUR_CHANNEL_USER</user>
		<password>YOUR_CHANNEL_PASSWORD</password>
	</credentials>
	<hotelCode>555</hotelCode>
	<rate code="STD">
		<room code="DBL">
			<applicableDates dateFrom="01/01/2020" dateTo="07/01/2020">
				<availableQuota>10</availableQuota>
				<release>2</release>
				<mealPlan code="RO">
					<occupation adults="1" children="0" babies="0" status="Open" amount="150.0"/>
					<occupation adults="2" children="0" babies="0" status="Open" amount="175.0"/>
					<occupation adults="2" children="1" babies="0" status="Open" amount="185.0"/>
				</mealPlan>
			</applicableDates>
		</room>
	</rate>
</PhoenixRoomRateUpdateRequest> 

````
## PhoenixRoomRateUpdateRequest 
Basándonos en la configuración anterior, supongamos que queremos actualizar la tarifa Estandard (código STD) para la habitación Doble (código DBL). 
La primera semana de Enero, tendrá 10 habitaciones libres, con un release de 2 días. Sin estancia mímina ni máxima, ni restricciones de entrada ni salida. 
Los precios para la ocupación de 1 Adulto es de 150€, para dos Adultos 175€ y dos adultos + 1 niño 185€ en pensión Solo Alojamiento (código RO) 
