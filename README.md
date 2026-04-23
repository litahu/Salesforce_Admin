# **"VitalCore CRM" - Implementación Salesforce**

Este proyecto demuestra el ciclo completo de una implementación Salesforce: desde el levantamiento de requerimientos y el modelado de datos, hasta la automatización de procesos, la inteligencia comercial con reportes y tableros, y la apertura al mundo exterior mediante un portal interactivo en Experience Cloud para VitaCore Labs.<br>

#### **🧰 Stack Tecnológico aplicados** <br>
- **Salesforce Sales Cloud** : Object Manger, Lightning App Builder, Profile Manager, Page Layout Editor, Flow Builder, Data Loader, Report Builder y Themes & Branding. [Ver](https://www.salesforce.com/trailblazer/litahume)<br>

- **Salesforce Experience Cloud** : Experience Builder, Salesforce Knowledge, Guest User Profile, Omnicanalidad y Screen Flow público integrado al portal. [Ver](https://trailhead.salesforce.com/es-MX/content/learn/projects/build-a-community-with-knowledge-and-chat)<br>

- **Viewer** : Relevo de requerimientos junto a áreas comerciales y técnicas.[Ver](https://vita-murex.vercel.app/)<br>

El proyecto fue desarrollado en 4 Sprints reales siguiendo buenas prácticas de configuración declarativa en Salesforce:
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


## 📁**ETAPA 2: Migración, calidad de datos y reportería**


<p align="center">
  <kbd> <img width="800" alt="eer" src="https://github.com/litahu/Salesforce_Admin/blob/main/resource_sfadmin/sprint_2_sales_admin.PNG"></kbd> <br>
</p>

## 📁**ETAPA 3: Automatización y reportería**


<p align="center">
  <kbd> <img width="800" alt="eer" src="https://github.com/litahu/Salesforce_Admin/blob/main/resource_sfadmin/sprint3_adminsales.PNG"></kbd> <br>
</p>

## 📁**ETAPA 4: Portal Experience Cloud**

<p align="center">
  <kbd> <img width="800" alt="eer" src="https://github.com/litahu/Salesforce_Admin/blob/main/resource_sfadmin/sprint4_adminforce.PNG"></kbd> <br>
</p>






