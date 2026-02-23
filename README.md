# PROPUESTA DE DESARROLLO: SISTEMA DE GESTIÓN DE IDENTIDAD QR

**Preparado para:** Bryan Mayanga

**Elaborado por:** Diego A. Ladron de Guevara Aguirre, Carla Noelia Aguirre Mayanga, Leonardo Ordeñez Lopez

**Fecha:** 22 de febrero de 2026

---

## 1. Visión General del Proyecto

El objetivo es desarrollar una plataforma tecnológica robusta que permita la creación, gestión y visualización de perfiles de emergencia mediante códigos QR únicos. El sistema está diseñado para ser escalable, seguro y de **bajo costo de mantenimiento** utilizando arquitectura de Nube Serverless (AWS).

---

## 2. Infraestructura: AWS Serverless y Costos Operativos

# hacer la calculadora de servisio usados

Para este proyecto, utilizaremos la nube de **Amazon Web Services (AWS)**.

* **Bajos Gastos Fijos:** A diferencia de un hosting tradicional (S/ 50-100 mensuales), AWS solo te cobrará por cada vez que alguien use la web. Si no hay tráfico, el costo es bajo, cercano al 0.
* **Tu Propiedad:** Tú crearás la cuenta con tu propia tarjeta. Esto garantiza que tú eres el único dueño de la base de datos. Yo solo me encargo de la configuración técnica.
# Verificar con la calculadora costos del ses
* **Ahorro en Notificaciones:** Usaremos **AWS SES** para los correos electrónicos, que permite enviar miles de mensajes de forma gratuita o por fracciones de céntimo.

---

## 3. PROPUESTA A: "MVP OPERATIVO + PANEL ADMIN"

*Ideal para lanzar el negocio en 1 mes con control total y ventas presenciales.*

### **¿Cómo funcionará el sistema?**

1. **Captación:** En una tablet o PC, registras los datos del usuario (niño, mascota, etc.).
2. **Generación:** El sistema crea un código QR único vinculado a esa información.
3. **Fabricación:** El panel te permite descargar el QR para imprimirlo manualmente.
4. **Uso:** Al escanear el QR, se ve la info de emergencia y un botón de contacto WhatsApp.
5. **Alertas de Vencimiento:** El sistema revisará diariamente las fechas y **te enviará un correo automático** avisándote qué clientes están por vencer para que puedas contactarlos y renovarles manualmente.

### **¿Qué obtendrás al final?**
- **Web app usuario para observar mos dstos de la persona cuando escaneas el qr**
* **Panel Administrativo: especificar que hace, poner para roles diferentes** Tu centro de control para buscar usuarios por DNI y generar QRs.
* **Sistema de Alertas:** Notificaciones a tu correo sobre suscripciones por expirar.
se necesita intenet en las tablets para funcioanr con la web (parametrico en el panel tsmbien)
### **Inversión y Tiempo:**

* **Tiempo:** 4 semanas (Dedicación 8h diarias).
* **Inversión Especial (Familiar): S/ 5,000.00** *(Valor real mercado: S/ 8,500.00)*

---

## 4. PROPUESTA B: "SAAS PRO + AUTOMATIZACIÓN TOTAL"

*Solución avanzada para automatizar cobros, fabricación e identidad de marca propia.*

### **¿Cómo funcionará el sistema?**

1. **Dominio Propio (Marca):** Tu página tendrá su nombre oficial (Ej: `www.tumarca.pe`), lo cual permite que tu marca aparezca en la URL de cada QR.

Reportes de usuarios (estsfisticas)
### **¿Qué obtendrás al final?**

* **Todo lo de la Propuesta A.**
* **Dominio Especial Registrado:** Configuración de la marca en la URL (.pe / .com).

### **Inversión y Tiempo:**

* **Tiempo:** 8 a 10 semanas.
* **Inversión Especial (Familiar): S/ 8,000.00** *(Valor real mercado: S/ 18,000.00)*
* *Nota: El costo del nombre del dominio (aprox. S/ 110 anual) es cubierto por el cliente.*

---

## 5. Comparativa Técnica de Capacidades

| Función | Opción 1 (MVP) | Opción 2 (SaaS Pro) |
| --- | --- | --- |
| **Arquitectura** | AWS Serverless (Pago por uso) | AWS Serverless (Pago por uso) |
| **Dominio Personalizado** | URL Genérica | **URL con tu Marca (propio)** |
| **Pagos** | Manual (Efectivo/Yape externo) | A|
| **Impresión** | Manual (Descarga de archivo) | Automática (Conexión IoT) |
| **Alertas Vencimiento** | **Email solo al administrador** | **Email a admin y al cliente** |
| **Mantenimiento** | (Segun uso AWS) | (Según metricas de uso AWS)|

---

## 6. ¿Qué esperar del desarrollo?

Trabajaré bajo una metodología de **entregas semanales**:

* **Semana 1:** Configuración de AWS, Seguridad (Login) y Base de Datos.
* **Semana 2:** Formulario de registro y Panel de Usuario.
* **Semana 3:** Panel de Administrador, Generador de QR y Sistema de correos SES.
* **Semana 4:** Pruebas finales, ajustes de diseño y entrega de accesos.

**Nota:** Todo el código será supervisado por un desarrollador Senior para garantizar que la plataforma sea profesional y no presente fallos.

---

## 7. Próximos Pasos

Para iniciar con la **Opción 1**:

1. **Aceptación:** Confirmar la propuesta por este medio.
2. **Configuración:** Sesión de 30 min para crear tu cuenta AWS con tu tarjeta.
3. **Inicio:** Abono del **50% de adelanto (S/ 2,500.00)** para comenzar el desarrollo mañana mismo.
