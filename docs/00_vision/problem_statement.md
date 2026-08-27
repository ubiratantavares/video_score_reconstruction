# Declaração do Problema

## O Problema Central
**Como reconstruir uma grade musical estruturada a partir da execução audiovisual de uma obra?**

## Dimensões da Abordagem
- **Problema:** A lacuna entre a mídia audiovisual bruta e a partitura estruturada.
- **Hipótese:** Integrar dados de vídeo (OMR) e áudio (AMT) gera resultados e contexto superiores a transcrições unimodais.
- **Solução:** Pipeline que extrai, alinha as fontes no tempo e reconstrói as notas gerando MusicXML nativo.
- **Implementação:** Arquitetura Hexagonal robusta em Python, blindando as lógicas musicais contra a instabilidade das bibliotecas de IA (OpenCV, PyTorch).
