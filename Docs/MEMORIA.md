<h1><span style="color: #1187d6;">Dark Blue - Mar de Acero</span></h1>

-   **Autor:** Alberto Tabernero Valle
-   **Ciclo:** Desarrollo de Aplicaciones Web
-   **Centro:** I.E.S. Alonso de Avellaneda (Alcalá de Henares, Madrid)
-   **Año académico:** 2025/2026

---

## 1. Introducción y Justificación

**Descripción del proyecto:**  
_Dark Blue: Mar de Acero_ es un juego web estratégico basado en _Hundir la Flota_, con modos "offline" (lógica inteligente de disparos) y online player vs player.

**Finalidad:**  
Proporcionar un juego divertido, original y emocionante, combinando estrategia, interacción social y progresión del jugador.

**Objetivos:**

-   Partidas online en tiempo real sincronizadas.
-   Sistema con ataques especiales.
-   Perfil y progresión del jugador.
-   Tienda virtual con créditos.

**Motivación:**  
 La motivación para realizar este proyecto surge del interés personal por el desarrollo de videojuegos, el arte y el diseño audiovisual.
Además, se ha buscado crear un proyecto **original y ambicioso**, que vaya más allá de los ejemplos vistos en clase, incorporando tecnologías no tratadas en profundidad durante el ciclo, como WebSockets, Angular Signals o sistemas de sincronización en tiempo real.
En el plano personal, aparte de ser un reto a nivel técnico, me apetecía mostrar y compartir mi creatividad con todo el mundo. Más allá de la posible explotación como producto, lo cual aparentemente es factible.

---

## 2. Estudio de Viabilidad

Como sabía que no llegaría al despliegue dada la complejidad y principalmente al factor tiempo, la prioridad era sacar un proyecto funcional y bastante completo. Al quedarme en la fase de desarrollo y no pasar a producción, no he llegado a valorar los costes que podría suponer. Pero entiendo que no serían elevados para un despliegue inicial modesto y sin patrocinio.
Barajé el despliegue en contenedores docker y de esta manera alojarlos en un mismo server, con lo cual supongo que con un alquiler de alojamiento web sería suficiente.

### 2.1 Viabilidad Económica

-   Hosting: 0–5€/mes
-   Dominio: 10–15€/año
-   Herramientas: gratuitas
-   Licencias: open source

#### 2.1.1 Retorno de la inversión (ROI)

El proyecto no nace con un objetivo económico inmediato. No obstante, podría evolucionar hacia:

-   Monetización mediante publicidad.
-   Microtransacciones dentro del juego.
-   Donativos libres al desarrollador.

El retorno de la inversión sería posible a medio o largo plazo, dependiendo de su difusión y aceptación.

---

### 2.2 Viabilidad Legal

-   GDPR para datos personales
-   Licencias de Angular, Spring Boot, Tailwind, SweetAlert2
-   Recursos gráficos y audio libres o editados

#### 2.2.1 Cumplimiento normativo

El proyecto debe cumplir con:

-   **Reglamento General de Protección de Datos (RGPD)**, en caso de almacenar datos personales.
-   Políticas de privacidad y gestión de cookies, si se publica de forma abierta.

---

### 2.2.2 Propiedad intelectual

El proyecto es **original**.  
Los recursos gráficos y sonoros utilizados son:

-   De creación propia.
-   Libres de derechos (Pixabay).
-   Generados o asistidos por herramientas de IA (Gemini, ChatGPT).

Se respetan las condiciones de uso y atribución cuando corresponde.

### 2.3 Viabilidad de Tiempo

| Fase               | Duración  |
| ------------------ | --------- |
| Análisis y diseño  | 2 semanas |
| Frontend           | 4 semanas |
| Backend y DB       | 3 semanas |
| Integración online | 3 semanas |
| Documentación      | 1 semana  |

**Metodología:** iterativa tipo Scrum/Kanban.

---

## 3. Análisis y Diseño del Proyecto

### 3.1 Arquitectura web

La aplicación sigue una arquitectura **SPA (Single Page Application)**:

-   **Frontend** desarrollado con Angular 19.
-   **Backend** basado en Spring Boot.
-   Comunicación REST para operaciones generales.
-   Comunicación en tiempo real mediante WebSockets (STOMP).

Esta arquitectura permite una experiencia fluida y desacoplada.

### 3.2 Tecnologías y herramientas utilizadas

#### Frontend

-   Angular 19
-   TypeScript
-   Angular Signals
-   RxJS
-   Tailwind CSS 4
-   SweetAlert2
-   STOMP + SockJS
-   Animaciones CSS
-   Audio integrado

#### Backend

