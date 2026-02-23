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

### **Definición Detallada del Panel Administrativo (Backoffice):**

El acceso al sistema está blindado por **AWS Cognito**, asegurando que cada usuario acceda solo a las funciones permitidas según su nivel:

#### **A. Módulo Super-Admin (Control Total)**

* **Gestión de Staff:** Panel para crear, suspender o eliminar cuentas de **Reclutadores**.
* Contador de perfiles: Activos, Vencidos y **Pendientes de Entrega**.
* Reporte de usuarios próximos a vencer (ventana de 7 días).
* **Kill-Switch Administrativo:** Bloqueo inmediato de la cartilla pública sin borrado de data (permite reactivación rápida tras pago).
* **Auditoría de Operaciones:** Registro histórico: *"El Reclutador X activó la suscripción del usuario Y el día Z"*.
* **Gestión de Logs:** Visualización de estadísticas de interacción (conteo de escaneos y horas de actividad).

#### **B. Módulo Reclutador (Ventas y Registro)**

* **Formulario de Registro y Pre-activación:** Registro de datos del usuario. Al guardar, el perfil se crea automáticamente en estado **"Pendiente de Entrega"**.
* *Nota: En este estado, la suscripción NO corre y el tiempo de servicio no se consume.*
* **Activación Manual de Suscripción:** Una vez que el cliente recibe su pulsera física con el QR, el Reclutador (o el Admin) presiona el botón **"Activar Servicio"**.
* **Acción:** El sistema registra la fecha actual como "Fecha de Inicio" y calcula automáticamente la fecha de vencimiento.
* **Buscador y Verificación:** Filtro por Nombre o ID para confirmar que la información en la cartilla es correcta antes de la entrega final.
* **Gestor de Salida (QR):** Generación y descarga de la imagen del código para su fabricación física.

#### **C. Interfaz de Cartilla (Vista del Usuario Final)**

Es la página optimizada para móviles que aparece al escanear el QR:

* **Estados de Visualización:**
1. **Estado Pendiente:** Si se escanea antes de la activación, mostrará: *"Tu servicio está en proceso de entrega. Pronto estará activo"*.
2. **Estado Activo:** Muestra el Layout limpio con nombre o alias, características relevantes y botón de contacto directo a WhatsApp.
3. **Estado Vencido/Bloqueado:** Muestra: *"Perfil no disponible actualmente. Contacte a soporte"*.
* **Footer de Soporte:** Enlace directo de "Soporte" que redirige al contacto oficial de administración (Bryan).

---

### **Implementación Técnica de Logs y Suscripción**

1. **Registro de Escaneos (Logs):** Se implementará un microservicio en **AWS Lambda + DynamoDB** que guardará el `ID_QR`, `Fecha/Hora` y `Tipo de dispositivo`. Esto permite al Admin ver en qué momentos hay más actividad.
2. **Lógica de Suscripción:** El campo `fecha_inicio` en la base de datos permanecerá nulo (`NULL`) hasta que se presione el botón de activación. Esto garantiza una facturación justa para el cliente y evita que el soporte técnico tenga que corregir fechas de vencimiento manualmente por retrasos en la entrega física.


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
* Implementación del **Buscador Inteligente** por ID. o nombre.
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

El cobro de los servicios de infraestructura se realiza en **Dólares (USD)**.

| Servicio | Función | Escenario 1 (Inicio) | Escenario 2 (Crecimiento) | Escenario 3 (Escala) |
| --- | --- | --- | --- | --- |
| **Volumetría** |  | *1,000 reg / 5,000 esc* | *10,000 reg / 50,000 esc* | *50,000 reg / 250,000 esc* |
| **AWS Lambda** | Procesamiento | $0.00 USD* | $0.15 USD | $1.10 USD |
| **DynamoDB** | Base de Datos | $0.27 USD | $1.40 USD | $4.10 USD |
| **API Gateway** | Conexión | $0.11 USD | $1.10 USD | $5.50 USD |
| **AWS Cognito** | Seguridad | $0.00 USD* | $0.00 USD* | $2.80 USD |
| **AWS SES** | Alertas Email | $0.14 USD | $1.10 USD | $5.00 USD |
| **S3 / CloudFront** | Almacenamiento | $0.30 USD | $2.50 USD | $9.60 USD |
| **Monitoreo** | Logs/Seguridad | $0.55 USD | $2.75 USD | $6.90 USD |
| **TOTAL USD** |  | **$1.37 – $2.75 USD** | **$9.00 – $14.00 USD** | **$35.00 – $49.00 USD** |

> **IMPORTANTE:** Para seguridad financiera, activaremos una **"Alerta de Presupuesto"** a los **$15.00 USD**. Amazon enviará un correo automático si el consumo proyectado supera este monto.

