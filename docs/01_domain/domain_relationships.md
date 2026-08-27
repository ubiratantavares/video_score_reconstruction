# Relacionamentos e Invariantes Musicais

## 1. Composição de Agregados (Hierarquia Rígida)
- `MusicalScore` abriga obrigatoriamente `1..N` `MusicalPart`.
- `MusicalPart` é dona de `1..N` `Staff`.
- `Staff` possui serialmente `1..N` `Measure`.
- `Measure` encapsula `0..N` `MusicalEvent`.

## 2. Invariantes Lógicas de Domínio (As Regras Inquebráveis)
Qualquer violação estrutural das invariantes abaixo reverterá as transações em memória:
- **Consistência Métrica (Measure Integrity):** A soma exata fracionária de todos os eventos inseridos internamente num `Measure` jamais poderá superar a lotação descrita pela própria `TimeSignature` matriz.
- **Sincronia Mestra Global:** Ao salvar, instanciar ou recuperar a `MusicalScore`, o total computado final de compassos deve corresponder idêntica e horizontalmente ao longo de todas as `MusicalParts` abrigadas (formatação tabular obrigatória).
- **Genealogia Rastreada:** Ao finalizar o ciclo de extração, todo `MusicalEvent` na grade aponta inexoravelmente e retrospectivamente a sua raiz de detecção original pelo `AlignmentMap`.