-   Java 17
-   Spring Boot 3.5
-   Spring Security + JWT
-   Spring WebSocket
-   Spring Data MongoDB
-   WebFlux
-   Maven

#### Base de datos

-   MongoDB (NoSQL)
-   Archivos media estáticos (servidos por Spring)

#### Herramientas adicionales

-   Git / GitHub
-   VS Code
-   IntelliJ IDEA
-   Audacity
-   Gimp
-   ChatGPT
-   Gemini

---

### 3.4 Requisitos Funcionales y No Funcionales

#### **Funcionales:**

-   registro/login
-   partidas player vs IA y player vs player
-   ataques especiales
-   chat
-   tienda
-   perfil

#### **No funcionales:**

-   (Limitación actual )ataques especiales en online sólo x2Shot está operativo

### 3.5 Estructura de Navegación

```
Registro
 |
Login
 |
Menu
 ├─ Nueva partida
 ├─ Online
 ├─ Opciones
 │   ├─ Estadísticas
 │   ├─ Gestión de usuario
 │   └─ Tienda
 └─ Salir

```

### 3.6. Organización de la lógica de negocio

**Backend controllers:**

-   Auth: (registro, login)
-   Perfil
-   Game: (Partidas creación, control de turnos, ataque especial)
-   IA para juego online
-   WebSockets (topic gameId)
-   Item: (tienda y perfil)
-   Config para resources media

### 3.7. Modelo de datos simplificado

#### Principales o más significativos

```typeScript
GAME:

type SpecialOnline = {
  special1: string,
  special2: string,
  counter1: number,
  counter2: number,
  activeSpecial1: boolean,
  activeSpecial2: boolean
}

export default interface Game {
  gameId: string;
  online: boolean;
  stage: number;
  phase: 'JOINED' | 'WAITING' | 'PLACEMENT' | 'BATTLE' | 'END';
  player1: string;
  avatarPlayer1: string;
  player2: string;
  avatarPlayer2: string;
  turn: string;
  isEnd: boolean;
  boardPlayer1: Board;
  boardPlayer2: Board;
  readyPlayer1: boolean;
  readyPlayer2: boolean;
  winner: string | null;
  specialPlayer1: SpecialOnline | null;
  specialPlayer2: SpecialOnline | null;
}

PERFIL:

export default interface Perfil {
  id?: string;
  username: string;
  nickname: string;
  avatar: string;
  idActualGame?: string;
  stats: Stats;
}

STATS:

export default interface Stats {
  fechaRegistro: Date;
  stage: Number;
  coins: Number;
  wins: Number;
  losses: Number;
  playTime?: number; // total en milisegundos
  currentStartTime?: number; // timestamp del inicio actual
  rango?: string;
  specials?: string[];
  specialSlot1?: string;
  specialSlot2?: string;
}

WEBSOCKET MESSAGES:

type ShotResult = {
  hit: boolean;
  miss: boolean;
  destroyed: boolean;
};
type ShotsResponse ={
  position: string;
  result: 'HIT' | 'MISS' | 'DESTROYED';
}

export default interface GameMessage {

  phase?: 'EXIT' | 'JOINED' | 'WAITING' | 'PLACEMENT' | 'BATTLE' | 'END';
  game?: Game;
  lastShot?: ShotResult;
  shots?: ShotsResponse[];
  player?: string;
  slot?: number;
  special?: string;

  type?: 'GAME' | 'CHAT' | 'EXIT' | 'SPECIAL' | 'AI_SHOTS';
  sender?: string;
  content?: string;
  timestamp?: string;
}

```

## 4. Conclusiones

La realización de Dark Blue como proyecto de fin de grado de Desarrollo de Aplicaciones Web, ha sido una experiencia muy enriquecedora. En la que he aprendido, basándome en la experiencia de su desarrollo, cosas a tener muy en cuenta para futuros proyectos.
En la fase inicial de desarrollo me centré excesivamente en el frontend, desarrollando gran parte de la lógica de negocio en angular. Entonces, cuando fui a implementar el modo online, me di cuenta del error que eso supone. Para no tener que rehacer todo tuve que duplicar alguna parte de la lógica y separarla para el modo online, para no afectar a toda la parte funcional del juego.
No obstante, a pesar de las dificultades en el desarrollo, he de decir que me he divertido bastante y he podido sacar a la luz algo original y creativo.
Me hubiera gustado añadir muchas cosas más, como cinemáticas, historia, diálogos y un sinfín de mejoras e ideas que me rondan la cabeza para hacer un juego vivo y atractivo.
Pero, bajando a la tierra, el tiempo era limitado y había que sacar algo funcional.
Estoy valorando muy positivamente el refactorizar y continuar el proyecto, pero portándolo a la plataforma para móvil.

---
