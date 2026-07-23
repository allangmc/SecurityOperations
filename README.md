# Security Operations

## Operações de Segurança da Informação: Logs, Automação e Resposta a Incidentes

## Sobre o projeto

Este projeto apresenta uma pesquisa sobre o funcionamento das operações modernas de cibersegurança, com foco na pesquisa sobre logs, automação de processos de segurança e resposta a incidentes.

A pesquisa foi desenvolvida com o apoio do NotebookLM e baseada em fontes técnicas e institucionais relacionadas a Security Operations Centers, SIEM, SOAR, análise de eventos e tratamento de incidentes de segurança.

Este é um projeto de pesquisa e documentação. Não envolve a implementação de um laboratório prático ou a configuração de ferramentas em ambiente real.

## Contexto e objetivos

O objetivo desta pesquisa é compreender como equipes de segurança utilizam logs, ferramentas de monitoramento e automações para identificar atividades suspeitas, investigar alertas e responder a possíveis incidentes.

Também busca entender o papel de um Analista SOC N1 durante o processo de triagem e escalonamento de ocorrências.

## Curadoria de fontes

* [NIST — False Positive](https://csrc.nist.gov/glossary/term/false_positive)
* [UnderDefense — AI SOC SLA Guide](https://underdefense.com/blog/ai-soc-sla-guide/)
* [Swimlane — SIEM vs. SOAR](https://swimlane.com/blog/siem-soar/)
* [Accountable — Security Incident vs. Event](https://www.accountablehq.com/post/security-incident-vs-event-what-s-the-difference-definitions-examples)

## Engenharia de prompts e “cicatrizes”

### O que são logs e por que são importantes para a segurança?

Foram testados dois modelos de prompt para obtenção dos resultados: um pedindo a formatação do conteúdo em ebook e outro diretamente no chat, utilizando a seguinte pergunta mais abrangente:

> Como as operações modernas de cibersegurança utilizam logs, automação e processos de resposta a incidentes para detectar, investigar e tratar ameaças?

A resposta obtida foi que os logs constituem a base de toda visualização técnica em operações de segurança. Os logs são a evidência da atividade nos sistemas e na rede.

Existem também regras restritas para a retenção desses registros. Nesse ponto, entramos na área de compliance e conformidade de uma organização.

Os logs estão diretamente ligados às ferramentas SIEM. É por meio deles que são obtidas interpretações sobre determinada atividade representar ou não uma ameaça.

Nesse momento, já estamos no campo da análise. A análise pressupõe uma conclusão e, portanto, ameaças, comportamentos e insights podem ser identificados por meio dos logs.

### Qual é a diferença entre evento, alerta e incidente?

Foram testados dois modelos de prompt: um perguntando diretamente a diferença entre os três conceitos e outro solicitando exemplos práticos que os correlacionassem.

* **Evento:** qualquer mudança observável em um sistema, como o registro de um funcionário realizando login.
* **Alerta:** evento que sinaliza um comportamento anômalo, podendo ser entendido como uma hipótese de ameaça.
* **Incidente:** situação na qual a hipótese de ameaça se concretiza, podendo envolver um conjunto de eventos que caracteriza uma violação da tríade CIA: confidencialidade, integridade e/ou disponibilidade.

De um evento a um incidente, temos momentos diferentes. Um incidente geralmente não ocorre sem sinais anteriores, e tanto alertas quanto incidentes são compostos por eventos relacionados.

### Como um Analista SOC N1 realiza a triagem de um alerta?

Esta é uma abordagem tática da atuação de um Analista SOC N1 diante de um alerta, com base nos conceitos trabalhados anteriormente.

#### Abordagem e possível alvo

Primeiro, o analista deverá observar as informações iniciais de credenciais e o possível alvo afetado pelo alerta.

Em uma analogia com uma abordagem policial, seria como perceber um comportamento suspeito e perguntar ao indivíduo quem ele é e para onde está indo.

Se o usuário suspeito estiver acessando um ambiente crítico, a ocorrência poderá apresentar maior criticidade. Se estiver acessando um ambiente comum e compatível com sua função, o fator de criticidade poderá ser menor.

#### Falso positivo?

O analista deverá investigar o que causou a interpretação de comportamento anormal.

O sinal será comparado a outros sinais anteriormente classificados como legítimos. Semelhanças relevantes podem indicar um falso positivo.

Atualizações ou patches recentes também podem influenciar a geração do alerta.

#### Threat Intelligence na prática

Para aumentar a conclusividade da análise, os indicadores relacionados ao evento serão comparados com fontes públicas e privadas.

Caso endereços IP, domínios, hashes ou outros indicadores estejam registrados em listas de bloqueio, por exemplo, a suspeita de uma ameaça aumenta significativamente.

#### Investigação de histórico e comportamento

O analista deverá investigar o comportamento histórico do host e do usuário para compreender se aquela atividade é comum ou anômala.

Também deverá observar possíveis sinais de movimentação suspeita ou exfiltração de dados.

#### Tomada de decisão

Ao confirmar um incidente, caracterizado como um verdadeiro positivo e uma ameaça em atuação, todo o registro deverá ser documentado.

A documentação deve incluir:

* linha do tempo;
* impactos identificados;
* severidade calculada;
* evidências coletadas;
* indicadores analisados;
* decisão tomada.

Quando aplicável, as atividades poderão ser relacionadas às técnicas do MITRE ATT&CK, facilitando a atuação do Tier 2, que dará andamento ao Incident Response Plan.

## Glossário dos principais conceitos

### Alerta

Notificação de uma possível atividade suspeita gerada por uma ferramenta, regra de detecção ou análise humana. Um alerta representa uma hipótese que precisa ser investigada.

### Ativo

Qualquer recurso que possui valor para a organização, como dados, sistemas, dispositivos, aplicações, pessoas, serviços e infraestrutura.

### Automação de segurança

Uso de tecnologias para executar tarefas de segurança com pouca ou nenhuma intervenção manual, seguindo regras e procedimentos definidos.

### CIA

Sigla para os princípios de confidencialidade, integridade e disponibilidade:

* **Confidencialidade:** somente pessoas autorizadas podem acessar a informação.
* **Integridade:** a informação deve permanecer correta e protegida contra alterações indevidas.
* **Disponibilidade:** sistemas e informações devem estar acessíveis quando necessários.

### Correlação de eventos

Processo de relacionar eventos provenientes de diferentes fontes para identificar padrões, sequências ou comportamentos suspeitos.

### Escalonamento

Encaminhamento de um alerta ou incidente para um nível mais especializado, uma equipe responsável ou uma autoridade com maior poder de decisão.

### Evento

Qualquer ocorrência observável em um sistema, aplicação, dispositivo ou rede.

### Evidência

Informação que ajuda a demonstrar, explicar ou reconstruir uma atividade relacionada a um possível incidente.

### Exfiltração de dados

Transferência não autorizada de informações para fora do ambiente da organização.

### Fadiga de alertas

Redução da capacidade de atenção dos analistas causada por um volume excessivo de alertas, especialmente falsos positivos e ocorrências de baixa relevância.

### Falso negativo

Situação em que uma atividade maliciosa ocorre, mas não é detectada ou não gera alerta.

### Falso positivo

Alerta que indica uma possível ameaça, mas que, após a investigação, é identificado como atividade legítima ou não maliciosa.

### Hash

Valor gerado por uma função matemática a partir de um arquivo ou conjunto de dados. Pode ser utilizado para identificar arquivos e verificar sua integridade.

### Host

Dispositivo conectado a uma rede, como computador, servidor, máquina virtual ou equipamento de rede.

### Incidente de segurança

Ocorrência que ameaça ou viola a confidencialidade, a integridade ou a disponibilidade de dados e sistemas, exigindo investigação ou resposta.

### Incident Response Plan — IRP

Plano que define como a organização deve preparar-se, identificar, conter, erradicar e recuperar-se de incidentes de segurança.

### Indicador de comprometimento — IoC

Evidência técnica que pode estar relacionada a uma atividade maliciosa, como endereço IP, domínio, hash, arquivo ou chave de registro.

### Linha do tempo

Organização cronológica dos eventos e ações relacionados a uma investigação.

### Log

Registro produzido por um sistema, aplicação, dispositivo ou serviço sobre uma atividade executada.

### MITRE ATT&CK

Base de conhecimento que organiza táticas, técnicas e procedimentos utilizados por adversários em ataques cibernéticos.

### Normalização

Processo de transformar logs de diferentes fontes em uma estrutura padronizada para facilitar pesquisas e correlações.

### Playbook

Sequência documentada ou automatizada de ações que deve ser executada diante de determinado tipo de alerta ou incidente.

### Regra de correlação

Lógica utilizada por uma ferramenta para relacionar múltiplos eventos e identificar um possível comportamento suspeito.

### Retenção de logs

Período e condições definidos para o armazenamento dos registros gerados pelos sistemas.

### Severidade

Classificação do impacto potencial ou confirmado de uma ameaça ou incidente.

### SIEM

Solução que centraliza, normaliza, pesquisa, correlaciona e analisa eventos de segurança, podendo gerar alertas.

### SLA

Acordo de nível de serviço que define prazos, responsabilidades e padrões esperados para o atendimento de alertas, chamados ou incidentes.

### SOC

Centro de Operações de Segurança responsável pelo monitoramento, detecção, investigação e resposta a ameaças.

### SOC N1

Primeiro nível operacional do SOC. Realiza monitoramento, triagem inicial, coleta de evidências, classificação, documentação e escalonamento.

### SOC N2

Nível responsável por investigações mais aprofundadas, análise técnica avançada e apoio à resposta a incidentes.

### SOAR

Tecnologia utilizada para integrar ferramentas, automatizar tarefas e orquestrar processos de investigação e resposta.

### Tática

No MITRE ATT&CK, representa o objetivo que o atacante deseja alcançar em determinada etapa do ataque.

### Técnica

No MITRE ATT&CK, representa a maneira utilizada pelo atacante para alcançar um objetivo.

### Threat Intelligence

Informações analisadas sobre ameaças, atacantes, vulnerabilidades, campanhas, técnicas e indicadores de comprometimento.

### Triagem

Processo inicial de análise de um alerta para determinar sua validade, contexto, impacto, severidade e necessidade de escalonamento.

### Verdadeiro positivo

Alerta cuja investigação confirma a existência de atividade maliciosa ou violação de segurança.

## Prompts reutilizáveis para futuras revisões

### Prompt 1 — Revisão geral do conteúdo

> Explique os principais conceitos de Security Operations, incluindo logs, SIEM, SOAR, eventos, alertas, incidentes, Threat Intelligence e resposta a incidentes. Utilize linguagem acessível para um estudante iniciante em Segurança da Informação e apresente exemplos práticos.

### Prompt 2 — Evento, alerta e incidente

> Explique a diferença entre evento, alerta e incidente de segurança. Crie cinco cenários práticos e, em cada cenário, identifique quais elementos são eventos, qual situação gerou o alerta e em que momento o caso pode ser classificado como incidente.

### Prompt 5 — Exercício de classificação

> Crie dez situações relacionadas a operações de segurança. Minha tarefa será classificá-las como:
>
> * evento normal;
> * evento suspeito;
> * alerta;
> * falso positivo;
> * verdadeiro positivo;
> * incidente.
>
> Não mostre as respostas imediatamente. Depois que eu responder, corrija cada item e explique o raciocínio.

## Autor

**Allan Moraes**

Graduando em Defesa Cibernética e certificado ISC2 CC, em desenvolvimento profissional para atuação em Segurança da Informação, SOC e Cybersecurity.
