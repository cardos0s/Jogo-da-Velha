# Jogo-da-Velha
 **Jogo da Velha Remoto – Pygame & Sockets**

Este projeto é uma robusta implementação do clássico Jogo da Velha (Tic-Tac-Toe), projetado para partidas multiplayer remotas através de comunicação em rede TCP/IP Sockets.

A interface gráfica interativa é construída com a biblioteca Pygame, proporcionando uma experiência visual agradável e responsiva. Além da jogabilidade em tempo real, o sistema incorpora funcionalidades essenciais como cadastro e login de usuários, chat integrado entre os jogadores e o registro completo de todas as partidas e jogadas em um banco de dados SQLite.

Cada partida é iniciada em uma sessão independente, permitindo que o servidor seja configurado com portas dinâmicas para gerenciar múltiplas sessões.

---

 Funcionalidades

- Interface (GUI): Pygame Interativo, interface gráfica rica e responsiva para uma experiência de jogo agradável.
- Comunicação de baixo nível (Cliente-Servidor) para sincronizar jogadas e mensagens em tempo real. 
- Banco de dados leve e local para gerenciar credenciais de usuários e o histórico detalhado das jogadas. 
- Sistema de autenticação para identificação dos jogadores e rastreamento de seus históricos. 
- Canal de comunicação de texto em tempo real entre os dois jogadores durante a partida.
- Opção para iniciar imediatamente uma nova partida ao final de um jogo, mantendo a conexão ativa. 

---

🛠️ Tecnologias Utilizadas
O projeto foi desenvolvido inteiramente em Python, aproveitando o poder das seguintes bibliotecas:

Python 3.10+: Linguagem de desenvolvimento principal.

Pygame: Utilizada para a criação da interface gráfica (GUI), renderização do tabuleiro e manipulação de eventos.

Socket: Módulo padrão do Python para a comunicação em rede (TCP/IP), essencial para o tráfego de dados entre Cliente e Servidor.

SQLite3: Módulo padrão para a persistência de dados (login/senha e registro de jogadas).

threading: Utilizado para gerenciar a concorrência na comunicação, permitindo que o programa receba jogadas e mensagens do chat sem travar a GUI.

---

Como Executar o Projeto
Siga os passos abaixo para configurar e iniciar o ambiente de jogo.

---
🧩 Pré-requisitos:
Certifique-se de que o Python 3.10 ou superior está instalado em seu sistema operacional.

🕹️ Instalação do Pygame:
Abra seu terminal ou prompt de comando e instale a biblioteca Pygame:
pip install pygame

⚙️ Execução em Ordem
A execução do sistema deve seguir a ordem correta de inicialização dos módulos de conexão e da interface.

1. Configuração Inicial e Servidor

O primeiro jogador a iniciar atuará como o Servidor.
python servidor.py
Inicia o Servidor: Após o login, execute o servidor. Ele ficará em estado de espera, aguardando a conexão do Cliente.

2. Conexão do Cliente (Segundo Jogador)

O segundo jogador se conecta ao servidor para iniciar o jogo.

Comando	Descrição
python login.py	Cadastro/Login: O Cliente deve se cadastrar ou autenticar para ser identificado na partida.
python cliente_gui.py	Inicia a GUI do Jogo: O Cliente deve rodar este script e, na interface, inserir o IP da máquina do Servidor e a Porta utilizada para se conectar.

💡 Observação:
Ao final de uma partida, o sistema fornece as opções:

🔁 Nova Partida – reutiliza a conexão existente.

❌ Sair – encerra a conexão e fecha o jogo.

🔐 Banco de Dados (SQLite)

O projeto utiliza o SQLite para gerenciar dados persistentes, armazenados no arquivo banco.db na raiz do projeto.

Estrutura das Tabelas
Tabela	Conteúdo	Finalidade
USUARIOS	Nome de Usuário e Senha (Hash)	Gerencia as credenciais de login e autenticação dos jogadores.
PARTIDAS	ID, Jogadores, Vencedor, Data	Armazena o registro de cada partida realizada no sistema.
JOGADAS	ID da Partida, Jogador, Posição, Timestamp	Armazena detalhadamente a sequência de movimentos em cada jogo — ideal para auditoria ou replay.

✨ Dica:
Caso o arquivo banco.db seja removido, ele será recriado automaticamente ao iniciar o jogo, garantindo o funcionamento do sistema.
