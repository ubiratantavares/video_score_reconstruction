# Requisitos Não Funcionais (Atributos de Qualidade)

- **RNF-01 Hexagonal Isolado:** Domínio codificado livre de `import pytorch`, `import cv2` ou `import music21`. Comunicação ocorre exlusivamente através das portas de injeção (Ports and Adapters).
- **RNF-02 Dinâmica de Modelos (Extensibilidade):** O sistema deve comportar a substituição indolor de implementações de rede neural em evolução, sem demandar refatoração na lógica musical.
- **RNF-03 Rastreio Transparente (Observabilidade):** As notas fixadas devem expor seus metadados para garantir que pesquisadores e engenheiros consigam ligar a nota na grade (XML) aos segundos originais de onde as Inteligências a tiraram.
- **RNF-04 Testabilidade Trivial:** É mandatório conseguir validar unitariamente o núcleo musical apenas invocando Python built-in, isentando as pipelines e as máquinas desenvolvedoras de configurar setup oneroso de GPUs e Weights gigantescos em laboratório local.
- **RNF-05 Custo Computacional Prevenido:** Inferência massiva nos Adaptadores Secundários funcionará com isolamento robusto para não transbordar e crachar a estabilidade de processamento do ecossistema central do fluxo.
