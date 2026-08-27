# Visão Orquestral dos Casos de Uso

Ator Mestre: `Orquestrador (Application Service)`

## Sequenciamento Natural (Linear Flow)
1. **UC-001 Ingest Video:** Validação inicial da integridade das mídias carregadas na requisição.
2. **UC-002 Extract Audio:** Ejeção e cacheamento da waveform extraída.
3. **UC-003 Analyze Visual Score:** Detecção passiva e isolada dos blocos geométricos da imagem e compassos.
4. **UC-004 Separate Sources:** *Demixing* e particionamento da orquestração.
5. **UC-005 Transcribe Music:** Escaneamento e conversão de áudio limpo para arrays de notas não formatadas.
6. **UC-006 Align:** Criação pontual da ponte física e matemática entre visões modais (O mapa referencial).
7. **UC-007 Reconstruct Score:** Preenchimento sequencial, polifônico e hierárquico da árvore relacional abstrata (`MusicalScore`).
8. **UC-008 Export MusicXML:** Desserialização da grade formatada para as normas do esquema de arquivos XML da música.
9. **UC-009 Extract Parts:** Encaminhamento do arquivo exportado para o renderizador de pauta padrão (PDF).

> **Aviso Estrutural:** O projeto sustenta curtos-circuitos no fluxo para suportar experimentação científica sem repetir etapas custosas. O UC-007, por exemplo, pode ser acionado injetando-se diretamente as anotações sem reprocessamento de vídeo na camada primária.
