
Trilha EPR - Simulador de Fluxograma Acadêmico
O Trilha EPR é uma aplicação web desenvolvida para auxiliar estudantes de graduação em Engenharia de Produção na gestão, no planejamento e na otimização de seus fluxos acadêmicos. A ferramenta integra a importação de dados do sistema acadêmico (SIGAA), a simulação de grades horárias com suporte de algoritmos de recomendação e a visualização de métricas de desempenho por meio de um painel analítico avançado.

Principais Funcionalidades
Importação de Histórico Escolar (SIGAA): Sistema de leitura de arquivos PDF e extração de texto operando integralmente no lado do cliente (Client-Side). Esta abordagem garante a privacidade dos dados do usuário, em conformidade com as diretrizes da Lei Geral de Proteção de Dados (LGPD), visto que nenhuma informação acadêmica é enviada a servidores externos durante a importação.

Mapeamento de Pré-requisitos e Co-requisitos: O sistema calcula dinamicamente o estado da grade do aluno, bloqueando seleções inválidas e alertando sobre quebras de hierarquia curricular.

Simulação de Matrícula via IA: Integração com uma API em Python que atua como motor de otimização. O algoritmo analisa o histórico do aluno, a carga horária desejada e a trilha de especialização escolhida (Operações, Logística, Pesquisa Operacional/Dados ou Gestão/Economia) para sugerir a grade ideal.

Prevenção de Choques de Horário: Motor interno de colisão ("Mesh Collision") que avalia os turnos e os horários das disciplinas selecionadas, emitindo alertas visuais imediatos em caso de sobreposição.

Dashboard Analítico: Painel de telemetria contendo Indicadores-Chave de Desempenho (KPIs), acompanhamento de horas complementares (Módulo Livre) e gráficos de radar (Chart.js) que mapeiam as competências adquiridas pelo discente ao longo do curso.

Exportação de Dados: Capacidade de gerar o registro da grade simulada em formato de imagem (PNG) ou exportação em texto estruturado para a área de transferência.

Arquitetura e Tecnologias
A aplicação foi construída visando alta performance, baixa latência e responsividade plena, não dependendo de frameworks front-end pesados.

Front-end: HTML5, CSS3, JavaScript (Vanilla).

Bibliotecas Integradas:

PDF.js: Para o processamento e parse local de arquivos PDF.

PapaParse: Para a leitura e estruturação da base de dados de disciplinas via arquivo CSV.

Chart.js: Para a renderização das métricas visuais no painel analítico.

html2canvas: Para a renderização e exportação da interface gráfica em formato de imagem.

Back-end (Motor de Simulação): API RESTful desenvolvida em Python, responsável pelo processamento lógico das sugestões de trilhas e otimização de grade.

Instalação e Execução Local
Como a interface da aplicação é baseada em tecnologias web nativas, a sua execução não requer processos complexos de compilação ou gerenciadores de pacotes para o front-end.


Configuração do Ambiente de API
O motor de simulação por Inteligência Artificial depende de um serviço de retaguarda (Backend). A configuração de apontamento para este serviço está localizada no início do arquivo app.js:

JavaScript
const AMBIENTE = 'prod'; // 'dev' para desenvolvimento local, 'prod' para produção

const API_URL = AMBIENTE === 'dev'
    ? 'http://ENDERECO_IP_LOCAL:PORTA/otimizar'
    : 'https://URL_DA_API_EM_PRODUCAO/otimizar';
Certifique-se de ajustar a variável API_URL para o endereço adequado caso esteja executando o backend em ambiente local.

Estrutura do Projeto
index.html: Estrutura principal da interface, modais e elementos flutuantes.

style.css: Folhas de estilo com suporte a design responsivo (Mobile-First) e modo escuro nativo.

app.js: Lógica central da aplicação, controle de estado, requisições de API e manipulação do DOM.

disciplinas.csv: Banco de dados estático contendo códigos, nomes, cargas horárias, áreas de conhecimento e requisitos das disciplinas do curso.

Licença
Este projeto foi desenvolvido para fins acadêmicos e de otimização de processos estudantis. Sinta-se à vontade para propor melhorias através de Pull Requests ou para relatar problemas através da aba Issues do repositório.
```bash
git clone [https://github.com/SEU_USUARIO/trilha-epr.git](https://github.com/SEU_USUARIO/trilha-epr.git)
cd trilha-epr
