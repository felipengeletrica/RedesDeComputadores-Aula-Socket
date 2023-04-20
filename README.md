<h1>Conexões de servidores TCP e UDP</h1>

-Abrimos o terminal no diretório do Servidor em python e rodamos os seguintes comandos:
TCP ->
	-python3 Server-TCP-Multicliente.py para conectar ao SV.
	
	![](/img/tcp-Captura%20de%20tela%20de%202023-04-13%2018-36-11.png)
	
	-python3 netcat -v 127.0.0.1 65432 para usar como cliente e enviar mensagens para o SV.
	
	<img src="https://github.com/felipengeletrica/RedesDeComputadores-Aula-Socket/blob/cado/img/TCP-Captura%20de%20tela%20de%202023-04-13%2018-36-08.png"

UDP ->
	-python3 Server-UDP-Simple.py para conectar ao SV.
	
	<img src="https://github.com/felipengeletrica/RedesDeComputadores-Aula-Socket/blob/cado/img/udp-Captura%20de%20tela%20de%202023-04-13%2018-31-18.png"
	
	-python3 netcat -u 127.0.0.1 65431 para usar como cliente e enviar mensagens para o SV.
	
	<img src="https://github.com/felipengeletrica/RedesDeComputadores-Aula-Socket/blob/cado/img/udp-Captura%20de%20tela%20de%202023-04-13%2018-30-32.png"
	
-Utilizamos o comando nmap no terminal:

	-nmap -sU -p65431 localhost para identificar se a porta UDP estava aberta
 	-nmap -p65432 localhost para identificar se a porta TCP estava aberta
	
	<img src="https://github.com/felipengeletrica/RedesDeComputadores-Aula-Socket/blob/cado/img/NMAP-UDP-TCP-Captura%20de%20tela%20de%202023-04-13%2018-51-36.png"

<h2>Instruções para uso do Wireshark para filtrar dados provenientes de conexões UDP e TCP</h2>

-Abrimos terminal e rodamos o comando "sudo wireshark" para executar o programa para escutarmos as portas 65432/TCP e 65431/UDP com os filtros:

	-TCP.PORT==65432
	
	<img src="https://github.com/felipengeletrica/RedesDeComputadores-Aula-Socket/blob/cado/img/UDP-WIRESHARK-Captura%20de%20tela%20de%202023-04-13%2018-34-20.png"
	
	-UDP.PORT==65431
	
	<img src="https://github.com/felipengeletrica/RedesDeComputadores-Aula-Socket/blob/cado/img/TCP-Captura%20de%20tela%20de%202023-04-13%2018-36-27.png"

-Filtrando dados de conexões TCP

	Abra o Wireshark e inicie a captura de tráfego na interface de rede desejada.
	Digite "tcp" na barra de filtro e pressione Enter.
	Você verá agora apenas os pacotes TCP que foram capturados.
	Identifique a conexão de 3 vias (three-way) olhando os pacotes de SYN, SYN-ACK e ACK.
	O pacote SYN é enviado pelo cliente para iniciar a conexão.
	O pacote SYN-ACK é enviado pelo servidor em resposta ao SYN para confirmar que está aberto para a conexão.
	O pacote ACK é enviado pelo cliente em resposta ao SYN-ACK para confirmar que a conexão está estabelecida.
	O estado de cada uma dessas etapas é:
	SYN: Estado "SYN_SENT"
	SYN-ACK: Estado "SYN_RCVD"
	ACK: Estado "ESTABLISHED"

-Filtrando dados de conexões UDP

	Abra o Wireshark e inicie a captura de tráfego na interface de rede desejada.
	Digite "udp" na barra de filtro e pressione Enter.
	Você verá agora apenas os pacotes UDP que foram capturados.
	Ao contrário do TCP, o protocolo UDP é "connectionless", o que significa que não há conexão estabelecida antes de enviar dados. Cada pacote é enviado independentemente.

-Filtros de TCP e UDP

	Para filtrar apenas os pacotes de um endereço IP específico, use "ip.addr == [endereço IP]".
	Para filtrar apenas os pacotes de uma porta TCP ou UDP específica, use "tcp.port == [número da porta]" ou "udp.port == [número da porta]", respectivamente.

-Usando o programa nmap para verificar a porta aberta

	Certifique-se de ter o nmap instalado em seu sistema operacional.
	Abra o terminal e digite "nmap [endereço IP]" e pressione Enter.
	Nmap irá mostrar as portas abertas no endereço IP fornecido.

-Camadas OSI usadas em TCP e UDP

	TCP utiliza as camadas 4 (Transporte), 3 (Rede) e 2 (Enlace de dados) do modelo OSI.
	UDP utiliza apenas as camadas 4 (Transporte) e 3 (Rede) do modelo OSI.

-Conclusão

	O Wireshark é uma ferramenta poderosa para a análise de tráfego de rede e pode ser útil em várias situações, como solucionar problemas de rede, monitorar a segurança de rede e muito mais. É importante ter conhecimento básico dos protocolos de rede TCP e UDP para entender melhor as informações exibidas pelo Wireshark. Com os filtros adequados, podemos filtrar os pacotes de rede que são relevantes para a análise. O programa nmap também é útil para verificar as portas abertas em um determinado endereço IP. Além disso, é importante entender as camadas do modelo OSI utilizadas pelos protocolos TCP e UDP para entender como eles são             implementados na rede.
