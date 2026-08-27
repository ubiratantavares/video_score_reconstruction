# Contratos Injetáveis (Ports)

Portas expõem tipagens isoladas em protocolos passivos (`typing.Protocol`). Ignoram sintaticamente as APIs e tensores periféricos.

## Portas Controladoras de Entrada (Driving)
- `ReconstructionUseCasePort`: Gateway de recebimento de comandos do mundo externo (Chamadas da CLI, Request FastAPI, Notebook Executions).

## Portas Subordinadas de Saída (Driven)
- `VideoReaderPort`: Contrato universal para acesso iterativo de matrizes nativas oriundas de mídias encapsuladas.
- `AudioExtractorPort`: Processo formal demarcando extração PCM demultiplexada.
- `VisualScoreRecognizerPort (OMR)`: Exige varredura gráfica, devolvendo exclusos DTOs mapeando as pautas.
- `AcousticEventTranscriberPort (AMT)`: Exige submissão estrita da onda em troca do mapa acústico sequenciado (Roll Sheet preditiva).
- `ScoreExporterPort`: Demanda a transcrição absoluta e serialização das abstrações de grade perfeitas de memória para intercâmbio de mercado (XML).
- `ScoreRendererPort`: Interface de delegação via script secundário objetivando a visualização em PDFs segmentados.
