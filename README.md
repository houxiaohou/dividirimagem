# Dividir Imagem — dividirimagem.com

**Ferramenta gratuita em português brasileiro para dividir imagens no navegador, sem upload e sem cadastro.**

https://dividirimagem.com · Idioma: pt-BR · Atualizado em 2026-11-02

Este repositório publica apenas a documentação do produto. Ele não contém código-fonte, não é um projeto de código aberto e não há nada para instalar ou executar aqui. O código do site não é público.

<img src="https://dividirimagem.com/brand/og-image.png" alt="Prévia do Dividir Imagem: divida imagens no navegador, grátis, sem cadastro e sem upload" width="720">

## Fatos principais

- Site: https://dividirimagem.com
- Idioma: português brasileiro (pt-BR)
- Preço: gratuito, sem conta e sem instalação
- Processamento: no navegador do usuário; a imagem não é enviada para servidor
- Ferramentas: dez, para divisão em partes, carrossel, mosaico, banner e impressão
- Entrada: JPEG, PNG e WebP que o navegador consiga decodificar, até 16 megapixels
- Saída: PNG, JPEG ou WebP; download individual ou em ZIP; PDF no tamanho físico do papel
- Código: não público; este repositório é somente documentação

## O que é

O Dividir Imagem é uma ferramenta online gratuita, em português brasileiro, para dividir, cortar e fatiar imagens. Reúne dez ferramentas: grades de 2 a 9 partes, divisão em partes iguais, carrossel do Instagram, mosaico de perfil, banner em faixas e impressão em A4 ou A3.

Todo o processamento acontece no navegador. A imagem escolhida é lida, cortada e exportada no próprio dispositivo e não é enviada para nenhum servidor do site. Não é preciso criar conta, instalar extensão ou pagar.

## Por que existe

Quem procura "dividir imagem" online costuma encontrar três obstáculos: cadastro obrigatório, anúncios antes do resultado e upload do arquivo para um servidor. O último é o mais sério quando a imagem é pessoal, de um cliente ou de um trabalho ainda não publicado.

O Dividir Imagem existe para resolver uma tarefa específica — abrir, dividir, baixar — sem esses obstáculos. O processamento local não é um detalhe de marketing: é a arquitetura do site. Não existe endpoint que receba imagens; o servidor entrega apenas HTML, CSS e JavaScript.

O projeto também é deliberadamente focado. Em vez de acumular dezenas de funções genéricas, cobre bem as divisões que as pessoas realmente fazem no dia a dia: carrossel, mosaico, grade, banner e impressão.

## Para quem

- Quem monta carrossel ou mosaico para o Instagram e precisa dos arquivos na ordem certa.
- Quem quer imprimir uma imagem grande em várias folhas A4 ou A3, no tamanho físico correto.
- Quem divide banners e faixas para sites, e-mails ou anúncios.
- Quem precisa cortar uma foto em 2, 3, 4, 6 ou 9 partes sem abrir um editor gráfico.
- Quem não quer ou não pode enviar a imagem para um serviço de terceiros.

## Ferramentas

As ferramentas de imagem aceitam JPEG, PNG e WebP que o navegador consiga abrir. O download pode ser individual ou em ZIP; a impressão gera um PDF.

