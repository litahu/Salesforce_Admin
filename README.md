# **"VitalCore CRM - Implementación Salesforce**

**Viewer** : [Mi muro](https://vita-murex.vercel.app/)<br>

<br>
**Proyecto de automatización y digitalización comercial para VitaCore Labs**
El proyecto fue desarrollado en 4 Sprints reales, gestionando requerimientos del cliente, construyendo soluciones de extremo a extremo y siguiendo buenas prácticas de configuración declarativa en Salesforce.

## 📁**ETAPA 0: Enunciado del problema**

VitaCore Labs es un laboratorio farmacéutico B2B con equipo de visitadores médicos que gestiona relaciones comerciales con hospitales, clínicas y médicos especialistas.

```
Industria
**Sector Salud — Laboratorio Farmacéutico B2B**
---
VitaCore Labs es un laboratorio farmacéutico que opera con un equipo de visitadores médicos responsables de gestionar relaciones con clínicas, hospitales y médicos especialistas a lo largo del territorio.
```

```
El Desafío
**Operación dispersa, sin visibilidad ni automatización**
---
El cliente necesitaba centralizar la gestión comercial, eliminar el registro manual de visitas médicas y obtener visibilidad en tiempo real sobre el desempeño del equipo de campo y la cobertura de médicos.
```

```
La Solución
**CRM personalizado + Experience Cloud para autoservicio**
---
Implementación de Sales Cloud con objetos personalizados para visitas médicas, automatización de flujos con Screen Flows y Flow Builder, carga masiva de datos históricos, tableros de gestión y un portal interactivo para pacientes en Experience Cloud.
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




