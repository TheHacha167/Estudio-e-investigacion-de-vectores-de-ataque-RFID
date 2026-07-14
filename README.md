# Estudio e investigación de vectores de ataque RFID

Repositorio de evidencias experimentales asociado al Trabajo Fin de Máster:

**Estudio e investigación de vectores de ataque RFID**

**Autores:** Jesús Rodríguez Hijona y Tomás Salvador Salgueiro  
**Titulación:** Máster Universitario en Ciberseguridad  
**Universidad:** Universidad Internacional de La Rioja (UNIR)  
**Curso académico:** 2025-2026

---

## Descripción

Este repositorio contiene las evidencias experimentales recopiladas durante la realización del Trabajo Fin de Máster **Estudio e investigación de vectores de ataque RFID**.

El trabajo analiza de forma práctica la seguridad de cuatro tecnologías RFID/NFC:

- EM4100
- MIFARE Classic 1K
- MIFARE Ultralight EV1
- MIFARE DESFire EV1

Las pruebas se realizaron en un entorno de laboratorio controlado, utilizando principalmente un Proxmark3 RDV4 con firmware Iceman/RFID Research Group.

El repositorio complementa la memoria del TFM mediante:

- Registros de consola
- Resultados de identificación
- Evidencias de lectura y escritura
- Recuperación de claves
- Volcados de memoria anonimizados
- Pruebas de clonación y verificación
- Pruebas de cambio y restauración de claves
- Grabaciones audiovisuales de los principales experimentos

El objetivo es mejorar la trazabilidad, transparencia y reproducibilidad de los resultados descritos en la memoria.

---

## Alcance ético y legal

Todas las pruebas se realizaron exclusivamente sobre tarjetas, etiquetas, llaveros y dispositivos propiedad de los autores y adquiridos para su utilización en laboratorio.

No se realizaron pruebas sobre:

- Credenciales de terceros
- Sistemas de control de acceso en producción
- Tarjetas de pago
- Lectores o controladoras ajenas
- Infraestructuras sin autorización expresa
- Información personal o confidencial

El contenido se publica exclusivamente con fines académicos, defensivos, formativos y de reproducibilidad.

La existencia de comandos, registros o vídeos no constituye autorización para aplicar estas técnicas sobre sistemas ajenos.

---

## Entorno experimental

- **Dispositivo principal:** Proxmark3 RDV4
- **Firmware:** Iceman / RFID Research Group
- **Versión:** 4.21611
- **Frecuencias analizadas:** 125/134 kHz y 13,56 MHz
- **Tecnologías evaluadas:** EM4100, MIFARE Classic 1K, MIFARE Ultralight EV1 y MIFARE DESFire EV1

También se emplearon, cuando resultó necesario:

- Etiquetas T5577 regrabables
- Tarjetas MIFARE Classic regrabables de distintas generaciones
- Flipper Zero
- Chameleon Ultra
- Ordenador de análisis para el almacenamiento de registros y volcados

---

## Estructura del repositorio

```text
Estudio-e-investigacion-de-vectores-de-ataque-RFID/
├── README.md
├── LICENSE.md
├── evidencias/
│   ├── em4100/
│   ├── mifare-classic/
│   ├── mifare-ultralight-ev1/
│   └── mifare-desfire-ev1/
├── dumps/
├── videos/
└── documentacion/
```

---

## Evidencias de EM4100

Las pruebas sobre EM4100 incluyen la identificación de la tecnología, la lectura del identificador, su reproducción sobre una etiqueta T5577 y la verificación posterior.

### Archivos de consola

```text
00_identificacion_lf_search.txt
01_lectura_em4100.txt
02_clonacion_em4100.txt
03_verificacion_em4100.txt
```

### Vídeo

