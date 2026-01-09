# Simón Inteligencia Inmobiliaria

## Instrucciones para Claude Code

### Archivos en esta carpeta:
- `src/App.jsx` - Componente React (YA LISTO con botón PDF corregido)
- `public/` - Aquí va el PDF (descargalo de Claude.ai)

### Paso 1: Descargar el PDF
Descarga el archivo `simon-inteligencia-inmobiliaria-dic2025.pdf` desde Claude.ai y ponelo en la carpeta `public/`

### Paso 2: Abrir Claude Code aquí
```bash
cd "C:\Users\LUCHO\Desktop\Censo inmobiliario\simon-intel"
claude
```

### Paso 3: Decile a Claude Code:
```
Inicializa un proyecto Vite + React aquí.
El App.jsx ya está en src/.
El PDF está en public/.
Solo necesito que configures Vite y hagas deploy a Vercel.
No uses TypeScript.
```

### Estructura final esperada:
```
simon-intel/
├── public/
│   └── simon-inteligencia-inmobiliaria-dic2025.pdf
├── src/
│   ├── App.jsx (✅ YA ESTÁ)
│   └── main.jsx (Claude Code lo crea)
├── index.html (Claude Code lo crea)
├── package.json (Claude Code lo crea)
└── vite.config.js (Claude Code lo crea)
```
