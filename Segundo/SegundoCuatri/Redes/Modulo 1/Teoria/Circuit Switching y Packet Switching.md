Explica los **dos tipos de conmutación de red**:

- **Circuit Switching (conmutación de circuitos)**:
    
    - Se establece un camino dedicado entre emisor y receptor.
        
    - Se reservan recursos (ancho de banda, buffers).
        
    - No se pierde información, pero no es flexible → si falla un nodo, hay que reiniciar.
        
    - Ejemplo: red telefónica tradicional.
        
- **Packet Switching (conmutación de paquetes)**:
    
    - No se reserva un camino fijo → cada paquete puede tomar rutas distintas.
        
    - Se comparten los recursos.
        
    - Puede perderse información, pero **se adapta a fallas**.
        
    - Es lo que usa **Internet (TCP/IP)**.
        

Incluye cálculos de **tiempos de transmisión, uso de enlaces, necesidad de buffers** y ejemplos con Ethernet.

👉 Es clave para entender por qué Internet funciona con **packet switching** y no con circuitos dedicados.