[Vídeo 1 — Copiar EM4100 a T5577](https://youtu.be/opEQlmbebFo)

El vídeo muestra:

1. Identificación del llavero EM4100.
2. Lectura del identificador de la credencial.
3. Clonación del identificador sobre una etiqueta T5577 regrabable.
4. Verificación de que la nueva etiqueta reproduce correctamente el identificador original.

La grabación documenta el proceso completo de clonación de una credencial EM4100 en un entorno de laboratorio controlado.

---

## Evidencias de MIFARE Classic 1K

Las pruebas incluyen tres escenarios:

1. Claves predeterminadas
2. Personalización parcial de claves
3. Personalización completa de claves

También se documenta la clonación sobre tarjetas regrabables y la comparación entre distintos tipos de credenciales.

### Archivos de consola

```text
00_identificacion_hf_search_tarjeta.txt
01_autopwn.txt
02_clonacion_gen1a.txt
03_verificacion_clon.txt
04_cambio_claves_custom.txt
05_static_nested_ataque.txt
06_claves_completas_fallo.txt
07_info_original.txt
08_info_gen1a.txt
09_info_gen2.txt
10_info_gen3.txt
11_info_llavero.txt
12_identificacion_hf_search_llavero.txt
13_autopwn_llavero.txt
```

### Vídeo

[Vídeo 2 — Recuperación de claves y lectura de sectores de MIFARE Classic 1K](https://youtu.be/-vQIvSAxuf0)

El vídeo muestra:

1. Identificación de la tarjeta MIFARE Classic 1K.
2. Obtención de la información de la tarjeta mediante Proxmark3.
3. Consulta de sus características y parámetros principales.

La grabación corresponde a la fase de identificación y caracterización inicial de la tarjeta utilizada durante la evaluación experimental.

---

## Evidencias de MIFARE Ultralight EV1

Las pruebas analizan la memoria accesible, las operaciones de escritura, la configuración de contraseña y el efecto del parámetro de protección `AUTH0`.

### Archivos de consola

```text
01_identificacion_hf_search.txt
02_info_hf_mfu_info.txt
03_dump_memoria.txt
04_escritura_sin_password.txt
05_lectura_verificacion.txt
06_restauracion_pagina.txt
07_config_password_custom.txt
08_config_auth0.txt
09_escritura_sin_pwd_falla.txt
10_escritura_pwd_default_falla.txt
11_escritura_pwd_correcto_ok.txt
12_pwdgen.txt
```

Los resultados corresponden a la muestra analizada y a su configuración inicial.

---

## Evidencias de MIFARE DESFire EV1

Las pruebas analizan el estado inicial de la tarjeta, la autenticación mediante la clave maestra predeterminada del nivel PICC, el cambio de dicha clave y la verificación posterior.

### Archivos de consola

```text
01_identificacion_hf_search.txt
02_info_hf_mfdes_info.txt
03_lsapp_sin_auth.txt
04_auth_clave_default.txt
05_getuid.txt
06_freemem.txt
07_changekey_custom.txt
08_auth_clave_default_falla.txt
09_auth_clave_custom_ok.txt
10_restauracion_clave_default.txt
```

### Vídeo

[Vídeo 3 — Identificación de una tarjeta MIFARE DESFire EV1](https://youtu.be/d1-o3jhK1DQ)

El vídeo muestra:

1. Identificación de la tarjeta MIFARE DESFire EV1 mediante Proxmark3.
2. Detección de la tecnología y obtención de la información básica de la credencial (UID anonimizado, ATQA, SAK y características del protocolo ISO/IEC 14443-A).

La grabación documenta el proceso de identificación y caracterización inicial de la tarjeta antes de la realización de las pruebas experimentales descritas en el Trabajo Fin de Máster.

---

## Volcados de memoria

El repositorio incluye volcados JSON asociados a las muestras de laboratorio.

Antes de su publicación deben anonimizarse y renombrarse para evitar exponer UID reales.

Nombres recomendados:

```text
classic_sample_01_dump.json
classic_sample_02_dump.json
ultralight_sample_01_dump.json
```

Los volcados publicados deben eliminar o sustituir:

- UID
- Claves
- Contraseñas
- PACK
- Datos de usuario
- Rutas locales
- Información reutilizable

---

## Grabaciones audiovisuales

| Vídeo | Descripción | Enlace |
|---|---|---|
| Vídeo 1 | Copia de una credencial EM4100 sobre un soporte T5577 | [Ver vídeo](https://youtu.be/opEQlmbebFo) |
| Vídeo 2 | Recuperación de claves y lectura de sectores de MIFARE Classic 1K | [Ver vídeo](https://youtu.be/-vQIvSAxuf0) |
| Vídeo 3 | Evaluación y cambio de clave en MIFARE DESFire EV1 | [Ver vídeo](https://youtu.be/d1-o3jhK1DQ) |

Antes de compartir los vídeos públicamente se debe comprobar que no muestran:

- UID reales
- Claves o contraseñas
- Nombres de usuario
- Rutas locales
- Números de serie
- Datos personales
- Información de sistemas reales

---

## Correspondencia con la memoria del TFM

| Tecnología | Evidencia | Apartado del TFM |
|---|---|---|
| EM4100 | Identificación y lectura | 5.2.1 y 5.2.2 |
| EM4100 | Reproducción sobre T5577 | 5.2.3 |
| MIFARE Classic | Claves predeterminadas | 5.3.2 |
| MIFARE Classic | Static Nested | 5.3.3 |
| MIFARE Classic | Claves personalizadas | 5.3.4 |
| MIFARE Classic | Detección de tarjetas regrabables | 5.3.5 |
| MIFARE Classic | Comparación con llavero | 5.3.6 |
| MIFARE Ultralight EV1 | Lectura de memoria | 5.4.3 |
| MIFARE Ultralight EV1 | Configuración de protecciones | 5.4.4 |
| MIFARE DESFire EV1 | Identificación y acceso | 5.5.1 y 5.5.2 |
| MIFARE DESFire EV1 | Clave maestra predeterminada | 5.5.3 |
| MIFARE DESFire EV1 | Resistencia sin clave conocida | 5.5.4 |

---

## Anonimización

Antes de publicar las evidencias se deben eliminar o sustituir:

- Identificadores reales
- Claves reutilizables
- Contraseñas
- Claves de sesión
- Nombres de usuario
- Rutas del sistema de archivos
- Números de serie
- Información personal
- Referencias a sistemas o instalaciones reales

Los valores sustituidos pueden aparecer como:

```text
[UID_REDACTED]
[KEY_REDACTED]
[PASSWORD_REDACTED]
[LOCAL_PATH_REDACTED]
```

---

## Integridad de las evidencias

Se recomienda calcular un hash SHA-256 para cada archivo publicado.

```bash
find evidencias -type f -exec sha256sum "{}" \; > checksums.sha256
```

Comprobación:

```bash
sha256sum -c checksums.sha256
```

La versión asociada a la entrega final del TFM debe identificarse mediante una etiqueta:

```text
v1.0.0
```

---

## Limitaciones

Las pruebas se realizaron sobre un número reducido de muestras. Por ello, el repositorio no demuestra que:

- Todas las credenciales de una misma familia se comporten de forma idéntica
- Una credencial reproducida sea aceptada por cualquier sistema de producción
- Un ataque que no tuvo éxito en laboratorio sea imposible en otras condiciones
- Los tiempos registrados sean aplicables a cualquier entorno
- Las herramientas utilizadas cubran todos los vectores de ataque existentes

---

## Uso responsable

Este repositorio no debe utilizarse para:

- Acceder a sistemas sin autorización
- Copiar credenciales pertenecientes a terceros
- Modificar tarjetas ajenas
- Interferir con sistemas de control de acceso
- Realizar pruebas sobre infraestructuras en producción sin permiso
- Obtener datos personales o confidenciales

Los autores no respaldan el uso ilegal o no autorizado de las técnicas documentadas.

---

## Citación

Para citar el repositorio:

> Rodríguez Hijona, J., & Salvador Salgueiro, T. (2026). *Estudio e investigación de vectores de ataque RFID: evidencias experimentales y materiales de reproducibilidad* (Versión 1.0.0).

Para citar el trabajo académico:

> Rodríguez Hijona, J., & Salvador Salgueiro, T. (2026). *Estudio e investigación de vectores de ataque RFID* [Trabajo Fin de Máster, Universidad Internacional de La Rioja].

---

## Licencia

La documentación del repositorio puede publicarse bajo una licencia Creative Commons Attribution 4.0 International, siempre que sea compatible con las normas de la Universidad Internacional de La Rioja.

Las grabaciones y los volcados pueden estar sujetos a condiciones adicionales debido a la naturaleza del contenido experimental.

---

## Contacto

Las consultas académicas relacionadas con este repositorio deberán realizarse a través de los perfiles de los autores o mediante los canales asociados a la entrega institucional del Trabajo Fin de Máster.
