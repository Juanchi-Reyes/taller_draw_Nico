# Taller Práctico: Análisis de Sistemas - RPG Manager 
**Materia:** Análisis de Sistemas  
**Estudiante:** Juan Nicolás Reyes Saavedra - 20242578031  
**Universidad:** Universidad Distrital Francisco José de Caldas  

---

## Diagramas del Sistema (Exportados a SVG)

### 1. Diagrama de Contexto (Nivel 0)
Muestra el sistema RPG Manager y sus interacciones con las entidades externas.
![Diagrama de Contexto](diagramas-drawio/01_contexto_rpg.svg)

### 2. Diagrama de Casos de Uso
Describe las funcionalidades principales que los actores (Jugador, Game Master, etc.) pueden realizar en el sistema.
![Diagrama de Casos de Uso](diagramas-drawio/02_casos_uso_rpg.svg)

### 3. Diagrama de Actividades: CU-07 Combatir en la Arena
Flujo paso a paso detallando los carriles de responsabilidad, decisiones y paralelismo durante el combate.
![Actividades CU-07](diagramas-drawio/03_actividades_cu07.svg)

### 4. Diagrama de Actividades: CU-03 Crear Personaje
Flujo paso a paso detallando la validación de nombres, elección de clase y creación del inventario.
![Actividades CU-03](diagramas-drawio/03_actividades_cu03.svg)

---

##  Respuestas a las Preguntas de Reflexión

**1. ¿Por qué el diagrama de contexto no muestra la base de datos del RPG Manager si el sistema sí la usa?**  
Porque el diagrama de contexto (Nivel 0) trata al sistema como una "caja negra" única frente a sus entidades externas[cite: 5]. Está prohibido mostrar procesos internos y almacenes de datos (bases de datos) en este nivel; estos se detallan a partir del DFD de Nivel 1[cite: 5, 7].

**2. ¿Cuál es la diferencia entre el flujo de datos "datos del personaje" y el caso de uso "Crear Personaje"?**  
El flujo de datos representa la información específica que viaja entre las entidades y el sistema (siempre es un sustantivo)[cite: 5], mientras que el caso de uso representa la acción u objetivo final que el actor busca conseguir usando el sistema (siempre se nombra con un Verbo + Sustantivo)[cite: 5, 9]. 

**3. Da un ejemplo propio del RPG Manager de `<<include>>` y otro de `<<extend>>` que no estén en este taller.**  
*   **`<<include>>`:** *CU Comprar ítem en la tienda* `<<include>>` *CU Descontar saldo*. (Siempre que compras, obligatoriamente se debe cobrar).
*   **`<<extend>>`:** *CU Vender ítem obsoleto* `<<extend>>` *CU Gestionar Inventario*. (Opcionalmente, mientras revisas tu inventario, decides vender algo).

**4. ¿Qué información aporta el diagrama de actividades que el de casos de uso no puede mostrar?**  
El diagrama de casos de uso responde al "¿Qué hace el sistema?" (vista general)[cite: 2], mientras que el diagrama de actividades responde al "¿Cómo ocurre paso a paso?"[cite: 2]. Aporta el orden cronológico de las acciones, las decisiones lógicas con guardas (condicionales), los flujos paralelos (fork/join) y, gracias a los carriles, define claramente quién tiene la responsabilidad (Actor o Sistema) en cada instante[cite: 13].

**5. El paso "Calcular daño al oponente" será un método en POO. ¿En qué clase crees que vive y por qué?**  
Debería vivir en una clase mediadora o controladora como `Combate` o `ArenaDeCombate`. El cálculo del daño requiere conocer las estadísticas ofensivas del atacante y las defensivas del defensor, por lo que una clase gestora de la partida es la ideal para invocar la lógica que enfrenta ambos datos sin sobrecargar la entidad `Personaje`.

**6. ¿Cuándo preferirías PlantUML y cuándo draw.io en un proyecto real?**  
Preferiría **PlantUML** para documentación técnica que cambia frecuentemente, ya que se escribe mediante código y permite un excelente control de versiones en Git (se pueden leer los cambios línea a línea)[cite: 2]. Usaría **draw.io** cuando necesite presentar y explicar flujos visuales a clientes o perfiles no técnicos, ya que ofrece un control total del diseño, colores y organización espacial de las figuras[cite: 2].