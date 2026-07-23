# SecurityOperations
Operações de Segurança da Informação: Logs, Automação e Resposta a Incidentes

## Sobre o projeto

Este projeto apresenta uma pesquisa sobre o funcionamento das operações modernas de cibersegurança, com foco na pesquisa sobre logs, automação de processos de segurança e resposta a incidentes.

A pesquisa foi desenvolvida com o apoio do NotebookLM e baseada em fontes técnicas e institucionais relacionadas a Security Operations Centers, SIEM, SOAR, análise de eventos e tratamento de incidentes de segurança.

Este é um projeto de pesquisa e documentação. Não envolve a implementação de um laboratório prático ou a configuração de ferramentas em ambiente real.

## Contexto e Objetivos

O objetivo desta pesquisa é compreender como equipes de segurança utilizam logs, ferramentas de monitoramento e automações para identificar atividades suspeitas, investigar alertas e responder a possíveis incidentes.

Também busca entender o papel de um Analista SOC N1 durante o processo de triagem e escalonamento de ocorrências.

## Curadoria de Fontes

https://csrc.nist.gov/glossary/term/false_positive
https://underdefense.com/blog/ai-soc-sla-guide/
https://swimlane.com/blog/siem-soar/
https://www.accountablehq.com/post/security-incident-vs-event-what-s-the-difference-definitions-examples

## Engenharia de Prompts e "Cicatrizes"

- O que são logs e por que são importantes para a segurança?
  Foram testados dois modelos de prompt para obtenção dos resultados, um pedindo a formatação do conteúdo em ebook e outra diretamente no chat para resposta com o modelo de pergunta mais abrangente: "Como as operações modernas de cibersegurança utilizam logs, automação e processos de resposta a incidentes para detectar, investigar e tratar ameaças?"
  E resposta obtida foi que os logs contituem a base de toda visualização técnica em operações de segurança, os logs são a evidência da atividade nos sistemas e rede. Existem também regras restritas para a retenção destes registros, a este ponto estamos na seara de compliance e conformidade de uma organização.
  Logs estão diretamente ligados a ferramentas SIEM, é através deles que são obtidas interpretações se se trata de uma ameaça ou não. Já estamos no campo de análise, a análise pressupõe uma conclusão, portanto, tanto ameaças quanto comportamentos e insights podem ser obtidos através dos logs.
  
- Qual é a diferença entre evento, alerta e incidente?
  Foram testados também dois modelos de prompt, um perguntando exatamente o que se lê acima, e outro pedindo exemplos práticos correlacionando estes 3 atores.
  Um evento é qualquer mudança observável em um sistema, podendo ser o registro ou um funcionário fazendo login no sistema.
  Um alerta é um tipo de evento que sinaliza um comportamento anômalo, outro sinônimo para essa resposta seria "hipotese de ameaça".
  Um incidente é um tipo de alerta que se concretizou de hipotese de ameaça para fato, podendo ser um conjunto de eventos que caracterizam uma clara violação da tríade CIA, confidencialidade, integridade e/ou disponibilidade.
  Notei que de um evento a um incidente, temos momentos diferentes, respectivamente início e final, já que um incidente geralmente não ocorre sem um alerta, e um alerta e um incidente são compostos de eventos intrínsecamente.

- Como um Analista SOC N1 realiza a triagem de um alerta?
    Aqui está a abordagem tática de um analista N1 de SOC, desde os conceitos trabalhados nas perguntas anteriores, agora temos a abordagem de um analista ao observar o alerta na prática. Vamos lá.
  
  Abordagem e possível alvo
    Primeiro o analista deverá observar as informações de credenciais iniciais somadas ao possível alvo afetável deste alerta, em uma abordagem policial, seria como perceber um comportamento suspeito e perguntar ao suspeito, quem é e onde está indo. Se o usuário suspeito está indo a um beco escuro, pode ser um fato de criticidade maior, enquanto se for a uma igreja ou sinagoga por exemplo, poderá ter um fator de criticidade menor.
  
  Falso positivo?
    Seguindo na abordagem policial, o analista irá "perguntar" o que causou esta interpretação de comportamento anormal? O sinal será comparado a outros sinais que não eram malignos, semelhanças contundentes podem começar a concluir um falso positivo, uptades ou patches recentes podem ter também influencia sobre este alerta.
  
  Threat Intellingence na prática
    Para conclusividade, as credenciais deste evento serão comparadas a fontes publicas e privadas, se estas credenciais encontram-se registradas em listas de bloqueio por exemplo, caso estejam, aumenta significativamente a suspeita de uma ameaça.
  
  Investigação de histórico e comportamento
    Este individuo vai mesmo a igreja, ou está mentindo? Novamente figurando com a ilustração da abrodagem policial, temos uma investigação no comportamento deste host, para entender se historicamente é comum que isso aconteça ou não, e mesmo se há uma exfiltração de dados.
  
  Tomada de decisão
    Ao confirmar um incidente, que é um verdadeiro positivo, ou seja, uma ameaça em atuação, todo registro deste incidente com linha do tempo, impactos e severidade calculada deverá ser documentada com o padrão das técnicas do MITRE ATT&CK facilitando a atuação do Tier 2, que deverá dar andamento ao Incident Response Plan.
  
## Glossário dos principais conceitos
 
  Alerta
Notificação de uma possível atividade suspeita gerada por uma ferramenta, regra de detecção ou análise humana. Um alerta representa uma hipótese que precisa ser investigada.

  Ativo
Qualquer recurso que possui valor para a organização, como dados, sistemas, dispositivos, aplicações, pessoas, serviços e infraestrutura.

  Automação de segurança
Uso de tecnologias para executar tarefas de segurança com pouca ou nenhuma intervenção manual, seguindo regras e procedimentos definidos.

  CIA
