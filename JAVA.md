<h1><p align="center"> Execute .jar com 2 clicks <p></h1>

# Como executar um arquivo java com dois?

Cansado de executar arquivos .jar no terminal?, então siga esses passos para resolver esse problema!

É simples primeiro basta que você crie um arquivo chamado java.desktop em /usr/share/Applications da seguinte forma:
 
 > No terminal digite:
 ~~~
 sudo nano /usr/share/applications/java.dektop
 ~~~

Nota: O terminal vai ficar um pouco diferente após o comando acima.

Após ter executado o comando acima, copie o código abaixo, e cole no arquivo java.desktop que você abriu no terminal clicando com o botão direito e em colar no terminal!, se abrir alguma janela quando você clicar com o botão direito e colar, confirme a operação.

 ~~~
 [Desktop Entry]
 
 Name=Java Launcher 
 
 Comment=Java Application Launcher
 
 Exec=/usr/bin/java -jar %f
 
 Icon=java
 
 Terminal=false
 
 Type=Application
 
 NoDisplay=true
 
 Categories=Utility
 
 MimeType=application/x-java-archive; 
 ~~~

Para sair da interface do nano no terminal você pressiona "Ctrl + x" em seguida a tecla "s" para salvar e a tecla "Enter" para confirmar.

Após você ter criado o arquivo e colado o conteúdo acima você deverá navegar até o arquivo java aonde você dará todas as permissãoes de leitura, escrita e gravação da seguinte maneira:

Primeiro digite.

 > sudo touch /usr/share/applications/java.dektop

Depois digite o comando a seguir que irá dar as permissões que o nosso arquivo prescisa.

 > sudo chmod 777 /usr/share/applications/java.dektop

Agora você irá navegar em Arquivos de Sistemas até o arquivo que você criou, mas o nome dele vai estar como 'Java Launcher' que foi definido no código que você colou no terminal. Click com o botão direito, em propiedades, vá em 'Launcher' localizada na barra da janela depois em 'Opções' e em seguida marque a caixa 'usar notificações de inicialização'.
                                       
Pronto agora você pode executar qualquer arquivo .jar com dois click

OBS: Nano é um editor de texto que abre no terminal.

Método testado em Manjaro GNU/Linux interface gráfica XFCE: 22/10/2020
 