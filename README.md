# Estrutura de Software para Sistema de Logins de Venda de Ingressos

Este repositório contém a descrição detalhada da estrutura de software para um sistema de logins de venda de ingressos para um mega show de Rock em Rio. O sistema é projetado para garantir que apenas clientes autenticados possam comprar ingressos, com um foco especial na gestão eficiente de solicitações de compra e na proteção contra ataques de negação de serviço (DDoS) e outras formas de abuso.

## Componentes Principais

### Frontend do Cliente

O Frontend do Cliente é a interface de usuário que permite aos clientes acessar o site e fazer login. Ele é responsável pela interação com o cliente, exibindo informações sobre os ingressos disponíveis e processando solicitações de compra.

- **Interface de Usuário**:
 - **Página de Login**: Formulário para inserção de credenciais do usuário.
 - **Página de Ingressos**: Exibe detalhes dos ingressos disponíveis, incluindo preços e opções de compra.
 - **Página de Carrinho**: Permite aos usuários selecionar ingressos e revisar suas compras antes de finalizar.

- **Processamento de Solicitações**:
 - **Módulo de Autenticação**: Verifica as credenciais do usuário e gerencia sessões.
 - **Módulo de Seleção de Ingressos**: Permite aos usuários selecionar ingressos e adicioná-los ao carrinho.
 - **Módulo de Finalização de Compra**: Processa o pagamento e finaliza a compra dos ingressos selecionados.

### Servidor de Aplicativos

O Servidor de Aplicativos gerencia a lógica de negócios e processa as solicitações dos clientes. Ele verifica a disponibilidade de ingressos antes de processar uma compra, implementa um sistema de fila de solicitações para garantir a ordem de chegada das compras, e protege contra ataques de negação de serviço (DDoS) e outras formas de abuso.

- **Lógica de Negócios**:
 - **Módulo de Gerenciamento de Ingressos**: Controla a disponibilidade de ingressos, incluindo a adição, remoção e atualização de ingressos.
 - **Módulo de Processamento de Pedidos**: Gerencia o processo de compra, incluindo a verificação de disponibilidade, cálculo de preços e processamento de pagamentos.

- **Verificação de Disponibilidade**:
 - **Módulo de Consulta de Disponibilidade**: Verifica a disponibilidade de ingressos no banco de dados antes de permitir uma compra.
 - **Módulo de Atualização de Disponibilidade**: Atualiza a disponibilidade de ingressos após uma compra bem-sucedida.

### Banco de Dados

O Banco de Dados armazena informações sobre os ingressos disponíveis, clientes registrados e histórico de compras. Ele garante consistência e integridade dos dados.

- **Tabela de Ingressos**: Armazena informações sobre os ingressos disponíveis, incluindo tipo, preço e disponibilidade.
- **Tabela de Clientes**: Armazena informações sobre os clientes registrados, incluindo nome, endereço de e-mail e detalhes de pagamento.
- **Tabela de Compras**: Registra todas as compras realizadas, incluindo detalhes do ingresso, cliente e data da compra.

### Sistema de Cache

O Sistema de Cache mantém em cache informações sobre a disponibilidade de ingressos para reduzir o tempo de resposta e aliviar a carga do banco de dados. Ele atualiza as informações periódicamente ou em tempo real para garantir precisão.

- **Cache de Disponibilidade de Ingressos**:
 - **Armazenamento de Dados**: Um armazenamento em memória que mantém informações sobre a disponibilidade de ingressos.
 - **Algoritmo de Expulsão**: Um algoritmo que determina quais dados devem ser removidos do cache quando ele está cheio.
 - **Atualização de Dados**: Um mecanismo que atualiza os dados em cache com base em mudanças no banco de dados.

### Sistema de Filas

O Sistema de Filas gerencia a ordem de chegada das solicitações de compra. Ele garante que cada cliente seja atendido de forma justa e que os ingressos não sejam vendidos para mais de uma pessoa.

- **Fila de Solicitações de Compra**:
 - **Armazenamento de Solicitações**: Um armazenamento que mantém as solicitações de compra em uma fila.
 - **Algoritmo de Priorização**: Um algoritmo que determina a ordem de processamento das solicitações de compra.

### Monitoramento e Logging

O Monitoramento e Logging registra atividades do sistema para auditoria, solução de problemas e análise de desempenho. Ele alerta para picos de tráfego, comportamento anormal e possíveis ataques.

- **Registro de Atividades**: Um sistema que registra todas as atividades do sistema, incluindo solicitações de entrada, processamento de compra e liberação de ingressos.
- **Alertas**: Um sistema que envia alertas em caso de picos de tráfego, comportamento anormal ou falhas no processamento de solicitações.

### Balanceador de Carga

O Balanceador de Carga distribui o tráfego de entrada entre vários servidores para evitar sobrecarga e garantir disponibilidade.

- **Algoritmo de Distribuição de Carga**:
 - **Round Robin**: Um algoritmo simples que distribui as requisições de entrada de forma sequencial entre os servidores.
 - **Least Connections**: Um algoritmo que distribui as requisições para o servidor com o menor número de conexões ativas.
 - **IP Hash**: Um algoritmo que distribui as requisições com base no endereço IP do cliente.

### Serviço de Autenticação e Autorização

O Serviço de Autenticação e Autorização gerencia o processo de login e autenticação dos clientes. Ele garante que apenas clientes autenticados possam acessar a funcionalidade de compra de ingressos.

- **Módulo de Autenticação**:
 - **Verificação de Credenciais**: Verifica as credenciais do usuário contra as informações armazenadas no banco de dados.
 - **Geração de Token**: Gera um token de autenticação único para o usuário após uma autenticação bem-sucedida.

- **Módulo de Autorização**:
 - **Verificação de Token**: Verifica o token de autenticação fornecido pelo usuário para cada solicitação.
 - **Gerenciamento de Permissões**: Determina as permissões do usuário com base em seu perfil e funções.

---
