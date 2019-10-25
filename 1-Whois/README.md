
## Antes de começar
**Whois** ou **quem é?** é um protocolo TCP que funciona por padrão na porta **43** e usamos para consultar informações de um determinado IP ou domínio.

## O que podemos encontrar com o Whois ?
Podemos encontrar informações como
- Nome do domínio
- Quem registrou o domínio
- Quando foi criado
- Até quando é valido
- Servidores DNS
- Pais
- email de contato
- Nome do responsável
- CPF/CNPJ

Alguns sites podem ter configurado para não mostrar informações do proprietário e onde podemos buscar essas informações de forma publica ?

Temos diversos sites , segue dois exemplos
```sh
https://hackertarget.com/whois-lookup/
https://br.godaddy.com/whois
```

Além dos domínios também podemos pesquisar por IPS , dessa forma podemos buscar informações sobre a rede e assim encontrar informações como
- Range de rede
- CIDR
- Organização responsável
- Endereço
- Cidade
- Pais

Podemos testar usando o hackertarget
```sh
https://hackertarget.com/whois-lookup/
```

## Colocando a mão na massa

### Consulta de Whois usando uma URL
Conseguimos saber o nome do resposavel (resposaveis tambem, mas conseguimos evitar que essas informações fiquem disponiveis), e-mail de contato, quando foi criado, vencimento, CPNJ ou até CPF.

Vamos usar o site
```sh
assertivasolucoes.com.br
```

Vamos usar o site e vamos passar a URL que queremos testar
```sh
https://hackertarget.com/whois-lookup/
```

Podemos ver o resultado da consulta
```sh
% Copyright (c) Nic.br
%  The use of the data below is only permitted as described in
%  full by the terms of use at https://registro.br/termo/en.html ,
%  being prohibited its distribution, commercialization or
%  reproduction, in particular, to use it for advertising or
%  any similar purpose.
%  2019-10-16T21:40:30-03:00

domain:      assertivasolucoes.com.br
owner:       HEDERSON VICTOR ALBERTINI
ownerid:     224.309.078-36
country:     BR
owner-c:     ASEMC2
admin-c:     ASEMC2
tech-c:      ASEMC2
billing-c:   ASEMC2
nserver:     ns-1795.awsdns-32.co.uk
nsstat:      20191014 AA
nslastaa:    20191014
nserver:     ns-694.awsdns-22.net
nsstat:      20191014 AA
nslastaa:    20191014
nserver:     ns-1441.awsdns-52.org
nsstat:      20191014 AA
nslastaa:    20191014
nserver:     ns-5.awsdns-00.com
nsstat:      20191014 AA
nslastaa:    20191014
saci:        yes
created:     20130516 #11469082
changed:     20190523
expires:     20240516
status:      published
provider:    SUPERDOMINIOS (53)

nic-hdl-br:  ASEMC2
person:      Assertiva Soluções em Marketing e Crédit
e-mail:      felipe.vieira@assertiva.info
country:     BR
created:     20130430
changed:     20190522

% Security and mail abuse issues should also be addressed to
% cert.br, http://www.cert.br/ , respectivelly to cert@cert.br
% and mail-abuse@cert.br
%
% whois.registro.br accepts only direct match queries. Types
% of queries are: domain (.br), registrant (tax ID), ticket,
% provider, contact handle (ID), CIDR block, IP and ASN.
```

### Consulta de Whois usando um IP
Para a consulta de um IP só precisamos passar qual o IP que queremos testar, poderiamos realizar um ping para saber o possivel IP, mas a ideia é a busca usando informação publica. Podemos usar o **SharingmyIP** para retornar o possivel IP e até subdominios.

Vamos usar o site e vamos passar um IP que queremos testar
```sh
https://hackertarget.com/whois-lookup/
```

O resultado da consulta é
```sh
#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/resources/registry/whois/tou/
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/resources/registry/whois/inaccuracy_reporting/
#
# Copyright 1997-2019, American Registry for Internet Numbers, Ltd.
#


NetRange:       54.160.0.0 - 54.175.255.255
CIDR:           54.160.0.0/12
NetName:        AMAZON-2011L
NetHandle:      NET-54-160-0-0-1
Parent:         NET54 (NET-54-0-0-0-0)
NetType:        Direct Allocation
OriginAS:       
Organization:   Amazon Technologies Inc. (AT-88-Z)
RegDate:        2014-06-20
Updated:        2014-06-20
Ref:            https://rdap.arin.net/registry/ip/54.160.0.0



OrgName:        Amazon Technologies Inc.
OrgId:          AT-88-Z
Address:        410 Terry Ave N.
City:           Seattle
StateProv:      WA
PostalCode:     98109
Country:        US
RegDate:        2011-12-08
Updated:        2019-07-25
Comment:        All abuse reports MUST include:
Comment:        * src IP
Comment:        * dest IP (your IP)
Comment:        * dest port
Comment:        * Accurate date/timestamp and timezone of activity
Comment:        * Intensity/frequency (short log extracts)
Comment:        * Your contact details (phone and email) Without these we will be unable to identify the correct owner of the IP address at that point in time.
Ref:            https://rdap.arin.net/registry/entity/AT-88-Z


OrgRoutingHandle: IPROU3-ARIN
OrgRoutingName:   IP Routing
OrgRoutingPhone:  +1-206-266-4064
OrgRoutingEmail:  aws-routing-poc@amazon.com
OrgRoutingRef:    https://rdap.arin.net/registry/entity/IPROU3-ARIN

OrgTechHandle: ANO24-ARIN
OrgTechName:   Amazon EC2 Network Operations
OrgTechPhone:  +1-206-266-4064
OrgTechEmail:  amzn-noc-contact@amazon.com
OrgTechRef:    https://rdap.arin.net/registry/entity/ANO24-ARIN

OrgNOCHandle: AANO1-ARIN
OrgNOCName:   Amazon AWS Network Operations
OrgNOCPhone:  +1-206-266-4064
OrgNOCEmail:  amzn-noc-contact@amazon.com
OrgNOCRef:    https://rdap.arin.net/registry/entity/AANO1-ARIN

OrgAbuseHandle: AEA8-ARIN
OrgAbuseName:   Amazon EC2 Abuse
OrgAbusePhone:  +1-206-266-4064
OrgAbuseEmail:  abuse@amazonaws.com
OrgAbuseRef:    https://rdap.arin.net/registry/entity/AEA8-ARIN


#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/resources/registry/whois/tou/
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/resources/registry/whois/inaccuracy_reporting/
#
# Copyright 1997-2019, American Registry for Internet Numbers, Ltd.
#
```
> Dessa forma conseguimos obter informações da rede, range de IP, proprietario do bloco de rede, informações do proprietario e até uma possivel localização.
