# Cortocircuito y selectividad en tableros BT

Herramienta web para calcular corrientes de cortocircuito en tableros de baja tensión y verificar protecciones y selectividad.

**Uso:** abrir la página publicada en GitHub Pages, o el archivo `index.html` directamente en el navegador. No requiere instalación ni servidor.

## Qué calcula

- Ik3 máx, ip, Ik1 máx, Ik3/Ik2/Ik1 mín por barra, según IEC 60909-0 (factor c, K_T, κ, aporte de motores).
- Panel de bornes del transformador: R, X, Z de red, trafo y total; In del transformador.

## Qué verifica

| Verificación | Norma |
|---|---|
| Poder de corte Icu ≥ Icc presunta | AEA 90364-4-43, 434.5.1 |
| Ib ≤ In ≤ Iz | AEA 90364-4-43, 433.1 |
| Desconexión automática a Icc mín (0,4 s / 5 s) | AEA 90364-4-41, 411.3.2 |
| I²t ≤ k²S² (fase y PE) | AEA 90364-4-43, 434.5.2; AEA 90364-5-54, 543.1.2 |
| Selectividad por bandas tiempo-corriente | IEC 60947-2 anexo A; AEA 90364-5-53, 536 |
| Icw / Ipk del tablero frente a Ik3 / ip | IEC 61439-1/-2 |

Las cláusulas AEA siguen la numeración IEC 60364. Confirmar contra la edición vigente de cada proyecto.

## Limitaciones

- Las curvas de disparo son bandas genéricas según IEC 60947-2, no curvas de un fabricante. El límite de selectividad en zona instantánea debe tomarse de las tablas del fabricante y cargarse en el campo correspondiente.
- Sin I²t pasante de catálogo, la verificación térmica usa I²·t de apertura (conservador para interruptores limitadores).
- Secuencia cero de cables aproximada como lazo (R + Rpe) + j2X.
- No incluye fusibles, función G ni la selectividad con la protección MT del transformador.
- Pk debe ser la pérdida en carga del protocolo de ensayo, no la pérdida en vacío P0.

## Datos

Los proyectos se guardan solo en el navegador de cada usuario (localStorage). Para compartir un proyecto, usar "Guardar o cargar proyecto" y pasar el JSON.

Herramienta de apoyo al cálculo. Los resultados deben ser revisados por el responsable técnico del proyecto.
