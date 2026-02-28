# 🎙️ Transcripción de Audio con IA en Mac M1

## 📋 Descripción
Proyecto de transcripción automática de audio utilizando **whisply** y **MLX Whisper** en Mac con chip M1. Implementa diarización de hablantes usando Hugging Face.

## 🛠️ Tecnologías utilizadas
- **whisply** - Interfaz de transcripción
- **MLX Whisper** - Modelo optimizado para Apple Silicon
- **pyannote** - Diarización de hablantes
- **Python 3.10** - Entorno virtual
- **Hugging Face** - Autenticación para modelos gated

## ✨ Características implementadas
- ✅ Transcripción de alta calidad con modelo `large-v3-turbo`
- ✅ Identificación de diferentes hablantes (diarización)
- ✅ Interfaz gráfica local
- ✅ Optimización para Mac M1 (Apple Silicon)

## 📸 Capturas de pantalla
*(Aquí pegarás tus imágenes)*

### Interfaz funcionando
![Interfaz whisply](capturas/interfaz_funcionando.png)


### Transcripción con hablantes
![Resultado con diarización](capturas/resultado_transcripcion.png)

## 🚀 Cómo ejecutarlo
```bash
# Clonar configuración
git clone [tu-repo]
cd Transcripcion_whisply

# Activar entorno
python3 -m venv venv
source venv/bin/activate
pip install "whisply[mlx,app]"

# Configurar token (opcional para diarización)
export HUGGINGFACE_TOKEN="tu_token_aqui"

# Ejecutar
whisply app
