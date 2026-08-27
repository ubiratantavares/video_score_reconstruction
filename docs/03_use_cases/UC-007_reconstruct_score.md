# UC-007: Reconstruct Score

**Ator Principal:** AppService (ReconstructionUseCase)
**Objetivo:** Consolidar lógicas musicais estruturando a matriz polifônica `MusicalScore` com base nos artefatos de IA.

## Fluxo Primário
1. O domínio inicia a instância `MusicalScore` em branco.
2. Metadados unificadores (tempo, tonalidades) são inseridos globalmente nas matrizes estruturais de cabeçalho.
3. Instâncias de `MusicalParts` e seus arrays de pautas e compassos são gerados proporcionalmente.
4. Itera-se ordenadamente sob o vetor dos eventos rústicos capturados no áudio.
5. Usa-se a tradução do tempo (`AlignmentMap`) para transmutar e classificar as notas acústicas em `MusicalEvent`.
6. Alocam-se as matrizes puras respeitando as tipagens nas caixas fixas (`Measure`).
7. Após consolidação polifônica iterativa, as rotinas de domínio checam Invariantes rígidas.
8. Retorno da raiz polifônica perfeitamente instanciada (Pronta para MusicXML).

## Resolução de Anomalias Rítmicas (Fallback e Quantização)
- **Ocorrência de Transbordo (Overflow):** Transcrições brutas indicarão que a batida avança e extrapola a capacidade delimitadora estrita da métrica atual (A nota não "cabe" onde tentamos alojá-la).
- **Procedimento Heurístico Padrão:** O Domínio fatiará automaticamente instâncias musicais (Criando laços e ligaduras de continuação `ties`) acomodando-as suavemente no final deste compasso e invadindo tecnicamente e legitimamente a cabeça do sub-sequente.
