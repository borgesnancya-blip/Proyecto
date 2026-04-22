# Pipeline BI: Power BI + GitHub + Microsoft Fabric 🚀

## 👤 Autora
**Nancy Borges** *Desarrolladora de Business Intelligence | Analista de Datos*

---

## 1. Introducción y Propósito 🎯
El presente proyecto detalla la arquitectura de un **pipeline de datos moderno** para Business Intelligence. El objetivo principal es trascender el desarrollo local tradicional de Power BI hacia un ecosistema escalable que implemente **Control de Versiones (Git)** y **Despliegue Continuo (CI/CD)** en la nube de **Microsoft Fabric**.

---

## 2. Arquitectura del Flujo de Trabajo 🏗️

### Etapa 1: Desarrollo y Modelado Semántico (Power BI Desktop) 📊
En lugar del archivo estándar `.pbix`, el proyecto se inicia utilizando el formato **Power BI Project (.pbip)**. 
- **Por qué:** Este formato descompone el reporte en metadatos y archivos de texto legibles, permitiendo que Git rastree cambios específicos en el modelo de datos y el diseño visual.
- **Acción:** Extracción de datos, limpieza y creación del modelo semántico.

### Etapa 2: Control de Versiones y Auditoría (VS Code + Git) 💻
Utilizo **Visual Studio Code** como interfaz de desarrollo para gestionar el repositorio local de Git.
- **Estrategia de Ramas:** Implemento una rama `develop` para pruebas y modificaciones, y una rama `main` para la versión de producción estable.
- **Trazabilidad:** Cada cambio significativo es documentado mediante un `commit`, garantizando una línea de tiempo donde es posible revertir errores o auditar modificaciones previas.
- **Comandos Clave:** ```bash
  git branch develop
  git checkout develop
  git commit -m "Descripción del cambio"
  git merge develop
  
### Etapa 3: Repositorio Central y CI/CD (GitHub) 🌐
GitHub actúa como la **"Única Fuente de Verdad" (Single Source of Truth)**, centralizando el código y automatizando el despliegue.
- **GitHub Actions:** He configurado un agente de sincronización automático mediante un archivo `.yml` en la carpeta `.github/workflows`. Este "disparador" se activa ante cada `push` en la rama `main`, notificando al ecosistema que existe una nueva versión lista para ser procesada.
- **Seguridad:** Conexión mediante **Personal Access Tokens (PAT)** siguiendo protocolos de seguridad corporativa y el principio de privilegio mínimo.

### Etapa 4: Despliegue en Microsoft Fabric ☁️
El punto culminante es la integración con **Microsoft Fabric**, donde el Workspace de producción se conecta directamente al repositorio de GitHub.
- **Sincronización Automática:** Fabric detecta los cambios en la rama `main` y actualiza los elementos del Workspace (informes y modelos semánticos) sin intervención manual.
- **Resultado:** Se garantiza que el negocio siempre tome decisiones basadas en la versión oficial, testeada y validada del dato.

---

## 3. Visualización del Pipeline 🖼️
![Arquitectura del Proyecto]
<img width="214" height="303" alt="Captura de pantalla (1452)" src="https://github.com/user-attachments/assets/0c435fa0-4c11-4eb7-a868-3b657c4f9e67" />

---

## 4. Beneficios de esta Implementación ✅
1.  **Escalabilidad:** Permite el trabajo colaborativo de múltiples analistas evitando conflictos de archivos.
2.  **Gobierno de Datos:** Control total sobre el historial de modificaciones (Quién, Qué y Cuándo), facilitando auditorías.
3.  **Eficiencia y Seguridad:** Reducción drástica de errores manuales y capacidad de realizar "Rollbacks" (volver a versiones anteriores) en segundos si algo falla.

---

## 5. Conclusión 🏁
Este pipeline profesionaliza el ciclo de vida del desarrollo de BI (**Data Lifecycle Management**), alineando las capacidades de Power BI con las mejores prácticas de la ingeniería de software moderna y preparando la infraestructura para el análisis de datos a escala empresarial.
