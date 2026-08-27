# 1. Estratégia documental geral

A documentação deve seguir esta cadeia de rastreabilidade:

```text
VISÃO DO PROJETO
       ↓
PROBLEMA E CONTEXTO
       ↓
ONTOLOGIA DO DOMÍNIO
       ↓
REQUISITOS
       ↓
CASOS DE USO
       ↓
ARQUITETURA
       ↓
CONTRATOS / PORTAS
       ↓
MODELO DE DADOS
       ↓
DESENHO TÉCNICO
       ↓
IMPLEMENTAÇÃO
       ↓
TESTES E VALIDAÇÃO
       ↓
EMPACOTAMENTO
       ↓
DEPLOY
       ↓
OPERAÇÃO E EVOLUÇÃO
```

A documentação deve ser **versionada no Git**, evoluir junto com o software e manter rastreabilidade entre requisitos, decisões arquiteturais, código e testes. Essa preocupação é coerente com a fonte anexada, que enfatiza documentação incremental, commits atômicos, testes, refatoração e integração progressiva. 

---

# 2. Fase 0 — Concepção e visão

**Objetivo:** definir precisamente o que é o projeto antes de discutir tecnologia.

Documentos:

```text
docs/
└── 00_vision/
    ├── project_vision.md
    ├── problem_statement.md
    ├── objectives.md
    ├── scope.md
    ├── stakeholders.md
    ├── assumptions_and_constraints.md
    └── success_criteria.md
```

### `project_vision.md`

Deve estabelecer:

* propósito;
* visão;
* problema;
* solução pretendida;
* público-alvo;
* contexto;
* valor produzido;
* visão de longo prazo.

### `problem_statement.md`

Formalizar:

> Como reconstruir uma grade musical multitrilha a partir de uma representação audiovisual de uma execução musical?

E separar claramente:

```text
Problema
≠
Hipótese
≠
Solução
≠
Implementação
```

### `scope.md`

Definir explicitamente:

**Dentro do escopo**

* vídeo;
* áudio;
* análise visual;
* OMR;
* MIR;
* AMT;
* separação de fontes;
* alinhamento;
* reconstrução da grade;
* MusicXML;
* MuseScore;
* partes instrumentais;
* PDF.

**Fora do escopo inicial**

Tudo aquilo que ainda não tenha justificativa experimental.

---

# 3. Fase 1 — Concepção ontológica

Esta é uma das partes que eu considero **mais importantes para este projeto**.

```text
docs/
└── 01_domain/
    ├── domain_concepts.md
    ├── domain_glossary.md
    ├── ontology.md
    ├── entities.md
    ├── value_objects.md
    ├── aggregates.md
    ├── domain_relationships.md
    └── domain_invariants.md
```

O objetivo não é criar imediatamente classes Python.

Primeiro devemos responder:

> **Quais são as coisas que existem conceitualmente no universo do problema?**

Por exemplo:

```text
Performance
Video
AudioTrack
Stem
MusicalScore
MusicalPart
Staff
Instrument
Measure
Note
Rest
Chord
Clef
KeySignature
TimeSignature
Tempo
MusicalEvent
Alignment
```

E principalmente estabelecer:

```text
Performance
      │
      ├── Video
      └── Audio
             │
             ▼
        Audio Analysis
             │
             ▼
          Stems
             
Visual Analysis
      │
      ▼
Score Representation
      │
      ▼
Alignment
      │
      ▼
MusicalScore
```

Aqui nasce a **linguagem ubíqua** do projeto.

---

# 4. Fase 2 — Requisitos

Somente depois da ontologia devemos formalizar os requisitos.

```text
docs/
└── 02_requirements/
    ├── requirements_overview.md
    ├── functional_requirements.md
    ├── non_functional_requirements.md
    ├── business_rules.md
    ├── constraints.md
    ├── use_cases.md
    ├── acceptance_criteria.md
    └── requirements_traceability.md
```

## Requisitos funcionais

Eu organizaria por capacidades:

### RF-01 — Entrada audiovisual

Receber:

* arquivo de vídeo;
* eventualmente fonte audiovisual externa.

### RF-02 — Extração

