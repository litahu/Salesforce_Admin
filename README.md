# 💊 **"VitalCore CRM" - Implementación Salesforce**

### **Construido con 🛠️** <br>
- **Analítica funcional** : Prototipo de requerimientos de acuerdo a la elicitación del negocio. [Ver](https://github.com/litahu/Salesforce_Admin/blob/main/resource_sfadmin/Primer_prototipo.pdf)<br>
- **Salesforce Experience Cloud** : Experience Builder, Salesforce Knowledge, Guest User Profile, Omnicanalidad y Screen Flow público integrado al portal. [Ver](https://www.salesforce.com/trailblazer/litahume)<br>
 
<br>
  
Este proyecto demuestra el ciclo completo de una implementación Salesforce: desde el levantamiento de requerimientos y el modelado de datos, hasta la automatización de procesos, la inteligencia comercial con reportes y tableros, y la apertura al mundo exterior mediante un portal interactivo en Experience Cloud para VitaCore Labs.<br>

### Tabla de contenido <!-- omit in toc -->

El proyecto fue desarrollado en 4 Sprints reales siguiendo buenas prácticas de configuración declarativa en Salesforce:
- [ETAPA 0: Enunciado del problema](https://github.com/litahu/Salesforce_Admin?tab=readme-ov-file#etapa-0-enunciado-del-problema)
- [ETAPA 1: Construcción en Developer Org](https://github.com/litahu/Salesforce_Admin?tab=readme-ov-file#etapa-1-construcción-en-developer-org)
- [ETAPA 2: Migración, calidad de datos y reportería](https://github.com/litahu/Salesforce_Admin?tab=readme-ov-file#etapa-2-migración,-calidad-de-datos-y-reportería)
- [ETAPA 3: Automatización y reportería](https://github.com/litahu/Salesforce_Admin?tab=readme-ov-file#etapa-3-automatización-y-reportería)
- [ETAPA 4: Portal Experience Cloud](https://github.com/litahu/Salesforce_Admin?tab=readme-ov-file#etapa-4-portal-experience-cloud)

<br>
   
## 📁**ETAPA 0: Enunciado del problema**

#### **📋 Descripción del Proyecto**
VitaCore Labs es un laboratorio farmacéutico B2B que opera con un equipo de visitadores médicos que gestiona relaciones comerciales con hospitales, clínicas y médicos especialistas.
**Industria** : Sector salud

```
El Desafío
Operación dispersa, sin visibilidad ni automatización
El cliente necesitaba centralizar la gestión comercial, eliminar el registro manual de visitas médicas
y obtener visibilidad en tiempo real sobre el desempeño del equipo de campo y la cobertura de médicos.
```

```
La Solución
CRM personalizado + Experience Cloud para autoservicio
Implementación de Sales Cloud con objetos personalizados para visitas médicas, automatización de flujos
con Screen Flows y Flow Builder, carga masiva de datos históricos, tableros de gestión y un portal
 interactivo para pacientes en Experience Cloud.
```

#### **🎫 Levantamiento de requerimientos**
Lideré la definición de historias de usuario para implementar soluciones end-to-end bajo un enfoque ágil


### Sprint 1 — Identidad, Modelo de Datos y Gestión de Usuarios

<details>
  <summary> Haga clic para ver las HU </summary>
    <br> 

```

#### Épica 1: Identidad y Experiencia VitaCore CRM

---

**HU-01: App personalizada VitaCore CRM**

> **Como** Visitador Médico,
> **quiero** ingresar a Salesforce mediante una aplicación propia llamada "VitaCore CRM",
> **para** trabajar únicamente con las herramientas relevantes a mi rol.

**Criterios de Aceptación:**
- [ ] Existe una Lightning App llamada **VitaCore CRM** visible solo para el equipo de ventas.
- [ ] Las apps estándar (Sales / Service) están ocultas para usuarios no administradores.
- [ ] La app incluye las pestañas: Cuentas, Contactos, Productos Farma, Visitas Médicas.

---

**HU-02: Identidad corporativa aplicada en Salesforce**

> **Como** colaborador de VitaCore Labs,
> **quiero** que Salesforce refleje nuestra identidad visual,
> **para** sentir que es un sistema propio, profesional y confiable.

**Criterios de Aceptación:**
- [ ] Tema configurado con los colores: Azul VitaCore `#005b96`, Verde Salud `#28a745`, Gris Neutro `#f4f6f9`.
- [ ] Barra de navegación de VitaCore CRM con los colores corporativos.
- [ ] Interfaz visual consistente en todas las páginas del sistema.

---

#### Épica 2: Modelado de Datos del Negocio

---

**HU-03: Gestión de Hospitales y Clínicas (Cuentas)**

> **Como** Visitador Médico,
> **quiero** registrar Hospitales y Clínicas como Cuentas,
> **para** centralizar la información institucional y tener visibilidad de mis clientes.

**Criterios de Aceptación:**
- [ ] Las Cuentas representan Hospitales y Clínicas con tipo de registro diferenciado.
- [ ] Todas las Cuentas tienen un propietario asignado.
- [ ] Un Visitador Médico puede ser dueño de sus propias cuentas.

---

**HU-04: Registro de Médicos como Contactos**

> **Como** Visitador Médico,
> **quiero** registrar a los médicos como Contactos vinculados a sus instituciones,
> **para** gestionar mi cartera de especialistas de forma centralizada.

**Criterios de Aceptación:**
- [ ] Campo `Especialidad_Medica__c` (picklist) creado en el objeto Contacto.
- [ ] Campo `Fecha_Ultima_Visita__c` (date) visible en el layout de página.
- [ ] Contacto vinculado a una Cuenta (hospital/clínica) mediante campo lookup.

---

**HU-05: Objeto personalizado Visita Médica**

> **Como** Visitador Médico,
> **quiero** registrar mis visitas con toda la información relevante,
> **para** mantener un historial completo de interacciones con cada médico.

**Criterios de Aceptación:**
- [ ] Objeto `Visita_Medica__c` creado con campos: Médico (lookup Contact), Fecha, Producto Ofrecido (lookup), Estado (picklist: Planificada / Ejecutada / Vencida), Comentarios (long text area).
- [ ] Layout de página configurado y asignado al perfil Visitador Médico.
- [ ] Objeto visible en la app VitaCore CRM como pestaña independiente.

---

**HU-06: Perfiles, Roles y Permisos**

> **Como** equipo de implementación,
> **quiero** definir perfiles y roles diferenciados,
> **para** que cada usuario acceda solo a lo que necesita según su función.

**Criterios de Aceptación:**
- [ ] Perfil "Visitador Médico" con acceso limitado a los objetos del CRM.
- [ ] Perfil "Gerencia" con acceso a reportes y tableros.
- [ ] Jerarquía de roles configurada: Dirección → Gerencia Comercial → Visitador Médico.
- [ ] Permission Sets creados para accesos adicionales puntuales sin modificar perfiles base.

**🛠️ Herramientas utilizadas:** Lightning App Builder · Profile Manager · Object Manager · Page Layout Editor · Themes & Branding · Role Hierarchy

---
```  

</details>

 
### Sprint 2 — Carga Masiva de Datos y Automatización

<details>
  <summary> Haga clic para ver las HU </summary>
    <br> 

```
#### Épica 3: Migración Masiva de Datos Históricos

---

**HU-07: Carga masiva de clínicas y médicos desde CSV**

> **Como** COO de VitaCore Labs,
> **quiero** que el historial del archivo `Maestro_Historico_2025.csv` sea importado al CRM,
> **para** no comenzar desde cero y contar con el contexto del último año desde el día uno.

**Criterios de Aceptación:**
- [ ] Mapeo de columnas CSV definido: columna = campo, fila = registro, hoja = objeto.
- [ ] Carga realizada con **Data Loader** en el orden correcto: Accounts → Contacts → Visitas Médicas.
- [ ] Cero duplicados gracias a Matching Rules y Duplicate Rules configuradas.
- [ ] Cada médico queda vinculado automáticamente a su hospital correspondiente.
- [ ] Prueba inicial realizada en Developer Org antes de la carga definitiva.

---

**HU-08: Reglas de deduplicación y calidad de datos**

> **Como** equipo de implementación,
> **quiero** configurar reglas de duplicados y matching,
> **para** garantizar que los datos históricos y futuros ingresen limpios y sin repeticiones.

**Criterios de Aceptación:**
- [ ] Matching Rules configuradas para Cuentas (nombre institución) y Contactos (nombre + email).
- [ ] Duplicate Rules en modo "Bloquear" para registros idénticos.
- [ ] Reporte de errores del Data Loader revisado y resuelto antes de aprobar la carga.

---

#### Épica 4: Automatización de Procesos Comerciales

---

**HU-09: "Botón de pánico" para registro rápido de visitas**

> **Como** Visitador Médico,
> **quiero** un asistente simple de 3 pasos para registrar una visita desde mi celular,
> **para** no perder tiempo navegando por pantallas cuando salgo de un consultorio.

**Criterios de Aceptación:**
- [ ] Screen Flow de 3 pantallas: (1) ¿A quién visité? → lookup Contact. (2) ¿Qué le ofrecí? → lookup Producto Farma. (3) ¿Cómo me fue? → campo Resultado / Comentarios.
- [ ] Al guardar, el Flow crea automáticamente el registro en `Visita_Medica__c`.
- [ ] Botón visible en la Home Page y accesible desde la app móvil de Salesforce.
- [ ] Testeado en Salesforce Mobile App con usuarios del perfil Visitador Médico.

---

**HU-10: Actualización automática de "Fecha de Última Visita"**

> **Como** COO de VitaCore,
> **quiero** que al guardar una visita el sistema actualice automáticamente la ficha del médico,
> **para** siempre saber cuándo fue el último contacto sin buscar en el historial.

**Criterios de Aceptación:**
- [ ] Record-Triggered Flow en objeto `Visita_Medica__c`, trigger: After Save (nuevo registro).
- [ ] El Flow navega al Contacto relacionado y actualiza `Fecha_Ultima_Visita__c` con la fecha actual.
- [ ] Proceso 100% automático, sin intervención del visitador médico.

---

**HU-11: "Guardián de los Lunes" — auditoría programada**

> **Como** COO de VitaCore,
> **quiero** que cada lunes a las 8:00 AM el sistema revise las visitas pendientes de la semana anterior,
> **para** marcarlas como vencidas automáticamente y mantener la agenda limpia.

**Criterios de Aceptación:**
- [ ] Scheduled Flow configurado para ejecutarse todos los lunes a las 08:00 AM.
- [ ] El Flow filtra Visitas con Estado = "Abierto" o "Pendiente" y fecha anterior a hoy - 7 días.
- [ ] Actualiza el campo Estado a "Vencida" en cada registro encontrado.
- [ ] Opcionalmente envía notificación al gerente con el conteo de visitas vencidas.

**🛠️ Herramientas utilizadas:** Data Loader · Screen Flow · Record-Triggered Flow · Scheduled Flow · Matching Rules · Duplicate Rules

---
```  

</details>
 
### Sprint 3 — Reportes y Tableros de Gestión

<details>
  <summary> Haga clic para ver las HU </summary>
    <br> 

```
#### Épica 5: Inteligencia Comercial — Reportes y Tableros

---

**HU-12: Tablero de Ventas para la Gerencia**

> **Como** COO de VitaCore,
> **quiero** un tablero de ventas con métricas clave en tiempo real,
> **para** tomar decisiones sin depender de informes manuales enviados por correo.

**Criterios de Aceptación:**
- [ ] Ranking de actividad: Top 5 visitadores con más visitas ejecutadas del mes (gráfico de barras).
- [ ] Cobertura de mercado: médicos registrados por especialidad (gráfico de torta/anillo). Objeto: Contact · Campo: Especialidad · Filtro: Todos los médicos activos.
- [ ] Producto estrella: medicamento más promocionado en visitas (gráfico de barras). Objeto: Visita_Medica__c · Campo: Producto_Ofrecido__c · Filtro: Estado = Ejecutada.
- [ ] Comparativo mensual: visitas realizadas vs. planificadas (gráfico combinado).
- [ ] Tablero disponible en la sección "Ventas" del home gerencial.

---

**HU-13: Tablero de Auditoría de Calidad**

> **Como** COO de VitaCore,
> **quiero** un tablero de auditoría que detecte problemas de calidad de datos,
> **para** identificar y corregir el trabajo incompleto de los visitadores.

**Criterios de Aceptación:**
- [ ] Reporte de visitas sin comentarios (campo Comentarios vacío).
- [ ] Reporte de visitas sin producto asociado (campo Producto_Ofrecido__c nulo).
- [ ] Lista de alerta: médicos sin visita en los últimos 90 días (cruce entre Contact y Visita_Medica__c).
- [ ] Todo agrupado en un tablero "Auditoría de Calidad" con acceso restringido a Gerencia.

---

**HU-14: Tablero "Mi Desempeño" para el Visitador Médico**

> **Como** Visitador Médico,
> **quiero** ver mis propias métricas de desempeño,
> **para** hacer seguimiento a mis metas sin necesitar pedir informes a mi gerente.

**Criterios de Aceptación:**
- [ ] Tablero filtrado por "Mis registros" para mostrar solo los datos del usuario activo.
- [ ] KPIs visibles: total de visitas del mes, visitas ejecutadas vs. planificadas, médicos activos en cartera.
- [ ] Tablero accesible desde la Home Page del Visitador Médico.

**🛠️ Herramientas utilizadas:** Report Builder · Dashboard Builder · Report Types personalizados · Filtros de reporte · Sharing Settings

---
```  

</details>

### Sprint 4 — Portal Interactivo en Experience Cloud
<details>
  <summary> Haga clic para ver las HU </summary>
    <br> 

```
#### Épica 6: Portal del Paciente en Experience Cloud

---

**HU-15: Configuración del sitio Experience Cloud VitaCore**

> **Como** equipo de implementación,
> **quiero** crear y configurar un sitio en Experience Cloud,
> **para** exponer datos del CRM de forma segura y ofrecer autoservicio al paciente o médico externo.

**Criterios de Aceptación:**
- [ ] Sitio Experience Cloud creado con template LWR o Customer Service.
- [ ] Theme configurado con identidad visual de VitaCore (colores `#005b96` y `#28a745`, logo, tipografía).
- [ ] Estructura de páginas definida: Home, Artículos, Formulario de Consulta, Mis Turnos.
- [ ] Guest User Profile configurado con permisos mínimos necesarios (principio de menor privilegio).

---

**HU-16: Formulario de consulta médica — Screen Flow público**

> **Como** paciente de VitaCore,
> **quiero** completar un formulario de consulta desde el portal sin necesitar login,
> **para** solicitar información o reintegros de forma autónoma sin llamar al laboratorio.

**Criterios de Aceptación:**
- [ ] Screen Flow con 3 pantallas: (1) Datos de contacto, (2) Motivo de consulta / carga de archivo, (3) Confirmación.
- [ ] Al guardar, el Flow crea un Caso (Case) en Salesforce asignado al equipo de soporte.
- [ ] Guest User Profile tiene permiso Create en objeto Case y puede ejecutar el Flow.
- [ ] El Flow está marcado como disponible para usuarios invitados en sus propiedades.
- [ ] Componente estándar "Flow" insertado en la página del portal desde Experience Builder.

---

**HU-17: Base de conocimiento (Knowledge) en el portal**

> **Como** paciente de VitaCore,
> **quiero** acceder a artículos informativos sobre medicamentos y bienestar desde el portal,
> **para** resolver mis dudas sin necesitar contactar directamente al laboratorio.

**Criterios de Aceptación:**
- [ ] Salesforce Knowledge habilitado y configurado con al menos 2 tipos de artículo (FAQ, Instructivo).
- [ ] Artículos publicados y visibles para usuarios invitados en el portal.
- [ ] Componente de búsqueda de artículos integrado en la Home del portal.

---

**HU-18: Seguridad y permisos del usuario invitado**

> **Como** Tech Lead de la implementación,
> **quiero** que los permisos del Guest User Profile estén correctamente definidos,
> **para** garantizar que los usuarios públicos solo puedan crear registros autorizados sin acceder a datos internos del CRM.

**Criterios de Aceptación:**
- [ ] Guest Profile tiene acceso Create-only en objeto Case. Sin acceso a Account, Contact ni Visita_Medica__c.
- [ ] Field-level security revisada: solo los campos necesarios del Case son visibles al invitado.
- [ ] Screen Flow público configurado con la opción "Available for Guest Users" activada.
- [ ] Prueba de seguridad realizada en modo incógnito para validar el comportamiento del usuario no autenticado.

**🛠️ Herramientas utilizadas:** Experience Cloud · Experience Builder · Screen Flow (público) · Salesforce Knowledge · Guest User Profile · LWR Template · Sharing Rules

---
```  

</details>
<br>
  
## 📁**ETAPA 1: Construcción en Developer Org**

#### **Modelado de datos**
```
Account (Hospital / Clínica)
│
├── Contact (Médico Especialista)
│     ├── Especialidad (picklist)
│     ├── Fecha_Ultima_Visita__c (date)
│     └── Lookup → Account
│
├── Visita_Medica__c (Objeto Personalizado)
│     ├── Medico__c (lookup → Contact)
│     ├── Producto_Ofrecido__c (lookup → Producto_Farma__c)
│     ├── Estado__c (picklist: Planificada / Ejecutada / Vencida)
│     ├── Fecha_Visita__c (date)
│     └── Comentarios__c (long text area)
│
└── Producto_Farma__c (Objeto Personalizado)
      ├── Nombre_Comercial__c (text)
      ├── Categoria__c (picklist)
      └── Principio_Activo__c (text)
```


<p align="center">
  <kbd> <img width="800" alt="eer" src="https://github.com/litahu/Salesforce_Admin/blob/main/resource_sfadmin/sprint1_adminsales.PNG"></kbd> <br>
</p>

<br>
  
## 📁**ETAPA 2: Migración, calidad de datos y reportería**


<p align="center">
  <kbd> <img width="800" alt="eer" src="https://github.com/litahu/Salesforce_Admin/blob/main/resource_sfadmin/sprint_2_sales_admin.PNG"></kbd> <br>
</p>

<br>
  
## 📁**ETAPA 3: Automatización y reportería**


<p align="center">
  <kbd> <img width="800" alt="eer" src="https://github.com/litahu/Salesforce_Admin/blob/main/resource_sfadmin/sprint3_adminsales.PNG"></kbd> <br>
</p>

<p align="center">
  <a href="https://drive.google.com/file/d/1CotmTgXQKgvfI75MK0KpXVGWM8ugF24I/view?usp=sharing" style="font-size:18px; font-weight:bold;">🔗 Ver demo</a>
</p>

<br>
  
## 📁**ETAPA 4: Portal Experience Cloud**

<p align="center">
  <kbd> <img width="800" alt="eer" src="https://github.com/litahu/Salesforce_Admin/blob/main/resource_sfadmin/sprint4_adminforce.PNG"></kbd> <br>
</p>

<br>

## **🏆 Impacto del Proyecto** <br>
- **1000+** : Registros históricos migrados con Data Import Wizard en carga masiva automatizada. 
- **360** : Visibilidad comercial en tiempo real para la dirección ejecutiva.
- **Reducción de 25 % en los tiempos de operación** : Eliminé tareas manuales del equipo de campo a través de 3 Flujos automáticos. 

<br>
  
## **✒ Autor** <br>
**Licencia** : Este proyecto está bajo la Licencia (Lita's Project).
* **Lita Huánuco Medina** -  [Lita Hume](https://www.linkedin.com/in/litahumedata/)

<br>
  
## **🎁 Expresiones de Gratitud** <br>
- **Guayerd y Cooperación Alemana** : Mi profundo agradecimiento por la oportunidad de formación y por brindarme las herramientas técnicas para dominar el ecosistema de Salesforce. Gracias a su apoyo, hoy manejo con confianza herramientas como Object Manager, Lightning App Builder, Flow Builder, Data Import Wizard, Dashboard y Chat Híbrido(Chatbot + Chatlive con agente). Estas competencias han sido el motor de mi evolución en el ecosistema Salesforce. Infinitas gracias 🤍<br>
  
- **Mentores** : Un agradecimiento especial a **Anita, Rebeca y Pablo**, quienes me guiaron con paciencia y sabiduría para levantar este proyecto desde sus cimientos, ¡Se logró! Sus consejos fueron la brújula en los momentos de duda, recordándome siempre una máxima: "Confíen en el proceso". Mis mejores deseos en todos sus emprendimientos ✨<br>
  
- **Familia** : Gracias por ser mi soporte incondicional y mi fuente de motivación. Su paciencia durante las horas de estudio y su fé en mis capacidades fueron el combustible necesario para llegar a la meta. Este logro es tan mío como de ustedes ❤ <br>

Gracias por leer hasta el final! 📢



