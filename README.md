# **"VitalCore CRM" - Implementación Salesforce**

#### **🧰 Stack Tecnológico aplicados** <br>
- **Salesforce Sales Cloud** : Object Manger, Lightning App Builder, Profile Manager, Page Layout Editor, Flow Builder, Data Loader, Report Builder y Themes & Branding. [Ver](https://www.salesforce.com/trailblazer/litahume)<br>

- **Salesforce Experience Cloud** : Experience Builder, Salesforce Knowledge, Guest User Profile, Omnicanalidad y Screen Flow público integrado al portal. [Ver](https://trailhead.salesforce.com/es-MX/content/learn/projects/build-a-community-with-knowledge-and-chat)<br>
<br>

- **Viewer** : Relevo de requerimientos junto a áreas comerciales y técnicas.[Ver](https://vita-murex.vercel.app/)<br>

<br>
<br>

#### **📋 Descripción del Proyecto**
Proyecto de implementación de Salesforce CRM para VitaCore Labs, un laboratorio farmacéutico B2B con equipo de visitadores médicos que gestiona relaciones comerciales con hospitales, clínicas y médicos especialistas.
El proyecto fue desarrollado en 4 Sprints reales, gestionando requerimientos del cliente, construyendo soluciones de extremo a extremo y siguiendo buenas prácticas de configuración declarativa en Salesforce

```
Industria
Sector Salud — Laboratorio Farmacéutico B2B
VitaCore Labs es un laboratorio farmacéutico que opera con un equipo de visitadores médicos responsables
de gestionar relaciones con clínicas, hospitales y médicos especialistas a lo largo del territorio.
```

## 📁**ETAPA 0: Enunciado del problema**

VitaCore Labs es un laboratorio farmacéutico B2B con equipo de visitadores médicos que gestiona
relaciones comerciales con hospitales, clínicas y médicos especialistas.

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

## 📁**ETAPA 1: Toma de  requerimientos**
Se realizo un levantamiento de requerimientos en historias de usuario, para la gestion de la solución en metodologias agiles

<p align="center">
  <kbd> <img width="800" alt="eer" src="https://github.com/litahu/Seguimiento_de_ventas/blob/main/Assets/final_inform.PNG"></kbd> <br>
</p>

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



