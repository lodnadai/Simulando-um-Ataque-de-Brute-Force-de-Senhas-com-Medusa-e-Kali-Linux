/projeto
│
├── brute_force.py           # Simulação de força bruta
├── password_spraying.py     # Teste de uma senha em vários usuários
├── validar_credenciais.py   # Função de autenticação simulada
├── wordlist_reader.py       # Leitura de wordlist
├── wordlist.txt             # Senhas de teste
└── /images                  # (Opcional) prints e diagramas
# Simulando-um-Ataque-de-Brute-Force-de-Senhas-com-Medusa-e-Kali-Linux
Ataque de Brute Force de Senhas 
# Simulação de ataque de força bruta

wordlist = ["1234", "admin", "senha", "root", "toor"]
senha_correta = "root"

print("=== Simulação de Força Bruta ===")

for senha in wordlist:
    print(f"Tentando senha: {senha}")
    if senha == senha_correta:
        print(f"[+] Senha encontrada: {senha}")
        break
else:
    print("[-] Nenhuma senha encontrada.")
O ataque tentaria várias senhas para 1 usuário em:

FTP

SSH

SMB

HTTP Login

Exemplo com Medusa:
medusa -h 192.168.0.10 -u admin -P wordlist.txt -M ftp
# Simulação de Password Spraying

usuarios = ["admin", "root", "joao", "maria"]
senha_tentada = "123456"

credenciais_reais = {
    "admin": "toor",
    "root": "123456",
    "joao": "senha123",
    "maria": "maria2024"
}

print("=== Simulação de Password Spraying ===")

for usuario in usuarios:
    print(f"Tentando login: {usuario}:{senha_tentada}")
    if credenciais_reais.get(usuario) == senha_tentada:
        print(f"[+] Acesso encontrado! Usuário vulnerável: {usuario}")
        break
else:
    print("[-] Nenhum usuário vulnerável encontrado.")
    medusa -h 192.168.0.10 -U users.txt -p 123456 -M smbnt
Validação de Credenciais
# Validação simples de credenciais

usuario_input = "admin"
senha_input = "admin123"

credenciais = {
    "admin": "admin123",
    "convidado": "guest",
    "maria": "senha"
}

def autenticar(usuario, senha):
    return credenciais.get(usuario) == senha

if autenticar(usuario_input, senha_input):
    print("[+] Usuário autenticado com sucesso!")
else:
    print("[-] Credenciais inválidas.")
Leitura de Wordlist
with open("wordlist.txt", "r") as f:
    linhas = f.read().splitlines()

print("=== Wordlist Carregada ===")
for linha in linhas:
    print(linha)
Os scripts acima simulam o que o Kali faria com:

Medusa

Hydra

Ncrack

Patator

O ataque real enviaria tentativas para:

✔ FTP
✔ SSH
✔ SMB
✔ HTTP
✔ RDP
✔ MySQL
✔ POP3
✔ Telnet

Exemplo real do Medusa:
Medidas de Mitigação
1. Limite de tentativas de login

Bloqueio após 3 a 5 erros.

2. Fail2Ban

Bloqueio automático de IPs suspeitos.

3. MFA / 2FA

Impossibilita login mesmo com senha vazada.

4. Políticas de senha forte

Exigir:

tamanho mínimo

caracteres especiais

proibir senhas da wordlist

5. Monitoramento de logs

Detecção precoce de ataques.

6. Segmentação de rede

Impedir ataques laterais.
