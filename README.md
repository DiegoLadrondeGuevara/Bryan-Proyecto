# PROPUESTA DE DESARROLLO: SISTEMA DE GESTIÓN DE IDENTIDAD QR

**Preparado para:** Bryan Mayanga

**Elaborado por:** Diego A. Ladron de Guevara Aguirre, Carla Noelia Aguirre Mayanga, Leonardo Ordeñez Lopez

**Fecha:** 22 de febrero de 2026

---

## 1. Visión General del Proyecto

El objetivo es desarrollar una plataforma tecnológica robusta que permita la creación, gestión y visualización de perfiles de emergencia mediante códigos QR únicos. El sistema utiliza una arquitectura de **Nube Serverless (AWS)** para garantizar que sea escalable, seguro y de bajo costo operativo.

---

## 2. Infraestructura Cloud y Costos

Se utilizará la nube de **Amazon Web Services (AWS)** para garantizar estabilidad y estándares de seguridad empresarial.

* **Costos Variables:** El sistema se basa en el consumo real. Se estima un costo mensual inicial bajo (aprox. **S/ 30.00 – S/ 80.00**), sujeto al tráfico y volumen de datos. Si la actividad es baja, los costos se reducen significativamente.
* **Propiedad y Control:** El cliente realizará la apertura de su cuenta AWS y el registro de su método de pago. El cliente es el titular único de los datos y responsable del acceso administrativo y custodia de sus credenciales.
* **Notificaciones:** Se integrará **AWS SES** para el envío de alertas automáticas por correo electrónico con costos mínimos por volumen.

---

## 3. PROPUESTA A: "MVP OPERATIVO + PANEL ADMIN"

*Ideal para lanzar el negocio en el corto plazo con control total y ventas presenciales.*

### **¿Cómo funcionará el sistema?**

1. **Captación:** Registro de datos del usuario (niño, mascota, etc.) desde una tablet o PC.
2. **Generación:** Creación de un código QR único vinculado a la información.
3. **Fabricación:** Descarga del QR en formato de imagen para impresión manual.
4. **Visualización:** Al escanear el QR, se mostrará una **Cartilla Informativa** con: nombre o alias, características relevantes y botón de contacto directo a WhatsApp.
5. **Dominio Propio (Marca):** Configuración de URL personalizada (Ej: `www.tumarca.pe`).
6. **Alertas de Vencimiento:** Notificación automática diaria al administrador y al usuario que compra el servicio sobre suscripciones próximas a expirar.

### **Panel Administrativo (Backoffice):**

* **Gestión de Roles:**
* **Super-Admin:** Acceso total, gestión de administradores y métricas sensibles.
* **Operador:** Registro de usuarios, activación de QRs y descargas para impresión.


* **Gestión de Usuarios:** Buscador inteligente (DNI, Nombre, QR) y botón de **Desactivación Instantánea (Kill-Switch)** para anular QRs por falta de pago o pérdida.
* **Centro de Generación:** Formulario individual, previsualización del QR y cola de gestión para control de impresión manual.
* **Control de Suscripciones:** Semáforo de estados (Verde: Activo / Ámbar: Próximo a vencer / Rojo: Vencido/Bloqueado).
* **Seguridad:** Log de auditoría (quién hizo qué), historial de renovaciones e integración con **AWS Cognito** (opción de 2FA).

### **Inversión y Tiempo:**

* **Tiempo:** 6 a 8 semanas (Dedicación 8h diarias).
* **Inversión:** **S/ 6,500.00**

---

## 5. Requisitos de Hardware (Tablets)

Para garantizar el correcto funcionamiento del panel en el punto de venta:

* **Conectividad (Obligatoria):** Internet estable (Wi-Fi o 4G/5G). El sistema depende de la nube.
* **Pantalla Recomendada:** 10.1 pulgadas o superior.
* **Memoria RAM:** 4 GB o superior.
* **Sistema Operativo:** Android 11+ o iPadOS 15+.
* **Navegador:** Google Chrome actualizado.

---

## 6. Cronograma de Trabajo

