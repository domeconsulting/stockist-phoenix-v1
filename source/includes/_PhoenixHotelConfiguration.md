# PhoenixHotelConfiguration
> Ejemplo PhoenixHotelConfigurationRequest

````xml
<?xml version="1.0" encoding="UTF-8"?>
<PhoenixHotelConfigurationRequest>
    <credentials>
        <system>TEST</system>
        <vendorCode>VENDORTEST</vendorCode>
        <user>TESTUSER</user>
        <password>TESTPASSWORD</password>
    </credentials>
    <hotelCode>1234</hotelCode>
</PhoenixHotelConfigurationRequest>
````

> Ejemplo PhoenixHotelConfigurationResponse

````xml
<?xml version="1.0" encoding="utf-8"?>
<PhoenixHotelConfigurationResponse>
    <hotelConfig code="1234" name="Hotel Test">
        <roomConfig code="DBLSTD" name="Doble Estándar">
            <occupationConfig adults="1" children="0" babies="0"/>
            <occupationConfig adults="2" children="0" babies="0"/>
            <rateConfig code="NRF" name="Tarifa Non Refundable">                
                <mealPlanConfig code="HB" name="Half Board"/>
                <mealPlanConfig code="RO" name="Room Only"/>
                <property code="NRE"/>
            </rateConfig>
            <rateConfig code="ONLINE" name="Tarifa Online">
                <mealPlanConfig code="HB" name="Half Board"/>
                <mealPlanConfig code="RO" name="Room Only"/>
                <property code="ON"/>
            </rateConfig>
        </roomConfig>
        <roomConfig code="SGLSTD" name="Individual Estándar">
            <occupationConfig adults="1" children="0" babies="0"/>
            <rateConfig code="NRF" name="Tarifa Non Refundable">
                <mealPlanConfig code="HB" name="Half Board"/>
                <mealPlanConfig code="RO" name="Room Only"/>
                <property code="NRE"/>
            </rateConfig>
            <rateConfig code="ONLINE" name="Tarifa Online">
                <mealPlanConfig code="HB" name="Half Board"/>
                <mealPlanConfig code="RO" name="Room Only"/>
                <property code="ON"/>
            </rateConfig>
        </roomConfig>
    </hotelConfig>
</PhoenixHotelConfigurationResponse>
````

La recuperación de habitaciones y tarifas se realizará mediante el mensaje <b>PhoenixRoomRatesRetrievalRequest</b> que enviará Hotetec al cliente y el cliente deberá responder con un mensaje <b>PhoenixRoomRatesRetrievalResponse</b>. 


Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
credentials | [**Credentials**](##Credentials) | Sí |Credenciales de autenticación del usuario. Las debe proporcionar el cliente a Hotetec 
hotelCode | *String* | Sí | Código de hotel


## PhoenixHotelConfigurationRequest
Mensaje de respuesta de recuperación de habitaciones y tarifas 

Elemento | Tipo | Obl? |  Descripción
--------- | ----------- | ----------- | -----------
hotelConfig | [**HotelConfig**](##HotelConfig) | Sí |Definición de la configuracion del hotel
error | [**Error**](##Error) | Sí | Código de hotel

