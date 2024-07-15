# Documentação do Sistema de Integração de Laudos para o Hospital Iso Olhos

## Visão Geral

O sistema foi desenvolvido para o Hospital Iso Olhos com o objetivo de integrar os procedimentos realizados em cada laudo médico com o sistema FastMedic. Ele é composto por três aplicações desenvolvidas em Python3: **PreparaLaudo**, **PainelIntegração** e **Motor**. A seguir, apresentamos uma visão detalhada de cada uma dessas aplicações e suas funcionalidades.

## Principais Funcionalidades

O sistema realiza as seguintes operações:
- **Criação do Laudo**: Integração inicial dos laudos médicos com o sistema FastMedic.
- **Validação da Criação do Laudo**: Consulta para verificar se o laudo foi criado corretamente.
- **Atualização do Laudo**: Em caso de erro no retorno do FastMedic, permite a atualização do laudo.
- **Envio do Anexo**: Envia documentos anexos dos laudos.
- **Consulta da Autorização**: Verifica se o laudo foi autorizado e atualiza o sistema TASY em caso positivo.

## Detalhamento das Aplicações

### 1. PreparaLaudo

A aplicação **PreparaLaudo** é responsável pelo início do fluxo de integração com o sistema FastMedic. Ela possui uma interface onde o usuário seleciona a pasta que contém os laudos a serem integrados. As principais funções do PreparaLaudo são:

- **Captura dos Laudos**: O usuário seleciona a pasta que contém os laudos a serem processados. O sistema então captura todos os arquivos de laudos presentes nesta pasta.
- **Interpretação do Laudo**: O sistema analisa cada laudo, extraindo informações importantes como o número do atendimento.
- **Salvamento na Base do Integrador**: As informações extraídas, como o número do atendimento, são salvas na base de dados do integrador.
- **Envio para o Repositório de Laudos**: O laudo é enviado para um repositório específico, que será utilizado posteriormente pelo Motor para enviar os laudos para o FastMedic.

### 2. PainelIntegração

A aplicação **PainelIntegração** possui uma interface gráfica que permite aos usuários visualizarem e gerenciarem as integrações realizadas. Suas funcionalidades incluem:

- **Pesquisa Avançada**: Permite que os usuários pesquisem as integrações com base em critérios como status, data de atendimento e número de atendimento.
- **Exibição de Dados das Integrações**: Mostra detalhes das integrações, incluindo o XML enviado para o FastMedic, possíveis erros retornados pelo FastMedic e informações detalhadas dos procedimentos.
- **Reprocessamento de Integrações**: Caso uma integração falhe, o usuário pode selecionar a integração da lista e clicar em "Reprocessar". Isso salva a integração na base de dados do integrador para que seja reprocessada.

### 3. Motor

A aplicação **Motor** é o núcleo do sistema de integração, automatizando diversas etapas do processo. Suas principais responsabilidades incluem:

- **Consulta de Dados no TASY**: O Motor consulta a base de dados do TASY para obter informações detalhadas dos procedimentos realizados por atendimento.
- **Envio em Lote para o FastMedic**: Os dados dos procedimentos são enviados em lote para o FastMedic.
- **Verificação de Guias de Remessa**: O Motor verifica, por meio de guias de remessa, se o processamento dos procedimentos pelo FastMedic foi bem-sucedido.
- **Envio de Anexos**: Utilizando o repositório de laudos preenchido pelo PreparaLaudo, o Motor envia os anexos dos laudos para o FastMedic.
- **Consulta de Autorização**: O Motor aguarda a autorização dos procedimentos e, ao receber a autorização, atualiza o sistema TASY com essa informação, garantindo que os dados dos atendimentos e procedimentos estejam sempre atualizados.

## Conclusão

Este sistema foi desenvolvido para otimizar e automatizar a integração de laudos médicos entre o sistema TASY do Hospital Iso Olhos e o sistema FastMedic, garantindo uma gestão eficiente e segura dos dados de atendimento e procedimentos médicos. Através das três aplicações detalhadas, o sistema permite um controle preciso e uma operação simplificada para os usuários envolvidos no processo de integração.