Sigla para os princípios de confidencialidade, integridade e disponibilidade.
Confidencialidade: somente pessoas autorizadas podem acessar a informação.
Integridade: a informação deve permanecer correta e protegida contra alterações indevidas.
Disponibilidade: sistemas e informações devem estar acessíveis quando necessários.

  Correlação de eventos
Processo de relacionar eventos provenientes de diferentes fontes para identificar padrões, sequências ou comportamentos suspeitos.

  Escalonamento
Encaminhamento de um alerta ou incidente para um nível mais especializado, uma equipe responsável ou uma autoridade com maior poder de decisão.

  Evento
Qualquer ocorrência observável em um sistema, aplicação, dispositivo ou rede.

  Evidência
Informação que ajuda a demonstrar, explicar ou reconstruir uma atividade relacionada a um possível incidente.

  Exfiltração de dados
Transferência não autorizada de informações para fora do ambiente da organização.

  Fadiga de alertas
Redução da capacidade de atenção dos analistas causada por um volume excessivo de alertas, especialmente falsos positivos e ocorrências de baixa relevância.

  Falso negativo
Situação em que uma atividade maliciosa ocorre, mas não é detectada ou não gera alerta.

  Falso positivo
Alerta que indica uma possível ameaça, mas que, após a investigação, é identificado como atividade legítima ou não maliciosa.

  Hash
Valor gerado por uma função matemática a partir de um arquivo ou conjunto de dados. Pode ser utilizado para identificar arquivos e verificar sua integridade.

  Host
Dispositivo conectado a uma rede, como computador, servidor, máquina virtual ou equipamento de rede.

  Incidente de segurança
Ocorrência que ameaça ou viola a confidencialidade, a integridade ou a disponibilidade de dados e sistemas, exigindo investigação ou resposta.

  Incident Response Plan — IRP
Plano que define como a organização deve preparar-se, identificar, conter, erradicar e recuperar-se de incidentes de segurança.

  Indicador de comprometimento — IoC
Evidência técnica que pode estar relacionada a uma atividade maliciosa, como endereço IP, domínio, hash, arquivo ou chave de registro.

  Linha do tempo
Organização cronológica dos eventos e ações relacionados a uma investigação.

  Log
Registro produzido por um sistema, aplicação, dispositivo ou serviço sobre uma atividade executada.

  MITRE ATT&CK
Base de conhecimento que organiza táticas, técnicas e procedimentos utilizados por adversários em ataques cibernéticos.

  Normalização
Processo de transformar logs de diferentes fontes em uma estrutura padronizada para facilitar pesquisas e correlações.

  Playbook
Sequência documentada ou automatizada de ações que deve ser executada diante de determinado tipo de alerta ou incidente.

  Regra de correlação
Lógica utilizada por uma ferramenta para relacionar múltiplos eventos e identificar um possível comportamento suspeito.

  Retenção de logs
Período e condições definidos para o armazenamento dos registros gerados pelos sistemas.

  Severidade
Classificação do impacto potencial ou confirmado de uma ameaça ou incidente.

  SIEM
Solução que centraliza, normaliza, pesquisa, correlaciona e analisa eventos de segurança, podendo gerar alertas.

  SLA
Acordo de nível de serviço que define prazos, responsabilidades e padrões esperados para o atendimento de alertas, chamados ou incidentes.

  SOC
Centro de Operações de Segurança responsável pelo monitoramento, detecção, investigação e resposta a ameaças.

 SOC N1
Primeiro nível operacional do SOC. Realiza monitoramento, triagem inicial, coleta de evidências, classificação, documentação e escalonamento.

  SOC N2
Nível responsável por investigações mais aprofundadas, análise técnica avançada e apoio à resposta a incidentes.

  SOAR
Tecnologia utilizada para integrar ferramentas, automatizar tarefas e orquestrar processos de investigação e resposta.

  Tática
No MITRE ATT&CK, representa o objetivo que o atacante deseja alcançar em determinada etapa do ataque.

  Técnica
No MITRE ATT&CK, representa a maneira utilizada pelo atacante para alcançar um objetivo.

  Threat Intelligence
Informações analisadas sobre ameaças, atacantes, vulnerabilidades, campanhas, técnicas e indicadores de comprometimento.

  Triagem
Processo inicial de análise de um alerta para determinar sua validade, contexto, impacto, severidade e necessidade de escalonamento.

  Verdadeiro positivo
Alerta cuja investigação confirma a existência de atividade maliciosa ou violação de segurança.

## Prompts reutilizáveis para futuras revisões

  Prompt 1 - Revisão geral do conteúdo
Explique os principais conceitos de Security Operations, incluindo logs, SIEM, SOAR, eventos, alertas, incidentes, Threat Intelligence e resposta a incidentes. Utilize linguagem acessível para um estudante iniciante em Segurança da Informação e apresente exemplos práticos.

  Prompt 2 - Evento, alerta e incidente
Explique a diferença entre evento, alerta e incidente de segurança. Crie cinco cenários práticos e, em cada cenário, identifique quais elementos são eventos, qual situação gerou o alerta e em que momento o caso pode ser classificado como incidente.

  Prompt 5 - Exercício de classificação
Crie dez situações relacionadas a operações de segurança. Minha tarefa será classificá-las como:
evento normal;
evento suspeito;
alerta;
falso positivo;
verdadeiro positivo;
incidente.

Não mostre as respostas imediatamente. Depois que eu responder, corrija cada item e explique o raciocínio.

## Autor

**Allan Moraes**

Graduando em Defesa Cibernética e certificado ISC2 CC, em desenvolvimento profissional para atuação em Segurança da Informação, SOC e Cybersecurity.