Extrair:

* áudio;
* frames;
* metadados.

### RF-03 — Análise visual

Identificar:

* pautas;
* sistemas;
* instrumentos;
* elementos de notação.

### RF-04 — Análise acústica

Identificar:

* fontes;
* eventos;
* pitch;
* onset;
* duração;
* ritmo.

### RF-05 — Separação

Separar fontes instrumentais quando possível.

### RF-06 — Alinhamento

Relacionar:

```text
tempo audiovisual
        ↕
compasso
        ↕
evento musical
        ↕
pauta
        ↕
instrumento
```

### RF-07 — Reconstrução

Construir o modelo simbólico:

```text
MusicalScore
```

### RF-08 — Exportação

Produzir:

```text
MusicXML
```

### RF-09 — Grade

Produzir a grade completa.

### RF-10 — Partes

Extrair:

```text
Trumpet.pdf
Trombone.pdf
Piano.pdf
Bass.pdf
...
```

### RF-11 — Validação

Permitir verificar/corrigir resultados.

---

# 5. Requisitos não funcionais

O documento deve evitar transformar "boas práticas" em requisitos artificiais.

Eu os organizaria por atributos de qualidade:

```text
RNF-01 Arquitetura
RNF-02 Manutenibilidade
RNF-03 Testabilidade
RNF-04 Extensibilidade
RNF-05 Desempenho
RNF-06 Confiabilidade
RNF-07 Reprodutibilidade
RNF-08 Observabilidade
RNF-09 Portabilidade
RNF-10 Segurança
RNF-11 Usabilidade
RNF-12 Interoperabilidade
```

Por exemplo:

> **RNF-05:** o sistema deve permitir substituição do algoritmo de transcrição automática sem alteração do núcleo de domínio.

Isso é muito mais útil que simplesmente escrever:

> "O sistema deve usar SOLID."

SOLID é **princípio de projeto**, não requisito funcional.

A própria fonte faz essa distinção ao estabelecer que princípios e padrões devem ser meios para alcançar qualidade, e não objetivos em si mesmos. 

---

# 6. Fase 3 — Casos de uso

```text
docs/
└── 03_use_cases/
    ├── UC-001_ingest_video.md
    ├── UC-002_extract_audio.md
    ├── UC-003_analyze_visual_score.md
    ├── UC-004_analyze_audio.md
    ├── UC-005_separate_sources.md
    ├── UC-006_transcribe_music.md
    ├── UC-007_align_performance_score.md
    ├── UC-008_reconstruct_score.md
    ├── UC-009_export_musicxml.md
    ├── UC-010_generate_full_score.md
    ├── UC-011_extract_parts.md
    └── UC-012_export_pdf.md
```

Cada caso de uso deve possuir:

```text
ID
Nome
Objetivo
Ator
Pré-condições
Entrada
Fluxo principal
Fluxos alternativos
Exceções
Saída
Pós-condições
Critérios de aceitação
```

---

# 7. Fase 4 — Arquitetura

Aqui entra formalmente a **Hexagonal Architecture**.

```text
docs/
└── 04_architecture/
    ├── architecture_overview.md
    ├── architectural_principles.md
    ├── hexagonal_architecture.md
    ├── domain_architecture.md
    ├── application_architecture.md
    ├── ports.md
    ├── adapters.md
    ├── component_model.md
    ├── deployment_architecture.md
    └── adr/
```

A regra arquitetural fundamental seria:

```text
                 DOMAIN
                   ▲
                   │
              APPLICATION
                   ▲
                   │
                 PORTS
                   ▲
                   │
                ADAPTERS
                   ▲
                   │
             INFRASTRUCTURE
```

E nunca:

```text
Domain → Demucs
Domain → OpenCV
Domain → Music21
Domain → MuseScore
Domain → FastAPI
```

---

# 8. Fase 5 — ADRs

Eu considero **ADR — Architecture Decision Record** indispensável.

Exemplos:

