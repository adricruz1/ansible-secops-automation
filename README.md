# 🚀 Ansible SecOps & Self-Healing Automation
![Ansible](https://img.shields.io/badge/Ansible-Automation-red)
![PowerShell](https://img.shields.io/badge/PowerShell-Windows-blue)
![Grafana](https://img.shields.io/badge/Grafana-Monitoring-orange)
![Windows](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-success)
![AIOps](https://img.shields.io/badge/Architecture-Self--Healing-brightgreen)

Automação de processos de Segurança da Informação, Infraestrutura, Resposta a Incidentes e **Auto-Remediação de Serviços (Self-Healing)** utilizando **Ansible**, **Semaphore**, **PowerShell** e **Grafana**.

---

# 🎯 Problema

Em ambientes corporativos, atividades como auditoria de servidores, verificação de antivírus, instalação de agentes de monitoramento e resposta a incidentes costumam ser repetitivas e suscetíveis a erros manuais.

Além disso, a indisponibilidade de serviços essenciais (como agentes de exportação de métricas) exige intervenção humana contínua, aumentando o **MTTR (Mean Time to Repair)** e sobrecarregando as equipes de infraestrutura e NOC.

---

# 💡 Solução

A solução centraliza a execução de playbooks de automação, padronizando processos operacionais e adicionando uma camada de **Auto-Remediação de Infraestrutura (AIOps)**.

Entre as funcionalidades implementadas estão:

- **Self-Healing / Auto-Remediação:** Detecção e reinicialização automática de serviços caídos via Webhook de maneira isolada;
- Auditoria automática de patches Windows;
- Instalação automatizada de agentes de monitoramento;
- Correção preventiva de agentes indisponíveis;
- Verificação de conformidade do antivírus;
- Integração com API REST utilizando PowerShell e Webhooks JSON;
- Dashboards operacionais no Grafana.

---

# 🏗️ Arquitetura

A solução foi construída utilizando os seguintes componentes:

- **Ansible** – Automação, sanitização de variáveis e execução das tarefas.
- **Ansible Semaphore** – Orquestração de tarefas, gestão de credenciais NTLM WinRM e consumo de Webhooks.
- **Grafana Alerting** – Monitoramento contínuo e gatilho de alertas em tempo real.
- **PowerShell** – Integração local em ambientes Windows e administração de serviços.

## 🔄 Fluxo de Auto-Remediação (Self-Healing)

```text
[ Windows Server ] ──(Queda do Serviço)──> [ Grafana Alerting ]
                                                    │
                                        (Custom Webhook JSON)
                                                    ▼
[ Ansible Playbook ] <──(Extrai Variable)─── [ Semaphore UI ]
        │
  (Sanitiza IP / Filtra Host)
        ▼
[ Serviço Restabelecido ] (Apenas no servidor afetado)
