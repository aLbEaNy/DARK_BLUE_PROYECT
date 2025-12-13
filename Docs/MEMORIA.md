<h1 style="color: #1187d6;">Dark Blue - Mar de Acero</h1>

- **Autor:** Alberto Tabernero Valle  
- **Ciclo:** Desarrollo de Aplicaciones Web
- **Centro:** I.E.S. Alonso de Avellaneda (Alcalá de Henares, Madrid)
- **Año académico:** 2025/2026  

---

## 1. Introducción y Justificación

**Descripción del proyecto:**  
*Dark Blue: Mar de Acero* es un juego web estratégico basado en *Hundir la Flota*, con modos "offline" (IA) y online player vs player.

**Finalidad:**  
Proporcionar un juego divertido, original y emocionante, combinando estrategia, interacción social y progresión del jugador.

**Objetivos:**  
- Partidas online en tiempo real sincronizadas.  
- Sistema con ataques especiales.  
- Perfil y progresión del jugador.  
- Tienda virtual con créditos.  

**Motivación:**  
 La motivación para realizar este proyecto surge del interés personal por el desarrollo de videojuegos, el arte y el diseño audiovisual.
Además, se ha buscado crear un proyecto **original y ambicioso**, que vaya más allá de los ejemplos vistos en clase, incorporando tecnologías no tratadas en profundidad durante el ciclo, como WebSockets, Angular Signals o sistemas de sincronización en tiempo real.
En el plano personal, a parte de ser un reto a nivel técnico, me apetecía mostrar y compartir mi creatividad con todo el mundo. Más hallá de la posible explotación como producto, lo cual aparentemente es factible.

---

## 2. Estudio de Viabilidad
 Como sabía que no llegaría al despliegue dada la complejidad y principalmente al factor tiempo, la prioridad era sacar un proyecto funcional y bastante completo. Al quedarme en la fase de desarrollo y no pasar a producción, no he llegado a valorar los costes que podría suponer. Pero entiendo que no serían elevados para un despliegue inicial modesto y sin patrocinio.
 Barajé el despliegue en contenedores docker y de esta manera alojarlos en un mismo server, con lo cual supongo que con un alquiler de alojamiento web sería suficiente.  

### 2.1 Viabilidad Económica
- Hosting: 0–5€/mes  
- Dominio: 10–15€/año  
- Herramientas: gratuitas  
- Licencias: open source 

#### 2.1.2 Retorno de la inversión (ROI)

El proyecto no nace con un objetivo económico inmediato. No obstante, podría evolucionar hacia:

- Monetización mediante publicidad.
- Microtransacciones dentro del juego.
- Donativos libres al desarrollador.

El retorno de la inversión sería posible a medio o largo plazo, dependiendo de su difusión y aceptación.

--- 

### 2.2 Viabilidad Legal
- GDPR para datos personales  
- Licencias de Angular, Spring Boot, Tailwind, SweetAlert2  
- Recursos gráficos y audio libres o editados 
#### 2.2.1 Cumplimiento normativo

El proyecto debe cumplir con:

- **Reglamento General de Protección de Datos (RGPD)**, en caso de almacenar datos personales.
- Políticas de privacidad y gestión de cookies, si se publica de forma abierta.

--- 

### 2.2.3 Propiedad intelectual

El proyecto es **original**.  
Los recursos gráficos y sonoros utilizados son:

- De creación propia.
- Libres de derechos (Pixabay).
- Generados o asistidos por herramientas de IA (Gemini, ChatGPT).

Se respetan las condiciones de uso y atribución cuando corresponde.


### 2.3 Viabilidad de Tiempo
| Fase | Duración |
|------|----------|
| Análisis y diseño | 2 semanas |
| Frontend | 4 semanas |
| Backend y DB | 3 semanas |
| Integración online | 3 semanas |
| Documentación | 1 semana |

**Metodología:** iterativa tipo Scrum/Kanban.

---

## 3. Análisis y Diseño del Proyecto

### 3.1 Arquitectura web

La aplicación sigue una arquitectura **SPA (Single Page Application)**:

- **Frontend** desarrollado con Angular 19.
- **Backend** basado en Spring Boot.
- Comunicación REST para operaciones generales.
- Comunicación en tiempo real mediante WebSockets (STOMP).

Esta arquitectura permite una experiencia fluida y desacoplada.



### 3.2 Tecnologías y herramientas utilizadas

#### Frontend
- Angular 19
- TypeScript
- Angular Signals
- RxJS
- Tailwind CSS 4
- SweetAlert2
- STOMP + SockJS
- Animaciones CSS
- Audio integrado

#### Backend
- Java 17
- Spring Boot 3.5
- Spring Security + JWT
- Spring WebSocket
- Spring Data MongoDB
- WebFlux
- Maven

#### Base de datos
- MongoDB (NoSQL)
- Archivos media estáticos (servidos por Spring)

#### Herramientas adicionales
- Git / GitHub
- VS Code
- IntelliJ IDEA
- Audacity
- Gimp
- ChatGPT
- Gemini

---





### 3.3 Análisis de Usuarios
- Jugador: perfil, XP, estadísticas, inventario  
- Administrador: gestión de usuarios y estadísticas (opcional)  

### 3.4 Requisitos Funcionales y No Funcionales
**Funcionales:** registro/login, partidas , ataques, chat, tienda  
**No funcionales:** <200ms en online, responsive, seguro, accesible  

### 3.5 Estructura de Navegación