```text
ADR-001-use-hexagonal-architecture.md
ADR-002-use-ddd-selectively.md
ADR-003-use-python-as-primary-language.md
ADR-004-use-musicxml-as-score-exchange-format.md
ADR-005-use-music21-for-musicxml-adapter.md
ADR-006-use-demucs-for-source-separation.md
ADR-007-use-omr-strategy-abstraction.md
ADR-008-use-musescore-for-score-rendering.md
ADR-009-use-intermediate-musical-representation.md
```

Cada ADR deve responder:

```text
Contexto
Problema
Alternativas
Decisão
Justificativa
Consequências
Status
```

Isso evita que decisões técnicas desapareçam da história do projeto.

---

# 9. Fase 6 — Especificação das portas

Esta fase é particularmente importante na arquitetura hexagonal.

```text
docs/
└── 05_interfaces/
    ├── inbound_ports.md
    ├── outbound_ports.md
    ├── audio_ports.md
    ├── omr_ports.md
    ├── mir_ports.md
    ├── transcription_ports.md
    ├── alignment_ports.md
    ├── score_ports.md
    └── rendering_ports.md
```

Exemplo conceitual:

```text
AudioSourceSeparator
MusicTranscriber
ScoreRecognizer
PerformanceAligner
ScoreRepository
MusicXmlExporter
ScoreRenderer
```

Isso concretiza DIP e ISP.

A fonte recomenda explicitamente interfaces pequenas, injeção de dependências e desacoplamento entre API, CLI, processamento e implementação nativa. 

---

# 10. Fase 7 — Modelo técnico

```text
docs/
└── 06_design/
    ├── domain_model.md
    ├── class_diagrams.md
    ├── sequence_diagrams.md
    ├── component_diagrams.md
    ├── data_model.md
    ├── file_formats.md
    ├── pipeline.md
    └── error_model.md
```

Aqui podemos finalmente transformar:

```text
Ontology
     ↓
Domain Model
     ↓
Python Classes
```

Essa ordem é importante.

**Não começar pelas classes.**

---

# 11. Fase 8 — Dataset e Ground Truth

Eu criaria uma documentação própria:

```text
docs/
└── 07_dataset/
    ├── dataset_strategy.md
    ├── source_policy.md
    ├── dataset_structure.md
    ├── annotation_guidelines.md
    ├── ground_truth.md
    ├── train_validation_test.md
    └── evaluation_protocol.md
```

O primeiro experimento deveria usar **um vídeo controlado**, antes de tentar processar os 72 vídeos.

O dataset deve permitir:

```text
Vídeo
 ↓
Áudio
 ↓
Frames
 ↓
Anotações
 ↓
Ground Truth
 ↓
Resultado do sistema
 ↓
Comparação
```

---

# 12. Fase 9 — Especificação experimental

Como o projeto possui uma dimensão de pesquisa, eu não misturaria avaliação científica com requisitos de software.

Criaria:

```text
docs/
└── 08_experiments/
    ├── experimental_protocol.md
    ├── hypotheses.md
    ├── metrics.md
    ├── baseline.md
    ├── experiments.md
    └── results.md
```

Métricas podem posteriormente incluir:

```text
Pitch Accuracy
Note F1
Onset Accuracy
Duration Accuracy
Rhythm Accuracy
Instrument Accuracy
Measure Accuracy
Score Completeness
MusicXML Validity
```

---

# 13. Fase 10 — Implementação

Somente agora a documentação começa a se aproximar diretamente do código:

```text
docs/
└── 09_implementation/
    ├── development_environment.md
    ├── project_structure.md
    ├── coding_guidelines.md
    ├── testing_strategy.md
    ├── configuration.md
    ├── logging.md
    └── error_handling.md
```

Aqui entram as práticas da fonte:

* Clean Code;
* SOLID;
* composição;
* baixo acoplamento;
* alta coesão;
* DRY;
* KISS;
* YAGNI;
* type hints;
* testes;
* refatoração.

A fonte também recomenda explicitamente modularização, funções/classes coesas, redução da complexidade ciclomática, testes e separação entre processamento e interfaces. 

---

# 14. Fase 11 — Estratégia de testes

```text
docs/
└── 10_testing/
    ├── test_strategy.md
    ├── unit_tests.md
    ├── integration_tests.md
    ├── end_to_end_tests.md
    ├── regression_tests.md
    ├── quality_metrics.md
    └── acceptance_tests.md
```

