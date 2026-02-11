# Tarea14-15_SGE

Este repositorio contiene el módulo **fichaje** personalizado para la empresa *Soluciones S.A.*, desarrollado como tarea de práctica.  

El objetivo del módulo es permitir el fichaje de empleados con acciones de **Entrada, Salida y Descanso**, y mostrar la identidad corporativa personalizada en Odoo.

---

## Funcionalidades

1. **Identidad Visual Personalizada**  
   - El menú principal del módulo muestra:  
     `Presencia - MiguelCeballos`  
   - Esto se refleja en el tablero principal de Odoo.

2. **Modelo de Datos**  
   - Campo `tipo_accion` del modelo `fichaje_asistencia` con opciones:  
     - `entrada` → Entrada  
     - `salida` → Salida  
     - `descanso` → Descanso  
   - El campo se guarda correctamente en la base de datos.

3. **Interfaz de Usuario**  
   - Las opciones de `tipo_accion` se muestran correctamente en:
     - Vista lista (`ListView`)
     - Formulario (`FormView`)  

---

## Instalación y Actualización

### Requisitos
- Odoo 17  
- Docker / Docker Compose  
- PostgreSQL (ya incluido en el entorno Docker)

### Pasos

1. Asegurarse de que los contenedores estén activos:
```bash
docker compose up -d
```
2. Actualizar el módulo desde Odoo
  - Ir a Apps → Buscar módulo fichaje → Pulsar Actualizar
Esto recarga los cambios en Python y XML.

3. Verificar que la opción Descanso aparece en el desplegable Accion al crear un nuevo registro.

---

## Validación SQL (pgAdmin)

Para comprobar que el registro se guarda correctamente:
```bash
SELECT *
FROM fichaje_asistencia
WHERE tipo_accion = 'descanso';
```

---

## Archivos clave
  - __manifest__.py -> nombre del módulo y metadatos
  - models/models.py -> definición del modelo fichaje.asistencia y campo tipo_accion
  - views/view.xml -> vistas lista, formularioy menú principal

---

## Resultado esperado

  - Menú principal pereonalizado: Presencia - MiguelCeballos
  - Campo tipo_accion con opción Descanso visible y operativa
  - Registro con tipo_accion = 'descanso' guardado en la base de datos

---

## Capturas
<img width="1365" height="194" alt="descanso" src="https://github.com/user-attachments/assets/2fac1679-bfd8-42ce-a619-fc1dd50c7ac7" />

<img width="1365" height="406" alt="pgadmin" src="https://github.com/user-attachments/assets/b5461a4d-8829-4197-9dff-ba64f6a8785f" />

---

## Notas técnicas

  - Odoo 17 requiere el contenedor y actualizar el módulo para reflejar cambios en campos Python (Selection)
  - En Docker, el módulo debe estar en el volumen correcto ( /mnt/extra-addons) para que Odoo lo lea
