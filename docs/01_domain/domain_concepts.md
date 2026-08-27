# Conceitos do Domínio por Categoria

## Instâncias Audiovisuais (Fronteira Externa)
- **Performance:** Instância raiz do mundo físico.
- **Video / AudioTrack / Stem:** Entidades primárias imutáveis (Inputs).

## Elementos de Extração (Dados de Transição)
- **VisualScoreRepresentation:** Polígono lógico capturado pelo OMR. Metadado contextual sem precisão sonora.
- **AcousticEvent:** Coordenada isolada contendo pitch (frequência) e coordenadas de *onset* (início).
- **AlignmentMap:** Dicionário complexo traduzindo posições nativas de segundo `(sec)` para indexações métricas `(measure_index, beat_fraction)`.

## Construtos Musicais (O Core Simbólico)
- **MusicalScore:** O Root Aggregate da nossa partitura (O documento inteiro).
- **MusicalPart & Staff:** Hierarquias divisoras organizacionais e visuais, respectivamente.
- **Measure:** Contêiner validador regido pela `TimeSignature`. Impede overflow rítmico intrinsecamente.
- **MusicalEvent:** Interface imutável e atômica. Contempla e herda restritamente subclasses puras `Note`, `Rest` e `Chord`.
