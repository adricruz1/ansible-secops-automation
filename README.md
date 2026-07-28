# 🚀 Ansible SecOps Automation

Automação de processos de Segurança da Informação, Infraestrutura e Resposta a Incidentes utilizando **Ansible**, **Semaphore**, **PowerShell** e **Grafana**.

---

# 🎯 Problema

Em ambientes corporativos, atividades como auditoria de servidores, verificação de antivírus, instalação de agentes de monitoramento e resposta a incidentes costumam ser repetitivas e suscetíveis a erros manuais.

Além disso, a execução dessas tarefas de forma manual aumenta o tempo de resposta da equipe de infraestrutura e segurança.

Este projeto foi desenvolvido para automatizar essas atividades através da integração entre Ansible, Semaphore, PowerShell e Grafana.

---

# 💡 Solução

A solução centraliza a execução de playbooks de automação e monitoramento, permitindo padronizar processos operacionais e reduzir atividades manuais.

Entre as funcionalidades implementadas estão:

- Auditoria automática de patches Windows;
- Instalação automatizada de agentes de monitoramento;
- Correção de agentes indisponíveis;
- Verificação de conformidade do antivírus;
- Integração com API REST utilizando PowerShell;
- Dashboards operacionais no Grafana.

---

# 🏗️ Arquitetura

A solução foi construída utilizando os seguintes componentes:

- **Ansible** – Automação e execução de playbooks.
- **Ansible Semaphore** – Orquestração dos playbooks via interface web e API.
- **PowerShell** – Integração com APIs REST e automação em ambientes Windows.
- **Grafana** – Visualização de métricas e dashboards operacionais (NOC).

---

# 📂 Estrutura do Projeto

```text
.
├── ansible/
│   └── playbooks/
│       ├── auditar_windows.yml
│       ├── corrigir_monitoramento.yml
│       ├── instalar_monitoramento.yml
│       └── verificar_antivirus.yml
├── grafana/
│   └── dashboards/
│       └── windows_noc.json
└── scripts/
    └── api_trigger.ps1
```
# ⚙️ Playbooks

## auditar_windows.yml

Realiza auditoria de atualizações pendentes em servidores Windows.

---

## instalar_monitoramento.yml

Automatiza a instalação de agentes de monitoramento em novos servidores.

---

## corrigir_monitoramento.yml

Executa ações de remediação para restaurar agentes indisponíveis.

---

## verificar_antivirus.yml

Verifica a conformidade e o status operacional do antivírus.

# 📈 Benefícios

- Redução de tarefas manuais.
- Padronização de processos operacionais.
- Melhoria na resposta a incidentes.
- Automação de auditorias.
- Facilidade para expansão da solução.

## 🔒 Observação

Este repositório representa uma versão demonstrativa do projeto, desenvolvida para fins de estudo e portfólio.

Nenhuma informação confidencial, credencial ou configuração interna da empresa foi incluída.

Usuário
    │
    ▼
PowerShell
    │
    ▼
Semaphore
    │
    ▼
Ansible
    │
    ├────────► Windows Server
    │
    └────────► Agentes de Monitoramento
                     │
                     ▼
                 Grafana
