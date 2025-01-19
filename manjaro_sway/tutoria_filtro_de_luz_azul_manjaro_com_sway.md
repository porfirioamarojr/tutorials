# Blue Light Filter
O filtro de luz azul é algo muito almejaado por muito programadores e pessoas
que possuem algum problema relacionado a sensibilizade deste canal. Além das
pessoas que utilizam essa coloração por causar um conforto nos olhos.

## Revisões
| Revisor | Data de Revisão |
| :----: | ----: |
| [Arthur Gorgônio](https://github.com/Arthurgorgonio) | 19/01/2025 |
| [Amaro Júnior](https://github.com/porfirioamarojr) | 08/04/2023 |

---

## Configurando

Primeiro instale o gammastep com
```sh
sudo pacman -S gammastep
```

Para ver se o `gammastep` está funcionando corretamente utilize com a opção `-V`
para testar isso. Agora que ele está instalado, pode ser utilizada a opção `-h`
para apresentar o help.

Mas antes que você prossiga, é necessário que você saiba a sua geolocalização.
Essa configuração pode ser feita manualmente por meio da api
[iplocation](https://www.iplocation.net/myip) ou utilizando a localização
automática do _geoclue_.

## Adicionando às configurações do SwayWM (i3WM)
De posse disso, só falta iniciar o `gammastep` juntamente com o sistema
operacional ou a sua interface gráfica. Neste tutorial será demonstrado essa
alteração no [swaywm](https://swaywm.org/), alterando o arquivo de configuração
do usuário, `/.config/sway/config`, agora dentro desse arquivo adicione a
seguinte linha:
```
exec gammastep -l -6.:-37 -t 6500:4500 -g 1.0 -b 1.0:0.6 -m wayland
```
Após isso, salve o arquivo e recarregue a interface. Agora o seu sistema irá
iniciar o serviço automaticamente.

## Configuração por meio de atalhos
Nem sempre queremos que a cor altere por estarmos apresentando a tela ou fazendo
alguma tarefa específica. Outras vezes queremos que o tom na cor quente fique
mais brando. Para contornar isso, vamos configurar um atalho no SwayWM para que
seja possível alterar o valor do `gammastep` sem a necessidade de ficar abrindo
o arquivo de configuração todas as vezes e atualizar o valor.

Neste sentido, vamos assumir as seguintes faixas:
- 6500 Diurno
- 5500 Transição
- 4500 Noturno

De posse do seu arquivo de configuração, adicione as seguintes linhas no arquivo:
```
set $mode_temp GammaStep: (d)ay, (t)ransition, (n)ight ou (k)ill
set $gamma gammastep
set $kill_gamma killall gammastep
bindsym $mod+t mode '$mode_temp'
exec $gamma -O 6500
mode '$mode_temp' {
  bindsym d exec $kill_gamma && $gamma -O 6500, mode 'default'
  bindsym t exec $kill_gamma && $gamma -O 5500, mode 'default'
  bindsym n exec $kill_gamma && $gamma -O 4500, mode 'default'
  bindsym k exec $kill_gamma, mode 'default'
  bindsym Escape mode 'default'
}
```

Agora, salve e recarregue o arquivo da interface, com isso será possível
alternar entre as temperaturas de modo simplificado.

> ***Importante**: Caso seja a primeira vez que você está utilizando o `gammastep`, talvez seja necessário reiniciar toda a interface do Sway ou iniciar o serviço pelo terminal com `gammastep -O 6500 &`. Nos próximos logins, o comando `exec $gamma -O 6500` já irá garantir que o gammastep esteja em execução no sistema.*


## Referências
- https://man.archlinux.org/man/extra/gammastep/gammastep.1.en
- https://www.mankier.com/5/geoclue#Synopsis
- https://github.com/Madic-/Sway-DE/issues/7