#### **Notas Importantes sobre el Pago de Nube**

* **Eficiencia Operativa:** El costo de infraestructura solo aumenta si el negocio crece y genera más registros. Si un mes no hay actividad, el costo se reduce proporcionalmente.
* **Transparencia:** El pago se realiza directamente de la tarjeta del cliente a Amazon Web Services. No existen intermediarios en este cobro.
* **Seguridad Financiera:** Como parte de la configuración inicial, activaremos **"Alertas de Presupuesto"**. Esto significa que Amazon te enviará un correo automático si el consumo mensual llegara a superar un monto límite establecido por ti (ejemplo: S/ 50.00), dándote control total sobre el gasto.

---
### 2. Precios por Extensión (Anual) (Dominio)

| **Extensión**                   | **Tipo**                | **Precio Promedio (Soles / USD)**                   | **Proveedor / Dónde comprar**                                                                                                        |
| ------------------------------- | ----------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **.pe**                         | Dominio Nacional        | **S/130 – S/200+** (~USD 35-55)                     | 🛒 **Hosting.pe** – registro directo en su web (dominios .pe y otros ccTLD) ([Hosting Perú][1])                                      |
|                                 |                         |                                                     | 🛒 **AltiplanoHost** – registro rápido de .pe y otras extensiones (USD ~29.90 primer año) ([AltiplanoHost Hosting y Dominios A1][2]) |
|                                 |                         |                                                     | 🛒 **DonDominio** – registrador internacional (aprox. €34.95/año) ([DonDominio][3])                                                  |
| **.com.pe**                     | Comercial Perú          | **S/130 – S/200+** (~USD 35-55)                     | 🛒 **Hosting.pe** – registro en su web de .com.pe ([Hosting Perú][1])                                                                |
|                                 |                         |                                                     | 🛒 **AltiplanoHost** – .com.pe desde USD 29.90 primer año ([AltiplanoHost Hosting y Dominios A1][2])                                 |
|                                 |                         |                                                     | 🛒 **Namecheap** – .com.pe desde ~$75.98 (precio estándar) ([Namecheap][4])                                                          |
| **.com**                        | Internacional           | **S/70 – S/90+** (~USD 15-20)                       | 🛒 **Hosting.pe** – .com disponible en su buscador ([Hosting Perú][1])                                                               |
|                                 |                         |                                                     | 🛒 **Namecheap** / **Hostinger** / **Google Domains** – dominio .com estándar a nivel mundial                                        |
| **.net / .org**                 | Alternativos            | **S/60 – S/90** (~USD 15-20)                        | 🛒 **Hosting.pe** – .net y .org también se ofrecen ([Hosting Perú][1])                                                               |
|                                 |                         |                                                     | 🛒 **Namecheap** – .net / .org registro internacional estándar                                                                       |
| **.net.pe / .org.pe / .nom.pe** | ccTLD Perú alternativos | **USD 5.90 – USD 39.90** (~S/24 – S/150) primer año | 🛒 **AltiplanoHost** – ofertas primer año para extensiones peruana alternativas ([AltiplanoHost Hosting y Dominios A1][2])           |
|                                 |                         |                                                     | 🛒 **DominiosPeru.pe** – .net.pe o .org.pe desde alrededor de USD 5.90 para proyectos u organizaciones ([dominios Perú][5])          |


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
* * **Cierre de Caja:** El sistema NO realiza cuadre de caja ni gestión de efectivo. El cliente debe llevar su control contable manualmente de forma externa.

## 10. Uso y Protección de Datos Personales

* **Responsabilidad de Datos:** El cliente (**Bryan Mayanga**) es el único responsable legal del tratamiento, consentimiento y uso de los datos personales registrados por los usuarios finales en la plataforma.
* **Privacidad por Diseño:** El sistema ha sido diseñado para no recolectar direcciones exactas ni geolocalización automática sin validación previa, minimizando los riesgos legales asociados a la privacidad.
* **Custodia de Credenciales:** Una vez entregadas las llaves de acceso (AWS Cognito y AWS Console), la seguridad y custodia de estas recae exclusivamente en el cliente.
* **Kill-Switch (No eliminación):** Por comodidad comercial, el sistema NO eliminará automáticamente los datos al vencer la suscripción para permitir reactivaciones. Solo el Super-Admin tendrá la facultad de eliminación definitiva mediante una función especial.
---

## 11. Próximos Pasos

Para iniciar con la **Opción 1**:

1. **Aceptación:** Creación y firma de los contratos.
2. **Configuración:** Sesión de 30 min - 1 hora para apertura de cuenta AWS.
3. **Inicio:** Abono del **50% de adelanto (S/ 3,250.00)** para comenzar el desarrollo.
