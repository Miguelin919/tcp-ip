---
layout: default
title: TCP - Control de Flujo
nav_order: 35
permalink: /control-de-flujo
---
##### **Autores:**
Miguel Lemus


##### **Fecha de creación:** 
{: .no_toc }

##### **Revisiones:** 
{: .no_toc }

##### **Fecha de revisión:** 
{: .no_toc }

# TÍTULO
Control de Flujo en TCP

#### Contenido:
  * Introducción
  * Control de flujo
  * Formato del segmento TCP

## Resumen
Con el protocolo TCP, en la capa de transporte, sus objetivos es transferir paquetes con un cierto orden utilizando el control de flujo con un mecanismo de confirmaciones, se numeran los byte para confirmar con los SYNs establecen los números de secuencia iniciales 


## TÍTULO
Control de Flujo en TCP

## SUBTÍTULO
Introducción
Transferencia fiable de datos: importante en nivel de aplicación, tansporte, enlace.
           | Aplicación |                     | Aplicación |
----------------------------------------------------------------------------------------
Transporte        |   --->  | Canal fiable | --->   |
----------------------------------------------------------------------------------------
El control de flujo utiliza el mecanismo de confirmaciones
    1 | -----> | 
      | Datos  | 1
    2 | <----- |
      |   ACK  | 2
    3 | -----> |
      | Datos  | 3
    4 | <----- |
      |   ACK  | 4
      
Control de flujo 
Receptor lee más despacio que lo que recibe (. . .)

Segmento TCP
  __________________________________________
  |<--------------32 bits----------------->|
  |   Puerto origen  | Puerto destino      |
  |         Número de secuencia            |  <-- Cuenta en bytes de datos (no en segmentos)
  |        Número de confirmación          |  <-- Cuenta en bytes de datos (no en segmentos)  
  |Long Cab.|No usado|U|A|P|R|S|F|Ventana  |
  | Checksum         | Puntero a urgentes  |
  |     Opciones (longitud variable)       |
  | Datos de aplicación (Longitud variable)|
  
Long Cab: Tamaño cabecera (palabras de 32bits)
U: Datos urgentes (casi no se usa), URG.
A: El No. ACK es valido
P: Pysh Entregar datos a App (PSH)
R: RST S: SYN F:FIN Establecimiento y fin de la conexión
Ventana: Tamaño de la ventana que se anuncia al emisor
Checksum
