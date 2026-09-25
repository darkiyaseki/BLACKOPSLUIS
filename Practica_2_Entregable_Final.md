# Práctica 2. Realizar diagrama de flujo del escenario 1 empleando Mermaid y compilar archivo markdown en Github que incluya STRIDE

# Modelado de Amenazas: Sistema de Autenticación y API de Usuarios

**Fecha:** 2026-08-31  
**Versión:** 1.0  
**Autores:** Yahir Martínez Chávez

## 1. Diagrama de Flujo de Datos (DFD) con Mermaid.js

A continuación se muestra la arquitectura lógica del sistema, los flujos de datos y las fronteras de confianza (Trust Boundaries) que separan las zonas seguras de las inseguras.

```mermaid
graph TD
    %% Definición de Estilos y Fronteras de Confianza
    classDef internet fill:#f9f,stroke:#333,stroke-width:2px;
    classDef secureZone fill:#bbf,stroke:#333,stroke-width:2px;
    
    %% Actores y Componentes
    Usuario["🌐 Usuario (Navegador/App)"] -- "1. Envía Credenciales (HTTPS)" --> API["⚙️ API Gateway / Backend"]
    Admin["👨‍💻 Administrador de Red"] -- "5. Mantenimiento (SSH)" --> BD[("🗄️ Base de Datos SQL")]
    
    API -- "2. Consulta / Guarda Usuario" --> BD
    API -- "3. Valida Token" --> Auth["🔑 Servicio de Auth Externo (OAuth)"]
    API -. "4. Registro de Auditoría" .-> Logs[("📋 Servidor de Logs / SIEM")]
    
    %% Fronteras de Confianza
    subgraph Internet ["Frontera de Internet (Insegura)"]
        Usuario
    end
    
    subgraph RedInterna ["Red Interna de la Empresa (Zona Segura)"]
        API
        BD
        Auth
        Logs
    end

    %% Aplicar Estilos
    class Usuario internet;
    class API,BD,Auth,Logs secureZone;

# Práctica 2. Realizar diagrama de flujo del escenario 1 empleando Mermaid y compilar archivo markdown en Github que incluya STRIDE

# Modelado de Amenazas: Sistema de Autenticación y API de Usuarios

**Fecha:** 2026-08-31  
**Versión:** 1.0  
**Autores:** Yahir Martínez Chávez

## 1. Diagrama de Flujo de Datos (DFD) con Mermaid.js

A continuación se muestra la arquitectura lógica del sistema, los flujos de datos y las fronteras de confianza (Trust Boundaries) que separan las zonas seguras de las inseguras.

```mermaid
graph TD
    %% Definición de Estilos y Fronteras de Confianza
    classDef internet fill:#f9f,stroke:#333,stroke-width:2px;
    classDef secureZone fill:#bbf,stroke:#333,stroke-width:2px;
    
    %% Actores y Componentes
    Usuario["🌐 Usuario (Navegador/App)"] -- "1. Envía Credenciales (HTTPS)" --> API["⚙️ API Gateway / Backend"]
    Admin["👨‍💻 Administrador de Red"] -- "5. Mantenimiento (SSH)" --> BD[("🗄️ Base de Datos SQL")]
    
    API -- "2. Consulta / Guarda Usuario" --> BD
    API -- "3. Valida Token" --> Auth["🔑 Servicio de Auth Externo (OAuth)"]
    API -. "4. Registro de Auditoría" .-> Logs[("📋 Servidor de Logs / SIEM")]
    
    %% Fronteras de Confianza
    subgraph Internet ["Frontera de Internet (Insegura)"]
        Usuario
    end
    
    subgraph RedInterna ["Red Interna de la Empresa (Zona Segura)"]
        API
        BD
        Auth
        Logs
    end

    %% Aplicar Estilos
    class Usuario internet;
    class API,BD,Auth,Logs secureZone;
