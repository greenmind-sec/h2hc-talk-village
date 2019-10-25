
## Antes de começar
Vamos imaginar que precisamos obter o máximo de informações sobre um domínio/subdomínio , como podemos fazer isso sem interagir diretamente com o alvo e sem realizar um ataque ao DNS ?

Podemos saber quais sites estão compartilhando o mesmo IP usando o SharingMyIP.

Atualmente muitas empresas usam hosts compartilhados , para economizar e simplicidade.

Além do preço baixo veja alguns benefícios:
- Segurança
- Disponibilidade
- Facilidade

## O que é Sharingmyip
SharingMyIP é um site onde podemos realizar consultas em um determinado domínio/subdomínio , dessa forma podemos saber possíveis sites que compartilham o mesmo IP que o site testado e assim podemos encontrar subdomínios , IPS e até sites que não imaginávamos que fizesse parte.

![SharingMyIP](https://i.imgur.com/CWJ7PCs.png)

## Realizando primeiro teste (Globo.com)
Vamos realizar o primeiro teste usando o domínio **globo.com** , podemos ver a imagem a baixo seguido dos resultados:
- Sites no mesmo IP
- DNS para globo.com
- Mail server
- Entradas de DNS relacionadas

![SharingMyIP](https://i.imgur.com/J5wpWsp.png)

Na parte site com o mesmo IP temos uma lista com alguns sites , veja
```sh
globo.com
blog.sexyhot.com.br
www.globosat.tv
globosat.tv
www.gshow.globo.com
ftp.neymaroficial.com
dev.neymaroficial.com
www.globoplay.globo.com
www.epoca.globo.com
bigbrotherbrasil.com
www.edglobo.globo.com
www.bigbrotherbrasil.com
www.vogue.globo.com
www.revistaglamour.globo.com
www.dev.globo.com
```

Alem disso podemos ver informações como name servers e até mail server.
```sh
globo.com name server ns04.globo.com.
globo.com name server ns01.globo.com.
globo.com name server ns02.globo.com.
globo.com name server ns03.globo.com.
globo.com mail is handled by 20 mx3.globo.locaweb.com.br.
globo.com mail is handled by 5 mx.globo.locaweb.com.br.
globo.com mail is handled by 10 mx2.globo.locaweb.com.br.
globo.com has address 186.192.90.5
globo.com has no AAAA record
```

Agora na aba entradas relacionadas de DNS podemos encontrar outros sites , com IPS diferentes e subdomínios diferentes.
```sh
www.globo.com - 186.192.82.163
www2.globo.com - 201.7.182.20
mail.globo.com - 74.125.29.121
smtp.globo.com - 64.97.152.33
pop3.globo.com - 64.97.152.33
ns1.globo.com - 201.7.180.171
ns2.globo.com - 64.151.87.25
mx.globo.com - 64.97.153.5
ra.globo.com - 201.7.180.198
webmail.globo.com - 186.192.90.5 <- mesmo IP
www3.globo.com - 186.192.82.8
ftp.globo.com - 201.7.184.43
ns3.globo.com - 186.192.89.5
stat.globo.com - 186.192.90.5
intranet.globo.com - 201.7.176.56
extranet.globo.com - 201.7.176.56
upload.globo.com - 201.7.184.47
news.globo.com - 186.192.90.5 <- mesmo IP
dev.globo.com - 186.192.90.5 <- mesmo IP
demo.globo.com - 201.7.180.200
blog.globo.com - 186.192.82.189
ad.globo.com - 63.140.35.208
ads.globo.com - 201.7.176.12
portal.globo.com - 186.192.82.163
labs.globo.com - 107.22.218.2
forum.globo.com - 186.192.90.5 <- mesmo IP
```

Sem interagir com os servidores da globo já sabemos:
- Possíveis servidores de email
- 14 sites com o mesmo IP
- 4 servidores de DNS usados
- 26 novos subdomínios

## Desenvolvendo ferramenta usando Python
Podemos criar um script rápido para nos ajudar nos testes , veja o exemplo:
```python
import requests
from bs4 import BeautifulSoup

url = "https://globo.com"
ip = "10.10.10.10"
rec_site = requests.get('http://sharingmyip.com/?site='+url)
#print(rec_site.text)

soup = BeautifulSoup(rec_site.text,'html.parser')
#print("Sites para o IP:\n"+soup.textarea.string)

'''
for i in range(len(soup.textarea)):
    print(soup.textarea.string)
'''
qt_textarea = len(soup('textarea'))
msg_list = ['Site (s) neste endereço','DNS para ','Entradas de DNS relacionadas para']
#for msg in range(msg_list):
for i in range(qt_textarea):
    if (i == 0):
        print(msg_list[0]+" "+ip)
        print(soup('textarea')[i].string)
    elif i == 1:
        print(msg_list[1]+" "+url)
        print(soup('textarea')[i].string)
    elif i == 2:
        print(msg_list[2]+" "+url)
        print(soup('textarea')[i].string)
    else:
        print("Aconteceu algo errado :D")
```

Temos agora o mesmo resultado que o site , a diferença que temos essa informação com um script em python e que nós desenvolvemos.

## Mão na massa com o site assertivasolucoes.com.br
Vamos iniciar os testes passando o nome do nosso alvo, vamos ver qual o IP usado e possiveis subdominios.

### Qual o IP do alvo ?
Ao testar podemos ver que foi retornado o IP **54.175.150.137**.
```sh
www.assertivasolucoes.com.br
assertivasolucoes.com.br
```

### Consultas DNS
```sh
assertivasolucoes.com.br name server ns-1441.awsdns-52.org.
assertivasolucoes.com.br name server ns-1795.awsdns-32.co.uk.
assertivasolucoes.com.br name server ns-5.awsdns-00.com.
assertivasolucoes.com.br name server ns-694.awsdns-22.net.
assertivasolucoes.com.br mail is handled by 10 aspmx.l.google.com.
assertivasolucoes.com.br mail is handled by 20 alt1.aspmx.l.google.com.
assertivasolucoes.com.br mail is handled by 20 alt2.aspmx.l.google.com.
assertivasolucoes.com.br mail is handled by 30 aspmx2.googlemail.com.
assertivasolucoes.com.br mail is handled by 30 aspmx3.googlemail.com.
assertivasolucoes.com.br has address 52.2.38.123
assertivasolucoes.com.br has address 54.175.150.137
assertivasolucoes.com.br has no AAAA record
```

### Entradas DNS relacionadas
Os subdominios encontrados foram os
```sh
www.assertivasolucoes.com.br - 54.175.150.137
mail.assertivasolucoes.com.br - 172.217.3.115
pop.assertivasolucoes.com.br - 172.217.3.115
pop3.assertivasolucoes.com.br - 172.217.3.115
ns1.assertivasolucoes.com.br - 189.126.108.2
ns2.assertivasolucoes.com.br - 201.76.40.2
database.assertivasolucoes.com.br - 172.20.30.46
webmail.assertivasolucoes.com.br - 172.217.3.115
ftp.assertivasolucoes.com.br - 52.7.217.236
auth.assertivasolucoes.com.br - 107.23.130.137
rh.assertivasolucoes.com.br - 52.217.32.35
ns3.assertivasolucoes.com.br - 187.45.246.2
vpn.assertivasolucoes.com.br - 54.173.153.195
ftp2.assertivasolucoes.com.br - 52.7.217.236
svn.assertivasolucoes.com.br - 54.153.98.144
blog.assertivasolucoes.com.br - 170.82.173.10
wiki.assertivasolucoes.com.br - 54.67.111.236
ad.assertivasolucoes.com.br - 192.175.103.101
portal.assertivasolucoes.com.br - 13.225.190.96
```

### IPS encontrados

Site
- www.assertivasolucoes.com.br - 54.175.150.137

Servidores de e-mail
- mail.assertivasolucoes.com.br - 172.217.3.115
- pop.assertivasolucoes.com.br - 172.217.3.115
- pop3.assertivasolucoes.com.br - 172.217.3.115
- webmail.assertivasolucoes.com.br - 172.217.3.115

Servidores DNS
- ns1.assertivasolucoes.com.br - 189.126.108.2
- ns2.assertivasolucoes.com.br - 201.76.40.2
- ns3.assertivasolucoes.com.br - 187.45.246.2

Possiveis databases
- database.assertivasolucoes.com.br - 172.20.30.46

Servidor FTP
- ftp.assertivasolucoes.com.br - 52.7.217.236
- ftp2.assertivasolucoes.com.br - 52.7.217.236

Possivel serviço de autenticação
- auth.assertivasolucoes.com.br - 107.23.130.137

Subdominio do RH
- rh.assertivasolucoes.com.br - 52.217.32.35

Servidor VPN
- vpn.assertivasolucoes.com.br - 54.173.153.195

Sistema de controle de versão
- svn.assertivasolucoes.com.br - 54.153.98.144

Subdominio blog
- blog.assertivasolucoes.com.br - 170.82.173.10

Podemos encontrar a wiki
- wiki.assertivasolucoes.com.br - 54.67.111.236

Subdominio de portal
- portal.assertivasolucoes.com.br - 13.225.190.96

Um subdominio ad, quem sabe um active diretory ?
- ad.assertivasolucoes.com.br - 192.175.103.101
