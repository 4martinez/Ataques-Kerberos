# ataques-kerberos-mimikatz

# 🛡️ Ataques Kerberos: Generación de Silver & Golden Tickets

**Autor:** Álvaro Martínez Cutillas  
**Fecha:** Abril 2025  
**Entorno:** Laboratorio simulado con Active Directory (AD)

---

## 🎯 Objetivo

Simular ataques avanzados sobre un entorno Windows AD utilizando técnicas de generación de Silver y Golden Tickets con Mimikatz, con el objetivo de obtener acceso persistente sin credenciales válidas.

---

## 🧪 Herramientas utilizadas

- **Mimikatz** – Inyección de tickets Kerberos
- **PowerView** – Enumeración de dominio
- **CrackMapExec** – Obtención de hashes NTDS
- **PowerShell** – Ejecución remota con tickets
- **Klist** – Verificación de tickets activos
- **Kali Linux + Windows Server** – Infraestructura de laboratorio

---

## 🧱 Infraestructura

| Máquina           | IP            | Rol                        |
|------------------|---------------|-----------------------------|
| Kali Linux       | 192.168.56.5  | Atacante (Linux)           |
| Windows User     | 192.168.56.3  | Usuario de dominio         |
| Windows DC       | 192.168.56.2  | Controlador de dominio     |
| Dominio          | example.com   | SID: S-1-5-21-895668554... |

---

## 🔐 Silver Ticket – Fases del ataque

1. **Hash NTLM generado desde Kali** con contraseña conocida (`HeyH0Password`)
2. **Enumeración de dominio** con PowerView
3. **Generación de Silver Ticket** con Mimikatz (`/service:cifs`)
4. **Inyección de ticket** y acceso al recurso compartido sin credenciales

---

## 👑 Golden Ticket – Fases del ataque

1. **Volcado de NTDS hashes con CrackMapExec** (incluyendo `krbtgt`)
2. **Generación de Golden Ticket con Mimikatz** (`/user:Administrator`)
3. **Verificación con Klist** (TGT válido de 10 años)
4. **Conexión remota por PowerShell** sin uso de credenciales

---

## ✅ Resultados

- Se accedió al Controlador de Dominio como `Administrator` sin credenciales reales
- Se confirmó acceso remoto y validación de identidad (`whoami`, `ipconfig`)
- El ejercicio refleja técnicas reales utilizadas en post-explotación y persistencia avanzada

---

## ⚠️ Disclaimer

Este proyecto fue desarrollado exclusivamente con fines educativos y en un entorno controlado.  
No debe ser aplicado en sistemas reales sin autorización expresa.

---

Este proyecto fue realizado como parte de un proceso formativo. La máquina analizada es de acceso público y el contenido aquí compartido es de elaboración propia, con fines educativos y demostrativos.

