# Solicitud de viáticos · SiteMinder México

Formulario web para que los colaboradores de SiteMinder México soliciten viáticos. El monto se calcula automáticamente conforme al Anexo B de la política y se dispersa en la tarjeta Minu del colaborador.

Administrado por **Sinergia Corporativo**.

## Arquitectura

```
Colaborador  →  index.html (GitHub Pages)
                    ↓ POST JSON
                Google Apps Script (Sinergia)
                    ├── Calcula monto conforme a Anexo B
                    ├── Guarda en Google Sheet (control)
                    ├── Notifica por correo (Líder, Finanzas, Sinergia)
                    └── Envía acuse al colaborador
```

## Configuración

Antes de publicar, hay que llenar dos parámetros:

1. En `index.html`, reemplazar `APPS_SCRIPT_URL` por la URL de la aplicación web publicada en Apps Script.
2. En la Apps Script (`Calculadora_Viaticos_Siteminder_v5.gs`), reemplazar `SHEET_ID`, `FINANZAS_EMAIL` y `SINERGIA_EMAIL` por los valores reales.

## Deploy

1. Subir el repo a GitHub y activar GitHub Pages desde la rama `main`.
2. La URL pública queda como `https://<usuario>.github.io/<repo>/`.
3. URLs personalizadas con prefill por query params: `?colaborador=Nombre&puesto=Cargo&area=Área&lider_email=lider@siteminder.com`.

## Anexo B (topes vigentes)

| Concepto | Nacional | Internacional |
|---|---|---|
| Alimentación (diaria, libre distribución entre 3 comidas) | $750 | $1,500 |
| Hospedaje (por noche) | $3,000 | $3,850 |
| Transporte local (por trayecto) | $500 | $500 |
| Renta de auto (por día, máx. 7) | $850 | $850 |
| Comunicaciones (por día) | No aplica | $500 |

Conceptos abiertos (tarifa de mercado, sujetos a comprobación): transporte aéreo / tren / autobús, combustible, peajes y casetas, capacitación.

## Soporte

Para dudas, ajustes o reportes: Sinergia Corporativo.
