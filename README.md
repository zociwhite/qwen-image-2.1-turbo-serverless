# Qwen-Image-2.1-Turbo Serverless (RunPod)

RunPod serverless worker for [Qwen/Qwen-Image-2.1-Turbo](https://huggingface.co/Qwen/Qwen-Image-2.1-Turbo)
via `diffusers.QwenImage21Pipeline` with **8 denoising steps** & **CFG=1** default.

- **Text-to-image**: omit `images` -> `prompt` + optional `width`/`height`.
- **Image editing**: pass `images` (1-10, base64 / data-URI / URL) or `image`.
- **Speed**: ~3-6 detik per gambar (8-step distilled).
- **RGBA transparency** supported.

## Input (`{"input": {...}}`)

| Key | Wajib | Default | Catatan |
|---|---|---|---|
| `prompt` | Ya | - | Deskripsi gambar baru / instruksi edit |
| `images` | Tidak | [] | 1-10 referensi (base64 raw, data URI, URL) |
| `image` | Tidak | - | Alias gambar pertama |
| `width` / `height` | Tidak | 1024 / 1024 | T2I (default 1024; preset 16:9 2752x1536) |
| `steps` | Tidak | 8 | Schedule 8-step bawaan checkpoint |
| `guidance_scale` | Tidak | 1.0 | Default 1.0 (single pass) |
| `seed` | Tidak | random | Integer |
| `output_format` | Tidak | png | png \| jpeg \| webp |

## Output

```json
{
  "image": "<base64 RAW>",
  "format": "png",
  "model": "Qwen/Qwen-Image-2.1-Turbo",
  "steps": 8
}
```
