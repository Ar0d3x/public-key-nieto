# Clave Pública PGP

¡Hola! En este repositorio comparto mi clave pública PGP para que puedas cifrar correos electrónicos o mensajes de manera segura, asegurándote de que solo yo pueda leerlos. Es perfecto para comunicaciones confidenciales con Proton Mail, Thunderbird u otras herramientas compatibles con PGP.

*Si te interesa Proton, aquí puedes obtener una prueba gratis de Proton Plus: [enlace recomendado](https://pr.tn/ref/4SVAYXNQ)*

---

## ¿Cómo contactarme de forma segura?

Dependiendo de tu cliente de correo, tienes varias opciones:

### ✅ Opción 1 — ProtonMail o Tuta

**ProtonMail**: De Proton a Proton el cifrado E2E es automático al escribirme a `dr.nietodavid@protonmail.com`.
**Tuta**: puedes enviarme un mensaje cifrado por contraseña (modo "confidencial"). Compárteme la contraseña por un canal seguro como Signal antes de enviar.

### ⚙️ Opción 2 — Usas Thunderbird u otro cliente compatible con PGP

¿Primera vez cifrando correos? Sigue la [guía paso a paso con Thunderbird](#-guía-paso-a-paso-correo-cifrado-con-thunderbird).

Importa mi clave pública desde cualquiera de estas fuentes:

- Este repositorio: [clave-publica-proton.asc](https://raw.githubusercontent.com/Ar0d3x/public-key-nieto/main/clave-publica-proton.asc) (descarga directa del archivo)
- [keys.openpgp.org](https://keys.openpgp.org), buscando por fingerprint
- Directamente con GnuPG (vía WKD):
  ```bash
  gpg --locate-keys dr.nietodavid@protonmail.com
  ```

Si tienes dudas sobre cómo importarla, consulta estas guías:
- [proton.me](https://proton.me)
- [Guía de cifrado asimétrico con Kleopatra — UNAM](https://www.seguridad.unam.mx/sites/default/files/guia-cifrado-asimetrico-con-kleopatra.pdf)
- [keys.openpgp.org](https://keys.openpgp.org)
- [openpgp.org](https://www.openpgp.org)
- [gnupg.org](https://gnupg.org)

**Al escribirme, adjunta tu clave pública** para que pueda responderte cifrado. Recuerda que, en la mayoría de los clientes, el **asunto del correo no se cifra**: usa uno genérico.

---

## 🦅 Guía paso a paso: correo cifrado con Thunderbird

[**Thunderbird**](https://www.thunderbird.net) es el cliente de correo libre y de código abierto de la Fundación Mozilla. Desde la versión 78 trae **OpenPGP integrado**: no necesitas instalar complementos ni programas adicionales. Funciona con cualquier cuenta de correo (Gmail, Outlook, Yahoo, tu dominio propio, etc.) en Windows, macOS y Linux.

> Los nombres de los menús pueden variar ligeramente según tu versión e idioma. Si no ves la barra de menú (Archivo, Editar, Herramientas…), presiona la tecla `Alt`.

### Paso 1 — Configura tu propia clave

Para enviarme correos cifrados y firmados necesitas tu propio par de claves.

1. Ve a **Configuración de la cuenta** → selecciona tu cuenta → **Cifrado de extremo a extremo**.
2. En la sección **OpenPGP**, pulsa **Añadir clave** y elige:
   - **Crear una nueva clave OpenPGP**, si aún no tienes una. Recomiendo el tipo **ECC (Curve25519)**.
   - **Importar una clave OpenPGP existente**, si ya tienes una creada en otro programa.
3. Selecciona la clave para que quede como **predeterminada** de esa cuenta.

**¿Para qué sirve?** Tu clave privada te permite **firmar** tus mensajes (prueba de que vienen de ti) y **descifrar** mis respuestas. Tu clave pública es la que yo usaré para responderte cifrado.

### Paso 2 — Importa mi clave pública

Tienes dos opciones:

**A. Búsqueda automática (la más sencilla)**
1. Abre **Herramientas → Administrador de claves OpenPGP**.
2. Ve a **Servidor de claves → Descubrir claves en línea**.
3. Escribe `dr.nietodavid@protonmail.com` y acepta.

Thunderbird buscará mi clave en keys.openpgp.org y mediante WKD (el directorio que publica Proton).

**B. Desde archivo**
1. Descarga [clave-publica-proton.asc](https://raw.githubusercontent.com/Ar0d3x/public-key-nieto/main/clave-publica-proton.asc).
2. En el **Administrador de claves OpenPGP**, ve a **Archivo → Importar clave(s) pública(s) desde archivo** y selecciónalo.

### Paso 3 — Verifica y acepta mi clave ⚠️

Este es el paso más importante y el que más se omite. Thunderbird **no cifrará** hacia una clave que no hayas aceptado.

1. En el **Administrador de claves OpenPGP**, haz doble clic sobre mi clave para abrir sus **Propiedades**.
2. Compara la **huella digital (fingerprint)** que aparece con esta:
   ```
   969C 0614 BA83 3E17 D0DC 6E5D E194 A408 A68C C1BE
   ```
   Contrástala también con otra fuente independiente (ver [Verificar autenticidad](#verificar-autenticidad)).
3. Solo si coincide exactamente, en **Tu aceptación** marca: **"Sí, he verificado en persona que esta clave tiene la huella digital correcta"**.

**¿Por qué importa?** Si alguien suplantara mi clave, tu mensaje quedaría cifrado para el atacante, no para mí. Verificar el fingerprint es lo que garantiza que solo yo pueda leerlo.

### Paso 4 — Redacta y envía el mensaje cifrado

1. Crea un mensaje nuevo dirigido a `dr.nietodavid@protonmail.com`.
2. En la barra de redacción, activa **Cifrar** (icono de candado). En el menú **OpenPGP** del redactor verifica que estén activas:
   - **Requerir cifrado**
   - **Firmar digitalmente**
   - **Adjuntar mi clave pública** (así podré responderte cifrado)
3. Si todo está bien, el pie de la ventana mostrará el estado de cifrado en verde. Si Thunderbird avisa que falta una clave o que no está aceptada, vuelve al Paso 3.
4. Envía.

**Sobre el asunto:** Thunderbird puede ocultar el asunto real dentro de la parte cifrada (opción **Cifrar el asunto** en *Cifrado de extremo a extremo → Configuración avanzada*). Aun así, el remitente, el destinatario, la fecha y los servidores por los que pasa el correo siguen siendo visibles: PGP protege el **contenido**, no los metadatos.

### Paso 5 — Lee mi respuesta

Cuando te responda, Thunderbird descifrará el mensaje automáticamente con tu clave privada y mostrará un indicador de que el mensaje estaba cifrado y firmado por mí.

> 💾 **Respalda tu clave privada.** Si la pierdes, no podrás leer los correos cifrados que recibas. En el **Administrador de claves OpenPGP**, selecciona tu clave → **Archivo → Respaldar claves secretas en archivo**, y guarda ese respaldo en un lugar seguro y cifrado.

---

## Clave Pública

### 🔑 ProtonMail

Para comunicaciones profesionales y confidenciales.

| Campo | Valor |
|---|---|
| **Email** | dr.nietodavid@protonmail.com |
| **Fingerprint** | `969C 0614 BA83 3E17 D0DC 6E5D E194 A408 A68C C1BE` |
| **Algoritmo** | Ed25519 / Curve25519 |

Descarga: [clave-publica-proton.asc](https://raw.githubusercontent.com/Ar0d3x/public-key-nieto/main/clave-publica-proton.asc)

```
-----BEGIN PGP PUBLIC KEY BLOCK-----

xjMEY+r88BYJKwYBBAHaRw8BAQdAYo1IYlCEVAC4VcSKX3VUOlNCGVRKqr5N
7JTjXSdEQRTNO2RyLm5pZXRvZGF2aWRAcHJvdG9ubWFpbC5jb20gPGRyLm5p
ZXRvZGF2aWRAcHJvdG9ubWFpbC5jb20+wowEExYIAD4FAmPq/PAJkOGUpAim
jMG+FiEElpwGFLqDPhfQ3G5d4ZSkCKaMwb4CGwMCHgECGQEDCwkHAhUIAxYA
AgIiAQAAaMYBAObb896uEcZtpLmLW6Ob9tkX940feZToMJQAut/fwSK8AP43
ICs2sqCYya4j8ZKk2WehwuqmNm1gCSAgS5jN2Yf6B844BGPq/PASCisGAQQB
l1UBBQEBB0B2ZbuwRkjJdhhJMMQKsBe5r/kSlTQqCxxnx+440+fTdAMBCgnC
eAQYFggAKgUCY+r88AmQ4ZSkCKaMwb4WIQSWnAYUuoM+F9Dcbl3hlKQIpozB
vgIbDAAAlBEA/3I7c0ttCVa/yiIUiLeVQUZCXcFHGAhNEs2wt3Inc6e5AP9C
XoKMgV1LAckTOi5pE11W7n3zWeiDQnthDL3w7dPFCw==
=lz6O
-----END PGP PUBLIC KEY BLOCK-----
```

---

## 📱 Para usuarios de Android

Si quieres cifrar correos desde tu celular, estas son las apps que uso y recomiendo. Todas disponibles en [**F-Droid**](https://f-droid.org) — el repositorio de apps open source y sin rastreadores.

[**OpenKeychain**](https://www.openkeychain.org) — gestión de llaves PGP en Android. Genera, importa y administra tus llaves directamente en tu dispositivo, sin depender de servicios externos. La llave privada nunca sale de tu hardware.

[**K-9 Mail**](https://k9mail.app) — cliente de correo open source con integración nativa con OpenKeychain. Soporta cifrado y firma PGP de forma transparente al redactar y leer correos.

Ambas funcionan perfectamente juntas y son el estándar recomendado para cifrado de correo en Android.

### 🛡️ ¿Quieres ir más lejos?

Si te tomas en serio la privacidad y seguridad, considera [**GrapheneOS**](https://grapheneos.org) — un sistema operativo Android de código abierto, compatible con dispositivos Google Pixel. Ofrece aislamiento de perfiles, cifrado robusto y eliminación de telemetría. OpenKeychain y K-9 funcionan perfectamente en GrapheneOS instaladas desde F-Droid.

---

## Verificar autenticidad

La forma confiable de verificar mi clave es **comparar el fingerprint en fuentes independientes**. Si un atacante alterara una de ellas, no coincidiría con las demás.

1. Importa la clave y muestra su fingerprint:
```bash
gpg --import clave-publica-proton.asc
gpg --fingerprint dr.nietodavid@protonmail.com
```

2. Compáralo con el publicado en al menos **dos** de estas fuentes:
   - Este repositorio (arriba)
   - Mi página personal, alojada en mi propio servidor: [dnieto.ar0drz.site/@david_nieto01](https://dnieto.ar0drz.site/@david_nieto01)
   - [keys.openpgp.org](https://keys.openpgp.org)
   - Pregúntamelo directamente por Signal

Debe coincidir exactamente:

```
969C 0614 BA83 3E17 D0DC 6E5D E194 A408 A68C C1BE
```

---

¡Gracias por visitar! Si me contactas usando esta clave, verifica siempre el fingerprint para evitar suplantación. Si actualizo la clave en el futuro, lo anunciaré aquí con un nuevo commit. ¿Tienes dudas? Envíame un correo cifrado y charlamos. 😊
