# API Gateway
**Componente del Trabajo de Fin de Máster (TFM)** > *Máster en Ingeniería de Software y Sistemas Informáticos (MSSI)*

Este componente es un API Gateway basado en **Spring Cloud Gateway** que constituye el punto único de entrada al backend, abstrayendo la complejidad de la arquitectura de microservicios.

Funcionalidades principales:
* Desacopla la capa de presentación de la infraestructura interna.
* Traduce peticiones POST a parámetros GET mediante filtros personalizados.
* Resuelve nombres lógicos a través de Eureka para el enrutamiento dinámico.

Para más detalles sobre la gestión de rutas y filtros, consulta la [Documentación de Sping Cloud Gateway](https://docs.spring.io/spring-cloud-gateway/reference/index.html).

## 🛠️ Stack

El proyecto integrando las siguientes librerías:

* **Spring Boot**: Framework base para la creación de la aplicación.
* **Spring Cloud Gateway**: Motor reactivo principal para la gestión de rutas, predicados y filtros de red.
* **Spring Cloud Netflix Eureka Client**: Habilita la comunicación con el servidor de descubrimiento.
* **Spring Boot Actuator**: Monitorización del estado de salud del servicio.
* **Lombok**: Librería para la reducción de código repetitivo mediante anotaciones.

## 🌐 Endpoints

| Endpoint | Descripción | 
| :--- | :--- | 
| `GET /ms-finance/finance/{ticker}` | Calcula ratios financieros y métricas de crecimiento a partir de los estados contables de la entidad. |
| `GET /ms-finance/news/{ticker}` | Recupera en tiempo real noticias vinculadas al símbolo bursátil. |
| `GET /ms-sector-analysis/market/{ticker}` | Recupera métricas bursátiles de un ETF representativo. |
| `GET /ms-sector-analysis/trends/{ticker}` | Utiliza la función de sugerencias de Google Trends para proponer palabras clave y temas relacionados con el sector. |
| `GET /ms-sector-analysis/time-series/{keyword}` | Proporciona una serie temporal que muestra la popularidad relativa de un término de búsqueda en Google. |

## ⚡ Ejecucción

Navega hasta el directorio raíz del proyecto y ejecuta el siguiente comando en tu terminal:

```bash
docker compose up --build -d
```
