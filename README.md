<div align="center">

# ⚡ MarketingFlow — Enterprise Marketing Command Center

![Architecture](https://img.shields.io/badge/Architecture-Next.js_14_App_Router-0A0A0F?style=for-the-badge&logo=next.js&logoColor=38BDF8&labelColor=141622&color=38BDF8)
![Engine](https://img.shields.io/badge/Engine-Heuristic_Inference_Pipeline-0A0A0F?style=for-the-badge&logo=googlecloud&logoColor=A855F7&labelColor=141622&color=A855F7)
![Workspace](https://img.shields.io/badge/Integration-Google_Workspace_OAuth_2.0-0A0A0F?style=for-the-badge&logo=google&logoColor=00E5FF&labelColor=141622&color=00E5FF)
![Security](https://img.shields.io/badge/SecOps-Docker_Non--Root_%7C_Cloudflare_WAF-0A0A0F?style=for-the-badge&logo=cloudflare&logoColor=10B981&labelColor=141622&color=10B981)

**Centro de Comando Estratégico, Orquestación Multicanal y Automatización Algorítmica de Pauta Digital conectado en tiempo real con Google Workspace.**

</div>

---

## 🎯 1. Problema de Negocio y Solución de Ingeniería

Las direcciones de mercadotecnia y líderes de marca gestionan simultáneamente presupuestos publicitarios (Meta Ads, Google Ads, TikTok Ads), calendarios editoriales, activos en la nube y embudos de prospectos en herramientas fragmentadas, perdiendo trazabilidad financiera y velocidad de ejecución.

**MarketingFlow** unifica toda la operación en una arquitectura **Bento Grid de alto contraste** (`#0A0A0F` / `#141622`) sincronizada con **Google Workspace** (Drive, Sheets, Calendar, Slides y Gmail) e impulsada por dos pipelines algorítmicos empresariales:
- **`HeuristicInferenceService` (`/api/v1/engine/predictive`):** Auditoría de métricas financieras (ROI, CPA, CPL, CTR), redistribución de pujas y estructuración de campañas bajo esquemas JSON estrictos.
- **`CreativeAutomationService` (`/api/v1/marketing/automation`):** Pipeline heurístico con *Domain Guardrail* para la estructuración de piezas visuales publicitarias, redacción persuasiva (AIDA/PAS) y segmentación de audiencias.

---

## 🏗️ 2. Arquitectura del Sistema y Flujo de Datos

```mermaid
flowchart LR
    subgraph UI["🎨 Frontend Command Center (Next.js 14)"]
        BENTO["Bento Grid Dashboard<br/>(6 Módulos Dinámicos)"]
        DRAWER["Panel Estratégico Lateral<br/>( ARY Engine)"]
        STUDIO["Módulo F: Estudio Creativo<br/>(CreativeStudioModule)"]
    end

    subgraph API["⚙️ Capa Algorítmica Empresarial"]
        PRED["POST /api/v1/engine/predictive<br/>(HeuristicInferenceService)"]
        AUTO["POST /api/v1/marketing/automation<br/>(CreativeAutomationService)"]
        GUARD["Domain Guardrail &<br/>Strict JSON Schema"]
    end

    subgraph CLOUD["☁️ Ecosistema Externo & Persistencia"]
        GWS["Google Workspace Hub<br/>(Drive, Sheets, Calendar, Slides)"]
        ADS["Canales de Pauta & CRM<br/>(Meta Graph, TikTok, WhatsApp)"]
    end

    DRAWER -->|Payload Contextual| PRED
    STUDIO -->|Briefing + Estilo + Tono| AUTO
    PRED --> GUARD
    AUTO --> GUARD
    BENTO <-->|OAuth 2.0 / Webhooks| GWS
    GUARD -->|Activos & Reportes| GWS
    BENTO -->|Despacho 1-Clic| ADS

    classDef uiNode fill:#141622,stroke:#38BDF8,stroke-width:2px,color:#F8FAFC;
    classDef apiNode fill:#1E1B4B,stroke:#A855F7,stroke-width:2px,color:#F8FAFC;
    classDef cloudNode fill:#064E3B,stroke:#10B981,stroke-width:2px,color:#F8FAFC;

    class BENTO,DRAWER,STUDIO uiNode;
    class PRED,AUTO,GUARD apiNode;
    class GWS,ADS cloudNode;
```

---

## 🧩 3. Módulos Operativos del Bento Grid

| Código | Módulo | Capacidades Técnicas | Integración Principal |
| :---: | :--- | :--- | :--- |
| **A** | **Gestión de Proyectos y Campañas** | Control de entregables (SEO, Social Ads, Contenido, Email), barras de progreso y ejecución presupuestaria. | Google Tasks & Sheets |
| **B** | **Métricas y Finanzas en Vivo** | Visualización interactiva con Recharts de ROI (`3.8x`), CPL, CPA, CTR y curvas de inversión diaria. | Google Sheets Live API |
| **C** | **Calendario de Contenidos** | Programación mensual/semanal, edición en línea, vista previa de activos y aprobación en 1 clic. | Google Calendar + Meta Graph |
| **D** | **CRM Omnicanal & WhatsApp** | Captura de leads con *Lead Scoring* (`0-100`), embudo de conversión y automatización de respuesta. | WhatsApp Cloud API + Gmail |
| **E** | **Google Workspace Hub** | Árbol estandarizado de carpetas (`01_Estrategia` a `05_CRM_Leads`) y acceso directo a Docs, Sheets y Slides. | Google Drive + Apps Script |
| **F** | **Estudio Creativo & ` ARY`** | Automatización de propuestas visuales (`1:1`, `9:16`, `16:9`), copywriting AIDA y segmentación táctica. | `/api/v1/marketing/automation` |

---

## 🛡️ 4. Ingeniería de Ciberseguridad (DevSecOps)

```mermaid
flowchart TD
    REQ["Solicitud Cliente HTTP POST"] --> WAF["Cloudflare WAF & Rate Limiting"]
    WAF --> VAL["Validación Estricta de Tipos<br/>(ValidationException HTTP 400)"]
    VAL --> DOM["Guardrail Heurístico de Dominio<br/>(Bloqueo HTTP 403 fuera de Marketing)"]
    DOM --> SCHEMA["Contrato de Salida Tipado<br/>(Strict JSON Schema HTTP 200)"]
    SCHEMA --> DOCK["Contenedor Alpine Aislado<br/>(Usuario no-root: nextjs:1001)"]

    classDef secPrimary fill:#141622,stroke:#00E5FF,stroke-width:2px,color:#FFFFFF;
    classDef secGuard fill:#1E1B4B,stroke:#A855F7,stroke-width:2px,color:#FFFFFF;
    classDef secInfra fill:#064E3B,stroke:#10B981,stroke-width:2px,color:#FFFFFF;

    class REQ,WAF secPrimary;
    class VAL,DOM,SCHEMA secGuard;
    class DOCK secInfra;
```

- **Aislamiento de Contenedores (Non-Root):** Ejecución sobre `node:20-alpine` en compilación *multi-stage standalone* bajo el usuario sin privilegios `nextjs` (`UID 1001:1001`), con directivas `no-new-privileges:true` y `cap_drop: ALL`.
- **Guardrail de Dominio y Protección de Cuota:** Rechazo determinista de peticiones ajenas al ámbito de mercadotecnia digital (`ERROR_OUT_OF_DOMAIN`) y validación temprana de payloads.
- **Integridad Criptográfica:** Historial de versiones firmado criptográficamente (`Verified` SSH/GPG) y separación física entre el núcleo privado y la vitrina pública mediante `git subtree`.

---

## 🎨 5. Sistema de Diseño (Paleta Cromática)

| Token | Hex | Aplicación Visual |
| :--- | :---: | :--- |
| **Obsidian Matte** | `#0A0A0F` | Fondo principal de baja fatiga visual |
| **Spatial Panel** | `#141622` | Tarjetas Bento Grid con efecto *Glassmorphism* |
| **Electric Sky** | `#38BDF8` | Indicadores de rendimiento, acciones primarias y bordes activos |
| **Neon Lavender** | `#A855F7` | Badges de motor predictivo, acentos analíticos y gradientes |
| **Emerald Signal** | `#10B981` | Confirmaciones de sincronización en vivo con Google Workspace |

---

<div align="center">
  <sub>Desarrollado bajo estándares de Arquitectura Empresarial y DevSecOps • 2026</sub>
</div>
