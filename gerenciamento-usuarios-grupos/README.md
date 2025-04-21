# Gerenciamento de Usuários e Grupos no Linux

Este projeto tem como objetivo praticar o gerenciamento de usuários e grupos em sistemas Linux, utilizando comandos essenciais como `useradd`, `passwd`, `groupadd`, `usermod` e validação via arquivos do sistema (`/etc/passwd`, `/etc/group`, `/var/log/secure`).

---

## Tarefas Realizadas

### Task 1 – Validação do diretório de trabalho
- Comando executado: `pwd`
- Diretório esperado: `/home/ec2-user`

---

### Task 2 – Criação de Usuários

Foram criados os seguintes usuários com a senha padrão `P@ssword1234!`:

| Nome       | Sobrenome | User ID     | Função                 |
|------------|-----------|-------------|------------------------|
| Alejandro  | Rosalez   | arosalez    | Sales Manager          |
| Efua       | Owusu     | eowusu      | Shipping               |
| Jane       | Doe       | jdoe        | Shipping               |
| Li         | Juan      | ljuan       | HR Manager             |
| Mary       | Major     | mmajor      | Finance Manager        |
| Mateo      | Jackson   | mjackson    | CEO                    |
| Nikki      | Wolf      | nwolf       | Sales Representative   |
| Paulo      | Santos    | psantos     | Shipping               |
| Sofia      | Martinez  | smartinez   | HR Specialist          |
| Saanvi     | Sarkar    | ssarkar     | Finance Specialist     |

**Comandos principais:**
```bash
sudo useradd <user_id>
sudo passwd <user_id>
```

**Validação:**
```bash
sudo cat /etc/passwd | cut -d: -f1
```

---

### Task 3 – Criação de Grupos e Associação de Usuários

**Grupos criados:**
- Sales
- HR
- Finance
- Shipping
- Managers
- CEO
- Personnel

**Comando para criar grupo:**
```bash
sudo groupadd <group_name>
```

**Associação de usuários aos grupos:**

| Grupo     | Usuários                           |
|-----------|------------------------------------|
| Sales     | arosalez, nwolf, ec2-user          |
| HR        | ljuan, smartinez, ec2-user         |
| Finance   | mmajor, ssarkar, ec2-user          |
| Shipping  | eowusu, jdoe, psantos, ec2-user    |
| Managers  | arosalez, ljuan, mmajor, ec2-user  |
| CEO       | mjackson, ec2-user                 |

**Comando para adicionar usuários ao grupo:**
```bash
sudo usermod -a -G <group_name> <user_id>
```

**Validação:**
```bash
cat /etc/group
```

---

### Task 4 – Testes de Login e Permissões

- Login com: `su <user_id>`
- Teste de criação de arquivo em `/home/ec2-user` sem permissão:
```bash
touch myFile.txt
```

**Resultado esperado:**
```
Permission denied
```

- Tentativa de usar `sudo` com usuário não autorizado:
```bash
sudo touch myFile.txt
```

**Mensagem esperada:**
```
<usuário> is not in the sudoers file. This incident will be reported.
```

**Validação de log com journalctl (caso /var/log/secure não exista):**
```bash
sudo journalctl | grep 'sudo'
```

---

## Comandos utilizados

- `useradd`
- `passwd`
- `groupadd`
- `usermod`
- `su`, `exit`
- `cat`, `cut`, `grep`
- `pwd`, `touch`
- `journalctl` (ou `/var/log/secure`)

---

## Observações

- O usuário `ec2-user` foi adicionado a todos os grupos.
- Todos os usuários foram criados com a senha padrão `P@ssword1234!`.
- Os comandos foram executados em uma instância EC2 no Amazon Linux.
- Quando o arquivo `/var/log/secure` não estava disponível, utilizou-se o `journalctl` para visualizar logs de auditoria de sudo.

---

## Objetivo

Este projeto reforça habilidades básicas e fundamentais de administração de sistemas Linux, essenciais para funções DevOps, SysAdmin e suporte técnico.
