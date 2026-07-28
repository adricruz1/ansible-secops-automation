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
