# Premissas e Restrições

## Premissas Operacionais (Assumptions)
- **Visibilidade Constante:** A partitura é legível no vídeo durante o MVP (sendo digital, fixa, ou em visualização "Synthesia").
- **Estrutura Métrica Forte:** A performance adere solidamente a andamentos e métricas definidas, permitindo a quantização (sem rubato livre severo).
- **Qualidade Acústica:** Áudio íntegro o suficiente para permitir *demixing* isolado, isento de saturação ou ruído impeditivo de background.

## Restrições do Sistema (Constraints)
- **Linguagem Principal:** Núcleo desenvolvido em **Python**, facilitando integração posterior com o ecossistema de Machine Learning.
- **Formato Final Simbólico:** Intercâmbio garantido via **MusicXML**.
- **Regra Arquitetural Inegociável:** O domínio (que rege teoria musical ocidental) é estritamente isolado de dependências e bibliotecas externas pesadas.
