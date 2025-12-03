## Grupo Pegazus

O **Grupo Pegazus** é responsável pelo desenvolvimento do **Beergam**, um **ERP voltado para e-commerce**, focado em escalabilidade, observabilidade e boas práticas de engenharia de software.

Nosso objetivo atual é **lançar e evoluir continuamente a plataforma**, garantindo uma base sólida para novos módulos, integrações e para o crescimento do produto.

- **Produto principal**: Beergam – ERP para e-commerce  
- **Público deste repositório**: desenvolvedores, contribuidores e novos membros do time  
- **Principais valores técnicos**: código limpo, baixo acoplamento, alta coesão, testes e automação


### Arquitetura em Alto Nível

A plataforma Beergam é composta por múltiplos serviços, com separação clara de responsabilidades:

- **Backend principal (`Beergam_project_backend`)**  
  - API REST em Flask responsável pela lógica de negócio principal do ERP.  
  - Comunicação assíncrona via **Celery** e **Redis** (fila/pubsub).  
  - Persistência em **MySQL**.  
  - Observabilidade e métricas com **Grafana**.  
  - Orquestração e empacotamento com **Docker**.  
  - Pipelines de **CI/CD com GitHub Actions**.  
  - Integração com o serviço de **Socket** via Redis (pub/sub).

- **Frontend principal (`Beergam_react_router`)**  
  - Aplicação **React** com **React Router** para SPA orientada a rotas.  
  - Gerenciamento de estado com **Zustand**.  
  - Fetch e cache de dados com **React Query**.  
  - Estilização com **Tailwind CSS**.  
  - Build com **Vite**.  
  - Comunicação com o backend via **REST (Axios)**.  
  - Comunicação em tempo real via **Socket.IO**.

- **Serviço de Socket (`Beergam_project_socket`)**  
  - Responsável por comunicação em tempo real (notificações, atualizações instantâneas etc.).  
  - Implementado com **Socket.IO** em JavaScript.  
  - Integra-se ao restante da stack via **pub/sub com Redis**.

- **Frontend legado (`Beergam_project_frontend`)**  
  - Primeira versão de frontend em **React + Tailwind + Storybook + TypeScript**.  
  - Classificado como **legado**, mantido apenas para referência histórica e eventual migração.

- **Sistema de Afiliados (`Beergam_project_afiliados`)**  
  - Projeto ainda **não iniciado**.  
  - Stack e integrações serão definidas conforme evolução da plataforma.


## Stack Tecnológica Principal

- **Frontend**: `React`, `React Router`, `React Query`, `Zustand`, `Tailwind CSS`, `Vite`, `Axios`.  
- **Backend**: `Flask`, `Celery`, `MySQL`, `Redis`.  
- **Comunicação em tempo real**: `Socket.IO`, `Redis (pub/sub)`.  
- **Infra / DevOps**: `Docker`, `GitHub Actions`.  
- **Observabilidade**: `Grafana`.  


## Boas Práticas e Filosofia de Código

O Grupo Pegazus busca manter uma base de código sustentável, extensível e compreensível, adotando:

- **Princípios SOLID**  
  - **S**ingle Responsibility: cada classe/componente com uma única responsabilidade bem definida.  
  - **O**pen/Closed: módulos abertos para extensão e fechados para modificação.  
  - **L**iskov Substitution, **I**nterface Segregation, **D**ependency Inversion aplicados principalmente nas camadas de domínio, serviços e integrações.

- **Object Calisthenics**  
  - Classes pequenas, com foco em uma única coisa.  
  - Métodos curtos e com baixo nível de aninhamento.  
  - Evitar estruturas de dados primitivas “nuas” para representar conceitos de domínio.  
  - Redução de acoplamento e facilidade de testes.

Esses princípios orientam tanto o backend quanto o frontend, aumentando a manutenibilidade e a qualidade do código.


## Status da Plataforma

- **API principal (Backend)**: [`https://api.beergam.com.br/v1/health/`](https://api.beergam.com.br/v1/health/)  
- **Serviço de WebSocket**: [`https://ws.beergam.com.br/health`](https://ws.beergam.com.br/health)  
- **Aplicação Web**: [`https://www.beergam.com.br/`](https://www.beergam.com.br/)

Esses endpoints de *health check* auxiliam no monitoramento do ambiente de produção e na automação de alertas.
