Informe de Laboratorio: Seguridad en Amazon S3 y Roles IAM

1\. Resumen Ejecutivo

Este laboratorio demuestra la implementación de controles de acceso en AWS mediante el uso de identidades de IAM y políticas basadas en recursos. Se validó cómo las políticas de bucket pueden restringir acciones incluso cuando se poseen roles con permisos generales.



2\. Tareas Realizadas y Evidencias

Tarea 5: Acceso al Bucket 2 mediante IAM Roles

Proceso: Se realizó la transición de la identidad devuser al rol BucketsAccessRole.



Resultado: Se obtuvo la autorización para cargar el archivo Image2.jpg exitosamente.



Tarea 6: Desafío de Política de Bucket (Bucket 3)

Conflicto: El acceso al bucket3 estaba denegado por una política JSON que exigía específicamente el rol OtherBucketAccessRole.



Solución: Se utilizó la función Switch Role para adoptar la identidad requerida por el recurso.



Resultado: La carga del objeto fue permitida tras la validación de la política del bucket.



3\. Conclusión y Calificación Final

Se logró comprender que la seguridad en AWS es una capa combinada: la identidad debe tener permiso y el recurso debe permitir esa identidad.



Puntaje Total: 15/15.



!\[Puntaje Final](final.png)