**Semana 1: Cimientos y Configuración Cloud**

* Apertura y configuración de la cuenta **AWS** del cliente.
* Configuración de seguridad y autenticación con **AWS Cognito**.
* Diseño y despliegue de la arquitectura de base de datos en **DynamoDB**.
* Configuración del entorno de desarrollo y repositorio.

**Semana 2: Visualización y Perfiles (Cartilla)**

* Desarrollo de la interfaz de la **Cartilla Informativa** (perfil público).
* Implementación de la lógica de visualización (datos de emergencia y contacto).
* Integración del botón de contacto directo a **WhatsApp**.
* Pruebas de visualización en dispositivos móviles y tablets.

**Semana 3: Panel Administrativo y Registro**

* Desarrollo del panel de gestión (Backoffice) para administradores.
* Creación del formulario de captación y registro de usuarios (niños, mascotas, etc.).
* Implementación del **Buscador Inteligente** por DNI, nombre o código.
* Configuración de roles: Super-Admin y Operador.

**Semana 4: Generación de QR y Dominio**

* Desarrollo del motor de generación de **códigos QR únicos**.
* Implementación de la función de descarga de QR en formato de imagen para impresión.
* Configuración y vinculación del **Dominio Propio** (Ej: `www.tumarca.pe`).
* Pruebas de escaneo y redirección desde el dominio personalizado.

**Semana 5: Suscripciones y Seguridad**

* Implementación del sistema de control de estados (Semáforo: Activo / Por vencer / Vencido).
* Desarrollo del botón de desactivación instantánea (**Kill-Switch**).
* Configuración de **AWS SES** para el envío de alertas automáticas por correo al administrador.
* Activación del Log de auditoría (historial de cambios y registros).

**Semana 6: Pruebas Finales, Ajustes y Despliegue**

* Pruebas de estrés y seguridad en toda la plataforma.
* Ajustes de interfaz de usuario (UX/UI) basados en pruebas reales en tablet.
* Configuración de **Alertas de Presupuesto** en AWS para control de costos.
* Lanzamiento oficial (Go-Live) y entrega de credenciales.

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

#### **Notas Importantes sobre el Pago de Nube**

* **Eficiencia Operativa:** El costo de infraestructura solo aumenta si el negocio crece y genera más registros. Si un mes no hay actividad, el costo se reduce proporcionalmente.
* **Transparencia:** El pago se realiza directamente de la tarjeta del cliente a Amazon Web Services. No existen intermediarios en este cobro.
* **Seguridad Financiera:** Como parte de la configuración inicial, activaremos **"Alertas de Presupuesto"**. Esto significa que Amazon te enviará un correo automático si el consumo mensual llegara a superar un monto límite establecido por ti (ejemplo: S/ 50.00), dándote control total sobre el gasto.

---
### 2. Precios por Extensión (Anual) (Dominio)

| Extensión | Tipo | Precio Promedio (Soles) | Nota |
| --- | --- | --- | --- |
| **.pe** | Dominio Nacional | **S/ 110 – S/ 130** | Es el más prestigioso para el mercado local. |
| **.com.pe** | Comercial Perú | **S/ 80 – S/ 110** | Muy usado por empresas peruanas. |
| **.com** | Internacional | **S/ 50 – S/ 80** | El estándar global; suele ser el más económico. |
| **.net / .org** | Alternativos | **S/ 60 – S/ 90** | Para tecnología u organizaciones. |
| **.org.pe** | Org. Peruana | **S/ 20 – S/ 40** | Precio especial para ONGs. |

### 2. Consideraciones Importantes

* **IGV:** Ten en cuenta que la mayoría de proveedores locales no incluyen el **18% de IGV** en sus precios de lista.
* **Ofertas de "Primer Año":** Muchos registradores ofrecen el primer año a un precio muy bajo (ej. **S/ 1.00** o **S/ 15.00**), pero la renovación al segundo año sube al precio regular. **Fíjate siempre en el costo de renovación.**
* **Punto.pe:** Es el administrador oficial de los dominios `.pe` en el país. Si compras directamente ahí, el precio es estándar (**S/ 110.00**), mientras que los revendedores pueden cobrar una comisión por gestión o darte descuentos si contratas hosting con ellos.

