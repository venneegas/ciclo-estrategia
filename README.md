# Ciclos — CRM de seguimiento de ovulación

Herramienta ligera, de un solo archivo, para registrar clientas y calcular su calendario de ovulación estimado a partir de la fecha de última menstruación (FUM).

## Qué hace

- Guarda una ficha por clienta: nombre, contacto, edad, regularidad del ciclo, FUM, duración promedio del ciclo, duración de la fase lútea y notas clínicas.
- Calcula automáticamente:
  - Fecha de ovulación estimada
  - Ventana fértil (5 días antes hasta 1 día después de la ovulación)
  - Próxima menstruación estimada
  - Proyección de los próximos 3 ciclos
- Muestra un calendario visual de 3 meses con los días de menstruación, ventana fértil y ovulación resaltados por clienta.

## Cómo funciona el cálculo

```
inicio_periodo(n)   = FUM + (duración_ciclo × n)
ovulación           = inicio_periodo + (duración_ciclo − duración_fase_lútea)
ventana_fértil      = [ovulación − 5 días, ovulación + 1 día]
próxima_menstruación = inicio_periodo + duración_ciclo
```

Por defecto la fase lútea se asume de 14 días (rango normal 9–17); es editable por clienta.

> **Nota importante:** es una estimación matemática que asume regularidad de ciclo. En ciclos irregulares o con pocos datos, el margen de error puede ser de varios días. No reemplaza métodos de confirmación (monitoreo de LH, temperatura basal, ecografía) ni criterio clínico. No es un método anticonceptivo.

## Privacidad y almacenamiento de datos

Todos los datos se guardan **únicamente en el navegador** de quien lo usa (`localStorage`). No hay backend, no se envía información a ningún servidor, y los datos no son accesibles desde otro dispositivo o navegador. Si limpias el caché del navegador o cambias de equipo, los datos no se transfieren automáticamente.

## Cómo usarlo

1. Abre `crm-ciclos.html` en cualquier navegador moderno (Chrome, Safari, Firefox, Edge). No requiere instalación ni servidor.
2. Haz clic en **"+ Nueva clienta"** para crear una ficha.
3. Completa al menos el nombre, la FUM y la duración del ciclo, y guarda los cambios.
4. Revisa el resumen del ciclo actual, los próximos 3 ciclos y el calendario visual.

## Alcance y limitaciones

- Pensado para uso individual o de una sola profesional gestionando su propia cartera de clientas desde su propio navegador.
- No incluye autenticación, backup en la nube ni sincronización entre dispositivos.
- No sustituye asesoría médica ni herramientas clínicas de diagnóstico.
