Esta es la versión final, profesional y "limpia" de la propuesta. He corregido los errores de redacción, eliminado las notas internas, blindado los puntos de costos de AWS y hardware, y estructurado los reportes para la Propuesta B.

---

# PROPUESTA DE DESARROLLO: SISTEMA DE GESTIÓN DE IDENTIDAD QR

**Preparado para:** Bryan Mayanga

**Elaborado por:** Diego A. Ladron de Guevara Aguirre, Carla Noelia Aguirre Mayanga, Leonardo Ordeñez Lopez

**Fecha:** 22 de febrero de 2026

---

## 1. Visión General del Proyecto

El objetivo es desarrollar una plataforma tecnológica robusta que permita la creación, gestión y visualización de perfiles de emergencia mediante códigos QR únicos. El sistema utiliza una arquitectura de **Nube Serverless (AWS)** para garantizar que sea escalable, seguro y de bajo costo operativo.

---

## 2. Infraestructura Cloud y Costos

Se utilizará la nube de **Amazon Web Services (AWS)** para garantizar estabilidad y seguridad de nivel bancario.

* **Costos Variables:** El sistema se basa en el consumo real. Se estima un costo mensual inicial bajo (aprox. **S/ 30.00 – S/ 80.00**), sujeto al tráfico y volumen de datos. Si no hay uso, el costo tiende a cero.
* **Propiedad y Control:** El cliente realizará la apertura de su cuenta AWS y el registro de su método de pago. El cliente es el titular único de los datos y responsable del acceso administrativo y custodia de sus credenciales.
* **Notificaciones:** Se integrará **AWS SES** para el envío de alertas automáticas por correo electrónico con costos mínimos por volumen.

---

## 3. PROPUESTA A: "MVP OPERATIVO + PANEL ADMIN"

*Ideal para lanzar el negocio en el corto plazo con control total y ventas presenciales.*

### **¿Cómo funcionará el sistema?**

1. **Captación:** Registro de datos del usuario (niño, mascota, etc.) desde una tablet o PC.
2. **Generación:** Creación de un código QR único vinculado a la información.
3. **Fabricación:** Descarga del QR en formato de imagen para impresión manual.
4. **Visualización:** Al escanear el QR, se mostrará una **Cartilla Informativa** con: nombre, edad, sexo, características físicas, correo del representante y botón de contacto directo a WhatsApp.
5. **Alertas de Vencimiento:** Notificación automática diaria al administrador sobre suscripciones próximas a expirar.

### **Panel Administrativo (Backoffice):**

* **Gestión de Roles:**
* **Super-Admin:** Acceso total, gestión de administradores y métricas sensibles.
* **Operador:** Registro de usuarios, activación de QRs y descargas para impresión.


* **Gestión de Usuarios:** Buscador inteligente (DNI, Nombre, QR) y botón de **Desactivación Instantánea (Kill-Switch)** para anular QRs por falta de pago o pérdida.
* **Centro de Generación:** Formulario individual, previsualización del QR y cola de gestión para control de impresión manual.
* **Control de Suscripciones:** Semáforo de estados (Verde: Activo / Ámbar: Próximo a vencer / Rojo: Vencido/Bloqueado).
* **Seguridad:** Log de auditoría (quién hizo qué), historial de renovaciones e integración con **AWS Cognito** (opción de 2FA).

### **Inversión y Tiempo:**

* **Tiempo:** 4 a 6 semanas (Dedicación 8h diarias).
* **Inversión Preferencial:** **S/ 5,500.00**

---

## 4. PROPUESTA B: "SAAS PRO"

*Solución avanzada para escala de marca, pagos automáticos e inteligencia de negocio.*

### **Alcance Adicional a la Propuesta A:**

1. **Dominio Propio (Marca):** Configuración de URL personalizada (Ej: `www.tumarca.pe`).
2. **Pasarela de Pagos:** Integración para cobros automáticos (Culqi/Mercado Pago) y activación inmediata de servicios.
3. **Módulo de Reportes (Estadísticas):**
* Gráficos de nuevos registros y renovaciones mensuales.
* Métricas de interacción (cantidad de escaneos por zona o perfil).
* Reportes exportables para gestión contable.


4. **Automatización de Notificaciones:** Correos automáticos de recordatorio dirigidos **tanto al administrador como al cliente final**.

### **Inversión y Tiempo:**