A pirâmide seria:

```text
             E2E
              ▲
         Integration
              ▲
           Unit
```

E haveria uma segunda dimensão:

```text
Software correctness
        +
Musical correctness
        +
Output correctness
```

Esse último ponto é importante: gerar um MusicXML sintaticamente válido não significa necessariamente gerar uma partitura musicalmente correta.

---

# 15. Fase 12 — Qualidade e desempenho

```text
docs/
└── 11_quality/
    ├── quality_model.md
    ├── performance.md
    ├── complexity.md
    ├── benchmarking.md
    ├── profiling.md
    └── technical_debt.md
```

Aqui entram as preocupações da fonte com:

* Big O;
* memória;
* gargalos;
* vetorização;
* OpenCV;
* processamento redundante;
* comparação de implementações.



No seu projeto, eu acrescentaria uma preocupação particularmente importante:

**custo computacional dos modelos de IA.**

---

# 16. Fase 13 — API e interfaces de usuário

```text
docs/
└── 12_interfaces/
    ├── cli.md
    ├── api.md
    ├── api_contract.md
    └── user_workflow.md
```

A API deve ser um **adaptador de entrada**, não o centro da aplicação.

Da mesma maneira:

```text
CLI
API
GUI
Notebook
```

podem utilizar os mesmos casos de uso.

---

# 17. Fase 14 — Empacotamento e distribuição

```text
docs/
└── 13_delivery/
    ├── packaging.md
    ├── dependencies.md
    ├── configuration.md
    ├── environment.md
    ├── release_process.md
    └── versioning.md
```

Aqui documentamos:

```text
Python
uv
FFmpeg
OpenCV
PyTorch
Music21
MuseScore
```

e suas dependências.

---

# 18. Fase 15 — Deploy

```text
docs/
└── 14_deployment/
    ├── deployment_strategy.md
    ├── runtime_architecture.md
    ├── docker.md
    ├── environment_variables.md
    ├── health_checks.md
    ├── monitoring.md
    ├── backup.md
    └── rollback.md
```

O deploy deve ser consequência da arquitetura, não algo pensado no final como uma atividade isolada.

O fluxo:

```text
Development
     ↓
Test
     ↓
Build
     ↓
Package
     ↓
Deploy
     ↓
Health Check
     ↓
Monitoring
```

---

# 19. Fase 16 — Rastreabilidade

Este documento será um dos mais importantes:

```text
docs/
└── 15_traceability/
    └── requirements_traceability_matrix.md
```

A matriz deve relacionar:

| Requisito | Caso de uso | Domínio      | Componente     | Teste | Resultado |
| --------- | ----------- | ------------ | -------------- | ----- | --------- |
| RF-001    | UC-001      | Performance  | VideoAdapter   | T-001 | ✓         |
| RF-002    | UC-002      | AudioTrack   | AudioAdapter   | T-002 | ✓         |
| RF-003    | UC-003      | Staff        | OMR Adapter    | T-003 | ✓         |
| RF-004    | UC-006      | Note         | AMT Adapter    | T-004 | ✓         |
| RF-005    | UC-008      | MusicalScore | Reconstruction | T-005 | ✓         |
| RF-006    | UC-009      | MusicalScore | XML Adapter    | T-006 | ✓         |

Assim conseguimos percorrer:

```text
Requisito
   ↓
Caso de uso
   ↓
Objeto de domínio
   ↓
Porta
   ↓
Adapter
   ↓
Implementação
   ↓
Teste
   ↓
Evidência
```

---

# 20. Estrutura documental final

Eu consolidaria tudo em:

```text
docs/
│
├── 00_vision/
├── 01_domain/
├── 02_requirements/
├── 03_use_cases/
├── 04_architecture/
│   └── adr/
├── 05_interfaces/
├── 06_design/
├── 07_dataset/
├── 08_experiments/
├── 09_implementation/
├── 10_testing/
├── 11_quality/
├── 12_interfaces/
├── 13_delivery/
├── 14_deployment/
└── 15_traceability/
```

E na raiz:

