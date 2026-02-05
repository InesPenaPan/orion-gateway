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
| `POST /ms-finance/finance/{ticker}` | Calcula ratios financieros y métricas de crecimiento a partir de los estados contables de la entidad. |
| `POST /ms-finance/news/{ticker}` | Recupera en tiempo real noticias vinculadas al símbolo bursátil. |
| `POST /ms-sector-analysis/market/{ticker}` | Recupera métricas bursátiles de un ETF representativo. |
| `POST /ms-sector-analysis/trends/{ticker}` | Utiliza la función de sugerencias de Google Trends para proponer palabras clave y temas relacionados con el sector. |
| `POST /ms-sector-analysis/time-series/{keyword}` | Proporciona una serie temporal que muestra la popularidad relativa de un término de búsqueda en Google. |
| `POST /ms-news/news/{company}` | Consulta las menciones en prensa de los últimos siete días sobre una entidad. |
| `POST /ms-crm/clients` | Lista todas las entidades corporativas registradas en el CRM. |
| `POST /ms-crm/opportunities` | Lista global de oportunidades con nombres de cliente y gestor vinculados. |
| `POST /ms-crm/opportunities/user/{userId}` | Métricas de rendimiento y oportunidades asignadas a un usuario específico. |
| `POST /ms-crm/opportunities/client/{clientId}` | Métricas de rendimiento y oportunidades asignadas a un usuario específico. |
| `POST /ms-crm/opportunities/clients/user/{userId}` | Relación de clientes únicos que integran la cartera de un usuario. |

## ⚡ Ejecucción

Navega hasta el directorio raíz del proyecto y ejecuta el siguiente comando en tu terminal:

```bash
docker compose up --build -d
```
Una vez levantado el contenedor, la API estará disponible en el puerto `8762`. Puedes verificar el funcionamiento realizando peticiones a través de tu navegador, cURL o Postman.

**[IMPORTANTE]** Es imprescindible incluir la cabecera `Content-Type: application/json` en todas las peticiones, ya que el Gateway procesa la lógica de enrutamiento a través del cuerpo de la solicitud.

Estructura base del Payload:

```bash
{
    "targetMethod": "GET",
    "queryParams": {},
    "body": {}
}
```

### 📂 Estructura del Proyecto

```bash
orion-gateway/
├── src/main/java/com/orion/gateway/
│   ├── config/                             # Configuración de beans y mapeadores
│   │   └── MapperConfig.java
│   ├── decorator/                          # Decoradores para la transformación de peticiones
│   │   ├── GetRequestDecorator.java
│   │   ├── PostRequestDecorator.java
│   │   └── RequestDecoratorFactory.java
│   ├── filter/                             # Filtros personalizados de Spring Cloud Gateway
│   │   └── RequestTranslationFilter.java
│   ├── model/                              # Modelos de datos y DTOs de entrada
│   │   └── GatewayRequest.java
│   ├── utils/                              # Utilidades para extracción de datos del body
│   │   └── RequestBodyExtractor.java
│   └── GatewayApplication.java             # Clase principal de Spring Boot
├── src/main/resources/
│   └── application.yaml                    # Configuración de rutas, filtros y Eureka
├── docker-compose.yml                      # Orquestación del despliegue en contenedores
├── Dockerfile                              # Definición de la imagen Docker del componente
├── .mvn/                                   # Archivos de configuración de Maven Wrapper
├── mvnw                                    # Maven Wrapper (Linux/macOS)
├── mvnw.cmd                                # Maven Wrapper (Windows)
└── pom.xml                                 # Definición de dependencias y plugins de Maven
```
