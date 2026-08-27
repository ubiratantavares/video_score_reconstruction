# Escopo do Projeto

## Dentro do Escopo (MVP)
- Ingestão multitrack e demultiplexação de vídeo/áudio.
- Análise visual básica (OMR) da partitura estática ou progressiva no vídeo.
- Análise acústica (AMT) e separação primária de fontes instrumentais.
- Alinhamento multimodal (tempo físico `segundos` vs. tempo musical `compassos/batidas`).
- Reconstrução estrutural rigorosa da grade em memória.
- Exportação autônoma para MusicXML.
- Geração renderizada das partes em PDF via utilitário de terceiros.

## Fora do Escopo Inicial
- Processamento de gravações "In the wild" com alto nível de oclusão e baixa resolução visual.
- Suporte a streaming de transcrição ao vivo (Real-time).
- Interfaces gráficas interativas (GUI).
- Formatadores simbólicos de notação exótica não contemplados pelo MusicXML 3.0+.
