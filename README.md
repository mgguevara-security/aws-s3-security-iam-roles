# Security Gap Analysis - S3 & IAM Roles Lab

## Description
Análisis técnico sobre la gestión de accesos en Amazon S3, validando la interacción entre IAM Roles y Bucket Policies para prevenir fugas de datos.

## Scenario
Se requería subir archivos críticos a buckets específicos de S3. El sistema presentaba restricciones de acceso basadas en políticas de recursos que bloqueaban incluso a usuarios con roles predefinidos, simulando un entorno de "Zero Trust".

## Objectives
- Validar la capacidad de subir objetos a S3 asumiendo roles específicos (IAM Switch Role).
- Identificar y mitigar errores de acceso (403 Access Denied) causados por Bucket Policies restrictivas.

## Tools Used
* **AWS Console:** Gestión de S3 e IAM.
* **IAM Roles:** Para la transición de identidades seguras.
* **Markdown:** Para la documentación técnica del laboratorio.

## Actions Performed
* **Identificación de Roles:** Se utilizó el rol `BucketsAccessRole` para el acceso inicial al Bucket 2.
* **Análisis de Errores:** Se detectó un bloqueo en el Bucket 3 debido a una política JSON que solo permitía el acceso al rol `OtherBucketAccessRole`.
* **Escalada de Privilegios Autorizada:** Se realizó el cambio al rol correcto para completar la carga de archivos.

## Evidence

Análisis de la carga exitosa en el Bucket 2 tras asumir el rol de desarrollo:

![Evidencia Bucket 2](img/backet2.png)

Análisis de la resolución del desafío en el Bucket 3 aplicando la política de recurso correcta:

![Evidencia Bucket 3](img/backet3.png)

## Outcome

**Conclusion:** Se confirmó que las políticas de bucket tienen prioridad sobre los permisos de IAM. El acceso fue exitoso solo tras alinear la identidad con la política del recurso.

**Calificación Final:** 15/15 puntos obtenidos.

![Resultado Final](img/final.png)

## Mitigation Strategies
* Implementar el principio de menor privilegio (PoLP).
* Auditar regularmente las Bucket Policies para evitar configuraciones erróneas que bloqueen el flujo de trabajo.
