# Atividade 5 – Configurações Básicas de Switches em Rede Hierárquica

## Descrição

Este repositório apresenta a continuação da prática de simulação de um ambiente de rede hierárquico desenvolvida no Cisco Packet Tracer.

Nesta atividade foram realizadas as configurações básicas de todos os switches da topologia, contemplando os equipamentos das camadas de **Core**, **Distribuição** e **Acesso (Edge)**.

## Objetivo

Realizar as configurações básicas solicitadas em todos os switches da rede:

- hostname;
- autenticação para acesso via console;
- autenticação para acesso ao modo privilegiado;
- criptografia de senhas;
- banner de aviso.

## Topologia

Adicione aqui a imagem da topologia completa da rede.

![Topologia da rede](capturas/01-topologia.png)

## Switches configurados

A topologia possui oito switches:

| Camada | Equipamentos |
| --- | --- |
| Core | SW-CORE-01 e SW-CORE-02 |
| Distribuição | SW-DIST-01 e SW-DIST-02 |
| Edge | SW-EDGE-01, SW-EDGE-02, SW-EDGE-03 e SW-EDGE-04 |

## Configurações realizadas

O padrão abaixo foi aplicado aos oito switches, alterando apenas o `hostname` de acordo com cada equipamento.

```cisco
enable
configure terminal

hostname SW-CORE-01

enable secret class
service password-encryption

line console 0
 password cisco
 login
exit

banner motd #ACESSO RESTRITO - SOMENTE USUARIOS AUTORIZADOS#

end
copy running-config startup-config
```

### Hostname

Cada equipamento recebeu um nome correspondente à sua função e posição na topologia.

```cisco
hostname SW-CORE-01
```

### Autenticação via console

Foi configurada uma senha para impedir acesso não autenticado ao console do equipamento.

```cisco
line console 0
 password cisco
 login
```

### Acesso ao modo privilegiado

O comando `enable secret` foi utilizado para proteger o acesso ao modo EXEC privilegiado.

```cisco
enable secret class
```

### Criptografia de senhas

Foi habilitada a criptografia das senhas armazenadas na configuração.

```cisco
service password-encryption
```

### Banner

Foi configurado um banner de aviso para os usuários que acessarem os equipamentos.

```cisco
banner motd #ACESSO RESTRITO - SOMENTE USUARIOS AUTORIZADOS#
```

## Verificação

As configurações foram verificadas por meio do comando:

```cisco
show running-config
```

Exemplo das evidências encontradas:

```text
service password-encryption
hostname SW-CORE-01
enable secret 5 ...

banner motd ^CACESSO RESTRITO - SOMENTE USUARIOS AUTORIZADOS^C

line con 0
 password 7 ...
 login
```

Após a configuração, o acesso ao console solicita autenticação e o comando `enable` solicita a senha do modo privilegiado.

## Evidências das configurações

Abaixo estão os espaços destinados às capturas de tela de cada switch. Para que as imagens apareçam automaticamente no README, coloque os arquivos dentro da pasta `capturas` utilizando exatamente os nomes indicados.

### SW-CORE-01

Configuração do SW-CORE-01 <img width="1920" height="1032" alt="Captura de tela 2026-10-06 163836" src="https://github.com/user-attachments/assets/138a4869-f227-4d56-8c82-7489daf86d86" />

### SW-CORE-02

Configuração do SW-CORE-02 <img width="1920" height="1032" alt="Captura de tela 2026-10-06 164140" src="https://github.com/user-attachments/assets/c97ccadc-9f5c-4e20-a0c5-17fd1dbe01e0" />

### SW-DIST-01

Configuração do SW-DIST-01 <img width="1920" height="1032" alt="Captura de tela 2026-10-06 170410" src="https://github.com/user-attachments/assets/9d1e0406-520c-4d83-a407-fc108b4869ed" />

### SW-DIST-02

Configuração do SW-DIST-02 <img width="1920" height="1032" alt="Captura de tela 2026-10-06 170621" src="https://github.com/user-attachments/assets/d4234d95-98af-47d6-8592-fd0416b1ced6" />

### SW-EDGE-01

Configuração do SW-EDGE-01 <img width="1920" height="1032" alt="Captura de tela 2026-10-06 171911" src="https://github.com/user-attachments/assets/797fd3ea-7fd1-44c4-b478-33254408d004" /> <img width="1920" height="1032" alt="Captura de tela 2026-10-06 171919" src="https://github.com/user-attachments/assets/dd3c2aab-803e-4464-85fd-65de769c3190" />


### SW-EDGE-02

Configuração do SW-EDGE-02 <img width="1920" height="1032" alt="Captura de tela 2026-10-06 172043" src="https://github.com/user-attachments/assets/366daada-52bb-4909-891b-3407ef1b2408" /> <img width="1920" height="1032" alt="Captura de tela 2026-10-06 172049" src="https://github.com/user-attachments/assets/5b6f0c34-8c1c-4977-8d37-cbec13ba2f28" />


### SW-EDGE-03

Configuração do SW-EDGE-03 <img width="1920" height="1032" alt="Captura de tela 2026-10-06 172146" src="https://github.com/user-attachments/assets/daa22a49-f012-4511-9144-c39d6eaec5c5" /> <img width="1920" height="1032" alt="Captura de tela 2026-10-06 172142" src="https://github.com/user-attachments/assets/c6eb4872-6970-444e-9365-a4a6de5faa52" />


### SW-EDGE-04

Configuração do SW-EDGE-04 <img width="1920" height="1032" alt="Captura de tela 2026-10-06 172228" src="https://github.com/user-attachments/assets/8ac0a155-2e92-4f48-9f02-db732b35d971" /> <img width="1920" height="1032" alt="Captura de tela 2026-10-06 172224" src="https://github.com/user-attachments/assets/10a8ca41-9189-4267-b5c7-b03f17d216eb" />


## Salvamento das configurações

Para manter as configurações após a reinicialização dos equipamentos foi utilizado:

```cisco
copy running-config startup-config
```
