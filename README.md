# 🔐 Cybersecurity — Roadmap Técnico Completo
## Do Zero ao Nível Profissional · 10 Fases · ~12 Meses

> **Filosofia central:** Você não está aprendendo ferramentas. Você está construindo um modelo mental de como sistemas funcionam, como falham, e como são protegidos — para então escolher de que lado da linha você quer estar.

---

## 📋 Índice

| Fase | Tema | Duração Estimada |
|------|------|-----------------|
| [Fase 0](#fase-0--fundamentos-absolutos) | Fundamentos: Redes, Linux, Scripting | Semanas 1–3 |
| [Fase 1](#fase-1--segurança-de-redes) | Segurança de Redes | Semanas 4–6 |
| [Fase 2](#fase-2--web-security--appsec) | Web Security / AppSec | Semanas 7–12 |
| [Fase 3](#fase-3--pentesting-de-sistemas) | Pentesting Linux, Windows e AD | Semanas 13–18 |
| [Fase 4](#fase-4--exploitation-fundamentals) | Exploitation Fundamentals | Semanas 19–24 |
| [Fase 5](#fase-5--red-team-operations) | Red Team Operations | Semanas 25–30 |
| [Fase 6](#fase-6--blue-team--soc--siem) | Blue Team / SOC / SIEM | Semanas 31–36 |
| [Fase 7](#fase-7--dfir) | DFIR — Forense & Incident Response | Semanas 37–42 |
| [Fase 8](#fase-8--cloud-security) | Cloud Security | Semanas 43–48 |
| [Fase 9](#fase-9--certificações-e-carreira) | Certificações e Carreira | Semanas 49–52 |
| [Recursos](#recursos-consolidados) | Recursos Consolidados | — |

**Carga horária sugerida:** 2–4h/dia · 4 dias/semana · ~12 meses  
**Pré-requisitos:** Lógica de programação básica, interesse genuíno em como sistemas funcionam  
**Data de referência:** Novembro/2026

---

## Legenda

| Ícone | Significado |
|-------|------------|
| 🇧🇷 | Conteúdo disponível em Português Brasileiro |
| 📌 | Documentação oficial obrigatória |
| 🎥 | Vídeo ou playlist recomendada |
| 📚 | Livro ou texto longo |
| 🔧 | Ferramenta prática |
| 🔴 | Perspectiva ofensiva (Red Team) |
| 🔵 | Perspectiva defensiva / detecção (Blue Team) |
| ⚪ | Fundamento — vale para ambas as trilhas |
| ⚠️ | Cuidado: use apenas em ambiente autorizado ou VM isolada |
| ⭐⭐⭐ | Dificuldade do recurso |

---

## Fase 0 — Fundamentos Absolutos

> **Objetivo:** Falar a língua dos sistemas antes de atacar ou defender qualquer um deles. Redes, Linux e código são o vocabulário mínimo de todo profissional de segurança.

### Por que começar aqui?

```
Sem redes:    você não entende o que está escaneando ou bloqueando
Sem Linux:    você não consegue operar 90% das ferramentas de segurança
Sem código:   você não consegue automatizar nada, e automação é poder
```

### Mapa de Fundamentos

```
┌─────────────────────────────────────────────────────────────┐
│                    CAMADA DE FUNDAMENTOS                     │
│                                                             │
│  REDES                LINUX               PROGRAMAÇÃO       │
│  ─────                ─────               ───────────       │
│  Modelo OSI           CLI básico           Python básico     │
│  TCP/IP               Permissões           Scripts de rede   │
│  DNS, DHCP            Processos            Automação         │
│  HTTP/S               systemd/cron         Manipulação SQL   │
│  TLS 1.3              Logs (/var/log)      Noções de JS      │
│  Subnetting           Bash scripting       Requests/sockets  │
│                                                             │
│  VIRTUALIZAÇÃO                                              │
│  ──────────────                                             │
│  VirtualBox / VMware                                        │
│  Redes Host-Only                                            │
│  Snapshots                                                  │
└─────────────────────────────────────────────────────────────┘
```

### Setup do Laboratório

```
LAB/
├── VM1 — Kali Linux (atacante)
│   ├── Ferramentas de pentest pré-instaladas
│   └── Python 3, Burp Suite Community
│
├── VM2 — Ubuntu / Windows 10 (alvo)
│   ├── Sem antivírus para testes iniciais
│   └── Snapshot limpo salvo
│
└── VM3 — Alvo Web (opcional)
    └── OWASP Juice Shop ou DVWA via Docker
```

**Configuração de rede:**

```
┌─────────────────────────────────────┐
│  HOST (sua máquina física)          │
│                                     │
│  ┌──────────┐    ┌──────────────┐  │
│  │  Kali    │◄──►│  Alvo (VM)   │  │
│  └──────────┘    └──────────────┘  │
│         ↑ Host-Only Network ↑       │
│    (SEM acesso à internet real)     │
└─────────────────────────────────────┘
```

> ⚠️ **CRÍTICO:** Configure a rede como **Host-Only** antes de qualquer teste. Tire snapshots ANTES de qualquer experimento.

### Livros

| Título | Link | Gratuito? | Dificuldade |
|--------|------|-----------|------------|
| 📚 Computer Networks: A Systems Approach | https://book.systemsapproach.org/ | **Sim** | ⭐ |
| 📚 The Linux Command Line (William Shotts) | https://linuxcommand.org/tlcl.php | **Sim (PDF)** | ⭐ |
| 📚 Automate the Boring Stuff with Python | https://automatetheboringstuff.com/ | **Sim (online)** | ⭐ |
| 📚 Bash Guide for Beginners (TLDP) | https://tldp.org/LDP/Bash-Beginners-Guide/html/ | **Sim** | ⭐ |
| 📚 Python for Everybody (Severance) | https://www.py4e.com/book | **Sim** | ⭐ |

### Documentação Oficial — Leitura Obrigatória

| Recurso | Link | O que cobre |
|---------|------|------------|
| 📌 RFC 791 — IPv4 | https://www.rfc-editor.org/rfc/rfc791 | Endereçamento e roteamento |
| 📌 RFC 1034 — DNS | https://www.rfc-editor.org/rfc/rfc1034 | Conceitos DNS |
| 📌 RFC 9110 — HTTP Semantics | https://www.rfc-editor.org/rfc/rfc9110 | HTTP moderno |
| 📌 RFC 8446 — TLS 1.3 | https://www.rfc-editor.org/rfc/rfc8446 | Criptografia de transporte |
| 📌 Linux man-pages | https://man7.org/linux/man-pages/ | Processos, cron, permissões |
| 📌 Wireshark User's Guide | https://www.wireshark.org/docs/wsug_html_chunked/ | Interface e filtros |

### 🎥 Vídeos — PT-BR

| Canal / Conteúdo | Link | Dificuldade |
|-----------------|------|------------|
| 🇧🇷 Curso em Vídeo — Redes de Computadores (playlist) | https://www.youtube.com/playlist?list=PLHz_AreHm4dkd4lr9G0Up-W-YaHYdTDuP | ⭐ |
| 🇧🇷 Curso em Vídeo — Python (playlist completa) | https://www.youtube.com/playlist?list=PLHz_AreHm4dlKP6QQCekuIPky1CiwmdI6 | ⭐ |
| 🇧🇷 Bóson Treinamentos — Linux/Ubuntu | https://www.youtube.com/@bosontreinamentos | ⭐ |
| 🇧🇷 LINUXtips — Linux Essentials | https://linuxtips.io/conteudo-gratuito/ | ⭐ |

### 🎥 Vídeos — Inglês

| Canal / Conteúdo | Link | Dificuldade |
|-----------------|------|------------|
| Professor Messer — Network+ N10-009 (playlist) | https://www.youtube.com/watch?v=k7IOn3TiUc8&list=PLG49S3nxzAnl_tQe3kvnmeMid0mjF8Le8 | ⭐ |
| freeCodeCamp — Python full course | https://www.youtube.com/watch?v=rfscVS0vtbw | ⭐ |
| NetworkChuck — Linux tutorials | https://www.youtube.com/@NetworkChuck/videos | ⭐ |
| Low Level Learning — C, ponteiros, memória | https://www.youtube.com/@LowLevelLearning | ⭐⭐ |

### Cursos Gratuitos

| Plataforma | Curso | Link | Horas est. |
|-----------|-------|------|-----------|
| Cisco NetAcad | Networking Essentials | https://www.netacad.com/ | 30–70h |
| TryHackMe | Networking Module | https://tryhackme.com/module/networking | 10–20h |
| TCM Academy | Free Tier (Linux 100, Prog 100) | https://tcm-sec.com/academy/tcm-academy-free-tier/ | 40h+ |
| LINUXtips | Linux Essentials | https://linuxtips.io/conteudo-gratuito/ | 11h+ |
| py4e | Python for Everybody | https://www.py4e.com/lessons | 30–50h |

### 🔧 Ferramentas Essenciais

| Ferramenta | Link | Para quê |
|-----------|------|---------|
| VirtualBox | https://www.virtualbox.org/wiki/Downloads | VMs e redes isoladas |
| Kali Linux | https://www.kali.org/get-kali/ | Distribuição de lab ofensivo |
| Ubuntu Desktop | https://ubuntu.com/download/desktop | VM Linux alvo/dev |
| Wireshark | https://www.wireshark.org/download.html | Captura e análise de pacotes |
| Python 3 | https://www.python.org/downloads/ | Automação e scripting |
| VS Code | https://code.visualstudio.com/download | Editor de código |

### Script de Exercício — Fundamentos Python + Redes

```python
# network_basics.py — Exercício de fundamentos
# Execute em VM isolada

import socket
import subprocess
import sys

def dns_lookup(domain):
    """Resolve DNS de um domínio"""
    try:
        ip = socket.gethostbyname(domain)
        print(f"[DNS] {domain} → {ip}")
        return ip
    except socket.gaierror as e:
        print(f"[ERRO] DNS falhou: {e}")
        return None

def port_check(host, port):
    """Verifica se uma porta está aberta"""
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.settimeout(1)
    result = sock.connect_ex((host, port))
    sock.close()
    
    status = "ABERTA" if result == 0 else "fechada"
    print(f"[PORT] {host}:{port} → {status}")
    return result == 0

def scan_common_ports(host):
    """Varre portas comuns (versão didática — use Nmap no lab real)"""
    common_ports = {
        21: "FTP", 22: "SSH", 23: "Telnet",
        25: "SMTP", 53: "DNS", 80: "HTTP",
        443: "HTTPS", 3306: "MySQL", 3389: "RDP"
    }
    
    print(f"\n[*] Escaneando {host}...")
    for port, service in common_ports.items():
        if port_check(host, port):
            print(f"    → {service} (:{port}) detectado")

if __name__ == "__main__":
    # Exercício: use somente em redes que você controla
    target = "scanme.nmap.org"  # alvo autorizado pelo Nmap
    dns_lookup(target)
    scan_common_ports(target)
```

> 🔵 **Perspectiva defensiva:** Execute isso contra sua própria VM e observe nos logs (`/var/log/auth.log`, `ufw.log`) o que fica registrado. Essa é a base da telemetria defensiva.

### Labs Práticos

| Plataforma | Lab | Link | Dificuldade |
|-----------|-----|------|------------|
| OverTheWire | Bandit (Linux terminal) | https://overthewire.org/wargames/bandit/ | ⭐ |
| TryHackMe | Cyber Security 101 path | https://tryhackme.com/path/outline/cybersecurity101 | ⭐ |
| TryHackMe | Wireshark: The Basics | https://tryhackme.com/room/wiresharkthebasics | ⭐ |
| picoCTF | General Skills | https://play.picoctf.org/practice | ⭐ |
| Wireshark | Sample Captures | https://wiki.wireshark.org/SampleCaptures | ⭐ |

### Checklist — Fase 0

- [ ] Configurei VM Dev + VM Alvo com rede Host-Only
- [ ] Consigo navegar no terminal Linux sem GUI
- [ ] Entendo o modelo OSI e onde cada protocolo vive
- [ ] Consigo capturar e filtrar tráfego HTTP/DNS no Wireshark
- [ ] Escrevi 3 scripts Python (automação, sockets, manipulação de texto)
- [ ] Consigo gerenciar serviços com systemd e agendar tarefas com cron
- [ ] Concluí o wargame Bandit (OverTheWire) até level 20

---

## Fase 1 — Segurança de Redes

> **Objetivo:** Entender como tráfego de rede pode ser mapeado, interceptado e manipulado — e como detectar e bloquear essas ações. Nmap é a pedra fundamental de qualquer pentest ou inventário defensivo.

### O que acontece quando você "escaneia" uma rede?

```
ATACANTE / AUDITOR           REDE                ALVO
     │                         │                   │
     │  SYN → porta 80         │                   │
     ├────────────────────────►│──────────────────►│
     │                         │                   │
     │◄────────────────────────│◄──────────────────┤  SYN-ACK (porta aberta)
     │                         │             ou    │
     │◄────────────────────────│◄──────────────────┤  RST (porta fechada)
     │                         │                   │
     │  RST (fecha handshake)  │                   │
     ├────────────────────────►│──────────────────►│

🔵 IDS/IPS observa o volume de SYNs simultâneos → alerta de port scan
```

### Protocolos para Dominar

| Protocolo | Camada OSI | O que aprender | Ferramenta |
|-----------|-----------|---------------|-----------|
| ARP | 2 | Resolução MAC, ARP spoofing | Wireshark, arpspoof |
| DNS | 7 (app) | Consultas, DNS poisoning, exfiltração via DNS | dig, Wireshark |
| TCP/UDP | 4 | Handshake, estados de porta, scanners | Nmap, tcpdump |
| HTTP/HTTPS | 7 | Headers, métodos, proxying, inspeção TLS | Burp, mitmproxy |
| SMB | 7 | Compartilhamento Windows, ataques relay | smbclient, Wireshark |

### Documentação Oficial

| Recurso | Link |
|---------|------|
| 📌 Nmap Reference Guide | https://nmap.org/book/man.html |
| 📌 Wireshark User Guide | https://www.wireshark.org/docs/wsug_html_chunked/ |
| 📌 tcpdump manual | https://www.tcpdump.org/manpages/tcpdump.1.html |
| 📌 Suricata documentation | https://docs.suricata.io/ |
| 📌 RFC 826 — ARP | https://www.rfc-editor.org/rfc/rfc826 |

### Livros

| Título | Link | Gratuito? | Dificuldade |
|--------|------|-----------|------------|
| 📚 Nmap Network Scanning (G. Lyon) | https://nmap.org/book/ | **Sim (online)** | ⭐⭐ |
| 📚 Beej's Guide to Network Programming | https://beej.us/guide/bgnet/ | **Sim** | ⭐⭐ |
| 📚 Suricata User Guide | https://docs.suricata.io/ | **Sim** | ⭐⭐ |

### 🎥 Vídeos — PT-BR

| Canal / Conteúdo | Link |
|-----------------|------|
| 🇧🇷 Curso em Vídeo — Redes (playlist completa) | https://www.youtube.com/playlist?list=PLHz_AreHm4dkd4lr9G0Up-W-YaHYdTDuP |
| 🇧🇷 Solyd — Introdução ao Hacking e Pentest | https://www.youtube.com/watch?v=OP48PsGX3NI |
| 🇧🇷 CS Academy — LAB SOC open source (playlist) | https://www.youtube.com/playlist?list=PLALjBisXuYJdavQDEeB0JcgqSRKSDhGPu |

### 🎥 Vídeos — Inglês

| Canal / Conteúdo | Link |
|-----------------|------|
| Professor Messer — Network+ N10-009 | https://www.youtube.com/watch?v=k7IOn3TiUc8&list=PLG49S3nxzAnl_tQe3kvnmeMid0mjF8Le8 |
| IppSec — HTB walkthroughs (enumeração) | https://www.youtube.com/playlist?list=PLidcsTyj9JXItWpbRtTg6aDEj10_F17x5 |
| Security Onion — canal oficial | https://www.youtube.com/@SecurityOnionSolutions/videos |

### 🔧 Ferramentas

| Ferramenta | Link | Para quê |
|-----------|------|---------|
| Nmap | https://nmap.org/download.html | Descoberta e auditoria de portas |
| Netcat / Ncat | https://nmap.org/ncat/ | Sockets, banner grabbing, tunnels |
| tcpdump | https://www.tcpdump.org/ | Captura de pacotes via CLI |
| Wireshark | https://www.wireshark.org/download.html | Análise visual de PCAP |
| Suricata | https://suricata.io/download/ | IDS/IPS baseado em assinaturas |
| Zeek | https://zeek.org/get-zeek/ | Logs de protocolo de rede |

### Cheat Sheet — Nmap Essencial

```bash
# Descoberta de hosts na rede
nmap -sn 192.168.1.0/24

# Scan de portas TCP comuns (top 1000)
nmap -sC -sV 192.168.1.10

# Scan completo com scripts de detecção
nmap -sC -sV -p- --open 192.168.1.10

# Scan UDP (mais lento)
nmap -sU --top-ports 100 192.168.1.10

# Output para arquivo (grepable + XML)
nmap -sC -sV -oA saida_scan 192.168.1.10

# Detecção de OS
nmap -O 192.168.1.10

# 🔵 DETECÇÃO: um scan intenso gera centenas de SYNs em segundos
# Suricata / Snort alertam por regra: "threshold: type threshold, track by_src"
```

### Labs Práticos

| Plataforma | Lab | Link | Dificuldade |
|-----------|-----|------|------------|
| TryHackMe | Wireshark: Traffic Analysis | https://tryhackme.com/room/wiresharktrafficanalysis | ⭐⭐ |
| TryHackMe | Tcpdump: Basics | https://tryhackme.com/room/tcpdump | ⭐ |
| TryHackMe | Nmap room | https://tryhackme.com/room/furthernmap | ⭐ |
| Wireshark | Sample Captures (PCAPs prontos) | https://wiki.wireshark.org/SampleCaptures | ⭐⭐ |
| Hack The Box | Starting Point — máquinas Linux | https://app.hackthebox.com/starting-point | ⭐⭐ |

### Checklist — Fase 1

- [ ] Consigo fazer um scan Nmap completo e interpretar o resultado
- [ ] Capturei e analisei um PCAP com DNS, HTTP e TLS no Wireshark
- [ ] Entendo o que é ARP spoofing e como detectar com Wireshark
- [ ] Configurei uma regra básica no Suricata para alertar port scan
- [ ] Sei a diferença entre IDS e IPS, e onde cada um se posiciona na rede
- [ ] Consigo usar tcpdump para capturar tráfego de uma porta específica

---

## Fase 2 — Web Security / AppSec

> **Objetivo:** A web é a superfície de ataque mais explorada do mundo. Dominar as vulnerabilidades do OWASP Top 10 — ofensivamente e defensivamente — é requisito para qualquer trilha em segurança.

### Como um ataque web funciona?

```
NAVEGADOR / ATACANTE                     SERVIDOR WEB
     │                                        │
     │  GET /produto?id=1 OR 1=1--            │
     ├───────────────────────────────────────►│
     │                       SELECT * FROM produtos
     │                       WHERE id=1 OR 1=1--
     │                       → retorna TODOS os produtos
     │◄───────────────────────────────────────┤
     │  HTTP 200 + dados sensíveis            │
     
🔴 ATACANTE vê dados que não deveria
🔵 WAF / input sanitization teria bloqueado antes do SELECT
```

### OWASP Top 10 — 2025 (Visão Geral)

| # | Vulnerabilidade | Impacto | Exemplo |
|---|----------------|---------|---------|
| A01 | Broken Access Control | Acesso a dados de outros usuários | IDOR, path traversal |
| A02 | Cryptographic Failures | Exposição de dados sensíveis | HTTPS não forçado, senhas em MD5 |
| A03 | Injection | Execução de código não intencional | SQLi, XSS, OS command injection |
| A04 | Insecure Design | Falhas arquiteturais | Lógica de negócio que permite fraude |
| A05 | Security Misconfiguration | Acesso a configs padrão | Admin:admin, listagem de diretório |
| A06 | Vulnerable Components | Exploração de dependências | Log4Shell, dependências desatualizadas |
| A07 | Auth Failures | Roubo de conta | Brute force sem rate limit, MFA ausente |
| A08 | Software Integrity Failures | Supply chain | Update sem verificação de assinatura |
| A09 | Logging Failures | Sem visibilidade do ataque | Sem logs de autenticação |
| A10 | SSRF | Acesso à infra interna | Buscar `http://169.254.169.254` |

### Documentação Oficial

| Recurso | Link | Prioridade |
|---------|------|-----------|
| 📌 OWASP Top 10:2025 (PT-BR) | https://top10.owasp.org/2025/pt-BR/ | **OBRIGATÓRIO** |
| 📌 OWASP API Security Top 10:2023 | https://api-security.owasp.org/editions/2023/en/0x00-header/ | ⭐⭐ |
| 📌 OWASP Cheat Sheet Series | https://cheatsheetseries.owasp.org/ | **OBRIGATÓRIO** |
| 📌 PortSwigger — All Topics | https://portswigger.net/web-security/all-topics | **OBRIGATÓRIO** |
| 📌 PortSwigger — All Labs | https://portswigger.net/web-security/all-labs | **OBRIGATÓRIO** |

### Livros

| Título | Link | Gratuito? | Dificuldade |
|--------|------|-----------|------------|
| 📚 OWASP Web Security Testing Guide (WSTG) | https://owasp.org/www-project-web-security-testing-guide/ | **Sim** | ⭐⭐ |
| 📚 OWASP Application Security Verification Standard | https://owasp.org/www-project-application-security-verification-standard/ | **Sim** | ⭐⭐ |
| 📚 Hacking APIs — Corey Ball | https://nostarch.com/hacking-apis | Comercial | ⭐⭐ |
| 📚 The Web Application Hacker's Handbook | Biblioteca/Editora | Comercial | ⭐⭐ |

### 🎥 Vídeos — PT-BR

| Canal / Conteúdo | Link |
|-----------------|------|
| 🇧🇷 Solyd — Introdução ao Hacking e Pentest 2.0 | https://www.youtube.com/watch?v=OP48PsGX3NI |
| 🇧🇷 Ricardo Longatto — Curso de Pentest | https://www.youtube.com/watch?v=3eJ79nmBs_A |
| 🇧🇷 Curso em Vídeo — Python (automação de testes) | https://www.youtube.com/playlist?list=PLHz_AreHm4dlKP6QQCekuIPky1CiwmdI6 |

### 🎥 Vídeos — Inglês

| Canal / Conteúdo | Link |
|-----------------|------|
| PortSwigger — Web Security Academy (vídeos de apoio) | https://portswigger.net/web-security/video-guidelines |
| IppSec — HTB web walkthroughs | https://www.youtube.com/playlist?list=PLidcsTyj9JXItWpbRtTg6aDEj10_F17x5 |
| LiveOverflow — Web Exploits | https://www.youtube.com/@LiveOverflow/playlists |
| TCM Security — Free Ethical Hacking | https://tcm-sec-academy.teachable.com/p/learn-penetration-testing-free |

**Busque no YouTube:**
- `"SQL Injection explained PortSwigger"`
- `"XSS tutorial Burp Suite"`
- `"SSRF attack explained"`
- `"OWASP Top 10 2025 walkthrough"`

### Cursos Gratuitos

| Plataforma | Curso | Link | Horas est. |
|-----------|-------|------|-----------|
| PortSwigger | Web Security Academy (TODOS os labs) | https://portswigger.net/web-security/all-labs | 80–150h |
| PortSwigger | SQL Injection learning path | https://portswigger.net/web-security/learning-paths/sql-injection | 8–15h |
| OWASP | Juice Shop (companion) | https://owasp.org/www-project-juice-shop/ | 12–25h |
| Google | Gruyere (XSS e autorização) | https://google-gruyere.appspot.com/ | 4–8h |
| TCM | Free Pentesting Resources | https://tcm-sec-academy.teachable.com/p/learn-penetration-testing-free | ~12h |

### 🔧 Ferramentas

| Ferramenta | Link | Para quê |
|-----------|------|---------|
| Burp Suite Community | https://portswigger.net/burp/communitydownload | Proxy HTTP, scanner manual |
| OWASP ZAP | https://www.zaproxy.org/download/ | DAST automatizado |
| OWASP Juice Shop | https://github.com/juice-shop/juice-shop | App vulnerável para treinar |
| DVWA | https://github.com/digininja/DVWA | Labs de vulnerabilidades clássicos |
| mitmproxy | https://mitmproxy.org/ | Proxy HTTP/S via CLI |
| Postman | https://www.postman.com/downloads/ | Testes de APIs REST |

### Matriz de Estudo — Vulnerabilidades Web

```
INICIANTE → INTERMEDIÁRIO → AVANÇADO

SQLi básico → SQLi blind → SQLi time-based → SQLi out-of-band
XSS reflected → XSS stored → XSS DOM → XSS via CSP bypass
CSRF básico → CSRF via JSON → CSRF com SameSite bypass
IDOR simples → IDOR em GUID → IDOR via mass assignment
SSRF básico → SSRF para metadata → SSRF blind

Para CADA vulnerabilidade documente:
  1. Causa raiz (por que existe?)
  2. Payload de exploit
  3. Mitigação correta
  4. Como detectar nos logs
```

### Labs Práticos

| Plataforma | Lab | Link | Dificuldade |
|-----------|-----|------|------------|
| PortSwigger | SQL Injection | https://portswigger.net/web-security/sql-injection | ⭐⭐ |
| PortSwigger | XSS | https://portswigger.net/web-security/cross-site-scripting | ⭐⭐ |
| PortSwigger | SSRF | https://portswigger.net/web-security/ssrf | ⭐⭐ |
| PortSwigger | API testing | https://portswigger.net/web-security/api-testing | ⭐⭐ |
| PortSwigger | ALL labs | https://portswigger.net/web-security/all-labs | ⭐–⭐⭐⭐ |

### Checklist — Fase 2

- [ ] Li o OWASP Top 10:2025 completo (PT-BR)
- [ ] Configurei Burp Suite com certificado no navegador
- [ ] Completei 20+ labs do PortSwigger Web Security Academy
- [ ] Explorei OWASP Juice Shop resolvendo 10+ desafios
- [ ] Para cada vuln que explorei, documentei a mitigação
- [ ] Sei a diferença entre autenticação e autorização
- [ ] Sei testar uma API REST buscando BOLA/BOPLA (OWASP API Top 10)

---

## Fase 3 — Pentesting de Sistemas

> **Objetivo:** Sair de um foothold (acesso inicial) e escalar privilégios em Linux, Windows e Active Directory. Esta fase é o coração do pentest corporativo.

### Metodologia de Pentest

```
┌─────────────────────────────────────────────────────────┐
│               FASES DO PENTEST (PTES)                   │
│                                                         │
│  1. PRÉ-ENGAJAMENTO    → ROE, escopo, NDA, cronograma   │
│  2. RECON              → OSINT, DNS, ASN, LinkedIn      │
│  3. MODELAGEM          → ameaças, superfície de ataque  │
│  4. EXPLORAÇÃO         → vulnerabilidades confirmadas   │
│  5. PÓS-EXPLORAÇÃO     → privesc, persistência, pivot   │
│  6. RELATÓRIO          → evidências, impacto, remediação│
└─────────────────────────────────────────────────────────┘
```

### Active Directory — Mapa de Ataques

```
┌──────────────────────────────────────────────────────────┐
│                   ACTIVE DIRECTORY                       │
│                                                          │
│  Domain Controller (DC)                                  │
│       ↑                                                  │
│  Kerberos KDC                                            │
│       ↑                                                  │
│  ┌────────────────────────────────────┐                  │
│  │          ATAQUES COMUNS           │                   │
│  │                                    │                  │
│  │  Kerberoasting   → TGS de SPN     │  🔵 SPNs expostos │
│  │  AS-REP Roasting → sem pré-auth   │  🔵 preauthNotReq │
│  │  Pass-the-Hash   → NTLM hash      │  🔵 Restrict NTLM │
│  │  Pass-the-Ticket → TGT/TGS        │  🔵 Proteg. cred  │
│  │  DCSync          → mimika.lsadump │  🔵 DS-Replic ACL │
│  │  Golden Ticket   → krbtgt hash    │  🔵 Reset krbtgt  │
│  │  BloodHound path → ACL abuse      │  🔵 Revisar ACLs  │
│  └────────────────────────────────────┘                  │
└──────────────────────────────────────────────────────────┘
```

### Documentação Oficial

| Recurso | Link |
|---------|------|
| 📌 PTES — Penetration Testing Execution Standard | http://www.pentest-standard.org/index.php/Main_Page |
| 📌 Microsoft — Active Directory Domain Services | https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/ |
| 📌 Metasploit Documentation | https://docs.metasploit.com/ |
| 📌 MITRE ATT&CK — Enterprise | https://attack.mitre.org/matrices/enterprise/ |
| 📌 HackTricks (referência viva) | https://book.hacktricks.wiki/ |

### Livros

| Título | Link | Gratuito? | Dificuldade |
|--------|------|-----------|------------|
| 📚 Metasploit Unleashed (OffSec) | https://www.offsec.com/metasploit-unleashed/ | **Sim** | ⭐⭐ |
| 📚 HackTricks — Linux/Windows/AD | https://book.hacktricks.wiki/ | **Sim** | ⭐⭐ |
| 📚 Penetration Testing — G. Weidman | https://nostarch.com/pentesting | Comercial | ⭐⭐ |
| 📚 NIST SP 800-115 | https://csrc.nist.gov/pubs/sp/800/115/final | **Sim** | ⭐⭐ |

### 🎥 Vídeos — PT-BR

| Canal / Conteúdo | Link |
|-----------------|------|
| 🇧🇷 Ricardo Longatto — Curso de Pentest | https://www.youtube.com/watch?v=3eJ79nmBs_A |
| 🇧🇷 Solyd — Hacking e Pentest | https://www.youtube.com/watch?v=OP48PsGX3NI |
| 🇧🇷 Mente Binária — CEB (exploração de binários) | https://mentebinaria.org.br/aprender/curso-de-exploracao-de-binarios-ceb/ |

### 🎥 Vídeos — Inglês

| Canal / Conteúdo | Link |
|-----------------|------|
| IppSec — HTB walkthroughs (Windows/Linux/AD) | https://www.youtube.com/playlist?list=PLidcsTyj9JXItWpbRtTg6aDEj10_F17x5 |
| TCM Security — Free Ethical Hacking | https://tcm-sec-academy.teachable.com/p/learn-penetration-testing-free |
| John Hammond — HTB/THM walkthroughs | https://www.youtube.com/@_JohnHammond/videos |

### 🔧 Ferramentas

| Ferramenta | Link | Para quê |
|-----------|------|---------|
| Kali Linux | https://www.kali.org/get-kali/ | Distro com tudo pré-instalado |
| Metasploit | https://github.com/rapid7/metasploit-framework | Framework de exploit |
| Impacket | https://github.com/fortra/impacket | Protocolos Windows (SMB, Kerberos) |
| BloodHound CE | https://github.com/SpecterOps/BloodHound | Análise de relações AD |
| NetExec | https://github.com/Pennyw0rth/NetExec | Auditoria de redes Windows |
| linPEAS / winPEAS | https://github.com/peass-ng/PEASS-ng | Enumeração de privesc |
| GTFOBins | https://gtfobins.github.io/ | Abusos de config Linux |
| pspy | https://github.com/DominicBreuker/pspy | Monitorar processos sem root |
| enum4linux-ng | https://github.com/cddmp/enum4linux-ng | Enumeração SMB/Samba |

### Cheat Sheet — Linux Privilege Escalation

```bash
# 1. Quem sou eu e onde estou?
id && whoami && hostname && uname -a

# 2. Procurar SUIDs (executáveis com permissão de root)
find / -perm -4000 -type f 2>/dev/null
# → Consultar GTFOBins para cada binário encontrado

# 3. Verificar sudo sem senha
sudo -l

# 4. Cron jobs de root (procurar scripts editáveis)
cat /etc/crontab
ls -la /etc/cron.*

# 5. Senhas em arquivos de configuração
grep -r "password" /etc/ 2>/dev/null
grep -r "password" /var/www/ 2>/dev/null

# 6. Versão do kernel (buscar CVEs)
uname -r
# → searchsploit linux kernel <versão>

# 🔵 DETECÇÃO: linPEAS gera muito ruído em /var/log/auth.log
# Monitorar execução de comandos de enumeração via auditd
```

### Labs Práticos

| Plataforma | Lab | Link | Dificuldade |
|-----------|-----|------|------------|
| TryHackMe | Jr Penetration Tester path | https://tryhackme.com/path/outline/jrpenetrationtester | ⭐⭐ |
| TryHackMe | Blue (Windows vulnerável) | https://tryhackme.com/room/blue | ⭐ |
| Hack The Box | Starting Point | https://app.hackthebox.com/starting-point | ⭐⭐ |
| VulnHub | VMs gratuitas | https://www.vulnhub.com/ | ⭐⭐ |
| Hack The Box Academy | AD / Linux / Windows | https://academy.hackthebox.com/ | ⭐⭐ |

### Checklist — Fase 3

- [ ] Realizei um pentest completo em VM própria (reconhecimento → relatório)
- [ ] Explorei uma máquina Linux e escalei para root
- [ ] Explorei uma máquina Windows e escalei para SYSTEM
- [ ] Configurei um mini-AD e executei Kerberoasting no lab
- [ ] Usei BloodHound para mapear paths de escalada no AD
- [ ] Produzi um relatório de pentest com evidências e remediações
- [ ] Sei a diferença entre pentest e red team

---

## Fase 4 — Exploitation Fundamentals

> **Objetivo:** Entender como vulnerabilidades de memória são exploradas — stack overflow, controle de EIP/RIP, bypass de mitigações modernas. Isso cria o modelo mental necessário para analisar CVEs e escrever exploits simples.

### Mitigações Modernas e Como Contorná-las

```
MITIGAÇÃO           O QUE FAZ                   BYPASS CLÁSSICO
─────────           ─────────                   ───────────────
Stack Canary     → valor entre vars e ret addr   Leak do canary
NX (DEP)         → stack não executável          ROP (Return-Oriented Programming)
ASLR             → randomiza endereços de base   Leak de endereço / brute force 32-bit
PIE              → texto do binário randomizado  Combinado com ASLR leak
RELRO            → seções de relocação RO        Partial RELRO ainda vuln em GOT overwrite
```

### Documentação Oficial

| Recurso | Link |
|---------|------|
| 📌 GDB Manual | https://sourceware.org/gdb/current/onlinedocs/gdb.html |
| 📌 pwntools docs | https://docs.pwntools.com/en/stable/ |
| 📌 AFL++ docs | https://aflplus.plus/docs/ |
| 📌 CWE-120 — Buffer Overflow | https://cwe.mitre.org/data/definitions/120.html |
| 📌 Exploit-DB | https://www.exploit-db.com/ |

### Livros

| Título | Link | Gratuito? | Dificuldade |
|--------|------|-----------|------------|
| 📚 Modern Binary Exploitation (RPISEC) | https://github.com/RPISEC/MBE | **Sim (slides + labs)** | ⭐⭐⭐ |
| 📚 pwn.college — Binary Exploitation | https://pwn.college/ | **Sim** | ⭐⭐ |
| 📚 Exploit Education (material didático) | https://exploit.education/ | **Sim** | ⭐⭐ |
| 📚 Hacking: The Art of Exploitation | https://nostarch.com/hacking2.htm | Comercial | ⭐⭐⭐ |

### 🎥 Vídeos — PT-BR

| Canal / Conteúdo | Link |
|-----------------|------|
| 🇧🇷 Mente Binária — CEB (curso completo) | https://mentebinaria.org.br/aprender/curso-de-exploracao-de-binarios-ceb/ |
| 🇧🇷 Vinicius Vieira — Buffer Overflow playlist | https://www.youtube.com/watch?v=VX27nq6EcjI&list=PLcKsaFvYl4l87C8_HhxkcFaoNhzC9bRw6 |
| 🇧🇷 Ricardo Longatto — Buffer Overflow | https://www.youtube.com/watch?v=59_gjX2HxyA |

### 🎥 Vídeos — Inglês

| Canal / Conteúdo | Link |
|-----------------|------|
| LiveOverflow — Binary Exploitation (playlist) | https://www.youtube.com/@LiveOverflow/playlists |
| pwn.college — aulas + challenges | https://future.pwn.college/dojo/intro-to-cybersecurity/module/binary-exploitation |
| TCM Security — Buffer Overflow introdutório | https://tcm-sec-academy.teachable.com/p/learn-penetration-testing-free |

### 🔧 Ferramentas

| Ferramenta | Link | Para quê |
|-----------|------|---------|
| GDB | https://www.sourceware.org/gdb/download/ | Debugger principal |
| pwndbg | https://github.com/pwndbg/pwndbg | Extensão visual do GDB |
| pwntools | https://github.com/Gallopsled/pwntools | Scripting de exploits em Python |
| ROPgadget | https://github.com/JonathanSalwan/ROPgadget | Encontrar gadgets ROP |
| AFL++ | https://github.com/AFLplusplus/AFLplusplus | Fuzzing de binários |
| boofuzz | https://github.com/jtpereyda/boofuzz | Fuzzing de protocolos de rede |

### Exemplo — Stack Buffer Overflow x86 (conceito)

```python
# exploit_bof.py — Conceito didático
# Alvo: binário compilado sem proteções (para fins de estudo)
# Compilar alvo com: gcc -m32 -fno-stack-protector -z execstack -o vuln vuln.c

from pwn import *

# Conectar ao processo ou socket
p = process('./vuln')  # ou remote('127.0.0.1', 4444)

# 1. Encontrar offset até EIP
#    → gerar padrão: cyclic(200) no pwndbg
#    → ler EIP no crash: cyclic_find(0x61616166)
offset = 112  # exemplo

# 2. Endereço de JMP ESP ou função alvo
jmp_esp = p32(0x08048456)  # encontrado com ROPgadget

# 3. Shellcode (execve /bin/sh) ou ROP chain
shellcode = asm(shellcraft.i386.linux.sh())

# 4. Montar payload
payload = b"A" * offset + jmp_esp + b"\x90" * 16 + shellcode

p.sendline(payload)
p.interactive()

# 🔵 DEFESA: compilar com -fstack-protector, habilitar ASLR (/proc/sys/kernel/randomize_va_space = 2)
```

### Labs Práticos

| Plataforma | Lab | Link | Dificuldade |
|-----------|-----|------|------------|
| pwn.college | Binary Exploitation | https://future.pwn.college/dojo/intro-to-cybersecurity/module/binary-exploitation | ⭐⭐ |
| ROP Emporium | ROP challenges | https://ropemporium.com/ | ⭐⭐⭐ |
| Exploit Education | Phoenix (overflow Linux) | https://exploit.education/phoenix/ | ⭐⭐ |
| picoCTF | Binary Exploitation | https://play.picoctf.org/practice | ⭐⭐ |
| OverTheWire | Narnia | https://overthewire.org/wargames/narnia/ | ⭐⭐ |
| OpenSecurityTraining2 | Cursos x86/exploração | https://ost2.fyi/ | ⭐⭐⭐ |

### Checklist — Fase 4

- [ ] Entendo o que é a stack e como funciona o prólogo/epílogo de uma função
- [ ] Encontrei o offset do EIP em um binário vulnerável via cyclic pattern
- [ ] Escrevi um exploit de stack overflow x86 funcional no lab
- [ ] Entendo o que são NX, ASLR, Stack Canary e PIE
- [ ] Consigo identificar gadgets ROP com ROPgadget
- [ ] Analisei 2 CVEs públicos no Exploit-DB e entendi o vetor de ataque
- [ ] Li os primeiros 5 módulos do Modern Binary Exploitation (RPISEC)

---

## Fase 5 — Red Team Operations

> **Objetivo:** Emular adversários reais usando TTPs documentadas no MITRE ATT&CK. Red team não é pentest: é simular um APT para testar detecção, resposta e resiliência organizacional.

### Red Team vs Pentest

```
                PENTEST                        RED TEAM
                ───────                        ────────
Objetivo:  Encontrar vulns              Testar detecção e resposta
Escopo:    Amplo (toda a infra)         Estreito (objetivo específico)
Duração:   Dias / semanas               Semanas / meses
Visibilidade: Blue Team sabe           Blue Team NÃO sabe (geralmente)
TTPs:      Oportunísticas              Emulação de adversário real
Resultado: Lista de vulns + fixes      Relatório de lacunas de detecção
```

### Kill Chain e ATT&CK

```
LOCKHEED MARTIN KILL CHAIN         MITRE ATT&CK (simplificado)
─────────────────────────          ──────────────────────────
1. Reconhecimento                  TA0043 — Reconnaissance
2. Weaponization                   TA0001 — Initial Access
3. Delivery                        TA0002 — Execution
4. Exploitation                    TA0003 — Persistence
5. Installation                    TA0004 — Privilege Escalation
6. C2 (Command & Control)          TA0005 — Defense Evasion
7. Actions on Objectives           TA0006 — Credential Access
                                   TA0007 — Discovery
                                   TA0008 — Lateral Movement
                                   TA0009 — Collection
                                   TA0010 — Exfiltration
                                   TA0011 — Command and Control
```

### Documentação Oficial

| Recurso | Link |
|---------|------|
| 📌 MITRE ATT&CK — Enterprise | https://attack.mitre.org/matrices/enterprise/ |
| 📌 MITRE D3FEND | https://d3fend.mitre.org/ |
| 📌 LOLBAS Project | https://lolbas-project.github.io/ |
| 📌 NIST SP 800-115 | https://csrc.nist.gov/pubs/sp/800/115/final |
| 📌 Adversary Emulation Plans | https://github.com/center-for-threat-informed-defense/adversary_emulation_library |

### 🎥 Vídeos — PT-BR

| Canal / Conteúdo | Link |
|-----------------|------|
| 🇧🇷 CS Academy — SOC Open Source (logs de operação) | https://www.youtube.com/playlist?list=PLALjBisXuYJdavQDEeB0JcgqSRKSDhGPu |
| 🇧🇷 Solyd — Hacking e Pentest | https://www.youtube.com/watch?v=OP48PsGX3NI |

### 🎥 Vídeos — Inglês

| Canal / Conteúdo | Link |
|-----------------|------|
| IppSec — HTB walkthroughs (cadeia de ataques) | https://www.youtube.com/playlist?list=PLidcsTyj9JXItWpbRtTg6aDEj10_F17x5 |
| SANS DFIR — defesa contra operações | https://www.youtube.com/c/SANSDigitalForensics/videos |
| 13Cubed — Windows Forensics (artefatos Red deixa) | https://www.youtube.com/watch?v=VYROU-ZwZX8&list=PLlv3b9B16ZadqDQH0lTRO4kqn2P1g9Mve |

### 🔧 Ferramentas

| Ferramenta | Link | Para quê |
|-----------|------|---------|
| Atomic Red Team | https://github.com/redcanaryco/atomic-red-team | Emulação controlada por TTP |
| MITRE Caldera | https://github.com/mitre/caldera | Emulação automatizada |
| Sliver C2 | https://github.com/BishopFox/sliver | Framework C2 (lab isolado) |
| Gophish | https://getgophish.com/ | Simulação de phishing (autorizado) |
| BloodHound CE | https://github.com/SpecterOps/BloodHound | Paths de ataque em AD |
| LOLBAS | https://lolbas-project.github.io/ | Binários legítimos para LOLBin |

### Blogs de Referência

| Blog | Link | Conteúdo |
|------|------|---------|
| **SpecterOps Blog** | https://specterops.io/blog/ | Adversary emulation / AD |
| **Outflank Blog** | https://www.outflank.nl/blog/ | Red team tradecraft maduro |
| **MDSec Research** | https://www.mdsec.co.uk/knowledge-centre/ | EDR evasion |
| **Red Canary Blog** | https://redcanary.com/blog/ | Detecções e operações |
| **ired.team** | https://ired.team/ | TTPs com código — referência #1 |

### Checklist — Fase 5

- [ ] Entendo a diferença entre pentest e red team (escopo, objetivo, resultado)
- [ ] Sei criar um plano de emulação com base em um adversário do ATT&CK
- [ ] Executei testes com Atomic Red Team e verifiquei os logs gerados
- [ ] Configurei Sliver C2 em VM isolada e entendi a arquitetura de C2
- [ ] Para cada TTP executada, documentei o log de detecção e a mitigação
- [ ] Sei o que são LOLBins e por que dificultam a detecção
- [ ] ⚠️ Todo exercício realizado em rede própria ou ambiente explicitamente autorizado

---

## Fase 6 — Blue Team / SOC / SIEM

> **Objetivo:** Usar todo o conhecimento ofensivo para construir detecções que sobrevivem a bypasses. Um bom Blue Team sabe o que o Red Team vai fazer antes de ele fazer.

### Arquitetura de um SOC

```
┌─────────────────────────────────────────────────────────────┐
│                     SOC — CAMADAS                           │
│                                                             │
│  DADOS                PROCESSAMENTO          RESPOSTA       │
│  ─────                ─────────────          ────────       │
│  Sysmon          →   Elasticsearch   →    Regras Sigma     │
│  Windows Logs    →   Kibana/Splunk    →    Alertas         │
│  Zeek/Suricata   →   Wazuh/Sentinel   →    Triagem L1/L2   │
│  EDR Telemetria  →   Correlação       →    Containment     │
│  Firewall Logs   →   Timeline         →    Relatório       │
│                                                             │
│  ENRICHMENT: MISP (threat intel) + MITRE ATT&CK (contexto) │
└─────────────────────────────────────────────────────────────┘
```

### Sysmon — Event IDs Críticos

| Event ID | Evento | O que detecta |
|---------|--------|--------------|
| **1** | Process Create | Processos suspeitos, PPID incomum |
| **3** | Network Connection | Conexões de processos inesperados |
| **7** | Image Load | DLLs suspeitas carregadas |
| **8** | CreateRemoteThread | Injeção de código |
| **10** | Process Access | OpenProcess em processos críticos |
| **11** | File Create | Criação de arquivos suspeitos |
| **12/13** | Registry Event | Persistência via registro |
| **22** | DNS Query | Resolução DNS suspeita / C2 |
| **25** | Process Tampering | Process Hollow detectado |

### Documentação Oficial

| Recurso | Link |
|---------|------|
| 📌 Sysmon PT-BR | https://learn.microsoft.com/pt-br/sysinternals/downloads/sysmon |
| 📌 SigmaHQ Documentation | https://sigmahq.io/docs/ |
| 📌 YARA-X Docs | https://virustotal.github.io/yara-x/docs/ |
| 📌 MITRE ATT&CK | https://attack.mitre.org/ |
| 📌 Splunk Docs | https://docs.splunk.com/ |
| 📌 Microsoft Sentinel PT-BR | https://learn.microsoft.com/pt-br/azure/sentinel/ |

### Livros

| Título | Link | Gratuito? |
|--------|------|-----------|
| 📚 NIST SP 800-92 — Log Management | https://csrc.nist.gov/pubs/sp/800/92/final | **Sim** |
| 📚 NIST SP 800-61 Rev3 — Incident Response | https://csrc.nist.gov/pubs/sp/800/61/r3/final | **Sim** |
| 📚 Sigma Rule Creation Guide | https://sigmahq.io/docs/guide/about.html | **Sim** |

### 🎥 Vídeos — PT-BR

| Canal / Conteúdo | Link |
|-----------------|------|
| 🇧🇷 CS Academy — LAB SOC Open Source (playlist) | https://www.youtube.com/playlist?list=PLALjBisXuYJdavQDEeB0JcgqSRKSDhGPu |
| 🇧🇷 CS Academy — Wazuh (playlist) | https://www.youtube.com/playlist?list=PLALjBisXuYJc15J1wWbxXwBLZcCSCjmUJ |
| 🇧🇷 CS Academy — MISP Threat Sharing | https://www.youtube.com/playlist?list=PLALjBisXuYJc6AaFy4bYje_UTlAhtVfOH |
| 🇧🇷 Mente Binária — AMO (YARA e malware) | https://mentebinaria.org.br/aprender/analise-de-malware-online-amo/ |

### 🎥 Vídeos — Inglês

| Canal / Conteúdo | Link |
|-----------------|------|
| TCM — Security Operations SOC 101 | https://certifications.tcm-sec.com/free-resources |
| 13Cubed — Intro to Windows Forensics | https://www.youtube.com/watch?v=VYROU-ZwZX8&list=PLlv3b9B16ZadqDQH0lTRO4kqn2P1g9Mve |
| SANS DFIR — incident handling | https://www.youtube.com/c/SANSDigitalForensics/videos |

### Cursos Gratuitos

| Plataforma | Curso | Link | Horas est. |
|-----------|-------|------|-----------|
| TryHackMe | SOC Level 1 path | https://tryhackme.com/path/outline/soclevel1 | 50–90h |
| Splunk | Free Training | https://www.splunk.com/en_us/training/free-courses/overview.html | 10–30h |
| Elastic | Free On-demand | https://www.elastic.co/pt/training/ | 10–20h |
| Microsoft Learn | Sentinel (PT-BR) | https://learn.microsoft.com/pt-br/training/browse/?products=azure-sentinel | 12–30h |
| Blue Team Labs Online | Catálogo free | https://blueteamlabs.online/ | 20–60h |

### 🔧 Ferramentas

| Ferramenta | Link | Para quê |
|-----------|------|---------|
| Sysmon | https://learn.microsoft.com/pt-br/sysinternals/downloads/sysmon | Telemetria Windows |
| Elastic Stack | https://www.elastic.co/downloads/ | SIEM/logs open source |
| Wazuh | https://wazuh.com/install/ | SIEM/XDR open source |
| YARA-X | https://github.com/VirusTotal/yara-x | Regras de detecção de arquivo |
| MISP | https://www.misp-project.org/download/ | Compartilhamento de IOCs |

### Exemplo — Regra Sigma

```yaml
# Detectar DLL Injection via CreateRemoteThread
title: DLL Injection via CreateRemoteThread em Processos do Sistema
id: 1a2b3c4d-0000-0000-0000-000000000001
status: experimental
description: |
    Detecta uso de CreateRemoteThread em processos críticos do sistema,
    técnica clássica de injeção de código e DLL injection.
author: Você
date: 2026/11/09
references:
    - https://attack.mitre.org/techniques/T1055/003/
tags:
    - attack.defense_evasion
    - attack.t1055.003
logsource:
    product: windows
    service: sysmon
detection:
    selection:
        EventID: 8   # CreateRemoteThread
        TargetImage|endswith:
            - '\explorer.exe'
            - '\svchost.exe'
            - '\lsass.exe'
            - '\winlogon.exe'
    filter_legit:
        SourceImage|endswith:
            - '\wmiadap.exe'
    condition: selection and not filter_legit
falsepositives:
    - Softwares de segurança legítimos
    - Ferramentas de debugging
level: high
```

### Exemplo — Regra YARA

```yara
// Detectar shellcode runner clássico (RWX + memcpy)
rule ShellcodeRunnerClassic {
    meta:
        author      = "Você"
        description = "Detecta padrão de VirtualAlloc RWX + shellcode runner"
        
    strings:
        $api_valloc = "VirtualAlloc" ascii nocase
        $api_wpm    = "WriteProcessMemory" ascii nocase
        $api_crt    = "CreateRemoteThread" ascii nocase
        
    condition:
        uint16(0) == 0x5A4D    // É um PE (MZ header)
        and $api_valloc
        and ($api_wpm or $api_crt)
}
```

### Labs Práticos

| Plataforma | Lab | Link | Dificuldade |
|-----------|-----|------|------------|
| TryHackMe | SOC Level 1 path | https://tryhackme.com/path/outline/soclevel1 | ⭐⭐ |
| Blue Team Labs Online | Casos práticos | https://blueteamlabs.online/ | ⭐⭐ |
| CyberDefenders | PCAP / host investigations | https://cyberdefenders.org/ | ⭐–⭐⭐⭐ |
| LetsDefend | Incidentes em SOC simulado | https://letsdefend.io/ | ⭐⭐ |
| Atomic Red Team | Testar suas detecções | https://github.com/redcanaryco/atomic-red-team | ⭐⭐ |

### Checklist — Fase 6

- [ ] Configurei Sysmon com config avançada (SwiftOnSecurity ou olafhartong)
- [ ] Configurei stack de logging (ELK ou Splunk Free) + ingestão de logs
- [ ] Criei 3+ regras Sigma funcionais e as testei com Atomic Red Team
- [ ] Criei 3+ regras YARA para detectar técnicas das fases anteriores
- [ ] Respondi 5 alertas no TryHackMe SOC Level 1 com evidências
- [ ] Sei mapear um alerta para uma TTP do MITRE ATT&CK
- [ ] Entendo o fluxo de trabalho de um analista SOC L1

---

## Fase 7 — DFIR

> **Objetivo:** Quando um incidente acontece, você precisa determinar: o que foi comprometido, como o atacante entrou, o que ele fez e quando. DFIR é investigação forense com precisão científica.

### Metodologia de Resposta a Incidentes (NIST 800-61)

```
┌─────────────────────────────────────────────────────────────┐
│          CICLO DE INCIDENT RESPONSE (NIST 800-61)           │
│                                                             │
│  1. PREPARAÇÃO      → Playbooks, ferramentas, treinamento   │
│         ↓                                                   │
│  2. DETECÇÃO        → Alertas, triagem, classificação       │
│         ↓                                                   │
│  3. CONTENÇÃO       → Isolar host, bloquear IP/domínio     │
│         ↓                                                   │
│  4. ERRADICAÇÃO     → Remover malware, fechar vetor        │
│         ↓                                                   │
│  5. RECUPERAÇÃO     → Restaurar serviços, monitorar        │
│         ↓                                                   │
│  6. LIÇÕES APRENDIDAS → Relatório final, melhorias         │
└─────────────────────────────────────────────────────────────┘
```

### Artefatos Forenses Windows — Mapa

| Artefato | Localização | O que revela |
|---------|------------|-------------|
| **Prefetch** | `C:\Windows\Prefetch\*.pf` | Programas executados, timestamp |
| **Registry** | `HKLM\Software`, `NTUSER.DAT` | Persistência, MRU, instalações |
| **Event Logs** | `C:\Windows\System32\winevt\Logs\` | Autenticação, processos, rede |
| **$MFT** | Raiz de cada volume NTFS | Histórico completo de arquivos |
| **LNK Files** | `%APPDATA%\Microsoft\Windows\Recent\` | Arquivos acessados |
| **Shellbags** | `NTUSER.DAT\Software\...\BagMRU` | Pastas acessadas (mesmo via rede) |
| **Amcache** | `C:\Windows\appcompat\Programs\Amcache.hve` | Executáveis com hash |
| **SRUM** | `C:\Windows\System32\sru\SRUDB.dat` | Uso de rede por processo |

### Documentação Oficial

| Recurso | Link |
|---------|------|
| 📌 Volatility 3 docs | https://volatility3.readthedocs.io/en/stable/ |
| 📌 Autopsy docs | https://www.autopsy.com/support/documentation/ |
| 📌 NIST SP 800-86 — Forense + IR | https://csrc.nist.gov/pubs/sp/800/86/final |
| 📌 Microsoft — Windows Event Auditing | https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/ |
| 📌 Velociraptor docs | https://docs.velociraptor.app/ |

### Livros

| Título | Link | Gratuito? | Dificuldade |
|--------|------|-----------|------------|
| 📚 The Art of Memory Forensics | Wiley / biblioteca | Comercial | ⭐⭐⭐ |
| 📚 NIST SP 800-61 Rev3 | https://csrc.nist.gov/pubs/sp/800/61/r3/final | **Sim** | ⭐⭐ |
| 📚 Volatility 3 Documentation | https://volatility3.readthedocs.io/en/stable/ | **Sim** | ⭐⭐ |

### 🎥 Vídeos — PT-BR

| Canal / Conteúdo | Link |
|-----------------|------|
| 🇧🇷 Papo Binário — AMO (Análise de Malware Online) | https://mentebinaria.org.br/aprender/analise-de-malware-online-amo/ |
| 🇧🇷 CS Academy — LAB SOC Open Source | https://www.youtube.com/playlist?list=PLALjBisXuYJdavQDEeB0JcgqSRKSDhGPu |
| 🇧🇷 Papo Binário — AMO YARA (aula 06) | https://www.youtube.com/watch?v=QL0kt8uQ8M0 |

### 🎥 Vídeos — Inglês

| Canal / Conteúdo | Link |
|-----------------|------|
| 13Cubed — Introduction to Windows Forensics (playlist) | https://www.youtube.com/watch?v=VYROU-ZwZX8&list=PLlv3b9B16ZadqDQH0lTRO4kqn2P1g9Mve |
| 13Cubed — Introduction to Memory Forensics (playlist) | https://www.youtube.com/watch?v=1PAGcPJFwbE&list=PLlv3b9B16Zaf-uDlgouB0DMiPNYU_sJFN |
| 13Cubed — Intro to Malware Analysis | https://www.youtube.com/watch?v=-Ml04jPMH3U&list=PLlv3b9B16ZafLdkYgJTR5jRQdY9CJJtTZ |
| SANS DFIR — talks e webcasts | https://www.youtube.com/c/SANSDigitalForensics/videos |

### 🔧 Ferramentas

| Ferramenta | Link | Para quê |
|-----------|------|---------|
| Volatility 3 | https://github.com/volatilityfoundation/volatility3 | Análise de RAM |
| Autopsy | https://www.autopsy.com/download/ | Forense de disco e timeline |
| FTK Imager | https://www.exterro.com/digital-forensics-software/ftk-imager | Imagens forenses |
| NetworkMiner | https://www.netresec.com/?page=NetworkMiner | Artefatos de PCAP |
| FLARE-VM | https://github.com/mandiant/flare-vm | VM de análise de malware |
| Velociraptor | https://docs.velociraptor.app/ | Coleta forense em endpoints |
| Eric Zimmerman Tools | https://github.com/EricZimmerman | 20+ ferramentas de artefatos Windows |
| plaso/log2timeline | https://github.com/log2timeline/plaso | Super timeline forense |

### Blogs de Referência

| Blog | Link |
|------|------|
| DFIR Report | https://thedfirreport.com/ |
| SANS DFIR Blog | https://www.sans.org/blog/?focus-area=digital-forensics |
| 13Cubed Resources | https://www.13cubed.com/ |
| Volatility Labs Blog | https://volatility-labs.blogspot.com/ |
| Malware Traffic Analysis | https://www.malware-traffic-analysis.net/ |

### Labs Práticos

| Plataforma | Lab | Link | Dificuldade |
|-----------|-----|------|------------|
| CyberDefenders | Blue/DFIR labs | https://cyberdefenders.org/ | ⭐–⭐⭐⭐ |
| Blue Team Labs Online | Incidentes | https://blueteamlabs.online/ | ⭐⭐ |
| Digital Corpora | Imagens de disco | https://digitalcorpora.org/ | ⭐⭐ |
| Malware Traffic Analysis | PCAPs de incidentes | https://www.malware-traffic-analysis.net/ | ⭐⭐ |
| Volatility Foundation | Test data para Volatility | https://github.com/volatilityfoundation/volatility3-test-data | ⭐⭐ |

### Checklist — Fase 7

- [ ] Investiguei artefatos Windows (Prefetch, Registry, Event Logs, LNK)
- [ ] Analisei dump de RAM com Volatility 3 (processos, conexões, strings)
- [ ] Produzi uma super timeline de incidente (UTC, hashes, cadeia de custódia)
- [ ] Analisei um PCAP de incidente e extraí IOCs de rede
- [ ] Realizei triage estática de um sample de malware (hashes, imports, strings)
- [ ] Produzi um relatório de incidente completo com hipótese e conclusão
- [ ] Mapeei o incidente investigado no MITRE ATT&CK

---

## Fase 8 — Cloud Security

> **Objetivo:** A maioria das infraestruturas empresariais vive na nuvem. Configurações erradas de IAM, buckets S3 públicos e permissões excessivas são os vetores de ataque mais comuns em 2026.

### Superfície de Ataque em Cloud

```
┌─────────────────────────────────────────────────────────────┐
│                    CLOUD ATTACK SURFACE                     │
│                                                             │
│  IDENTIDADE (IAM)                 DADOS                     │
│  → Chaves expostas no GitHub      → S3 Bucket público       │
│  → Permissões excessivas          → Banco sem criptografia  │
│  → MFA não habilitado             → Backups sem controle    │
│  → Service accounts amplas        → Logs sem retenção       │
│                                                             │
│  REDE                             CONTAINER / SERVERLESS    │
│  → Security Groups permissivos    → Imagem com vulns        │
│  → 0.0.0.0/0 em RDS               → RBAC mal configurado    │
│  → VPC sem segmentação            → Lambda com role ampla   │
│  → Sem VPN/PrivateLink            → Escape de container     │
└─────────────────────────────────────────────────────────────┘
```

### Documentação Oficial

| Recurso | Link |
|---------|------|
| 📌 AWS IAM User Guide | https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html |
| 📌 AWS CloudTrail User Guide | https://docs.aws.amazon.com/awscloudtrail/latest/userguide/ |
| 📌 AWS GuardDuty | https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html |
| 📌 Microsoft Entra ID (PT-BR) | https://learn.microsoft.com/pt-br/entra/identity/ |
| 📌 Google Cloud IAM | https://cloud.google.com/iam/docs/overview |
| 📌 Kubernetes RBAC | https://kubernetes.io/docs/reference/access-authn-authz/rbac/ |
| 📌 Docker Security | https://docs.docker.com/engine/security/ |

### Livros

| Título | Link | Gratuito? |
|--------|------|-----------|
| 📚 AWS Well-Architected — Security Pillar | https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html | **Sim** |
| 📚 Azure Security Documentation | https://learn.microsoft.com/pt-br/azure/security/ | **Sim (PT-BR)** |
| 📚 Kubernetes Security docs | https://kubernetes.io/docs/concepts/security/ | **Sim** |

### 🎥 Vídeos — PT-BR

| Canal / Conteúdo | Link |
|-----------------|------|
| 🇧🇷 LINUXtips — Descomplicando Docker | https://linuxtips.io/youtube/ |
| 🇧🇷 LINUXtips — Kubernetes Essentials | https://linuxtips.io/conteudo-gratuito/ |
| 🇧🇷 Microsoft Learn — SC-500 (auto-instrucional PT-BR) | https://learn.microsoft.com/pt-br/training/courses/sc-500t00 |

### 🎥 Vídeos — Inglês

| Canal / Conteúdo | Link |
|-----------------|------|
| AWS Events — Security e IAM | https://www.youtube.com/@AWSEvents/videos |
| Google Cloud Tech — Security | https://www.youtube.com/@googlecloudtech/videos |
| TechWorld with Nana — Kubernetes/Docker | https://www.youtube.com/@TechWorldwithNana/videos |

### Cursos Gratuitos

| Plataforma | Curso | Link | Horas est. |
|-----------|-------|------|-----------|
| Microsoft Learn | SC-500 self-paced (PT-BR) | https://learn.microsoft.com/pt-br/training/courses/sc-500t00 | Variável |
| AWS Skill Builder | Cursos digitais gratuitos | https://skillbuilder.aws/ | 10–30h |
| LINUXtips | Kubernetes Essentials | https://linuxtips.io/conteudo-gratuito/ | 4h+ |
| Kubernetes | Official Tutorials | https://kubernetes.io/docs/tutorials/ | 10–20h |

### 🔧 Ferramentas

| Ferramenta | Link | Para quê |
|-----------|------|---------|
| Prowler | https://github.com/prowler-cloud/prowler | CSPM multi-cloud |
| ScoutSuite | https://github.com/nccgroup/ScoutSuite | Auditoria de configuração cloud |
| Trivy | https://github.com/aquasecurity/trivy | Vulnerabilidades em containers/IaC |
| Falco | https://falco.org/docs/getting-started/ | Detecção runtime em Kubernetes |
| CloudSploit | https://github.com/aquasecurity/cloudsploit | Cloud configuration scanning |
| Pacu | https://github.com/RhinoSecurityLabs/pacu | Auditoria AWS (apenas lab autorizado) |
| CloudGoat | https://github.com/RhinoSecurityLabs/cloudgoat | ⚠️ Ambiente AWS vulnerável |
| flAWS.cloud | http://flaws.cloud/ | CTF de AWS |

### Labs Práticos

| Plataforma | Lab | Link | Dificuldade |
|-----------|-----|------|------------|
| flAWS.cloud | CTF de misconfigurações AWS | http://flaws.cloud/ | ⭐⭐ |
| Kubernetes Goat | Cluster Kubernetes vulnerável | https://github.com/madhuakula/kubernetes-goat | ⭐⭐ |
| AWS Free Tier | IAM + CloudTrail hands-on | https://aws.amazon.com/free/ | ⭐⭐ |
| Microsoft Learn SC-500 | Entra/Defender labs | https://learn.microsoft.com/pt-br/training/courses/sc-500t00 | ⭐⭐ |

### Checklist — Fase 8

- [ ] Configurei um ambiente AWS Free Tier com IAM mínimo
- [ ] Executei Prowler/ScoutSuite contra meu ambiente e interpretei os findings
- [ ] Sei como analisar CloudTrail para detectar atividade suspeita
- [ ] Configurei Trivy para escanear uma imagem Docker por vulnerabilidades
- [ ] Concluí o CTF flAWS.cloud
- [ ] Entendo o que é "least privilege" e por que é difícil aplicar na prática
- [ ] Sei a diferença entre CSPM, CWPP, CIEM e CNAPP (os acrônimos de cloud security)

---

## Fase 9 — Certificações e Carreira

> **Objetivo:** Transformar conhecimento técnico em emprego. Certificações são portas de entrada; portfólio é o que mantém você no processo seletivo.

### Mapa de Certificações — Por Trilha e Nível

```
INICIANTE                INTERMEDIÁRIO              AVANÇADO
─────────                ─────────────              ────────

⚪ CompTIA Network+      🔴 eJPT (INE)              🔴 OSCP (OffSec)
⚪ CompTIA Security+     🔴 PNPT (TCM)              🔴 OSED/OSEP
⚪ SC-900 (Microsoft)    🔵 CompTIA CySA+            🔵 GIAC GCIH/GCFE
⚪ ISC2 CC               🔵 BTL1 (Blue Team)         🔵 GIAC GREM
⚪ Google Cybersec.      ☁  Microsoft SC-500         ☁  AWS Security Spec.
                         🔴 eCPPT (INE)              ☁  CompTIA SecurityX

Recomendação de entrada: Security+ → eJPT (Red) ou SOC Level 1 → BTL1 (Blue)
```

**Nota:** AZ-500 foi aposentado em 31/08/2026 e substituído pelo SC-500.

### Certificações — Tabela Completa

| Certificação | Trilha | Nível | Prova | Observação |
|-------------|--------|-------|-------|-----------|
| CompTIA Network+ | Base | I | Pago | Fundamentos de rede |
| CompTIA Security+ | Generalista | I/M | Pago | Baseline do mercado |
| ISC2 CC | Base/Blue | I | Ver promoção | Treinamento gratuito |
| Microsoft SC-900 | Base/Cloud | I | Pago | Learn PT-BR grátis |
| eJPT (INE) | Red júnior | I/M | Pago | Intro pentest prático |
| PNPT (TCM) | Red | M | Pago | Foco em relatório e AD |
| eCPPT (INE) | Red | M | Pago | Confirmar versão atual |
| OSCP / PEN-200 | Red | A | Pago alto | Exige base prática sólida |
| CompTIA CySA+ | SOC | M | Pago | Avaliação defensiva |
| BTL1 (Security Blue Team) | SOC/DFIR | I/M | Pago | Foco em blue team prático |
| GIAC GCIH | IR | M/A | Pago alto | Resposta a incidentes |
| GIAC GCFE | Forense | A | Pago alto | Forense Windows |
| Microsoft SC-500 | Cloud/Azure | M | Pago | Substitui AZ-500 (2026) |
| AWS Security Specialty | Cloud | A | Pago | AWS operacional |
| CompTIA SecurityX | Arquitetura | A | Pago | Antigo CASP+ |

### Documentação Oficial

| Recurso | Link |
|---------|------|
| 📌 CompTIA Security+ | https://www.comptia.org/certifications/security |
| 📌 OffSec OSCP | https://www.offsec.com/courses/pen-200/ |
| 📌 INE Certifications | https://security.ine.com/certifications/ |
| 📌 Microsoft SC-500 (PT-BR) | https://learn.microsoft.com/pt-br/credentials/certifications/cloud-and-ai-security-engineer-associate/ |
| 📌 AWS Security Specialty | https://aws.amazon.com/certification/certified-security-specialty/ |
| 📌 TCM Security — roadmaps de carreira | https://tcm-sec.com/how-to-become-a-soc-analyst/ |

### 🎥 Vídeos — Carreira e Certificações

| Canal / Conteúdo | Link |
|-----------------|------|
| Professor Messer — Security+ SY0-701 (playlist gratuita) | https://www.youtube.com/watch?v=KiEptGbnEBc&list=PLG49S3nxzAnl4QDVqK-hOnoqcSKEIDDuv |
| Professor Messer — Network+ N10-009 | https://www.youtube.com/watch?v=k7IOn3TiUc8&list=PLG49S3nxzAnl_tQe3kvnmeMid0mjF8Le8 |
| IppSec — write-ups e raciocínio | https://www.youtube.com/playlist?list=PLidcsTyj9JXItWpbRtTg6aDEj10_F17x5 |

### Cursos Gratuitos de Entrada

| Plataforma | Curso | Link |
|-----------|-------|------|
| Microsoft Learn | SC-900 self-paced (PT-BR) | https://learn.microsoft.com/pt-br/credentials/certifications/security-compliance-and-identity-fundamentals/ |
| TCM Academy | Free Tier (40h+) | https://tcm-sec.com/academy/tcm-academy-free-tier/ |
| TryHackMe | SOC Level 1 path | https://tryhackme.com/path/outline/soclevel1 |
| PortSwigger | Web Security Academy | https://portswigger.net/web-security/ |

### Como Montar o Portfólio

```
REPOSITÓRIO GITHUB (público, bem documentado)
│
├── network-analysis/
│   └── Análise de PCAP com hipóteses e IOCs (sem dados sensíveis)
│
├── appsec-labs/
│   └── Relatórios de labs vulneráveis + mitigações (nunca flags privadas)
│
├── pentest-report-template/
│   └── Escopo, ROE, evidências, severidade e correções
│
├── soc-detection/
│   └── Regras Sigma + YARA + casos de teste
│
├── dfir-case-study/
│   └── Timeline UTC, hashes, logs, hipótese, conclusão
│
└── cloud-security/
    └── IaC seguro + análise de misconfigs em lab isolado
```

### Plataformas para Primeiros Empregos e Bug Bounty

| Plataforma | Link | Para quê |
|-----------|------|---------|
| HackerOne | https://hackerone.com/directory/programs | Bug bounty — testar APENAS escopo autorizado |
| Intigriti | https://www.intigriti.com/programs | Bug bounty alternativo |
| LinkedIn | https://www.linkedin.com/ | Vagas e networking |
| GitHub Pages | https://pages.github.com/ | Publicar seu site/portfólio |
| CTFtime | https://ctftime.org/ | Competições CTF para portfólio |

### Checklist — Fase 9

- [ ] Perfil do LinkedIn atualizado com projetos técnicos
- [ ] GitHub com pelo menos 5 projetos organizados e documentados em inglês
- [ ] Publiquei 5 write-ups técnicos (CTF, labs, investigações)
- [ ] Escolhi a trilha principal (Red / Blue / Cloud) com base em interesse real
- [ ] Passei pelo menos 1 certificação de entrada (Security+ ou eJPT ou BTL1)
- [ ] Me cadastrei em pelo menos 1 plataforma de bug bounty (apenas escopo autorizado)
- [ ] Me candidatei a vagas de entrada: SOC Analyst L1 ou Junior Pentester

---

## Recursos Consolidados

### Livros — Lista Definitiva

| Livro | Link | Gratuito? | Prioridade |
|-------|------|-----------|-----------|
| 📚 Computer Networks: A Systems Approach | https://book.systemsapproach.org/ | **Sim** | Fase 0 |
| 📚 The Linux Command Line | https://linuxcommand.org/tlcl.php | **Sim** | Fase 0 |
| 📚 Automate the Boring Stuff with Python | https://automatetheboringstuff.com/ | **Sim** | Fase 0 |
| 📚 Nmap Network Scanning | https://nmap.org/book/ | **Sim** | Fase 1 |
| 📚 OWASP Web Security Testing Guide | https://owasp.org/www-project-web-security-testing-guide/ | **Sim** | Fase 2 |
| 📚 HackTricks (referência viva) | https://book.hacktricks.wiki/ | **Sim** | Fases 3–5 |
| 📚 Metasploit Unleashed (OffSec) | https://www.offsec.com/metasploit-unleashed/ | **Sim** | Fase 3 |
| 📚 Modern Binary Exploitation (RPISEC) | https://github.com/RPISEC/MBE | **Sim** | Fase 4 |
| 📚 NIST SP 800-61 Rev3 | https://csrc.nist.gov/pubs/sp/800/61/r3/final | **Sim** | Fase 7 |
| 📚 The Art of Memory Forensics | Wiley / biblioteca | Comercial | Fase 7 |
| 📚 AWS Well-Architected — Security Pillar | https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/ | **Sim** | Fase 8 |
| 📚 Security Engineering — Ross Anderson | https://www.cl.cam.ac.uk/~rja14/book.html | **Sim** | Referência |

### Canais YouTube — Lista Definitiva

**🇧🇷 Português:**

| Canal | Fases Relevantes | Link |
|-------|----------------|------|
| 🇧🇷 Curso em Vídeo — Redes | 0, 1 | https://www.youtube.com/@cursoemvideo |
| 🇧🇷 Curso em Vídeo — Python | 0, 2 | https://www.youtube.com/@cursoemvideo |
| 🇧🇷 Bóson Treinamentos | 0 | https://www.youtube.com/@bosontreinamentos |
| 🇧🇷 LINUXtips | 0, 8 | https://linuxtips.io/ |
| 🇧🇷 Solyd | 2, 3 | https://www.youtube.com/@SolydOficial |
| 🇧🇷 Ricardo Longatto | 2, 3, 4 | https://www.youtube.com/@RicardoLongatto |
| 🇧🇷 Mente Binária | 4, 7 | https://www.youtube.com/@MenteBinaria |
| 🇧🇷 Papo Binário | 4, 6, 7 | https://www.youtube.com/@PapoBinario |
| 🇧🇷 CS Academy | 1, 6, 7 | https://www.youtube.com/@cs_academy |

**Inglês:**

| Canal | Fases Relevantes | Link |
|-------|----------------|------|
| Professor Messer | 0, 1, 9 | https://www.youtube.com/@professormesser |
| NetworkChuck | 0, 1 | https://www.youtube.com/@NetworkChuck |
| TCM Security | 2, 3, 5, 6 | https://www.youtube.com/@TCMSecurityAcademy |
| IppSec | 2, 3, 5 — REFERÊNCIA #1 HtB | https://www.youtube.com/@ippsec |
| LiveOverflow | 2, 4 | https://www.youtube.com/@LiveOverflow |
| John Hammond | 2, 3, 7 | https://www.youtube.com/@_JohnHammond |
| 13Cubed | 6, 7 — REFERÊNCIA DFIR | https://www.youtube.com/@13Cubed |
| SANS DFIR | 6, 7, 8 | https://www.youtube.com/@SANSDigitalForensics |
| OALabs | 7 — Análise de malware | https://www.youtube.com/@OALabs |

### Sites e Blogs — Referência Rápida

| Site | URL | Tipo |
|------|-----|------|
| **ired.team** | https://ired.team | Técnicas ofensivas com código |
| **HackTricks** | https://book.hacktricks.wiki | Referência de enumeração e privesc |
| **PortSwigger Research** | https://portswigger.net/research | AppSec avançado |
| **DFIR Report** | https://thedfirreport.com/ | Incidentes reais detalhados |
| **Red Canary Blog** | https://redcanary.com/blog/ | Detection Engineering |
| **SpecterOps Blog** | https://specterops.io/blog/ | AD e adversary emulation |
| **Outflank Blog** | https://www.outflank.nl/blog/ | Red team maduro |
| **Elastic Security Labs** | https://www.elastic.co/security-labs/ | APT analysis + detection |
| **SANS DFIR Blog** | https://www.sans.org/blog/?focus-area=digital-forensics | IR e forense |
| **CERT.br Cartilha** | https://cartilha.cert.br/ | Noções de segurança PT-BR |
| **MSDN / Microsoft Learn** | https://learn.microsoft.com/ | Documentação oficial |

### Repositórios GitHub — Top 30

**Fundamentos e Referências:**
```
jlevy/the-art-of-command-line              → https://github.com/jlevy/the-art-of-command-line
GTFOBins/GTFOBins.github.io                → https://github.com/GTFOBins/GTFOBins.github.io
LOLBAS-Project/LOLBAS                      → https://github.com/LOLBAS-Project/LOLBAS
```

**Web / AppSec:**
```
juice-shop/juice-shop                      → https://github.com/juice-shop/juice-shop
digininja/DVWA                             → https://github.com/digininja/DVWA
OWASP/wstg                                 → https://github.com/OWASP/wstg
OWASP/crAPI                                → https://github.com/OWASP/crAPI
```

**Pentest / Ofensivo:**
```
peass-ng/PEASS-ng                          → https://github.com/peass-ng/PEASS-ng
SpecterOps/BloodHound                      → https://github.com/SpecterOps/BloodHound
Pennyw0rth/NetExec                         → https://github.com/Pennyw0rth/NetExec
fortra/impacket                            → https://github.com/fortra/impacket
DominicBreuker/pspy                        → https://github.com/DominicBreuker/pspy
```

**Exploitation:**
```
Gallopsled/pwntools                        → https://github.com/Gallopsled/pwntools
pwndbg/pwndbg                              → https://github.com/pwndbg/pwndbg
JonathanSalwan/ROPgadget                   → https://github.com/JonathanSalwan/ROPgadget
AFLplusplus/AFLplusplus                    → https://github.com/AFLplusplus/AFLplusplus
RPISEC/MBE                                 → https://github.com/RPISEC/MBE
```

**Red Team:**
```
redcanaryco/atomic-red-team                → https://github.com/redcanaryco/atomic-red-team
mitre/caldera                              → https://github.com/mitre/caldera
BishopFox/sliver                           → https://github.com/BishopFox/sliver
center-for-threat-informed-defense/...     → https://github.com/center-for-threat-informed-defense/adversary_emulation_library
```

**Blue Team / Detection:**
```
SigmaHQ/sigma                              → https://github.com/SigmaHQ/sigma
Neo23x0/signature-base                     → https://github.com/Neo23x0/signature-base
SwiftOnSecurity/sysmon-config              → https://github.com/SwiftOnSecurity/sysmon-config
olafhartong/sysmon-modular                 → https://github.com/olafhartong/sysmon-modular
sbousseaden/EVTX-ATTACK-SAMPLES            → https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES
```

**DFIR:**
```
volatilityfoundation/volatility3           → https://github.com/volatilityfoundation/volatility3
mandiant/flare-vm                          → https://github.com/mandiant/flare-vm
EricZimmerman (coleção de tools)           → https://github.com/EricZimmerman
log2timeline/plaso                         → https://github.com/log2timeline/plaso
```

**Cloud:**
```
prowler-cloud/prowler                      → https://github.com/prowler-cloud/prowler
aquasecurity/trivy                         → https://github.com/aquasecurity/trivy
falcosecurity/falco                        → https://github.com/falcosecurity/falco
RhinoSecurityLabs/cloudgoat                → https://github.com/RhinoSecurityLabs/cloudgoat
```

### Plataformas de Labs e CTFs

| Plataforma | URL | Tipo | Custo |
|-----------|-----|------|-------|
| TryHackMe | https://tryhackme.com | Paths guiados, rooms | Freemium |
| Hack The Box | https://app.hackthebox.com | Máquinas reais | Freemium |
| PortSwigger Academy | https://portswigger.net/web-security | AppSec completo | **Gratuito** |
| OverTheWire | https://overthewire.org/wargames/ | Wargames Linux | **Gratuito** |
| picoCTF | https://play.picoctf.org | CTF permanente | **Gratuito** |
| VulnHub | https://www.vulnhub.com | VMs para download | **Gratuito** |
| CyberDefenders | https://cyberdefenders.org | Blue team / DFIR | Freemium |
| Blue Team Labs Online | https://blueteamlabs.online | Investigações defensivas | Freemium |
| LetsDefend | https://letsdefend.io | SOC simulado | Freemium |
| flAWS.cloud | http://flaws.cloud | AWS misconfigs | **Gratuito** |
| pwn.college | https://pwn.college | Binary Exploitation | **Gratuito** |
| ROP Emporium | https://ropemporium.com | ROP challenges | **Gratuito** |
| CTFtime | https://ctftime.org | Calendário de CTFs | **Gratuito** |

### Frameworks e Cursos Gratuitos Completos

| Recurso | Link | Conteúdo |
|---------|------|---------|
| OpenSecurityTraining2 | https://ost2.fyi/ | Cursos técnicos avançados gratuitos |
| Malware Unicorn Workshops | https://malwareunicorn.org/workshops.html | RE e análise de malware |
| TCM Academy Free Tier | https://tcm-sec.com/academy/tcm-academy-free-tier/ | 40h+ grátis |
| MITRE ATT&CK | https://attack.mitre.org/ | Mapeamento de TTPs |
| MITRE D3FEND | https://d3fend.mitre.org/ | Contramedidas defensivas |
| OWASP Cheat Sheets | https://cheatsheetseries.owasp.org/ | Mitigações por vuln |
| Cisco NetAcad | https://www.netacad.com/ | Redes e Linux |

---

## Roadmap Visual — 12 Meses

```
MÊS  1  ████████░░░░░░░░░░░░░░░░  Fase 0: Fundamentos (Redes, Linux, Python)
MÊS  2  ████████░░░░░░░░░░░░░░░░  Fase 1: Segurança de Redes (Nmap, Wireshark, IDS)
MÊS  3  ████████░░░░░░░░░░░░░░░░  Fase 2: Web Security (OWASP, Burp, 20+ labs)
MÊS  4  ████████░░░░░░░░░░░░░░░░  Fase 2: Web Security (APIs, AppSec avançado)
MÊS  5  ████████░░░░░░░░░░░░░░░░  Fase 3: Pentesting (Linux + Windows)
MÊS  6  ████████░░░░░░░░░░░░░░░░  Fase 3: Pentesting (Active Directory)
MÊS  7  ████████░░░░░░░░░░░░░░░░  Fase 4: Exploitation (BOF, ROP, CVEs)
MÊS  8  ████████░░░░░░░░░░░░░░░░  Fase 5: Red Team Operations
MÊS  9  ████████░░░░░░░░░░░░░░░░  Fase 6: Blue Team / SOC / SIEM
MÊS 10  ████████░░░░░░░░░░░░░░░░  Fase 7: DFIR (Forense + IR)
MÊS 11  ████████░░░░░░░░░░░░░░░░  Fase 8: Cloud Security
MÊS 12  ████████░░░░░░░░░░░░░░░░  Fase 9: Certificações + Portfólio + Carreira

         ─────────────────────────────────────────────────────────►
         Fundamentos       Ofensivo/Defensivo       Especialização
```

---

## Checklist Final — Você Está Pronto Quando...

### Técnico

**Redes e Web:**
- [ ] Consigo fazer reconhecimento completo (OSINT + Nmap + enumeração de serviços)
- [ ] Explorei todas as categorias do OWASP Top 10:2025 em lab
- [ ] Realizei um pentest completo (recon → relatório) em ambiente autorizado
- [ ] Explorei um ambiente Active Directory e mapeei paths de ataque com BloodHound
- [ ] Escrevi um exploit de buffer overflow funcional (x86 ou x64)

**Ofensivo:**
- [ ] Implementei persistência e movimentação lateral em lab isolado
- [ ] Executei emulação de adversário com Atomic Red Team ou Caldera
- [ ] Mapeei TTPs de um exercício real no MITRE ATT&CK

**Defensivo:**
- [ ] Configurei stack completo de SIEM + Sysmon + logs de rede
- [ ] Criei 5+ regras Sigma e 5+ regras YARA funcionais e testadas
- [ ] Investiguei um incidente real (ou de lab) com timeline, IOCs e relatório
- [ ] Analisei dump de RAM com Volatility 3

**Cloud:**
- [ ] Auditei um ambiente cloud com Prowler/ScoutSuite
- [ ] Concluí o CTF flAWS.cloud
- [ ] Configurei Trivy em um pipeline de CI

### Portfólio
- [ ] GitHub com 5+ projetos organizados e documentados
- [ ] 5+ write-ups técnicos publicados (CTF, labs, investigações)
- [ ] Pelo menos 1 relatório de pentest com escopo, evidências e remediações
- [ ] Pelo menos 1 investigação DFIR com timeline e cadeia de custódia
- [ ] Perfil LinkedIn atualizado com projetos e certificações

### Certificações (escolha por trilha)
- [ ] ⚪ CompTIA Security+ (trilha geral)
- [ ] 🔴 eJPT / PNPT (trilha Red)
- [ ] 🔵 BTL1 / TryHackMe SOC L1 (trilha Blue)
- [ ] ☁ SC-500 ou AWS Security Specialty (trilha Cloud)

---

## Ética & Responsabilidade

### ✅ Sempre Permitido
- Pesquisa em VM isolada (rede Host-Only, sem internet para o host)
- Testes em plataformas autorizadas: TryHackMe, Hack The Box, PortSwigger, picoCTF
- Bug bounty exclusivamente em programas com escopo explícito
- Contribuição open source para projetos de segurança defensiva
- CTF, wargames e ambientes de prática

### ❌ Nunca Permitido
- Acesso a sistemas sem autorização explícita — mesmo que "parecidos com alvos de lab"
- Uso de técnicas ofensivas fora do escopo acordado
- Vazar ou publicar informações confidenciais de vulnerabilidades sem disclosure coordenado
- Qualquer ação coberta pela **Lei Carolina Dieckmann (Lei 12.737/2012)** no Brasil
- Usar ferramentas de pentest em redes de terceiros sem contrato assinado

### Regra de Ouro
> Hacking sem autorização é crime, não atividade educacional. Se você não tem um contrato, ROE assinado, ou está em plataforma de lab explicitamente autorizada — não faça. O conhecimento aqui existe para construir sistemas mais seguros e profissionais mais preparados, não para causar dano.

---

## Referências de Profissionais para Acompanhar

| Profissional | Twitter/X | Especialidade |
|-------------|----------|--------------|
| Marcus Hutchins (MalwareTech) | @MalwareTechBlog | Malware, IR, Blue Team |
| Kevin Robertson | @Kevin_Robertson | Active Directory, pentest |
| Will Schroeder | @harmj0y | Active Directory, BloodHound |
| Andy Robbins | @_wald0 | BloodHound, AD security |
| hasherezade | @hasherezade | Malware, PE analysis |
| 13Cubed (Richard Davis) | @13Cubed | DFIR, Windows Forensics |
| Ryan Chapman | @rj_chap | DFIR, Incident Response |
| Florian Roth | @cyb3rops | YARA, Sigma, Threat Intel |
| Lee Holmes | @Lee_Holmes | PowerShell, Blue Team |

---

*Roadmap compilado para fins educacionais e desenvolvimento de capacidades defensivas e ofensivas autorizadas. Use exclusivamente em ambientes controlados e com autorização explícita.*