* **Tiempo:** 8 a 12 semanas.
* **Inversión Preferencial:** **S/ 6,500.00**
* *Nota: Costos de dominio (.pe S/ 110/año aprox.) y comisiones de pasarela son cubiertos por el cliente.*

---

## 5. Requisitos de Hardware (Tablets)

Para garantizar el correcto funcionamiento del panel en el punto de venta:

* **Conectividad (Obligatoria):** Internet estable (Wi-Fi o 4G/5G). El sistema depende de la nube.
* **Pantalla Recomendada:** 10.1 pulgadas o superior.
* **Memoria RAM:** 4 GB o superior.
* **Sistema Operativo:** Android 11+ o iPadOS 15+.
* **Navegador:** Google Chrome actualizado.

---

## 6. Comparativa Técnica

| Función | Propuesta A (MVP) | Propuesta B (SaaS Pro) |
| --- | --- | --- |
| **Arquitectura** | AWS Serverless | AWS Serverless |
| **Dominio** | URL Genérica | **Propio (Tu Marca)** |
| **Pagos** | Registro Manual | **Automatizados (Online)** |
| **Alertas Vencimiento** | Solo al Administrador | **Admin y Cliente Final** |
| **Estadísticas** | Básicas | **Avanzadas y Exportables** |

---

## 7. Cronograma de Trabajo

* **Semana 1:** Configuración de AWS, Seguridad y Base de Datos.
* **Semana 2:** Formulario de registro y Visualización de Cartilla.
* **Semana 3:** Panel Administrativo y Generador de QR.
* **Semana 4:** Sistema de Alertas, pruebas finales y despliegue.

---

## **ANEXO TÉCNICO: ESTIMACIÓN DE COSTOS AWS (NUBE)**

El sistema utiliza una arquitectura **Serverless**, lo que permite que los costos operativos sean proporcionales al uso real del negocio. A continuación, se presenta una estimación de gastos mensuales basada en la calculadora oficial de AWS, proyectada en tres niveles de crecimiento:

### **1. Proyección de Gastos Mensuales por Escenario**

| Servicio | Función | Escenario 1 (Inicio) | Escenario 2 (Crecimiento) | Escenario 3 (Escala) |
| --- | --- | --- | --- | --- |
|  | **Volumetría estimada** | *1,000 registros / 5,000 escaneos* | *10,000 registros / 50,000 escaneos* | *50,000 registros / 250,000 escaneos* |
| **AWS Lambda** | Procesamiento y lógica | S/ 0.00* | S/ 0.50 | S/ 4.00 |
| **DynamoDB** | Base de Datos segura | S/ 1.00 | S/ 5.00 | S/ 15.00 |
| **API Gateway** | Conexión Tablet <> Nube | S/ 0.40 | S/ 4.00 | S/ 20.00 |
| **AWS Cognito** | Seguridad y Logins | S/ 0.00* | S/ 0.00* | S/ 10.00 |
| **AWS SES** | Envío de Alertas (Email) | S/ 0.50 | S/ 4.00 | S/ 18.00 |
| **S3 / CloudFront** | Almacenamiento y Velocidad | S/ 1.10 | S/ 9.00 | S/ 35.00 |
| **Monitoreo** | Logs y seguridad activa | S/ 2.00 | S/ 10.00 | S/ 25.00 |
| **TOTAL ESTIMADO** |  | **S/ 5.00 – S/ 10.00** | **S/ 35.00 – S/ 50.00** | **S/ 130.00 – S/ 180.00** |

### **2. Notas Importantes sobre el Pago de Nube**

* **Eficiencia Operativa:** El costo de infraestructura solo aumenta si el negocio crece y genera más registros. Si un mes no hay actividad, el costo se reduce al mínimo técnico (cercano a S/ 0.00).
* **Transparencia:** El pago se realiza directamente de la tarjeta del cliente a Amazon Web Services. No existen intermediarios en este cobro.
* **Seguridad Financiera:** Como parte de la configuración inicial, activaremos **"Alertas de Presupuesto"**. Esto significa que Amazon te enviará un correo automático si el consumo mensual llegara a superar un monto límite establecido por ti (ejemplo: S/ 50.00), dándote control total sobre el gasto.

---

## 9. Próximos Pasos

Para iniciar con la **Opción 1**:

1. **Aceptación:** Creación y firma de los contratos.
2. **Configuración:** Sesión de 30 min - 1 hora para apertura de cuenta AWS.
3. **Inicio:** Abono del **50% de adelanto (S/ 2,750.00) o (S/ 3,250.00)** para comenzar el desarrollo.