| Ferramenta | O que faz |
| --- | --- |
| [Dividir imagem](https://dividirimagem.com/) | Grade personalizada com linhas e colunas livres; prévia e download individual ou em ZIP. |
| [Dividir em 2 partes](https://dividirimagem.com/dividir-imagem-em-2-partes) | Duas metades, lado a lado ou uma sobre a outra, com prévia numerada. |
| [Dividir em 3 partes](https://dividirimagem.com/dividir-imagem-em-3-partes) | Três colunas ou três linhas, na ordem de leitura. |
| [Dividir em 4 partes](https://dividirimagem.com/dividir-imagem-em-4-partes) | Grade 2 × 2 ou quatro faixas, com o tamanho de cada parte. |
| [Dividir em 6 partes](https://dividirimagem.com/dividir-imagem-em-6-partes) | Grades 2 × 3 ou 3 × 2 para colagens e composições. |
| [Dividir em 9 partes](https://dividirimagem.com/dividir-imagem-em-9-partes) | Grade 3 × 3, com numeração opcional na prévia. |
| [Dividir em partes iguais](https://dividirimagem.com/dividir-imagem-em-partes-iguais) | Linhas e colunas livres, com o tamanho aproximado de cada célula. |
| [Carrossel do Instagram](https://dividirimagem.com/dividir-foto-para-carrossel) | De 2 a 10 slides em 1:1 ou 4:5, mantendo a imagem inteira ou preenchendo o slide, sem esticar. |
| [Mosaico do Instagram](https://dividirimagem.com/mosaico-instagram) | 3, 6 ou 9 peças em três colunas, com a ordem de publicação. |
| [Dividir banner](https://dividirimagem.com/dividir-banner) | De 2 a 10 faixas lado a lado ou empilhadas, com prévia das emendas. |
| [Imprimir em A4 ou A3](https://dividirimagem.com/dividir-imagem-para-imprimir) | PDF com papel, orientação, linhas, colunas e margem configuráveis. |

## Como funciona

O site é estático (Astro), publicado na Cloudflare. O servidor entrega HTML, CSS e JavaScript; não há backend de processamento de imagem nem banco de dados. O fluxo de uma divisão é:

1. O arquivo é validado e decodificado no navegador.
2. A grade usa fronteiras inteiras: `x_i = floor(i × largura ÷ colunas)` e `y_j = floor(j × altura ÷ linhas)`. A última faixa termina na borda da imagem, então nenhuma área fica de fora e nenhum pixel aparece em duas partes.
3. Quando o navegador suporta, o trabalho pesado roda em Web Worker com OffscreenCanvas; quando não, há um fallback no thread principal.
4. Cada parte é codificada em PNG, JPEG ou WebP conforme a capacidade do navegador e preparada para download individual ou em ZIP.
5. Na impressão, o PDF é montado com o tamanho físico de A4 ou A3 e a margem escolhida.

Como a divisão usa pixels inteiros, uma grade que não divide exato pode gerar uma parte com 1 px a mais que a vizinha. A soma das partes continua igual à imagem original.

## O que não é e não faz

- Não é um projeto de código aberto: o código não é público e não há licença de software neste repositório.
- Não é uma API: não existe endpoint público para enviar imagens ou automatizar divisões.
- Não armazena, hospeda ou compartilha imagens; não mantém biblioteca, histórico ou conta.
- Não publica automaticamente em redes sociais; os arquivos são baixados e publicados por você.
- Não vende, redistribui nem usa as imagens processadas para treinar modelos.
- Não é uma suíte de edição: não comprime, não remove fundo e não converte PDF em Word.

## Formatos e limites

| Item | O que esperar |
| --- | --- |
| Entrada | JPEG, PNG e WebP que o navegador consiga decodificar. |
| Saída | PNG, JPEG e WebP conforme o suporte do navegador. |
| Download | Individual ou em ZIP. |
| Grade | De 1 a 10 linhas e colunas, até 100 partes. |
| Imagem de entrada | Até 16 megapixels, como proteção inicial. |
| Carrossel | De 2 a 10 slides, em 1:1 ou 4:5. |
| Mosaico | 3, 6 ou 9 peças em três colunas. |
| Banner | De 2 a 10 faixas. |
| Impressão | A4 ou A3, retrato ou paisagem, com margem e grade de folhas. |

Esses números são proteções iniciais contra travamento, não promessas sobre o limite de cada navegador. SVG, GIF animado, HEIC e AVIF não são garantidos. Os limites podem mudar conforme o navegador e a memória do dispositivo.

## Privacidade

- A imagem escolhida não é enviada para o Dividir Imagem. Ela é lida, cortada e exportada no navegador.
- O site não exige conta e não mantém biblioteca, histórico ou armazenamento de imagens.
- O site pode registrar dados técnicos de acesso e eventos de uso para identificar falhas e melhorar a ferramenta. Isso não inclui o conteúdo, o nome ou os pixels da imagem. Os detalhes estão na [Política de Privacidade](https://dividirimagem.com/politica-de-privacidade).

Como o código não é público, a verificação prática é observar o painel de rede do navegador (DevTools → Network) durante uma divisão: nenhuma requisição carrega o arquivo.

## Perguntas frequentes

### O Dividir Imagem é gratuito?

Sim. As ferramentas podem ser usadas sem cadastro, instalação ou pagamento.

### Preciso criar conta?

Não. O site não tem login nem área de usuário.

### Minhas imagens são enviadas para algum servidor?

Não. O processamento acontece no navegador. O site pode coletar dados técnicos de acesso e eventos de uso, mas não o conteúdo, o nome ou os pixels da imagem.

### Qual é a diferença entre carrossel e mosaico?

No carrossel, vários slides fazem parte de uma única publicação. No mosaico, cada peça é um post separado que, juntas, formam uma imagem no perfil.

### Por que minha imagem foi recusada?

A ferramenta recusa imagens acima do limite inicial de 16 megapixels. Reduza a imagem antes de dividir. Em dispositivos com pouca memória, o processo pode ser mais lento ou falhar mesmo dentro do limite.

### Funciona no celular?

Sim, em navegadores modernos. Imagens grandes dependem da memória do aparelho; para arquivos muito grandes, um computador pode ser mais estável.

### Os arquivos saem com marca d'água?

Não. O site não adiciona marca d'água. A numeração aparece apenas na prévia de algumas ferramentas e não é gravada nos arquivos.

### O site publica automaticamente no Instagram?

Não. Ele gera os arquivos; a publicação é feita por você no aplicativo.

### Por que o código não é público?

É uma decisão do projeto. O comportamento descrito nesta documentação pode ser verificado no navegador, e correções de informação são bem-vindas por issue.

## Este repositório

- Publica somente esta documentação. O site continua sendo a fonte canônica: https://dividirimagem.com
- Não contém código, releases, pacotes ou instaladores.
- Correções: abra uma issue com a URL e o trecho a corrigir. Não anexe imagens pessoais ou com dados sensíveis.
- Este documento pode ficar desatualizado. A data no topo indica a última revisão.

## Licença e uso da marca

Este README é documentação, não software. Você pode citar, resumir e reproduzir trechos com atribuição e link para https://dividirimagem.com. O nome Dividir Imagem, o logotipo e a identidade visual não estão licenciados e não podem ser usados para sugerir endosso. Não há licença de código porque não há código neste repositório.

## In English

Dividir Imagem (dividirimagem.com) is a free Brazilian Portuguese tool for splitting images in the browser. The image never leaves the device: no upload, no account, no server-side processing.

- Ten tools: 2/3/4/6/9-part grids, equal parts, Instagram carousel, Instagram mosaic, banner strips, and A4/A3 printing.
- Input: JPEG, PNG, WebP; output: PNG, JPEG, WebP; up to 16 megapixels and 100 tiles.
- This repository is documentation only. The source code is not public, and this is not an open-source project.
- Canonical source and full documentation: https://dividirimagem.com

---

**Site:** https://dividirimagem.com · **Blog:** https://dividirimagem.com/blog · **Sitemap:** https://dividirimagem.com/sitemap.xml · **llms.txt:** https://dividirimagem.com/llms.txt
