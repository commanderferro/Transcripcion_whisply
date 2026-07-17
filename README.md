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

## 📸 Capturas de pantalla de la terminal

<img width="594" height="385" alt="Terminal_funcionando" src="https://github.com/user-attachments/assets/8bc8d626-9f48-4f64-965d-0cbeaabc1fd8" />


### Interfaz whisply funcionando

<img width="1332" height="752" alt="Interfaz finalizando el proceso" src="https://github.com/user-attachments/assets/a0aac78f-ca9e-42c3-93c6-2ad311beca3a" />


### Transcripción con hablantes

<img width="1033" height="327" alt="ejemplo de diarizacion" src="https://github.com/user-attachments/assets/85cfa246-465d-4ddd-b7ef-59a8c887a16c" />

## 🚀 Cómo ejecutarlo
```bash
# Clonar configuración
git clone https://github.com/commanderferro/Transcripcion_whisply
cd Transcripcion_whisply

# Activar entorno
python3 -m venv venv
source venv/bin/activate
pip install "whisply[mlx,app]"

# Configurar token (opcional para diarización)
export HUGGINGFACE_TOKEN="tu_token_aqui"

# Ejecutar
whisply app
