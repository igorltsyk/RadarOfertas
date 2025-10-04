# Projeto: Radar de Ofertas

## 1. Descrição
Um bot de monitoramento automatizado que rastreia os preços de produtos específicos em sites de e-commerce. O objetivo principal é notificar o usuário quando o preço de um item de interesse cair abaixo de um valor pré-definido.

## 2. Objetivo
Automatizar a tarefa repetitiva e manual de verificar preços de produtos online, garantindo que o usuário aproveite as melhores ofertas e promoções sem esforço.

## 3. Funcionalidades (Roadmap)

### Versão 1.0 (MVP - Mínimo Produto Viável)
- [X] Monitorar **um único produto** a partir de uma URL fixa no código.
- [X] Extrair o nome e o preço do produto da página.
- [X] Comparar o preço extraído com um preço-alvo definido no código.
- [X] Imprimir um alerta simples no console se o preço for menor ou igual ao alvo.



### Versão 2.0 (Sistema de Alertas)
- [ ] Integrar com um serviço de notificação (ex: E-mail, Telegram).
- [ ] Enviar um alerta formatado com o nome do produto, o preço atual e o link.

### Versão 3.0 (Escalabilidade)
- [ ] Adaptar o código para ler uma lista de produtos (URL e preço-alvo) de um arquivo externo (ex: `produtos.json` ou `.csv`).
- [ ] O bot deverá monitorar todos os produtos da lista em uma única execução.

### Versão 4.0 (Automação Completa)
- [ ] Criar um script que executa o monitoramento de forma periódica (ex: a cada 6 horas) sem intervenção manual.

## 4. Estrutura de Arquivos Proposta
/radar_de_ofertas
|-- main.py               # Script principal do bot
|-- requirements.txt      # Lista de dependências Python
|-- produtos.json         # (Para Versão 3.0) Lista de produtos a monitorar
|-- .env                  # (Para Versão 2.0) Para guardar chaves de API e senhas
|-- .gitignore            # Para ignorar arquivos desnecessários no Git

## 5. Tecnologias Utilizadas
- **Linguagem:** Python 3.9+
- **Bibliotecas Principais:**
  - `requests`: Para fazer as requisições HTTP e buscar o conteúdo da página.
  - `BeautifulSoup4`: Para analisar o HTML da página e extrair as informações.
  - `smtplib` (Nativa do Python): Para o envio de e-mails (Versão 2.0).

  INÍCIO
  |
  V
[Definir URL e Preço Alvo]
  |
  V
[Acessar a URL da página] --> [Deu erro?] --SIM--> [Avisar "Erro de Conexão"] --> FIM
  |
NÃO
  |
  V
[Procurar a etiqueta do preço no HTML] --> [Não encontrou?] --SIM--> [Avisar "Estrutura Mudou"] --> FIM
  |
NÃO (Encontrou!)
  |
  V
[Limpar e converter o texto do preço para número]
  |
  V
[Preço Atual <= Preço Alvo?] --NÃO--> [Avisar "Preço ainda alto"] --> FIM
  |
SIM
  |
  V
[!! GERAR ALERTA DE SUCESSO !!]
  |
  V
FIM