
---

## 🌐 1. Organizaciones y Estándares

- **Internet no tiene un dueño único**, pero sí organismos que la regulan:
    
    - **ICANN**: gestiona nombres de dominio y direcciones IP a nivel global.
        
    - **IANA**: asigna direcciones IP y números de protocolos.
        
    - **LACNIC**: administra IPs en Latinoamérica y Caribe.
        
- **Estándares** → necesarios para que equipos distintos funcionen juntos:
    
    - Garantizan **interoperabilidad**, reducen costos, dan compatibilidad hacia atrás.
        
    - Organismos clave:
        
        - **ITU-T** (telefonía, módems, normas V).
            
        - **ISO** (normas internacionales, serie X para redes).
            
        - **IEEE** (LAN/MAN, estándar 802 como Ethernet y Wi-Fi).
            
        - **IETF** (Internet Engineering Task Force, publica los **RFCs**).
            

---

## 🔀 2. Circuit Switching vs Packet Switching

- **Circuit Switching (conmutación de circuitos)**:
    
    - Establece un camino dedicado entre emisor y receptor.
        
    - Se reservan recursos → no se pierde info.
        
    - Ejemplo: red telefónica clásica.
        
    - Desventaja: poco flexible, si falla un enlace hay que rehacer el circuito.
        
- **Packet Switching (conmutación de paquetes)**:
    
    - No hay camino fijo, cada paquete puede tomar rutas diferentes.
        
    - No se reservan recursos, se comparten.
        
    - Puede perderse info, pero se adapta a fallas.
        
    - Es el modelo que usa **Internet**.
        
- Ejemplo: Ethernet, TCP/IP → cada paquete lleva datos + control.
    

---

## 🌍 3. Funcionamiento de Internet

- Internet = **red mundial de redes** basada en **TCP/IP** y **packet switching**.
    
- **Estructura jerárquica**:
    
    - **ISP Tier 1**: alcance internacional, grandes carriers.
        
    - **ISP Tier 2**: nacionales, dependen de Tier 1.
        
    - **ISP Tier 3**: locales, dan Internet al usuario final.
        
- **Conexión entre ISPs**:
    
    - **Peering**: intercambio de tráfico entre pares, sin cobro (público o privado).
        
    - **Transit**: un ISP paga a otro de mayor jerarquía.
        
- **Sistemas Autónomos (AS)**: conjunto de redes bajo una administración única.
    
- **IXP (Internet Exchange Point)**: lugar físico donde ISPs intercambian tráfico → reduce costos y latencia. Ej: **CABASE** en Argentina.
    
- **Última milla**: tecnologías de acceso al usuario final → ADSL, Cablemodem, 4G/5G, WIMAX.
    
- **Medios de interconexión mundial**: cables submarinos, fibra terrestre, satélites.
    

---

## 🧱 4. Arquitectura de Niveles

- Dividir funciones en **capas** facilita la interoperabilidad.
    
- **Modelo OSI (7 capas)** vs **Modelo TCP/IP (4 capas)**:
    
    - **Físico (1)** ↔ **Link TCP/IP**: transmisión de bits.
        
    - **Enlace (2)** ↔ **Link TCP/IP**: frames sin errores, control de acceso al medio.
        
    - **Red (3)** ↔ **Internet TCP/IP**: direccionamiento (IP) y ruteo de paquetes.
        
    - **Transporte (4)** ↔ **Transporte TCP/IP**: extremo a extremo, confiabilidad (TCP/UDP).
        
    - **Sesión, Presentación, Aplicación (5–7)** ↔ **Aplicación TCP/IP**: protocolos de usuario (HTTP, DNS, FTP).
        
- Conceptos clave:
    
    - **Servicio**: lo que ofrece una capa a la superior.
        
    - **Protocolo**: reglas de comunicación dentro de una capa.
        
    - **Encapsulación**: cada capa agrega su cabecera al mensaje.
        

---

## ⏱ 5. Demoras y Transmisión

- **Demora de propagación (dp)** = distancia / velocidad de señal (ej: fibra, 2×10⁸ m/s).
    
- **Tiempo de bit (Tb)** = 1 / velocidad de transmisión (ej: 100 Mb/s → Tb = 0.01 µs).
    
