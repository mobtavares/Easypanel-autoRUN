
![Logo](https://gespubliconline.com.br/logo.png)


# Easypanel autoRUN

Script de inicialização simples para iniciar o serviço EasyPanel automaticamente ao iniciar o Ubuntu.




## Crie um novo script:

Abra um editor de texto e cole o seguinte código:

```bash
#!/bin/bash

# Verifica se o Docker está instalado
if ! command -v docker &> /dev/null
then
    echo "Docker não encontrado. Certifique-se de que o Docker está instalado."
    exit 1
fi

# Inicia o serviço EasyPanel
echo "Iniciando o serviço EasyPanel..."
docker service update easypanel --force

echo "O serviço EasyPanel foi iniciado com sucesso."
```

## Salve o script:

Salve o script com um nome significativo, como start_easypanel_service.sh.

## Dê permissão de execução ao script:

Abra um terminal, navegue até o diretório onde o script foi salvo e execute o seguinte comando:

```bash
chmod +x start_easypanel_service.sh
```

## Mova o script para o diretório /etc/init.d/ para que seja executado durante a inicialização

```bash
sudo mv start_easypanel_service.sh /etc/init.d/
```

## Adicione o script ao nível de execução padrão para iniciar automaticamente:
```bash
sudo update-rc.d start_easypanel_service.sh defaults
```

ou 

```bash
sudo mv start_easypanel_service.sh /etc/init.d/
```

Agora o serviço EasyPanel será iniciado automaticamente sempre que o Ubuntu for inicializado. Se precisar ajustar ou modificar o script mais tarde, você pode editá-lo novamente usando um editor de texto.

