# Motorola Edge 50 Fusion | CUSCO

![Motorola](https://img.shields.io/badge/Motorola-Edge_50_Fusion-087EA4?style=for-the-badge) ![Linux](https://img.shields.io/badge/Linux-5.10-087EA4?style=for-the-badge) ![Root](https://img.shields.io/badge/Root-KernelSU_Next-087EA4?style=for-the-badge)

Projeto de compilação GKI 5.10 com KernelSU Next Built-in e reempacotamento do boot original.

## ROM final 7 — compilação do zero

- Dispositivo: **Motorola Edge 50 Fusion (CUSCO)**.
- Firmware de destino informado pelo proprietário: **W1UUS36H.21-14-4-1-7**.
- [Workflow para compilar o kernel inteiro do zero](.github/workflows/build_kernel_final7.yml).
- [Execução e arquivos produzidos](https://github.com/paradaseimportsoficial-ops/Edge-50-Fusion-KernelSU-Next/actions/runs/45712445884).
- KernelSU Next estável **v3.4.2**, fixado no commit `4c706b5938665866ebe16944a481a7b91e3396af`.
- Compilação com **ThinLTO** e dois processos (`-j2`) para reduzir consumo de recursos; a saída exige CFI e SELinux habilitados na configuração.
- Perfil de compilação: `common/build.config.gki.aarch64`; nome local `-tecnico-root-v1`.
- Os fontes são baixados em um ambiente limpo e o kernel é compilado nessa execução, sem reutilizar kernel de artefato anterior.

O boot original fornecido pelo proprietário está comprimido e dividido em `inputs/final7/`. O workflow recompõe e valida a imagem antes da compilação.

SHA256 do boot original:

```text
83752024f78bb239ca979c01550ff51b6fefa4d0200ae35d08c72d8998f2f5d5
```

O pacote de saída inclui o boot com root, o boot original para recuperação, configuração do kernel, manifesto com revisões dos fontes, log da compilação e hashes dos arquivos. A etapa final valida `CONFIG_KSU=y`, o nome personalizado, o tamanho da imagem e a preservação do cabeçalho e ramdisk stock.

A conclusão da compilação deve ser conferida na página da execução. O funcionamento no aparelho e a compatibilidade dos drivers e módulos exigem teste real. Atualize para a ROM final 7 e confirme que ela inicia com o boot original antes de testar o boot com root. O ZIP de arquivos deve ser extraído; não é um módulo do KernelSU. Mantenha inicialmente o gerenciador já usado no aparelho.

## Histórico

- [Workflow anterior, com boot obtido do Drive](.github/workflows/build_kernel.yml).
- [Todas as execuções e artefatos](../../actions).

## Créditos

Técnico Root — organização do projeto. [KernelSU Next](https://github.com/KernelSU-Next/KernelSU-Next) e [Magisk](https://github.com/topjohnwu/Magisk) pertencem aos respectivos desenvolvedores.