---

## 7. Protocolo de Aceptación de Entregables y Garantía

Para garantizar la transparencia y el cumplimiento de los tiempos, el proceso de entrega se regirá bajo las siguientes condiciones:

* **Validación por Hitos:** Al finalizar cada semana (según el cronograma), el cliente revisará los avances. El silencio administrativo tras **48 horas** de presentado un avance se considerará como aceptado para proceder con la siguiente etapa.
* **Cierre de Alcance (MVP):** La inversión de **S/ 6,500.00** cubre exclusivamente las funcionalidades descritas en esta propuesta. Cualquier funcionalidad adicional, cambio de diseño estructural o integración externa no mencionada se cotizará como un **"Add-on"** independiente.
* **Periodo de Marcha Blanca (Garantía):** Una vez realizado el despliegue final (Semana 6), se otorgará un periodo de **15 días calendario** de soporte técnico gratuito. Este soporte cubre exclusivamente:
* Corrección de errores (bugs) en el código desarrollado.
* Ajustes menores de textos o colores en la interfaz.


* **Exclusiones de Garantía:** No se incluyen daños causados por manipulación indebida de las credenciales de AWS por parte del cliente, falta de pago en los servicios de la nube (Amazon) o vencimiento del dominio.
* **Acta de Conformidad Final:** Al término de la Semana 6 y tras la entrega de las credenciales maestras, se firmará un acta de conformidad que dará por concluido el proyecto y habilitará el pago del **50% restante**.

## 8. Operación y Soporte Posterior (Mantenimiento)

Finalizado el periodo de garantía de 15 días, el cliente podrá asegurar la continuidad del sistema mediante las siguientes modalidades:

* **Plan de Mantenimiento Evolutivo (Opcional):**
* **Servicios:** Monitoreo de salud del sistema en AWS, mantenimiento preventivo de bases de datos, ajustes menores de interfaz y soporte técnico ante incidencias.
* **Inversión Mensual:** **S/ 350.00** (Costo referencial sujeto a volumen de tickets).

* **Soporte On-Demand:** De no contratar el plan mensual, cualquier requerimiento posterior a los 15 días de garantía se facturará como **"Hora Técnica"** con una tarifa de **S/ 80.00 por hora**.

## 9. Exclusiones Explícitas del Alcance

Para evitar el *scope creep* y cumplir con el cronograma, se declara que el presente MVP **NO incluye**:

* Integración con pasarelas de pago automáticas (el registro de activación es **100% manual** en el panel).
* Desarrollo de Aplicación Móvil nativa (el sistema es una Web App Responsiva).
* Integración directa con hardware de impresión (la descarga del QR para impresión es manual).
* Geolocalización automática en tiempo real del escaneo.
* Módulo Multi-empresa o Sub-franquicias.
* Analítica avanzada de Business Intelligence o reportes contables complejos.

## 10. Uso y Protección de Datos Personales

* **Responsabilidad de Datos:** El cliente (**Bryan Mayanga**) es el único responsable legal del tratamiento, consentimiento y uso de los datos personales registrados por los usuarios finales en la plataforma.
* **Privacidad por Diseño:** El sistema ha sido diseñado para no recolectar direcciones exactas ni geolocalización automática sin validación previa, minimizando los riesgos legales asociados a la privacidad.
* **Custodia de Credenciales:** Una vez entregadas las llaves de acceso (AWS Cognito y AWS Console), la seguridad y custodia de estas recae exclusivamente en el cliente.

---

## 11. Próximos Pasos

Para iniciar con la **Opción 1**:

1. **Aceptación:** Creación y firma de los contratos.
2. **Configuración:** Sesión de 30 min - 1 hora para apertura de cuenta AWS.
3. **Inicio:** Abono del **50% de adelanto (S/ 3,250.00)** para comenzar el desarrollo.
