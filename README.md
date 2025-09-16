# Cloud Canvas - Simulador de Pipeline de Nuvem

Um simulador interativo de arrastar e soltar para projetar e validar arquiteturas de pipeline de nuvem da AWS, Azure e GCP. Teste seus conhecimentos em cenários do mundo real de forma prática e visual.

-----

### Visão Geral do Projeto

*(Recomendação: Grave um GIF curto da tela em ação e insira aqui. Ele deve mostrar o fluxo: selecionar plataforma -\> objetivo -\> dificuldade -\> arrastar serviços para o pipeline -\> avaliar -\> ver o feedback.)*

## 🚀 Sobre o Projeto

Cloud Canvas é uma ferramenta educacional projetada para ajudar estudantes, engenheiros de nuvem, arquitetos de soluções e entusiastas a solidificar seu conhecimento sobre os serviços de nuvem e suas interações. Em vez de apenas responder a perguntas de múltipla escolha, os usuários enfrentam cenários práticos onde devem construir a arquitetura correta arrastando e soltando os ícones dos serviços na ordem lógica.

Este projeto visa preencher a lacuna entre o conhecimento teórico e a aplicação prática, oferecendo um ambiente seguro e interativo para experimentar e aprender com os erros.

## ✨ Funcionalidades Principais

  - **Interface Intuitiva de Arrastar e Soltar**: Construa pipelines de forma visual e interativa.
  - **Suporte Multi-Cloud**: Desafios para AWS, com estrutura pronta para expandir para Azure e GCP.
  - **Desafios por Categoria**: Filtre simulados por área de interesse, como Engenharia de Dados, Análise de Dados e Operações.
  - **Níveis de Dificuldade**: Avance desde cenários fundamentais até arquiteturas complexas de nível Arquiteto.
  - **Feedback Imediato**: Receba validação instantânea da sua solução, com explicações detalhadas sobre a arquitetura correta.
  - **Suporte a Padrões Complexos**: Modele fluxos com etapas paralelas e serviços de orquestração (como AWS Step Functions).
  - **Responsivo e com Dark Mode**: Use em qualquer dispositivo, com o tema de sua preferência.
  - **Zero Dependências Externas**: Um único arquivo `index.html` que roda diretamente no navegador, sem necessidade de servidor ou instalação.

## 🛠️ Stack Técnica

  - **Frontend**: HTML5, CSS3
  - **Framework CSS**: [Tailwind CSS](https://tailwindcss.com/)
  - **Lógica**: JavaScript (Vanilla JS)
  - **Dados**: Todos os cenários e definições de serviços são armazenados em objetos JSON dentro do próprio arquivo HTML.

## 🏁 Como Começar

Este projeto é um único arquivo autocontido. Para usá-lo, basta seguir os passos:

1.  Clone o repositório ou baixe o arquivo `index.html`.
2.  Abra o arquivo `index.html` em qualquer navegador moderno (Chrome, Firefox, Edge, Safari).
3.  Pronto\! Comece a simulação.

## 🏗️ Estrutura do Projeto e Dados

A lógica principal e os dados dos desafios residem dentro das tags `<script>` no arquivo HTML. Se você deseja contribuir com novos cenários, é importante entender duas estruturas de dados principais:

### 1\. Objeto `services`

Este objeto define os metadados de cada serviço disponível no simulador.

```javascript
const services = {
    AWS: {
        's3': { name: 'S3', icon: 'url/to/icon.svg' },
        'lambda': { name: 'Lambda', icon: 'url/to/icon.png' },
        // ... outros serviços
    },
    Azure: { /* ... */ },
    GCP: { /* ... */ }
};
```

### 2\. Objeto `scenarios`

Este é o coração do simulador, contendo todos os desafios. Cada cenário é um objeto com a seguinte estrutura:

```javascript
{
    "id": "aws-de-001", // ID único
    "category": "data-engineering", // Categoria (data-engineering, data-analysis, cloud-operations)
    "difficulty": 3, // Nível de 1 a 5
    "question": "Descrição do problema a ser resolvido.",
    "solution": ["rds", "dms", "s3", "redshift"], // Array com a solução correta
    "availableServices": ["rds", "dms", "s3", "redshift", "lambda", "kinesis"], // Serviços na caixa de ferramentas
    "explanation": "Explicação do porquê esta é a solução correta."
}
```

#### Sintaxe Avançada para Soluções

O campo `solution` suporta padrões complexos:

  - **Fluxos Paralelos**: Use um array de arrays. A ordem dos arrays internos não importa.
    ```javascript
    // Exemplo: Firehose envia para S3 e Redshift em paralelo
    "solution": ["kinesis", "kinesis-firehose", [["s3"], ["redshift"]]]
    ```
  - **Orquestradores**: Use um objeto com a chave `orchestrator` e `flow`.
    ```javascript
    // Exemplo: Step Functions orquestrando um fluxo
    "solution": [{"orchestrator": "step-functions", "flow": ["lambda", "dynamodb"]}]
    ```

## 📄 Licença

Distribuído sob a licença MIT.
