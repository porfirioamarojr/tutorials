# Blue Light Filter

Primeiro instale o gammastep com ```sudo pacman -S gammastep ```.

Para ver se o gammastep está funcionando corretamente use [esses parametros](https://man.archlinux.org/man/community/gammastep/gammastep.1.en) para testar isso.

Agora você já sabe como funciona o gammastep!

Mas antes que você prossiga você precisa saber a localização da sua maquina manualmente ou utilizando a localização automatica pelo geoclue.

Para isso iremos utilizar a localização manual se, tiver o firefox instalado ótimo, [clique aqui](https://location.services.mozilla.com/v1/geolocate?key=geoclue) e você terá a localização mais aproximada da sua maquina. 

Agora você precisa iniciar o gammastep com seu sistema, para isso você precisa ir até o caminho dos seus arquivos de configuração do swayland, acredito que o caminho pro arquivo é ``` /.config/sway/config ```, agora dentro desse arquivo coloque as seguinte linha:

``` exec gammastep -l -6.2:-36.4 -t 5000:3000 -g 1.0 -b 1.0:1.0 -l manual -m wayland ```

Agora seu sistema irá iniciar o serviço automaticamente.

#

##### Esse tutorial foi construido apartir dos seguintes links:

https://www.mankier.com/5/geoclue#Synopsis
https://github.com/Madic-/Sway-DE/issues/7
https://man.archlinux.org/man/community/gammastep/gammastep.1.en