## 📥 **Guía de instalación detallada para Transcripción con whisply en Mac M1**

```markdown
# Guía de instalación detallada

## 📋 Requisitos previos

### Hardware
- Mac con chip **Apple Silicon (M1, M2, M3)**
- Mínimo 8GB RAM (16GB recomendado para audios largos)
- 10GB de espacio libre (para modelos y dependencias)

### Software necesario
- **macOS Ventura o superior**
- **Python 3.10** (versión específica para compatibilidad)
- **Homebrew** (gestor de paquetes de macOS)
- **Git** (para clonar el repositorio)
- **FFmpeg** (para procesamiento de audio)

## 🚀 Instalación paso a paso

### Paso 1: Instalar Homebrew (si no lo tienes)
Abre la Terminal y ejecuta:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Verifica la instalación:
```bash
brew --version
```

### Paso 2: Instalar FFmpeg
```bash
brew install ffmpeg
```

Verifica:
```bash
ffmpeg -version
```

### Paso 3: Instalar Python 3.10
```bash
# Instalar Python 3.10 específicamente
brew install python@3.10

# Verificar instalación
python3.10 --version
```

### Paso 4: Clonar el repositorio
```bash
# Ir al directorio donde quieres guardar el proyecto
cd ~/Documentos  # o la carpeta que prefieras

# Clonar el repositorio
git clone https://github.com/TU_USUARIO/transcripcion-whisply-m1.git
cd transcripcion-whisply-m1
```

### Paso 5: Crear y activar entorno virtual
```bash
# Crear entorno virtual con Python 3.10
python3.10 -m venv venv

# Activar el entorno virtual
source venv/bin/activate
```
Verás que el prompt cambia a `(venv)` al inicio de la línea.

### Paso 6: Instalar dependencias
```bash
# Actualizar pip
pip install --upgrade pip

# Instalar todas las dependencias
pip install -r requirements.txt

# O instalar whisply directamente con todas las opciones
pip install "whisply[mlx,app]"
```

### Paso 7: Configurar Hugging Face (para diarización)

#### 7.1 Crear cuenta en Hugging Face
1. Ve a [huggingface.co](https://huggingface.co/)
2. Haz clic en "Sign Up" y crea tu cuenta gratuita

#### 7.2 Aceptar condiciones de los modelos
Acepta los términos en estos dos enlaces (necesitas iniciar sesión):
- [pyannote/speaker-diarization-3.1](https://hf.co/pyannote/speaker-diarization-3.1)
- [pyannote/segmentation-3.0](https://hf.co/pyannote/segmentation-3.0)

Busca el botón **"Agree and access repository"** en cada página.

#### 7.3 Generar token de acceso
1. Ve a [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)
2. Haz clic en **"New token"**
3. Nombre: `whisply-mac`
4. Rol: **"read"** (solo lectura)
5. Copia el token generado (empieza con `hf_`)

### Paso 8: Probar la instalación

#### Opción A: Interfaz gráfica (recomendada para empezar)
```bash
# Configurar token (opcional, solo para diarización)
export HUGGINGFACE_TOKEN="hf_token_que_copiaste"

# Iniciar la interfaz
whisply app
```
Luego abre tu navegador en: **http://127.0.0.1:7860**

#### Opción B: Línea de comandos (para pruebas rápidas)
```bash
# Transcripción simple sin diarización
whisply run ruta/a/tu/audio.mp3 --model large --language es --no-diarize

# Transcripción con diarización (requiere token)
export HUGGINGFACE_TOKEN="hf_token_que_copiaste"
whisply run ruta/a/tu/audio.mp3 --model large --language es --diarize
```

## 🎯 Verificación de la instalación

Ejecuta estas comprobaciones para asegurarte de que todo funciona:

```bash
# 1. Verificar entorno virtual (debe mostrar (venv))
which python

# 2. Verificar versión de whisply
whisply --version

# 3. Ver modelos disponibles
whisply list

# 4. Probar con un audio de ejemplo pequeño
# Descarga un audio de prueba corto
curl -o prueba.wav https://www2.cs.uic.edu/~i101/SoundFiles/taunt.wav

# Transcríbelo
whisply run prueba.wav --model tiny --language en --no-diarize

# Ver el resultado
cat prueba.txt
```

## ⚙️ Configuración avanzada

### Hacer permanente el token de Hugging Face
Para no tener que exportar el token cada vez:
```bash
# Añadir al archivo de configuración del shell
echo 'export HUGGINGFACE_TOKEN="hf_token_que_copiaste"' >> ~/.zshrc

# Recargar configuración
source ~/.zshrc
```

### Configurar carpeta por defecto para transcripciones
```bash
# Crear alias para comando rápido
echo 'alias transcribe="whisply run --model large --language es --no-diarize --output ~/Transcripciones"' >> ~/.zshrc
source ~/.zshrc

# Usar: transcribe mi_audio.mp3
```

## 🐛 Solución de problemas comunes

### Error: "Command not found: whisply"
```bash
# Solución: Activar entorno virtual
cd ~/transcripcion-whisply-m1
source venv/bin/activate
```

### Error: "No module named 'mlx'"
```bash
# Solución: Instalar soporte MLX explícitamente
pip install "whisply[mlx]"
```

### Error: "Token required for pyannote"
```bash
# Solución: Exportar token y aceptar condiciones
export HUGGINGFACE_TOKEN="hf_token..."
# Asegúrate de haber aceptado las condiciones en los enlaces
```

### Error: "FFmpeg not found"
```bash
# Solución: Instalar FFmpeg
brew install ffmpeg
```

### Error de memoria para audios muy largos
```bash
# Usar modelo más pequeño o fragmentar el audio
whisply run audio_largo.mp3 --model medium --language es
```


¡Ya estás listo para transcribir! 🎉

## 📚 Recursos adicionales
- [Documentación oficial de whisply](https://pypi.org/project/whisply/)
- [Guía de tokens de Hugging Face](https://huggingface.co/docs/hub/security-tokens)
- [MLX Documentation](https://ml-explore.github.io/mlx/)
