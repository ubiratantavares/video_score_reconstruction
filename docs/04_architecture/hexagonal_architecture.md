# Macro-Arquitetura Hexagonal

A solidez do sistema baseia-se na aplicação imutável do paradigma *Ports and Adapters*.

## 1. O Núcleo do Hexágono
Desenvolvido em puro Python, completamente dissociado de I/O, processamento acelerado ou bibliotecas de terceiro. Depende em sua maioria das built-ins e `dataclasses`.
- **Camada de Domínio:** A lógica absoluta musical (Ontologia materializada, Classes da Grade, Quantização Matemática Fracionária e Validação de Invariantes Rítmicas).
- **Camada de Aplicação:** Os orquestradores estritos (`AppServices` que executam Casos de Uso), delegando requisições, interligando a infraestrutura ao Domínio sem maculá-lo.

## 2. A Periferia Estrutural (Infraestrutura)
As bibliotecas pesadas (*PyTorch, Librosa, OpenCV, Music21*) existem única e exlusivamente aqui.
- **Ports (Contratos/Interfaces):** Definições estritas ditando o que os pacotes ao redor necessitam responder. (Ditam o "O quê").
- **Adapters (Implementações):** Classes instanciáveis concretas que amarram ativamente o ecossistema volátil às assinaturas da Porta. (Ditam o "Como").

## Regra Fundamental da Dependência Lógica
O Código das dependências deve seguir inegociavelmente no sentido das setas apontando **da infraestrutura para dentro**:

`[Adapters de Interface / CLI] ---> [Aplicações/Casos de Uso] ---> [O Domínio Puro]`
