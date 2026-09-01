# 🚀 Ansible SecOps & Self-Healing Automation
![Ansible](https://img.shields.io/badge/Ansible-Automation-red)
![PowerShell](https://img.shields.io/badge/PowerShell-Windows-blue)
![Grafana](https://img.shields.io/badge/Grafana-Monitoring-orange)
![Prometheus](https://img.shields.io/badge/Prometheus-Metrics-E6522C)
![Telegram](https://img.shields.io/badge/Telegram-Alerts-26A5E4)
![Windows](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-success)
![AIOps](https://img.shields.io/badge/Architecture-Self--Healing-brightgreen)

Automação de processos de Segurança da Informação, Auditoria de Privilégios, Resposta a Incidentes e **Auto-Remediação de Serviços (Self-Healing)** utilizando **Ansible**, **Semaphore**, **PowerShell**, **Prometheus** e **Grafana**.

---

## 🎯 Problema

Em ambientes corporativos, atividades como auditoria de privilégios em servidores, verificação de antivírus, instalação de agentes de monitoramento e resposta a incidentes costumam ser repetitivas e suscetíveis a erros manuais.

A elevação não autorizada de privilégios (como a adição furtiva de usuários ao grupo de administradores locais) é um dos principais vetores em ataques de movimentação lateral. Além disso, a indisponibilidade de serviços essenciais exige intervenção humana contínua, aumentando o **MTTR (Mean Time to Repair)** e sobrecarregando as equipes de Infraestrutura, SecOps e NOC.

---

## 💡 Solução

A solução centraliza a execução de playbooks de automação, padronizando processos operacionais, auditando alterações críticas de segurança e adicionando uma camada de **Auto-Remediação de Infraestrutura (AIOps)**.

Entre as funcionalidades implementadas estão:

- **🛡️ Auditoria e Monitoramento de Privilégios (NOVO):** Detecção passiva e instantânea de adição (Event ID 4732) e remoção (Event ID 4733) de usuários no grupo de Administradores Locais, com alertas enriquecidos no Telegram (Hostname, Usuário Afetado, Executor);
- **⚡ Self-Healing / Auto-Remediação:** Detecção e reinicialização automática de serviços caídos via Webhook de maneira isolada (AIOps);
- Auditoria automática de patches no Windows Server;
- Instalação e manutenção automatizada do `windows_exporter` via Ansible;
- Verificação de conformidade de Antivírus;
- Dashboards e Alertas operacionais no Grafana integrados ao Telegram.

---

## 🖼️ Demonstração em Produção

### 📱 Alertas no Telegram (Auditoria de Privilégios em Tempo Real)
> Notificações ricas e limpas enviadas diretamente ao time de SecOps sem ruídos de metadados.

![Telegram Alerts]([docs/images/telegram_alert.png](https://github.com/adricruz1/ansible-secops-automation/blob/main/docs/images/evidencia-Telegram.png))

---

## 🏗️ Arquitetura

A solução foi construída utilizando os seguintes componentes:

- **Ansible / Semaphore UI** – Automação de infraestrutura, gestão de credenciais NTLM WinRM, implantação de coletores e orquestração de Webhooks.
- **PowerShell (Textfile Collector)** – Parse passivo de logs de auditoria de segurança (Event IDs 4732 e 4733) gerando métricas Prometheus locais sem impacto ao SIEM.
- **Prometheus & windows_exporter** – Coleta contínua de métricas do sistema operacional e métricas customizadas `.prom`.
- **Grafana Alerting & Telegram** – Motor de regras, avaliação de séries temporais e envio de alertas formatados.

### 🔄 1. Fluxo de Auto-Remediação (Self-Healing)

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
