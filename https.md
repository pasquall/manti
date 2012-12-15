# HTTPS Guia basico

* O que? e pra que?
* Certificadores
* Certificados
* Instalacao
* Testes
* HSTS
* Mais informacoes
* Referencias


## O que e? e pra que?

O HTTPS e´ um protocolo para comunicar-se de forma segura em redes, na verdade
e´ uma implementacao do HTTP sobre SSL. Ele e´ usado basicamente para garantir
a *confidencialidade*, a *autenticidade* e a *integridade*.


### Autenticidade

Os browsers tambem oferecem um recurso adicional para melhorar a confianca
desta conexao. Atraves dos certificados digitais e´ possivel garantir com 
certa seguranca que o site que esta´ acessando e´ realmente quem voce imagina
que seja.

Quando esta´ acessando um site de um banco ou de uma loja virtual, por exemplo,
e´ importante certificar que aquele e´ realmente o banco ou a loja que deseja
e nao alguem tentando passar-se por eles.

Ai entra o certificado digital, nada mais e´ do que uma garantia de um orgao 
independente que voce e´ voce mesmo. Para isso, eles possuem normas de verifi
cacao para ter certeza deste fato.


### Confidencialidade

Quando uma requisicao HTTP e´ feita, todo trafego e´ transportado em texto 
puro, desta forma, se sua conexao for interperceptada entre voce e o servidor 
que esta acessando, sera´ possivel ler tudo que foi comunicado.

No HTTPS toda a comunicacao e´ criptografada.


## Integridade

Não e´ possivel alterar os dados sem ser percebido (a grosso modo o pacote https vem com um lacre)[1]


## Certificadores

Certificadores ou melhor, autoridades certificadoras, sao as entidades respon
saveis pelo processo de validacao dos certificados. Se voce usa o Firefox, va
ate´ as preferencias, aba criptografia, botao ver certificados e finalmente
clique na aba autoridades. Vera´ as lista de autoridades certificadoras que 
ja´ vem embutida no Firefox.

Quando algum site e´ visitado e o mesmo esta´ assinado por algumas destas enti
dades, o Firefox exibira´ o famoso cadeado informando que o site e´ autentico.

E´ importante lembrar que uma invasao na entidade certificadora pode fazer com
que seu certificado vaze e outras pessoas podem passar-se por voce. Portanto,
recomenda-se cuidado extra nesta escolha.


## Certificados

Ao adquirir um certificado, diversas opcoes serao apresentadas, basicamente
temos duas opcoes distintas:

1) Certificado normal: dentro desta categoria poderemos ter outros tipos de 
certificado, so´ alterando o nivel de criptografia. Quando o site possue este
certificado, somente o cadeado aparece bem pequeno.

2) Certificado com verificacao extendida: e´ uma nova opcao no mercado, a
diferenca e´ que o processo de verificacao da entidade e´ um pouco mais
rigoroso o que garante uma protecao extra ao visitante. Visualmente a barra de
endereco fica verde ou azul (depende do browser, as cores podem variar), e´ 
mais evidente para o visitante que esta´ em um ambiente seguro.


## Instalacao

O processo de instalacao[2], comeca na escolha da entidade certificadora, depois
do tipo de certificado, feito isso voce devera gerar sua chave privada e um
CSR (Certificate Signing Request). Sao dois arquivos, a chave privada devera
ser guardada com muito cuidado, vazar esta informacao, significa que seu 
certificado nao e´ mais seguro. O CSR e´ outro arquivo gerado a partir da sua
chave privada, com o certificado e uma requisicao de assinatura.

O CSR devera´ ser enviado para a entidade certificadora que iniciara o processo
de validacao, que basicamente e´ verificar se o CNPJ da empresa existe, se 
pertence a ela mesma, se os responsaveis legais sao os que foram identifcados, 
se o dominio pertence ao solicitante. Dependendo do tipo de certificado ou do 
CA, um contao fisico sera necessario para concluir o processo de validacao.

Concluida esta etapa, o CA emitira o arquivo CRT, que e´ o certificado ja 
assinado pela autoridade, a partir deste ponto bastara configurar seu webserver
para receber seu certificado.


## Testes

Gosto muito de testes e realizar este procedimento apesar de simples pode 
esconder problemas serios de seguranca, portanto, a recomendacao e´ realizar
alguns testes.[3]

O site acima e´ bastante util para identificar estes problemas e indicar o que
mais pode ser feito para melhorar a seguranca e diminuir a incompatibilidade
com alguns ambientes.


## HSTS

O HSTS[4] e´ um novo padrao de seguranca que ainda nao e´ amplamente utilizado,
mas ajuda na configuracao para forcar o uso do SSL.


## Mais informacoes
[The First Few Milliseconds of an HTTPS Connection](http://www.moserware.com/2009/06/first-few-milliseconds-of-https.html)

##Referencias:
[1][Verificando a integridade dos dados](http://informatica.hsw.uol.com.br/criptografia7.htm)

[2][Guia de instalacao](http://www.certisign.com.br/atendimento-suporte/certificado-servidor/ssl-verisign/instalacao-configuracao)

[3][Teste sua implementacao](https://www.ssllabs.com/ssltest/index.html)

[4][Dicas-L sobre HSTS](http://www.dicas-l.com.br/arquivo/habilitando_o_hsts_no_apache_e_nginx.php)