```text
README.md
CHANGELOG.md
LICENSE
CONTRIBUTING.md
```

---

# 21. Ordem correta de construção

Eu **não escreveria todos esses documentos de uma vez**.

A ordem construtiva deveria ser:

```text
ETAPA 1
Visão
   ↓
ETAPA 2
Problema
   ↓
ETAPA 3
Ontologia
   ↓
ETAPA 4
Requisitos
   ↓
ETAPA 5
Casos de uso
   ↓
ETAPA 6
Arquitetura
   ↓
ETAPA 7
ADRs
   ↓
ETAPA 8
Portas
   ↓
ETAPA 9
Modelo de domínio
   ↓
ETAPA 10
Dataset / Ground Truth
   ↓
ETAPA 11
Design técnico
   ↓
ETAPA 12
Implementação
   ↓
ETAPA 13
Testes
   ↓
ETAPA 14
Experimentos
   ↓
ETAPA 15
Empacotamento
   ↓
ETAPA 16
Deploy
```

---

# 22. A documentação deve evoluir junto com os Sprints

Eu adotaria uma regra:

> **Nenhum Sprint deve produzir apenas código.**

Cada Sprint deve produzir:

```text
Documentação
+
Código
+
Testes
+
Evidência
```

Por exemplo:

### Sprint 0 — Concepção

```text
project_vision.md
problem_statement.md
scope.md
domain_glossary.md
```

### Sprint 1 — Ontologia

```text
ontology.md
domain_concepts.md
domain_relationships.md
```

### Sprint 2 — Requisitos

```text
functional_requirements.md
non_functional_requirements.md
use_cases.md
```

### Sprint 3 — Arquitetura

```text
hexagonal_architecture.md
ports.md
adapters.md
ADR-001...
```

### Sprint 4 — Primeiro experimento

```text
dataset_strategy.md
experimental_protocol.md
ground_truth.md
```

E assim sucessivamente.

---

# 23. O princípio documental mais importante

Eu adotaria uma regra de ouro para o repositório:

```text
CONCEITO
   ↓
DECISÃO
   ↓
REQUISITO
   ↓
DESIGN
   ↓
CÓDIGO
   ↓
TESTE
   ↓
EVIDÊNCIA
```

Isso evita um problema muito comum em projetos de software:

> primeiro escrever código, depois tentar descobrir por que o código existe.

No seu projeto, queremos exatamente o contrário.

---

## 24. Resultado esperado ao final

Quando o projeto estiver pronto, alguém deverá conseguir clonar o repositório e compreender:

```text
POR QUE
  ↓
O QUE
  ↓
PARA QUEM
  ↓
QUAL DOMÍNIO
  ↓
QUAIS REQUISITOS
  ↓
QUAIS CASOS DE USO
  ↓
QUAL ARQUITETURA
  ↓
QUAIS PORTAS
  ↓
QUAIS ADAPTERS
  ↓
COMO FOI IMPLEMENTADO
  ↓
COMO FOI TESTADO
  ↓
COMO FOI AVALIADO
  ↓
COMO É EXECUTADO
  ↓
COMO É DEPLOYADO
```

Essa abordagem também mantém a coerência com a fonte anexada: **modularização, SOLID, Clean Code, testes, refatoração, separação de responsabilidades, baixo acoplamento, interfaces e documentação incremental**, sem transformar cada princípio ou padrão em uma obrigação artificial. 

### Minha recomendação para o próximo passo

Eu **não começaria ainda pelo `functional_requirements.md`**.

O próximo artefato deveria ser **`project_vision.md`**, seguido de **`problem_statement.md`**, **`scope.md`** e, principalmente, **`domain_glossary.md`**. Depois disso podemos construir formalmente a **ontologia do domínio**, porque ela será a base para definir os requisitos funcionais e não funcionais com precisão.

Em outras palavras:

**Visão → Problema → Escopo → Ontologia → Requisitos → Casos de uso → Arquitetura Hexagonal → Design → Implementação → Testes → Deploy.**

Essa sequência reduz significativamente o risco de desenvolver uma solução tecnicamente sofisticada para um problema que ainda não foi formalmente definido.
