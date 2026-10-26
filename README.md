```mermaid
flowchart LR
    ROOT["CAPÍTULO 6<br/>CRONOGRAMA"]

    %% ========== INTRODUCCIÓN ==========
    subgraph S0["Introducción"]
        I1["Sirve para saber cómo y cuándo se entregan<br/>productos, servicios o resultados"]
        I2["Herramienta de comunicación<br/>con los interesados"]
        I3["Ciclo adaptativo / ágil"]
        I4["Alcance no definido por completo<br/>→ cronograma por iteración<br/>(mini-cronograma, ej. 15 días)"]
        I5["Cronogramas más flexibles<br/>Lecciones aprendidas cambian prioridades"]
        I6["Iteración corta mitiga<br/>la corrupción del alcance"]
        I3 --> I4 --> I5
        I4 --> I6
    end
    ROOT --> S0

    %% ========== PROCESOS ==========
    subgraph S1["Procesos de gestión del cronograma - PMBOK 6ª ed."]
        G1["Grupo Planificación"]
        G2["Grupo Control"]
        PR1["1. Planificar la gestión"]
        PR2["2. Definir actividades"]
        PR3["3. Secuenciar actividades"]
        PR4["4. Estimar duración"]
        PR5["5. Desarrollar cronograma"]
        PR6["6. Controlar cronograma"]
        G1 --> PR1 & PR2 & PR3 & PR4 & PR5
        G2 --> PR6
        PR1 --> PR2 --> PR3 --> PR4 --> PR5 --> PR6
        NP["Proyectos pequeños:<br/>procesos 2 a 5 en uno solo"]
        AG1["Ágil: Programación iterativa<br/>backlog + historias de usuario<br/>priorizadas por iteración"]
        AG2["Ágil: Programación bajo demanda<br/>se saca trabajo del backlog<br/>según recursos disponibles"]
        PR5 -.-> NP
        PR1 -.-> AG1
        PR1 -.-> AG2
    end
    ROOT --> S1

    %% ========== 1. PLANIFICAR ==========
    subgraph S2["1. Planificar la gestión del cronograma"]
        direction TB
        P1E["ENTRADAS<br/>Acta de constitución: hitos<br/>Planes: alcance y enfoque de desarrollo<br/>predictivo o adaptativo"]
        P1H["HERRAMIENTA<br/>Análisis de alternativas<br/>metodología, nivel de detalle,<br/>duración de iteración"]
        P1S["SALIDA<br/>Plan de gestión del cronograma"]
        P1E --> P1H --> P1S
        P1C["Contenido del plan"]
        P1S --> P1C
        P1C --> PC1["Metodología y herramientas<br/>CPM, Ágil"]
        P1C --> PC2["Unidades de medida<br/>horas, días, meses"]
        P1C --> PC3["Nivel de precisión<br/>±5%, ROM -25% a +75%"]
        P1C --> PC4["Umbrales de control<br/>ej. +20% sin acción correctiva"]
        P1C --> PC5["Reglas de % de avance<br/>horas trabajadas, 50/50"]
        P1C --> PC6["Cuentas de control de la EDT"]
        P1C --> PC7["Reserva para contingencias"]
        P1C --> PC8["Formato y frecuencia de informes"]
    end
    PR1 --> S2

    %% ========== 2. DEFINIR ==========
    subgraph S3["2. Definir las actividades"]
        direction TB
        P2E["ENTRADAS<br/>Plan de gestión del cronograma<br/>Línea base del alcance:<br/>enunciado, EDT y diccionario"]
        P2H1["Descomposición<br/>paquetes de trabajo → actividades"]
        P2H2["Planificación gradual<br/>detalle cercano, agregado lo lejano<br/>ej. 6 meses o próxima iteración"]
        P2N["Cuentas de control y<br/>paquetes de planificación<br/>cuando el alcance es difuso"]
        P2S1["Lista de actividades"]
        P2S2["Atributos de las actividades<br/>ID EDT, nombre, código,<br/>predecesora, sucesora, dependencia,<br/>adelantos o retrasos, recursos,<br/>fechas impuestas, restricciones,<br/>supuestos, responsable, lugar,<br/>nivel de esfuerzo"]
        P2S3["Lista de hitos<br/>eventos de duración 0"]
        P2S4["Solicitudes de cambio"]
        P2E --> P2H1 & P2H2
        P2H2 -.-> P2N
        P2H1 --> P2S1 & P2S2 & P2S3 & P2S4
    end
    PR2 --> S3

    %% ========== 3. SECUENCIAR ==========
    subgraph S4["3. Secuenciar las actividades"]
        direction TB
        P3E["ENTRADAS<br/>Plan del cronograma, línea base del alcance<br/>Actividades, atributos, hitos, supuestos"]
        P3H1["Diagramación por precedencia<br/>PDM / AON: actividad en el nodo"]
        P3H2["Determinación de dependencias"]
        P3H3["Adelantos y retrasos"]
        P3S["SALIDA<br/>Diagrama de red del cronograma<br/>Inicio → actividades → Fin"]
        P3ADM["ADM / AOA: actividad en la flecha<br/>no se usa en la actualidad"]
        P3GERT["Limitación PDM: sin programación condicional<br/>ni bucles → GERT"]
        P3E --> P3H1 & P3H2 & P3H3 --> P3S
        P3H1 -.-> P3ADM
        P3H1 -.-> P3GERT

        P3H1 --> T1["4 tipos de relación"]
        T1 --> T1a["FS final a inicio<br/>la más usada"]
        T1 --> T1b["FF final a final"]
        T1 --> T1c["SS inicio a inicio"]
        T1 --> T1d["SF inicio a final<br/>no se utiliza"]

        P3H2 --> D1["Obligatoria<br/>lógica dura"]
        P3H2 --> D2["Discrecional<br/>lógica blanda"]
        P3H2 --> D3["Externa"]
        P3H2 --> D4["Interna"]
        D5["Combinaciones: obligatoria externa,<br/>obligatoria interna, discrecional externa,<br/>discrecional interna"]
        D1 & D2 & D3 & D4 --> D5

        P3H3 --> L1["Adelanto: sucesora empieza<br/>antes, ej. con 50% de avance"]
        P3H3 --> L2["Retraso: espera adicional,<br/>ej. 30 días"]
    end
    PR3 --> S4

    %% ========== 4. ESTIMAR ==========
    subgraph S5["4. Estimar la duración de las actividades"]
        direction TB
        P4E["ENTRADAS<br/>Plan del cronograma, línea base del alcance<br/>Actividades, hitos, recursos, calendarios,<br/>riesgos, supuestos, lecciones"]

        subgraph FAC["Factores que influyen"]
            F1["Complejidad del alcance"]
            F2["Recursos y su calendario"]
            F3["Competencias y motivación"]
            F4["Restricciones y cambios tecnológicos"]
            F5["Ley de Parkinson<br/>el trabajo se expande al tiempo disponible"]
            F6["Síndrome del estudiante<br/>todo al último minuto"]
            F7["Procrastinación"]
        end

        subgraph REC["Recursos vs duración"]
            R1["No hay relación lineal<br/>9 mujeres no hacen un bebé en 1 mes"]
            R2["Ej. 1 pintor 4 días;<br/>8 pintores no es medio día"]
            R3["Especialización puede multiplicar<br/>productividad: 100 h → 5 x 10 h = 50 h"]
            R4["Ley de rendimientos decrecientes"]
            R1 --> R2
            R1 --> R4
            R3 --> R4
        end

        P4E --> FAC
        P4E --> REC

        subgraph HER["Herramientas de estimación"]
            H1["Análoga / descendente<br/>rápida y barata, pero imprecisa"]
            H2["Paramétrica<br/>estadística sobre datos históricos"]
            H3["3 valores PERT"]
            H4["De abajo hacia arriba<br/>dividir y sumar"]
            H5["Análisis de alternativas<br/>recursos óptimos, compresión, costo, riesgos"]
            H6["Análisis de reserva<br/>contingencia: riesgos conocidos<br/>gestión: riesgos desconocidos"]
            H7["Toma de decisiones<br/>votación, Puño a Cinco<br/>consenso con 3, 4 o 5 dedos"]
            H8["Reuniones Sprint ágiles<br/>dueño del producto + equipo + DP"]
        end
        P4E --> HER

        H2 --> EX1["Ej. 6.1: cargar 10 formularios<br/>Análoga = 47 h<br/>Paramétrica: y = 3,2699x − 0,4229<br/>R² = 0,92 → 32,28 h<br/>R² mayor a 0,7 = aceptable"]
        H1 --> EX1

        H3 --> PERT["Distribución Beta<br/>a optimista, b más probable, c pesimista"]
        PERT --> PF1["Media M = (a + 4b + c) / 6"]
        PERT --> PF2["Desv. estándar σ = (c − a) / 6"]
        PERT --> PF3["Varianza = σ²"]
        PERT --> PF4["Duración del proyecto = Σ M<br/>de la ruta crítica"]
        PERT --> PF5["Varianza del proyecto = Σ σ²<br/>NO se suman desviaciones"]
        PERT --> PF6["Alternativa: triangular<br/>M = (a + b + c) / 3"]
        PF5 --> NORM["Normal estándar<br/>±1σ = 68,26%<br/>±2σ = 95,45%<br/>±3σ = 99,73%"]
        PF2 --> NORM
        NORM --> EX2["Ej. 6.2: A=6, B=8, C=4, D=5, E=2<br/>Ruta crítica B-D = 13 sem<br/>Varianza = 4,56; σ = 2,13<br/>95% → 8,73 a 17,27 sem"]
        PF4 --> EX2

        P4S["SALIDAS<br/>Duración de actividades<br/>con rango y probabilidad<br/>Bases de la estimación<br/>supuestos, restricciones, confianza, riesgos"]
        HER --> P4S
    end
    PR4 --> S5

    %% ========== 5. DESARROLLAR ==========
    subgraph S6["5. Desarrollar el cronograma"]
        direction TB
        P5E["ENTRADAS<br/>Plan, línea base del alcance<br/>Actividades, diagramas de red, recursos,<br/>duraciones, bases de estimación, hitos,<br/>calendarios, riesgos, supuestos<br/>Acuerdos contractuales"]
        P5N["Proceso iterativo: integra actividades,<br/>secuencias, recursos y duraciones<br/>Revisión del equipo → ajustes"]
        P5LB["Cronograma aprobado por interesados<br/>= línea base de tiempos"]
        P5E --> P5N --> P5LB

        P5N --> T_CPM["Método de la ruta crítica"]
        P5N --> T_MOD["Técnicas de modelado<br/>Simulación Monte Carlo"]
        P5N --> T_CC["Método de la cadena crítica"]
        P5N --> T_OPT["Optimización de recursos"]
        P5N --> T_AR["Adelantos y retrasos"]
        P5N --> T_COMP["Compresión del cronograma"]
        P5N --> T_AGI["Planificación ágil de entregas"]

        subgraph CPM["Método de la ruta crítica"]
            direction TB
            C0["Ruta crítica = camino más largo<br/>Si se retrasa una actividad crítica,<br/>se retrasa el proyecto"]
            C1["Forward pass<br/>ES y EF<br/>EF = ES + duración<br/>ES = mayor EF de predecesoras"]
            C2["Backward pass<br/>LF y LS<br/>LS = LF − duración"]
            C3["Holgura total<br/>LS − ES = LF − EF"]
            C4["Holgura libre<br/>retraso sin afectar el ES<br/>de la sucesora"]
            C5["Holgura del proyecto<br/>vs fecha externa<br/>puede ser negativa"]
            C6["Ruta crítica cercana<br/>near critical path"]
            C7["Ej. págs. 190-194: B-D-H-J-K = 69 días<br/>A-C-G-J-K = 67 días casi crítica<br/>Holgura I = 36, C = 2, F = 41"]
            C0 --> C1 --> C2 --> C3
            C3 --> C4
            C3 --> C5
            C0 --> C6
            C3 --> C7
        end
        T_CPM --> CPM

        subgraph CCH["Método de la cadena crítica - Goldratt 1997"]
            direction TB
            K0["Cronograma considerando<br/>recursos críticos y limitados"]
            K1["Sobre-asignación<br/>ej. Juan en A y B a la vez"]
            K2["Re-asignar recursos → nueva ruta crítica"]
            K3["Cadena crítica = camino más largo<br/>con restricciones de recursos"]
            K4["Estimaciones recortadas<br/>a duraciones optimistas"]
            K5["Colchón de proyecto<br/>reserva global al final de la cadena"]
            K6["Colchones de alimentación<br/>en ramas que alimentan la cadena"]
            K7["Gestión: % avance de cadena<br/>vs % consumo del colchón<br/>Zona OK o ¡Cuidado!"]
            K8["Ej.: 14 días → 12 días<br/>Mejoras de 10% a 50% de plazos"]
            K9["Causas: Síndrome del estudiante<br/>y Ley de Parkinson"]
            K0 --> K1 --> K2 --> K3 --> K4 --> K5
            K3 --> K6
            K5 --> K7
            K4 --> K8
            K9 --> K4
            KNOTE["Con recursos ilimitados:<br/>cadena crítica = ruta crítica"]
            K0 -.-> KNOTE
        end
        T_CC --> CCH

        subgraph OPT["Optimización de recursos"]
            direction TB
            O1["Nivelación de recursos<br/>Ej. 6.3: de 40 personas a 30<br/>sin pasar de 12 semanas"]
            O2["Mover actividades con holgura<br/>(A o C), no las críticas B y D"]
            O3["Preferir Equilibrio 2<br/>C con 50% de holgura vs A con 33%"]
            O4["Evitar altibajos 30-20-30<br/>y convertir no críticas en críticas"]
            O5["El software nivela solo por holgura:<br/>falta criterio de clima, riesgos, disponibilidad"]
            O6["Equilibrio de recursos<br/>Ej. 6.4: máximo 20 personas<br/>→ proyecto de 16 semanas"]
            O7["Con recursos limitados<br/>todas las actividades pasan a ser críticas"]
            O8["Restricción que cambia:<br/>plazo, o alcance, calidad<br/>y satisfacción del cliente"]
            O1 --> O2 --> O3
            O1 --> O4
            O1 --> O5
            O1 --> O6 --> O7
            O6 --> O8
        end
        T_OPT --> OPT

        subgraph COMP["Compresión del cronograma - sin cambiar el alcance"]
            direction TB
            Z1["Intensificación - Crashing<br/>más recursos, menos duración<br/>→ más costo<br/>Ej. 6.5: A + M = 9.000 es la opción más barata"]
            Z2["Ejecución rápida - Fast-tracking<br/>actividades en paralelo<br/>→ más riesgo"]
            Z3["Reducir alcance<br/>ahorra tiempo y costo<br/>baja satisfacción del cliente"]
            Z4["Recortar calidad<br/>puede ahorrar tiempo y costo<br/>agrega riesgos"]
            Z5["Regla: actuar solo sobre la ruta crítica<br/>y primero informar el impacto<br/>al gerente o patrocinador"]
            Z6["Ej. 6.6: 27 → 24 meses<br/>ruta crítica F-G-C-D-E<br/>D y E en paralelo, mover recursos de H a D,<br/>sumar recursos a C"]
            Z7["Horas extra: guardarlas como<br/>reserva de contingencia"]
            Z5 --> Z1 & Z2 & Z3 & Z4
            Z1 --> Z6
            Z2 --> Z6
            Z7 -.-> Z1
        end
        T_COMP --> COMP

        subgraph AGIL["Planificación ágil de entregas"]
            direction TB
            A1["Proyecto"] --> A2["Entregas - hoja de ruta"]
            A2 --> A3["Iteraciones"]
            A3 --> A4["Funcionalidades<br/>historias de usuario"]
            A4 --> A5["Tareas"]
            A6["Primera iteración con alcance definido<br/>el resto se define progresivamente"]
            A7["Scrum: iteración = Sprint<br/>dura de 2 a 4 semanas"]
            A3 -.-> A6
            A3 -.-> A7
        end
        T_AGI --> AGIL

        subgraph P5SAL["SALIDAS"]
            direction TB
            SO1["Línea base del cronograma<br/>aceptada y aprobada por<br/>el equipo de dirección"]
            SO2["Cronograma"]
            SO3["Datos del cronograma<br/>hitos, atributos, histograma,<br/>reservas, supuestos, restricciones"]
            SO4["Calendarios del proyecto<br/>días laborales y no laborales"]
            SO5["Solicitudes de cambio<br/>y actualizaciones"]
            SO2 --> F1x["Diagrama de hitos<br/>para la alta gerencia"]
            SO2 --> F2x["Diagrama de barras - Gantt<br/>para equipo y DP"]
            SO2 --> F3x["Diagrama de red"]
        end
        P5LB --> P5SAL
    end
    PR5 --> S6

    %% ========== 6. CONTROLAR ==========
    subgraph S7["6. Controlar el cronograma"]
        direction TB
        P6E["ENTRADAS<br/>Línea base del alcance, plan,<br/>línea base del cronograma y del desempeño<br/>Cronograma, calendarios, lecciones<br/>Datos de desempeño del trabajo"]
        P6D["Objetivo: monitorear el avance<br/>vs línea base y gestionar cambios<br/>Ágil: control por iteración"]
        P6E --> P6D

        subgraph P6H["Herramientas"]
            direction TB
            X1["Revisiones del desempeño<br/>real vs línea base<br/>Valor ganado (cap. siguiente)"]
            X2["Medición de avance sin entregables<br/>Regla 50/50<br/>Regla 20/80<br/>Regla 0/100"]
            X3["Diagrama de quemado - burndown<br/>horas pendientes vs plan<br/>proyección de cumplimiento"]
            X4["Análisis de tendencias"]
            X5["Análisis de la variación<br/>causas y acciones correctivas<br/>o preventivas"]
            X6["Análisis ¿qué pasa si?"]
            X7["Método de la ruta crítica<br/>vigilar rutas casi críticas"]
            X8["Software<br/>Gantt de seguimiento"]
            X9["Optimización de recursos"]
            X10["Adelantos y retrasos"]
            X11["Compresión del cronograma<br/>intensificación o ejecución rápida"]
        end
        P6D --> P6H

        subgraph P6S["Salidas"]
            direction TB
            Y1["Información de desempeño<br/>SPI y SV"]
            Y2["Pronóstico del cronograma"]
            Y3["Solicitudes de cambio"]
            Y4["Actualizaciones"]
        end
        P6H --> P6S
    end
    PR6 --> S7

    %% ========== EJERCICIOS ==========
    subgraph S8["Ejercicios de diagramación por precedencia"]
        direction TB
        E7["Ej. 6.7<br/>Ruta crítica Ini-B-G-D-F-Fin = 15 sem<br/>Si H sube 1 sem: 2 rutas críticas<br/>= más riesgo, aunque la duración no cambie<br/>Cliente pide −3 sem: holgura −3"]
        E8["Ej. 6.8<br/>Ruta crítica A-B-D-E = 14 días<br/>Holgura de C = 3 días<br/>Si C = 8 días: holgura = 1<br/>Con F de 7 días: A-C-F-E = 18 días"]
        EQ["Preguntas tipo examen<br/>1) Opción A: reasignar a D → 14 sem<br/>2) Primero informar el impacto"]
    end
    ROOT --> S8

    %% ========== INTEGRACIÓN ==========
    subgraph S9["Integración de los procesos"]
        direction LR
        N1["1. Plan del cronograma"] --> N2["2. Actividades"]
        ALC["Alcance"] --> N2
        N2 --> N3["3. Diagrama de red"]
        N2 --> N4["4. Duración"]
        REC2["Recursos"] --> N4
        REC2 --> N5
        N3 --> N5["5. Cronograma"]
        N4 --> N5
        N5 --> N6["6. Controlar"]
        DD["Datos de desempeño"] --> N6
        N6 --> OUT1["Información"]
        N6 --> OUT2["Solicitudes de cambio"]
        N6 --> OUT3["Actualizaciones"]
    end
    ROOT --> S9

    %% ========== ESTILOS ==========
    classDef root fill:#1f4e79,color:#fff,stroke:#0b2a47,stroke-width:2px
    classDef proc fill:#2e75b6,color:#fff,stroke:#1f4e79
    classDef tool fill:#ddebf7,color:#000,stroke:#2e75b6
    classDef out fill:#e2efda,color:#000,stroke:#548235
    classDef warn fill:#fff2cc,color:#000,stroke:#bf9000
    class ROOT root
    class PR1,PR2,PR3,PR4,PR5,PR6 proc
    class P1H,P2H1,P2H2,P3H1,P3H2,P3H3,H1,H2,H3,H4,H5,H6,H7,H8,T_CPM,T_MOD,T_CC,T_OPT,T_AR,T_COMP,T_AGI tool
    class P1S,P2S1,P2S2,P2S3,P2S4,P3S,P4S,P5LB,SO1,SO2,SO3,SO4,SO5 out
    class P3ADM,P3GERT,F5,F6,F7,Z5 warn
```
