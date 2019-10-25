## O que é o Censys
Censys que foi criado em 2015 na universidade de Michigan , ele nos auxilia na busca de dispositivos , redes e infraestruturas.

![Censys 1](https://i.imgur.com/4OHE97L.png)

**45 das Fortune 500 usa dados do Censys**.
> Fortune 500 é uma revista que lista as 500 maiores corporações em todo o mundo.

![Censys 2](https://i.imgur.com/adbIJGo.png)

## Como podemos usar o Censys
Agora com a ajuda desse mecanismo de busca podemos encontrar facilmente informações como
- Latitude
- Longitude
- País
- Rota
- Portas abertas e protocolos
- Podemos ver o tipo de servidor usado
- Status do teste
- Titulo do IP usado
- Nome da rede  de sites e IPS.
- Identifica

![Censys 3](https://i.imgur.com/tmahhSn.png)

E podemos obter essas informações sem estar logado no censys , podemos criar uma conta free e já começar a usar.

## Já logado no sistema
Logado no sistema podemos já realizar consultas de **whois** , podemos obter informações nos formatos:
- Table
- JSON
- Raw WHOIS

Exemplo usando o site da globo.com:
```sh
https://censys.io/ipv4/186.192.90.5/whois
```

Além disso podemos encontrar:
- Informações básicas do domínio
- Informações de contato
- Informações sobre a rede
- Informações técnicas
- Informações administrativas
- Contato para relatar algum abuso

O que podemos fazer com essas informações ?
- Obter emails
- Obter range de rede e descobrir outros servidores
- CIDR , podemos encontrar outros servidores na mesma rede

## Buscando informações sobre sites
Podemos usar a opção de site que fica disponível em:
```sh
https://censys.io/domain?q=globo.com
```

Ao pesquisar temos vários resultados de sites , o primeiro foi o que nos buscamos e além disso temos as seguintes informações:
- Protocolos
- Tags
- Resultados
- Report
- Documentação

![Censys 4](https://i.imgur.com/YIk4W6s.png)

Ao selecionar o nosso site temos informações como
- Alexa rank
- Protocolos disponível
- Informações sobre as portas que estão abertas
- Qual o servidor usado
- Titilo do site
- Informações sobre certificados do HTTPS
- Banner do serviço
- Configurações de DNS

Veja usando como exemplo o site da globo.com
![Censys 5](https://i.imgur.com/yGrwWOl.png)

Além disso essas informações podem ser nos formatos
- JSON
- Tabelas

## Buscando informações sobre certificados
Podemos ver informações sobre certificados usando o seguinte link
```sh
https://censys.io/certificates?q=globo.com
```

![Censys 6](https://i.imgur.com/LmMFHLl.png)

## Censys API
Podemos usar o poder do Censys usando a API dele , dessa forma podemos criar ferramentas e até inserir em outros projetos.

Podemos ver a documentação em
```sh
https://censys.io/api
```

> Precisamos criar uma conta no Censys , com ela temos acesso a informações da conta , **API ID** , **Secret** , limites da conta.

## Criando conta
Podemos criar uma conta Free no seguinte link
```sh
https://censys.io/register
```

> Pode ser necessário validar a conta no seu email , caso não queira usar o seu email é possível usar **https://10minutemail.net/?lang=pt-br**.

### Informações de conta
Depois de criar uma conta podemos ir no link a baixo e ver informações da conta.
```sh
https://censys.io/account
```

Podemos encontrar informações como
- Nome
- Email
- Login
- Afiliação
- Telefone
- Mudar a senha
- Porcentagem de uso do plano
- Quando vai ser reiniciado o plano
- Tipo de plano
- Informações sobre resultados

### Informações sobre API
```sh
https://censys.io/account/api
```

No link acima é possível obter as credenciais para o uso da API e além disso podemos encontrar
- API ID
- Secret
- Observar limites da conta
- Resetar as chaves da API

### Formas de pagamento
Temos uma conta free , porem podemos pagar uma conta Pro ou até Enterprise.
```sh
https://censys.io/account/billing
```

## Censys API + Python
É possivel usar a API do censys com o Python.

Anteriormente já tivemos acesso as credenciais necessárias , agora vou mostrar a documentação do github.
```sh
https://github.com/censys/censys-python
```

E tem até alguns exemplos de uso.

### Projeto gelim/censys
Podemos usar um projeto bem interessante que está disponível no Github , ele nos auxilia para o uso da API do Censys com a linguagem python e ainda disponibiliza uma documentação.
```sh
https://github.com/gelim/censys
```

## Mão na massa com o - assertivasolucoes.com.br
Com as consultas que fizemos anteriormente conseguimos obter diversos subdominios com o **SharingMyIP**,mas será que foram todos ?

### Consulta de certificados com o Censys
Graças aos certificados conseguimos verificar se tem mais subdominios criados, graças aos certificados que podemos analisar com o Censys.

```sh
https://censys.io/certificates?q=assertivasolucoes.com.br
```

Analisando as respostas, temos aproximadamente 6 paginas e com sorte temos a possibilidade de encontrar mais subdominios.

Vou iniciar a busca da ultima pagina até a primeira e dessa forma vendo serviços que possam não funcionar mais.

### Busca de subdominios usando certificado
Foi criado um certificado para o site **pages.rdstation.com.br**, mas tambem foi reconhecido como **online.assertivasolucoes.com.br**.

Foi encontrado o subdominio.
- http://api.assertivasolucoes.com.br/

Tambem conseguimos encontrar o possivel subdominio de testes **httpstest.assertivasolucoes.com.br**.

Foi possivel achar o subdominio chamada **basecerta.assertivasolucoes.com.br**.

Um outro possivel subdominio de testes **managersmstest.assertivasolucoes.com.br**.

Foi encontrado um subdominio suspeito, que não responde, mas que aparentemente está online.
- batman.assertivasolucoes.com.br

Um sudominio de relatorios
- relatorio.assertivasolucoes.com.br

Outro subdominio interessante é o
- app.assertivasolucoes.com.br

Outro subominio que não responde, mas que está online é o
- provider.assertivasolucoes.com.br

Um possivel subdominio para gerenciar SMS
- managersms.assertivasolucoes.com.br

Um subdominio que pode nos retornar uma possivel API de feedback.
- apifeedback.assertivasolucoes.com.br

Um subdominio que aparentemente tem conexão com o S3 da amazon
- front.assertivasolucoes.com.br

Um subdominio interessante chamado **datajus**.
- datajus.assertivasolucoes.com.br

Um possivel subdominio de testes
- services-test.assertivasolucoes.com.br

Um subdominio com possiveis arquivos
- file.assertivasolucoes.com.br

Um subdominio informando **chave de usuario não informada**.
- observer.assertivasolucoes.com.br

Um possivel servidor para acessar bigdata.
- managerbigdata.assertivasolucoes.com.br
- managerbigdata-test.assertivasolucoes.com.br

Outro subdominio interessante
- provider-test.assertivasolucoes.com.br

Um possivel servidor de testes
- auth-test.assertivasolucoes.com.br

Outro possivel servidor de testes
- managerprovider-test.assertivasolucoes.com.br

Uma possivel API
- chamado-api.assertivasolucoes.com.br

Outro subdominio
- crl2.assertivasolucoes.com.br


- managerprovider.assertivasolucoes.com.br
- cadastro.assertivasolucoes.com.br
- wsscraper.assertivasolucoes.com.br
- provider.assertivasolucoes.com.br
- services.assertivasolucoes.com.br
- bigdata.assertivasolucoes.com.br
- wcs.assertivasolucoes.com.br
- managerprovider.assertivasolucoes.com.br
- managersociall.assertivasolucoes.com.br
- tokenid.assertivasolucoes.com.br
- managerbigdata.assertivasolucoes.com.br
- wsscraper.assertivasolucoes.com.br
- blog.assertivasolucoes.com.br
- spm.assertivasolucoes.com.br

Até conseguimos encontrar outro dominio que podemos usar nos testes
- assertiva.info

Alem de conseguimos achar outros 2 dominios
- solucoesassertiva.com
