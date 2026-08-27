# ADR 002: Injeção Simulada (Mocking) de Tensores Neural

**Status:** Aprovado e Vigente

## Contexto e Desafio Operacional
Acionar instâncias completas de modelagem e extração profunda AMT e OMR implica acoplar o ambiente base as drásticas requisições voláteis impostas aos hardwares locais (Tamanho de Weights, Limites de VRAM de CUDA ou ROCm e bibliotecas C++).

## Resolução e Imposição Arquitetônica
Ao rodar as orquestrações primárias no cotidiano do desenvolvimento, a estrutura utilizará formalmente de forma default **Mock Adapters** passivos. A IA não será instanciada; o Adaptador consumirá e despachará objetos estruturados injetando arrays cacheados contendo as detecções previamente transcritas num arquivo .json estático. 

## Benefícios Práticos
Isso destrava sumariamente as pipelines padronizadas. Os orquestradores de Integração Contínua (Github Actions/CI) atestarão a prova de integridade da grade matemática da métrica da partitura na arquitetura efetuando centenas de passagens analíticas por minuto usando o JSON limpo sem nunca despachar um servidor físico computacional de inferência, resguardando tempo brutal no ciclo TDD e desenvolvimento.
