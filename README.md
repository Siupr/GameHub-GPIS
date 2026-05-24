Plan de Gestión de la Configuración del Software (SCM)
Proyecto: GameHub 
Asignatura: Ingeniería del Software 2025-2026
Equipo: Grupo 3
Fase: 2 — Diseño de Ingeniería
________________________________________
1. Herramienta de control de versiones
El equipo utiliza GitHub como sistema de control de versiones, en coherencia con el tech stack definido en la Fase 1.
•	Repositorio: https://github.com/Siupr/GameHub-GPIS
•	Visibilidad: Público
•	Justificación: GitHub ofrece control de versiones distribuido, alojamiento remoto que actúa como copia de seguridad, herramientas integradas de revisión de código (Pull Requests) y gestión de tareas (Projects), todo en una única plataforma. Esto reduce la necesidad de herramientas externas y facilita la trazabilidad exigida en la evaluación individual.
________________________________________
2. Política de ramas
El equipo adopta un GitFlow simplificado, adaptado al tamaño del equipo (4 personas) y a la naturaleza académica del proyecto.
Rama	Propósito
main	Rama estable. Contiene únicamente código listo para entregar en cada inspección. Se permiten commits directos para facilitar el flujo, si no se hace muy molesto.
develop	Rama de integración. Aquí se fusionan las funcionalidades terminadas y revisadas.
feature/*	Ramas de trabajo. Una por integrante y fase, partiendo siempre de develop.



Convención de nombres
Las ramas de trabajo siguen el patrón feature/persona-faseM:
•	feature/fran-fase2
•	feature/carlos-fase2
•	feature/dani-fase2
•	feature/samya-fase2
Se ha optado por una rama por persona y fase (en lugar de una por tarea individual) para mantener el número de ramas manejable y fácil.
Flujo de trabajo
1.	Se crean las ramas feature/* desde develop.
2.	Cada compañero trabaja en su rama realizando commits frecuentes y descriptivos.
3.	Al terminar, abre un Pull Request hacia develop.
4.	Al cierre de cada fase, develop se fusiona en main.
________________________________________
3. Política de commits
•	Frecuencia: commits frecuentes y atómicos (un cambio lógico por commit). No se acumula el trabajo de un día entero en un único commit.
•	Mensajes descriptivos vinculados a la WBS, con el formato:
Añade <documento indicado>
Esta política se alinea con las reglas de registro de GrindStone, donde cada tarea debe corresponder con un elemento concreto de la WBS.
________________________________________
4. Herramienta colaborativa de gestión de tareas
Nos guiamos con el GrindStone del grupo, además de los documentos compartidos entre nosotros, ya que crear una tabla de tareas en GitHub a parte parece redundante.
________________________________________


5. Copias de seguridad y recuperación ante fallos
Copias de seguridad
•	Repositorio remoto en GitHub: el código reside en la nube, funcionando como copia de seguridad principal.
•	Clones locales: cada integrante mantiene su clon local actualizado mediante git pull frecuente, lo que genera múltiples copias distribuidas del repositorio.
•	Documentación: respaldada adicionalmente en Google Drive.
Recuperación ante fallos
Situación	Acción de recuperación
Pérdida del entorno local	Volver a clonar desde GitHub (git clone).
Commit problemático ya fusionado	Revertir el cambio con git revert.
Necesidad de volver a un estado estable	Restaurar desde el último commit de main.
Conflictos en una fusión	Resolver conflictos en local antes de completar el Pull Request.
________________________________________


6. Tabla de ramas y tareas WBS asociadas
Rama	                Trabajo	  Fase	Tareas WBS asociadas
feature/fran-fase1	  PM	      F1	  Informe Ejecutivo, WBS, Gantt, PERT
feature/fran-fase2	  PM	      F2	  COCOMO, Puntos Función, Presupuesto
feature/fran-fase3	  PM	      F3	  Post-Mortem
feature/carlos-fase1	Backend	  F1	  Tech Stack
feature/carlos-fase2	Backend	  F2	  UML Clases, UML Secuencia
feature/carlos-fase3	Backend	  F3	  Código fuente completo
feature/dani-fase1	  Frontend	F1	  Análisis de Riesgos
feature/dani-fase2	  Frontend	F2	  Wireframes, Plan SCM
feature/dani-fase3	  Frontend	F3	  Paquete de instalación
feature/samya-fase1	  QA/DBA	  F1	  Casos de Uso
feature/samya-fase2	  QA/DBA	  F2	  Diagrama ER, Reglas de consistencia
feature/samya-fase3	  QA/DBA	  F3	  Scripts BD, Plan de Testing, Informe de pruebas

