# ADR 001: Adoção Estrita da Arquitetura Hexagonal

**Status:** Aprovado e Vigente

## Contexto e Problema de Design
Em projetos de processamento multimídia, herdar componentes estruturais, classes, arrays NumPy e representações internas provindos diretamente de frameworks utilitários (OpenCV, Torch ou Music21) na camada lógica das aplicações polui criticamente as instâncias operacionais. Isso dificulta testes rápidos e cria fortes débitos técnicos para evolução das bibliotecas ao redor.

## Resolução Formal
Isolaremos inegociavelmente a "regra teórica musical estrutural" dentro de um núcleo Python puro e altamente desacoplado (**Domain-Driven Design focado** e **Ports & Adapters**).

## Avaliação e Benefícios
- Proteção imediata contra alterações destrutivas em pipelines bibliotecárias abertas.
- Desacoplamento massivo que promove tempos imensuravelmente reduzidos em testagem de Domínio (Milissegundos ao invés de Dezenas de Segundos).
- Padronização no trânsito via DTOs leves. O preço de desenvolver o boilerplate inicial é devolvido em manutenção zero no núcleo perante trocas de IA.
