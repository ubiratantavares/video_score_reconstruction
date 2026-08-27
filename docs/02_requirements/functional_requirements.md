# Requisitos Funcionais (Core Capabilities)

## RF-01: Ingestão de Mídia
- **1.1:** Reconhecer e abrir containers de vídeo padrão.
- **1.2:** Validar a integridade estrutural (FPS, Amostragem).

## RF-02: Isolamento Sensorial
- **2.1:** Demultiplexar e extrair matriz nativa PCM (.WAV).
- **2.2:** Gerenciar arrays sequenciais dos frames visuais.

## RF-03: Reconhecimento Ótico (OMR)
- **3.1:** Demarcar geometricamente os sistemas e pautas na imagem.
- **3.2:** Identificar referências fixas (Claves, andamento, barras de compasso).

## RF-04: Transcrição Sonora (AMT)
- **4.1:** Sub-dividir hastes instrumentais (`Stems`) do wave inteiro.
- **4.2:** Prever eventos melódicos (Onset, Duração e Pitch absoluto).

## RF-05: Sincronia Multimodal
- **5.1:** Ligar onsets nativos (áudio) às barras gráficas (vídeo).
- **5.2:** Emitir e injetar o `AlignmentMap`.

## RF-06: Formatação Lógica (Reconstrução)
- **6.1:** Orquestrar o preenchimento das partes garantindo tipagem pura de Domínio.
- **6.2:** Quantizar temporizações flutuantes e imperfeitas forçando encaixes fracionários estritos na métrica do compasso.

## RF-07: Saída Consolidada
- **7.1:** Estruturar o MusicXML universal livre de dependência.
- **7.2:** Comandar a renderização individual das pautas em PDF final.
