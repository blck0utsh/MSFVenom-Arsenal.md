![Banner Dark Tech](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExM2txcTJibTdiNGQyeHRjdHhxdGUwb2cyeXp6MHp1Yml3NHR1Njc1ZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o7TKs35oA1k40CcZW/giphy.gif)

# 🔍 Nmap: O Olho do Red Team 
> "Scannear sem técnica é como bater na porta da frente e esperar que ninguém ouça."

### 1. Varredura Rápida (Ping Sweep)
Descobre quais máquinas estão vivas na rede antes de atacar.
```bash
nmap -sn <IP DO ALVO>
```
### 🔍 2. Detecção de Serviços e Versões (-sV)
Fundamental para saber se o Windows é 7, 10 ou 11 e quais programas estão rodando.

```bash
nmap -sV <IP_ALVO>
```
### 🔍 3. Varredura Agressiva (-A)
O "tudo em um": detecta SO, versões, executa scripts básicos e faz traceroute.

```bash
nmap -A <IP_ALVO>
```
### 🔍 4. Varredura Furtiva (Stealth Scan -sS)
Tenta abrir a conexão mas não a completa (SYN Scan). É mais difícil de ser detectado por firewalls simples.

```bash
sudo nmap -sS <IP_ALVO>
```
### 🔍 5. Scripts do Nmap (NSE)
O Nmap tem "mini-programas" que já testam vulnerabilidades específicas.

```bash
nmap --script smb-vuln-ms17-010 <IP_ALVO>
```
