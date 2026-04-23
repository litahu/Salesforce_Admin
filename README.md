# 🧰 **"VitalCore CRM" - Implementación Salesforce**

Este proyecto demuestra el ciclo completo de una implementación Salesforce: desde el levantamiento de requerimientos y el modelado de datos, hasta la automatización de procesos, la inteligencia comercial con reportes y tableros, y la apertura al mundo exterior mediante un portal interactivo en Experience Cloud para VitaCore Labs.<br>

### **Stack Tecnológico aplicados** <br>
- **Salesforce Sales Cloud** : Object Manger, Lightning App Builder, Profile Manager, Page Layout Editor, Flow Builder, Data Loader, Report Builder y Themes & Branding. [Ver](https://www.salesforce.com/trailblazer/litahume)<br>

- **Salesforce Experience Cloud** : Experience Builder, Salesforce Knowledge, Guest User Profile, Omnicanalidad y Screen Flow público integrado al portal. [Ver](https://trailhead.salesforce.com/es-MX/content/learn/projects/build-a-community-with-knowledge-and-chat)<br>

- **Viewer** : Relevo de requerimientos junto a áreas comerciales y técnicas.[Ver](https://vita-murex.vercel.app/)<br>

  
### Tabla de contenido <!-- omit in toc -->

El proyecto fue desarrollado en 4 Sprints reales siguiendo buenas prácticas de configuración declarativa en Salesforce:
- [ETAPA 0: Enunciado del problema](https://github.com/litahu/Salesforce_Admin?tab=readme-ov-file#etapa-0-enunciado-del-problema)
  - [Descripción del Proyecto](https://github.com/litahu/Salesforce_Admin?tab=readme-ov-file#descripción-del-proyecto)
  - [Levantamiento de requerimientos](https://github.com/litahu/Salesforce_Admin?tab=readme-ov-file#levantamiento-de-requerimientos)
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
- **Guayerd y Cooperación Alemana** : Mi profundo agradecimiento por la oportunidad de formación y por brindarme las herramientas técnicas para dominar el ecosistema de Salesforce. Gracias a su apoyo, hoy manejo con confianza herramientas como Object Manager, Lightning App Builder, Flow Builder, Data Loader y la creación de reportes y tableros personalizados. Estas competencias han sido el motor de mi evolución en el ecosistema Salesforce. Infinitas gracias 🤍<br>
  
- **Mentores** : Un agradecimiento especial a **Anita, Rebeca y Pablo**, quienes me guiaron con paciencia y sabiduría para levantar este proyecto desde sus cimientos, ¡Lo logramos! Sus consejos fueron la brújula en los momentos de duda, recordándome siempre una máxima: "Confíen en el proceso". Mis mejores deseos en todos sus emprendimientos ✨<br>
  
- **Familia** : Gracias por ser mi soporte incondicional y mi fuente de motivación. Su paciencia durante las horas de estudio y su fe en mis capacidades fueron el combustible necesario para llegar a la meta. Este logro es tan mío como de ustedes ❤ <br>

Gracias por leer hasta el final! 📢



