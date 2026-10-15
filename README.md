# demo-monorepo

Repositori uji untuk membandingkan Trivy v0.56.2 dan v0.74.0.
Setiap folder adalah satu submodule dengan ekosistem berbeda.

## Hasil yang diharapkan (scan SCA)

| Target | Trivy 0.56.2 | Trivy 0.74.0 |
| --- | --- | --- |
| backend-go/go.mod | 38 | 38 (versi tampil dengan awalan `v`) |
| backend-php/composer.lock | 20 | 20 |
| frontend/package-lock.json | 30 | 30 |
| service-java/pom.xml | 21 | 21 |
| service-python/requirements.txt | 43 | 43 |
| worker-python/uv.lock | 0 (tidak terbaca) | 15 |
| **Total** | **152** | **167** |

Angka bisa berbeda di environment lain karena vulnerability DB terus diperbarui;
yang penting selisihnya hanya dari `uv.lock`.

Catatan: `service-java` sengaja dibuat single-module (satu `pom.xml`), karena stage
SAST di pipeline Jenkins belum mendukung repo dengan lebih dari satu `pom.xml`.
