# Blog Individual – Build Automático

Este repositório agora armazena **tanto** o projeto Quarto (arquivos `.qmd`, dados, CSS) quanto a pasta `docs/` com a versão renderizada publicada via GitHub Pages.

## Como funciona

1. O workflow em `.github/workflows/render-and-deploy.yml` roda a cada 15 minutos (ou sob demanda).
2. Ele instala as dependências listadas em `requirements.txt`, executa `quarto render index.qmd` e atualiza `docs/`.
3. O GitHub Pages deve estar configurado para servir `main / docs`, exibindo o site em `https://juanmmendes.github.io/blog-renderizado/`.

## Estrutura

```
.
├── about.qmd
├── index.qmd
├── dados_x.txt / dados_y.txt
├── styles.css
├── _quarto.yml        # define o output-dir como docs/
├── requirements.txt   # dependências Python usadas nos notebooks
├── docs/              # HTML/CSS já renderizados (output do Quarto)
└── .github/workflows/render-and-deploy.yml
```

Para atualizar manualmente:

```bash
quarto render index.qmd
git add docs/
git commit -m "Atualiza build"
git push origin main
```

Mas, em geral, o workflow cuidará de tudo automaticamente.
