# Implementações Ativas (Adapters)

O único local da arquitetura onde se instanciam frameworks pesados, garantindo a substituição elástica sem perturbar o andamento funcional da orquestração.

## Adapters Cognitivos e de Processamento Visual (OMR)
- `YoloStaffDetectorAdapter`: Submete frames a um inferidor YOLO para coletar bounding-boxes, emulando-os em representações geométricas neutras.
- `StaticCv2ScoreAdapter`: Heurística determinística leve estruturada com varreduras no OpenCV focada no experimento Baseline (MVP sem redes neurais densas).

## Adapters Preditivos Acústicos e Demix (AMT)
- `BasicLibrosaOnsetAdapter`: Transcrição analítica rudimentar de frequência.
- `OmnizartTranscriberAdapter`: IA madura encapsulada instigada na transcrição complexa de contraponto.
- `DemucsSeparatorAdapter`: Ferramenta pesada dedicada atômica à fragmentação e separação das "Hastes" (Stems) originais para lidar com sobreposição instrumental complexa.

## Adapters Formatadores de Saída (Symbolic Exporters)
- `Music21XmlExporterAdapter`: Tradutor isolado entre os modelos rijos e puros do Domínio desta arquitetura para a API mutável da ferramenta bibliotecária externa nativa do Python e finalização XML.

## Adapters Operacionais (Entrypoints/CLI)
- `TyperCliAdapter`: Ponto único de contato do ambiente de execução do sistema. Desembaraça os argumentos providos e injeta fisicamente as escolhas de modelo acima no construtor final e purificado.
