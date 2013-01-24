# Manual de Integração com o Serviço de Conteúdo

## Objetivo

O presente documento tem por finalidade demonstrar a integração com o serviço de conteúdo do site da [gazetaesportiva.net](http://www.gazetaesportiva.net).

## Estrutura de diretório

O conteúdo será disponibilizado através de um arquivos no formato XML:

> Exemplo Estrutura:

    - Pasta Raiz
      * 772260.xml (Notícia)
      * 120653.xml (Notícia)
      * ...

### Notícia

**Nome do arquivo:** O nome do arquivo XML é composto por até 10 caracteres ([0-9]{10}.xml), com nomenclatura
seqüencial.

> Exemplo:
* 120653.xml
* 1234.xml
* 1490308342.xml

**Coleta da notícia:** Para coletar as notícias é necessário que o cliente faça conexão FTP em um servidor da Ge.Net, para
visualizar o conteúdo de sua pasta exclusiva. Após a conclusão o processo de download dos arquivos, o
cliente deverá apagar o conteúdo da pasta.

**Alteração da notícia:** Quando há alteração no conteúdo da notícia, o nosso sistema recoloca a mesma no servidor FTP.
> Exemplo:

> Arquivo 1490308342.xml já foi coletado e excluído pelo sistema do cliente.
Quando o repórter fizer a alteração no conteúdo da notícia, o sistema da Ge.Net colocará a mesma no
servidor FTP com o mesmo nome utilizado anteriormente. Nesse caso: 1490308342.xml.
Logo, o sistema do cliente deve obter o arquivo, verificar em sua base se a mesma já foi obtida, e então
subscrevê-la.
Caso o cliente ainda não tenha obtido/excluído a notícia, o sistema da Ge.Net simplesmente subscreverá a
mesma.

**Exclusão da notícia:** O sistema simplesmente muda o formato de nome do arquivo para: [0-9]{10}-del.xml
> Exemplo:

> Arquivo 1490308342.xml foi excluído pelo repórter no sistema da Ge.Net.
Logo o sistema da Ge.Net enviara para o FTP um arquivo em branco, com o nome 1490308342-del.xml.
O cliente deve obter esse arquivo e então excluí-lo de sua base.


# Notícia

### Modelo de envio XML Notícias

Estrutura de diretório raiz:  `/`

Exemplo de arquivo XML referente à [notícia](http://www.gazetaesportiva.net/noticia/2013/01/goias/tecnico-do-goias-entende-lentidao-nas-contratacoes-e-normal.html):
    
```xml
<?xml version="1.0" encoding="UTF-8"?>
<item id="772260">
  <language>pt-BR</language>
  <copyright>Copyright 1998-2012 GazetaEsportiva.net</copyright>
  <webMaster><![CDATA[redacao@gazetaesportiva.com.br (Redação)]]></webMaster>
  <channels>
    <channel id="1" main="0" type="futebol" typeID="1"><![CDATA[Futebol]]></channel>
    <channel id="39" main="1" type="futebol" typeID="1"><![CDATA[Goiás]]></channel>
    <channel id="97" main="0" type="futebol" typeID="1"><![CDATA[Região Centro Oeste]]></channel>
    <channel id="103" main="0" type="futebol" typeID="1"><![CDATA[Campeonatos]]></channel>
    <channel id="482" main="0" type="futebol" typeID="1"><![CDATA[Campeonatos Estaduais]]></channel>
    <channel id="490" main="0" type="futebol" typeID="1"><![CDATA[Campeonato Goiano]]></channel>
  </channels>
  <url><![CDATA[http://www.gazetaesportiva.net/noticia/2013/01/goias/tecnico-do-goias-entende-lentidao-nas-contratacoes-e-normal.html]]></url>
  <pubDate>Mon, 07 Jan 2013 14:00:02 -0200</pubDate>
  <date>07/01/2013</date>
  <hour>14:00</hour>
  <category><![CDATA[Futebol/Mercado]]></category>
  <location>
    <city><![CDATA[Goiânia]]></city>
    <state><![CDATA[GO]]></state>
    <country/>
  </location>
  <title><![CDATA[Técnico do Goiás entende 'lentidão' nas contratações: "É normal"]]></title>
  <summary><![CDATA[<p>Com dificuldades para reforçar o seu time desta temporada, a diretoria do Goiás
  lamenta a lentidão das contratações. O técnico Enderson Moreira, que viu apenas quatro novidades na 
  reapresentação da última quinta-feira, afirmou que esta situação é normal e assegurou que o Esmeraldino 
  não largou atrás.</p>]]></summary>
  <story><![CDATA[<p>Com dificuldades para reforçar o seu time desta temporada, a diretoria do Goiás 
  lamenta a lentidão das contratações. O técnico Enderson Moreira, que viu apenas quatro novidades na 
  reapresentação da última quinta-feira, afirmou que esta situação é normal e assegurou que o Esmeraldino 
  não largou atrás.</p>
  <p>"Nós temos que esperar um pouquinho pelas boas oportunidades. As negociações são complicadas mesmo", 
  disse o treinador, que ainda pode perder o lateral direito Vítor, que pertence ao Palmeiras, e o atacante 
  Walter, emprestado pelo Porto, de Portugal, nesta semana.</p>
  <p>O goleiro Renan, ex-Internacional, o zagueiro Rodrigo, ex-Vitória, e os laterais William Matheus, ex-
  Vasco da Gama, e Diego, América-RJ, foram os contratados do Verdão para 2013. A cúpula esmeraldina ainda 
  espera o lateral direito Marcos, ex-Atlético-GO, e o atacante Neto Baiano, ex-Vitória.</p>
  <p>A estreia do Goiás no Estadual está marcada para o dia 20 deste mês, às 17 horas (de Brasília), contra 
  o Itumbiara, na Serrinha.</p>]]></story>
  <keywords><![CDATA[GENET, Campeonato Goiano, Goiás, Enderson Moreira, Contratações]]></keywords>
  <author_1/>
  <author_2/>
  <imgs/>
</item>
```

### Notícias com imagens
Algumas notícias podem conter imagens em qualquer parte do texto principal no seguinte formato.

> Exemplo:

> “Como já está se tornando de costume, **[imagem=1]** a briga pelo título da Fórmula 1 ultrapassou as pistas. Nesta segunda-feira, o inglês Lewis Hamilton acusou o brasileiro Felipe Massa de provocar o acidente envolvendo os dois carros no GP do Japão, nesse domingo. **[imagem=2]**”

Onde, **[imagem=1]** e **[imagem=2]** correspondem às imagens que, caso a nota tenha, ficam armazenadas na raiz da sua pasta exclusiva no formato **[número da notícia]_[número_sequencial].extensão**

> Exemplo para a nota de número **127**.xml

```xml
<imgs>
  <img id="1">
    <legenda><![CDATA[legenda da foto 1]]></legenda>
    <autor><![CDATA[autor da foto 1]]></autor>
  </img>
  <img id="2">
    <legenda><![CDATA[legenda da foto 2]]></legenda>
    <autor><![CDATA[autor da foto 2]]></autor>
  </img>
```

Na pasta raiz, haveria um arquivo com o nome **127_1**.jpg e outro arquivo com o nome **127_2**.jpg
Se a nota for excluída, os arquivos de imagens seguem o mesmo padrão da nota para exclusão:

* 127_1-del.jpg
* 127_2-del.jpg

É de responsabilidade do cliente armazenar e anexar as imagens às suas respectivas notícias, da forma que melhor lhe
for conveniente mas respeitando a sua localização dentro do texto principal.

### Detalhamento das tags:

**Tag principal:** _item_
> Contém todas as informações da matéria. O ID representa o AUTO INCREMENT no nosso banco de dados. Facilita para possíveis problemas nos dados.

**Tag:** _channels_
> Contém a lista de canais que a matéria pertence. É informado o id do canal (será fornecido uma lista dos canais, com seus respectivos ID’s para processos de DE-PARA) e se o mesmo é o canal principal ou não, (atributo main). Cada matéria possui apenas um canal principal. Existe uma classificação por assunto (type, typeID), para facilitar a macro-classificação das matérias, onde todo canal é classificado em nosso sistema. A sugestão é usar o assunto (type) do canal principal para classificação. Abaixo, segue tabela válida:
* Outros.
* Futebol (geral).
* Futebol (clube).
* Futebol (campeonato).
* Futebol (copa do mundo).
* Atletismo.
* Basquete.
* Motor.
* Tênis.
* Olimpíadas.

> Obs: A listagem está em constante mudança, para obter a lista completa e atualizada por favor entre em contato.

**Tag:** _url_
> URL da matéria no site GazetaEsportiva.

**Tag:** _pubDate_
> Data e hora de publicação no padrão timestamp usado em arquivos de RSS.

**Tag:** _date_
> Data de publicação.

**Tag:** _hour_
> Hora de publicação.

**Tag:** _category_
> Linha fina: assunto ao qual à matéria se relaciona. Essa informação não segue um padrão, é um texto
aberto para os editores.
* Ex: Motor/Fórmula 1, Futebol/Copa América, Tênis/Aberto da Austrália.

**Tags:** _location_
> Conjunto de tags que informa o local (região) da matéria.
* city – cidade
* state – estado
* country – país

**Tag:** _title_
> Título da matéria

**Tag:** _summary_
> Resumo da matéria. (Lide)

**Tag:** _story_
> A matéria em si, com quebras de parágrafos `<p>`

**Tag:** _keywords_
> Palavras-chave relacionadas à matéria.

**Tag:** _author_1_
> Crédito da matéria.
* Ex: Por Fernando Pessoa.

**Tag:** _author_2_
> Informações adicionais sobre o crédito
* Ex: Colaborou Machado de Assis.

**Tag:** _imgs_
> Com esta tag presente, indica que a notícia tem uma ou mais imagens

**Tag:** _img_
> Contém as informações da imagem. O atributo ID representa um número sequencial que identifica a imagem correspondente. As imagens ficam na raiz da pasta exclusiva.

**Tag:** _legenda_
> Contém a legenda da imagem (Pode estar nulo).

**Tag:** _autor_
> Contém o autor da imagem (Pode estar nulo).

**Tag:** _webMaster_
> Contém o contato do responsável da matéria (Pode estar nulo).

**Tag:** _language_
> Contém o formato do idioma utilizado no XML.

**Tag:** _copyright_
> Contém informações dos direitos autorais.
