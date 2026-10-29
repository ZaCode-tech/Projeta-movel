# ProjetaMóvel

App Android (Kotlin + Jetpack Compose) que transforma uma foto do ambiente em um projeto de marcenaria.

1. Tire uma foto do local (ou escolha da galeria).
2. Desenhe com o dedo a área onde o móvel vai ficar e confirme.
3. Responda "Qual móvel gostaria?" (ex.: *guarda-roupa*, *armário*, *estante*).
4. Veja cada modelo dentro da foto e troque com as setas `<` e `>`.
5. Informe as medidas do ambiente (parede, teto, comprimento) e do móvel (largura, altura, profundidade).
6. Receba o projeto: vista montada, peças desmontadas, lista de corte, passo a passo e arquivos para exportar.

## Exportações

| Formato | Uso |
|---|---|
| PDF (modelo) | Manual com vistas, peças desmontadas, lista de corte e montagem |
| PDF (todos os modelos) | Manual completo com todas as variações do móvel |
| DXF (3DFACE, mm) | Importar no SketchUp Pro e no Promob (Start / Studio), conforme a versão |
| OBJ (metros) | Importar no SketchUp e outros programas 3D |
| CSV | Lista de corte para planilhas e plugins |

> Os formatos nativos `.skp` e `.promob` são proprietários e **não** são gerados. Use DXF/OBJ para importar; teste na sua versão do programa.

## Como rodar

1. Instale o [Android Studio](https://developer.android.com/studio) (Koala ou mais novo) e o JDK 17.
2. `File > Open` e escolha a pasta do projeto; aguarde o Gradle sincronizar.
3. Conecte um celular Android (ou use o emulador) e clique em **Run**.

## Estrutura

```
app/src/main/java/com/projetamovel/
├── MainActivity.kt        telas (foto, desenho, modelos, medidas, resultado)
├── PdfExporter.kt         geração do PDF
└── domain/
    ├── Domain.kt          peças, projeto, lista de corte e exportadores DXF/OBJ/CSV
    └── Catalog.kt         catálogo de modelos paramétricos
docs/index.html            site de divulgação (GitHub Pages)
```

A pasta `domain/` não usa nada do Android, então pode ser movida para um módulo Kotlin Multiplatform.

## Adicionando modelos

Em `Catalog.kt`, adicione um `ModelOption` à lista `all` (nome, medidas padrão e a função que monta as peças) e, se for um móvel novo, suas palavras-chave em `keywords`.

## Site

Publique a pasta `docs/` com GitHub Pages: `Settings > Pages > Branch: main, pasta /docs`. Troque `SEU-USUARIO` e o e-mail em `docs/index.html`.

## Limitações da versão 0.1

- O móvel é posicionado na foto como **vista frontal 2D** dentro da área desenhada (não é realidade aumentada).
- Os modelos são **paramétricos próprios** (MDF 15 mm, fundo 6 mm). O conteúdo de livros e pacotes de projetos comprados tem direitos autorais e não faz parte deste repositório.
- iPhone: o caminho é migrar para Kotlin Multiplatform / Compose Multiplatform (precisa de um Mac com Xcode).

## Roadmap

- [ ] iPhone (Compose Multiplatform)
- [ ] Mais móveis: cômoda, rack, mesa, cozinha completa
- [ ] Visualização 3D e realidade aumentada
- [ ] Plano de corte otimizado para chapas de 2750 x 1850 mm
- [ ] Exportação de ferragens e orçamento
