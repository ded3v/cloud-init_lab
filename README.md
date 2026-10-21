# Laboratório Cloud-Init

Atividade prática da turma 5 de DevOps da Aponti, utilizando Cloud-Init para automatizar a configuração de uma máquina virtual Ubuntu.

## Objetivo

Configurar uma VM utilizando Vagrant e Cloud-Init, automatizando a criação de usuário, instalação de pacotes e execução de serviços.

## Configurações realizadas

- Atualização da lista de pacotes do Ubuntu.
- Criação do usuário `meu-usuario`, com acesso sudo sem senha.
- Configuração do acesso SSH por chave pública gerada no Windows.
- Instalação do Docker e Nginx.
- Criação de uma página HTML personalizada através do `write_files`.
- Inicialização dos serviços utilizando `runcmd`.
- Mensagem final após o provisionamento.

## Como executar

Com o Vagrant e VirtualBox instalados, executar na pasta do projeto:

```bash
vagrant up
vagrant reload
vagrant ssh
```

## Verificações

Dentro da VM, foram utilizados os seguintes comandos para verificar as configurações:

```bash
sudo cloud-init status --wait --long
id meu-usuario
groups meu-usuario
systemctl status docker
systemctl status nginx
sudo docker ps
```

Também foi realizado o teste de acesso SSH utilizando a chave gerada no Windows.

A página personalizada do Nginx pode ser acessada pelo navegador através do endereço:

**http://localhost:8080**

## Observações

O arquivo `user-data` contém as configurações aplicadas pelo Cloud-Init. A chave privada SSH foi mantida apenas no computador local, sendo utilizada somente a chave pública na configuração da VM.

O laboratório ajudou a entender como automatizar a preparação de um ambiente Linux, evitando a necessidade de configurar cada serviço manualmente.