# Diagramação e Mapeamento de Classes

Core relacional de Domínio purista livre de poluição da infraestrutura nativa ao redor (OMR/AMT).

```mermaid
classDiagram
    class MusicalScore {
        +List~MusicalPart~ parts
        +validate_global_sync()
    }
    class MusicalPart {
        +List~Staff~ staves
    }
    class Staff {
        +List~Measure~ measures
    }
    class Measure {
        +TimeSignature time_signature
        +List~MusicalEvent~ events
        +verify_overflow()
    }
    class MusicalEvent {
        <<Abstract>>
        +Fraction relative_onset
        +Fraction absolute_duration
        +AlignmentOrigin origin_reference
    }
    class Note {
        +Pitch structural_pitch
    }
    class Rest {
    }
    
    MusicalScore "1" *-- "1..*" MusicalPart
    MusicalPart "1" *-- "1..*" Staff
    Staff "1" *-- "1..*" Measure
    Measure "1" *-- "0..*" MusicalEvent
    MusicalEvent <|-- Note
    MusicalEvent <|-- Rest
```

*Nota Base:* Inserção direta de propriedades `origin_reference` capacitam, satisfazem e garantem inegociavelmente o forte critério rastreabilidade imposto pelos *RNF-03 (Observabilidade Transparente)* acoplando a partitura exportada a tela e segundo físico raiz original extraído.
