### Como transformar em um sistema embarcado
o processo é dividido em 3 etapas:
## Primerira etapa:
criar um arquivo chamado kiosk.service
  sudo nano etc/systemd/system/kiosk.service

após isso dentro do arquivo deve-se escrever:
  ```
  [Unit]
  Description=Start <nome da aplicação> Kiosk Mode
  After=graphical.target

  [Service]
  
  Type=simple
  User=<nome do usuário>
  Evironment="DISPLAY=:0
  Evironment="XAUTHORIRY=/home/<nome do usuário>/.Xauthority"
  ExecStart=/usr/bin/sudo -u <nome do usuário> /usr/bin/<nome da aplicação>
  Restart=always

  [Install]
  wantedBy=graphical.target 
  ```

salve o arquivo 

## Segunda Etapa:
criar um script para abrir o kiosk.service:
  sudo nano /usr/local/bin/wait_for_graphics.sh

Ediar o o arquivo: 
  while ! pgrep -u $USER -x "Xorg" > /dev/null && ! pgrep -u $USER -x "X" > /dev/null; do
    sleep 5
  done

  sleep 10

  systemctl restart kiosk.service

Salve o arquivo

transforme-o em um executável:
  sudo chmod +x /usr/local/bin/wait_for_graphics.sh

## Terceira Etapa:
por fim crie uma rotina no crontab
  crontab -e

na ultima linha do arquivo adicione:
  @reboot /usr/local/bin/wait_for_graphics.sh

Salve o arquivo 


Com isso a sua aplicação será forçada a abrir se estiver fechada.
