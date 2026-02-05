# API Gateway
**Componente del Trabajo de Fin de Máster (TFM)** > *Máster en Ingeniería de Software y Sistemas Informáticos (MSSI)*

Este componente es un API Gateway basado en **Spring Cloud Gateway** que constituye el punto único de entrada al backend, abstrayendo la complejidad de la arquitectura de microservicios.

Funcionalidades principales:
* Desacopla la capa de presentación de la infraestructura interna.
* Traduce peticiones POST a parámetros GET mediante filtros personalizados.
* Resuelve nombres lógicos a través de Eureka para el enrutamiento dinámico.

Para más detalles sobre la gestión de rutas y filtros, consulta la [Documentación de Sping Cloud Gateway](https://docs.spring.io/spring-cloud-gateway/reference/index.html).
