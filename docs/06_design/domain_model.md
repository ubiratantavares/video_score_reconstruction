# Arquitetura do Domínio e Tipagem Estruturada

Modelamento estritamente Python, ancorado fundamentalmente na adoção exaustiva do `@dataclass(frozen=True)` e Type Hints explícitas impedindo mutações fantasma de estado perante execuções complexas na memória.

## 1. Composição de Entidades com Identidade
Aquelas que possuem significado autônomo.
- `MusicalScore`: O *Root Aggregate* mestre que rege tudo; valida a sincronicidade dos instrumentos.
- `MusicalPart`: Identidade do instrumento unificado na grade inteira.
- `Staff`: O invólucro seqüencial contínuo.
- `Measure`: O recipiente rigorosamente limitado, guardião local das Invariantes Rítmicas matemáticas regido pela `TimeSignature`.

## 2. Objetos Imutáveis Transicionais (Value Objects)
- `Pitch` e `TimeSignature`.
- **Invariante Primitiva e Universal de Tempo:** Interdição sumária e rigorosa de instanciar números flutuantes `(float)` nas propriedades atreladas a compasso e duração temporal simbólica. A prevenção total perante bugs em *floating-point errors* impõe a adoção unânime de instâncias `fractions.Fraction` para ritmos fracionários nas instâncias da memória pura.

## 3. Subdivisão Atômica Visual 
- A Interface passiva `MusicalEvent (ABC)`.
  - Heranças definitivas instanciadas nos preenchimentos: `Note`, `Rest` e instâncias compostas `Chord`.

## 4. Referencial de Traduções Analíticas
- A ancoragem isolada `AlignmentAnchor`. Dita fisicamente e rastreia o alinhamento vinculativo convertendo dados analíticos brutos (Tempo Acústico Contínuo e Coordenadas de Imagens) em Posições Polifônicas Determinísticas restritivas da Métrica nativa.