- **Demora de transmisión (dtrans)** = tamaño paquete (bits) / tasa de bits.
    
- **Demora de encolamiento (dcola)** = espera en buffers si el enlace está ocupado.
    
- **Demora de procesamiento (dproc)** = leer cabecera y decidir ruta.
    
- Fórmulas típicas:
    
    - Tiempo total = dp + dtrans + dcola + dproc
        
    - Capacidad del canal = dp × Vt (bits en vuelo).
        

---

## 📦 6. Store and Forward

- Técnica usada por routers: **reciben el paquete completo antes de reenviarlo**.
    
- Implica:
    
    - Cada salto suma **demora de transmisión + propagación + procesamiento**.
        
    - Si llegan más paquetes de los que pueden salir, se encolan → **cola**.
        
    - Si no hay espacio en buffer → **pérdida de paquetes**.
        
- Ejemplo:
    
    - A → R1 → R2 → B, con 1000 B de datos, MTU 520 B → se fragmenta en varios paquetes.
        
    - Si un enlace es más lento → **cuello de botella**, se acumulan en buffer y puede haber pérdidas.
        
- Herramienta práctica: **traceroute** mide retardos hop por hop.
    

---

## 📚 7. Resumen final (lo esencial que tenés que manejar)

1. **Internet funciona con conmutación de paquetes (packet switching)**, no con circuitos.
    
2. **Los protocolos están organizados en capas (TCP/IP)**: enlace, red, transporte, aplicación.
    
3. **Los estándares (IEEE, IETF, ISO, ITU)** hacen posible que todo sea interoperable.
    
4. **Internet es jerárquica**: ISPs Tier 1, 2, 3, interconectados por peering y transit, con puntos de intercambio (IXP).
    
5. **Demoras en la red**: propagación (distancia), transmisión (tamaño/velocidad), procesamiento (routers), encolado (buffers).
    
6. **Store and Forward**: los routers reciben todo el paquete antes de reenviar; introduce retardos, necesidad de buffers y posibles pérdidas si hay congestión.
    

---

Buena pregunta 👌.

**OSI** significa **Open Systems Interconnection** (_Interconexión de Sistemas Abiertos_).

Es un **modelo de referencia de 7 capas** creado por la ISO (International Standards Organization) en los años 80 para **estandarizar cómo se comunican los sistemas de red**.

---

## 📚 Sus objetivos principales:

- Dividir la complejidad de la comunicación en **niveles** más simples.
    
- Permitir la **interoperabilidad** entre equipos de distintos fabricantes.
    
- Ser un marco de referencia (no un protocolo real).
    

---

## 🔢 Las 7 capas del modelo OSI

1. **Física**
    
    - Transmite **bits** (0 y 1) por el medio físico (cable, fibra, radio).
        
    - Define voltajes, señales, conectores.
        
2. **Enlace de datos**
    
    - Transmite **frames** (tramas) sin errores entre dos nodos vecinos.
        
    - Control de acceso al medio, direcciones **MAC**.
        
3. **Red**
    
    - Encargada de mover **paquetes** de un origen a un destino a través de la red.
        
    - Direccionamiento **IP**, ruteo.
        
4. **Transporte**
    
    - Comunicación **extremo a extremo** entre aplicaciones.
        
    - Confiabilidad, control de errores, control de flujo.
        
    - Ejemplos: **TCP** (confiable), **UDP** (rápido, no confiable).
        
5. **Sesión**
    
    - Gestiona el **diálogo** entre aplicaciones (inicio, mantenimiento, cierre de sesión).
        
6. **Presentación**
    
    - Traduce los datos para que las aplicaciones los entiendan.
        
    - Compresión, encriptación, codificación (ASCII, JPEG, MP3, etc.).
        
7. **Aplicación**
    
    - Donde viven los protocolos de usuario: **HTTP, FTP, SMTP, DNS**.
        

---

📌 En la práctica, Internet no usa OSI directamente, sino el modelo **TCP/IP (4 capas)**.

- Pero OSI se usa como **marco conceptual** para explicar y entender cómo funciona una red.
    

---


