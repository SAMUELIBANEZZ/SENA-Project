
# Fundamentos de Infraestructura y Ciberseguridad

Este documento recopila los conceptos técnicos y teóricos esenciales que sustentan la arquitectura de red y las políticas de seguridad del proyecto "Cúcuta Segura".

## 1. Segmentación de Redes y VLANs

La segmentación es una técnica de seguridad que divide una red física en múltiples redes lógicas (VLANs). Esto reduce la superficie de ataque, limita los dominios de broadcast y aísla el tráfico sensible.

* **SVI (Switch Virtual Interface):** Interfaz lógica configurada en un switch multicapa o de capa 2 para permitir la administración remota o el enrutamiento inter-VLAN.
* **Caso de Aplicación:** Implementación de una VLAN de administración (ej. `VLAN 99`) aislada del tráfico de usuarios.

> **Ejemplo de Configuración de Gestión SVI (Dual Stack):**
> Para garantizar la administración segura del equipo, se asignan direcciones IPv4 e IPv6 a la interfaz virtual:
> `interface vlan 99`
> `ip address 192.168.1.2 255.255.255.0`
> `ipv6 address 2001:db8:acad:1::2/64`
> El control de conectividad se verifica posteriormente mediante pruebas de ping de extremo a extremo hacia ambas direcciones.

## 2. Paradigma Zero-Trust (Confianza Cero)

Modelo de seguridad que asume que ninguna entidad (usuario, dispositivo o aplicación), ya sea dentro o fuera del perímetro de la red, es confiable por defecto. Todo acceso debe ser verificado de forma continua.

* **Referencia Técnica:** Modelo estandarizado por el **NIST SP 800-207**.

## 3. Amenazas Comunes en la Región

En el contexto del análisis para Cúcuta, se identifican vectores de ataque prevalentes:

* **Phishing:** Suplantación de identidad para el robo de credenciales.
* **Ransomware:** Secuestro de datos mediante cifrado, exigiendo rescate.
* **Ataques a Redes Inalámbricas:** Interceptación de tráfico en redes Wi-Fi públicas o con cifrado débil (WPA2 vulnerable), mitigable mediante auditorías con adaptadores en modo monitor.

## 4. Referencias y Bibliografía

1. **Cisco Networking Academy:** *Switching, Routing, and Wireless Essentials*. (Conceptos de VLANs y SVIs).
2. **NIST (National Institute of Standards and Technology):** *Zero Trust Architecture (SP 800-207)*.
3. **OWASP:** *Top 10 Vulnerabilidades de Seguridad*.
