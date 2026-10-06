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

## Salvamento das configurações

Para manter as configurações após a reinicialização dos equipamentos foi utilizado:

```cisco
copy running-config startup-config
```

## Evidências

A pasta `capturas` pode ser utilizada para armazenar os prints de comprovação da atividade, incluindo a topologia e as saídas do `show running-config` dos switches.

## Estrutura sugerida

```text
atividade-5-rede-hierarquica/
├── README.md
├── configuracoes.txt
├── capturas/
│   └── README.md
└── atividade-5-rede-hierarquica.pkt
```
