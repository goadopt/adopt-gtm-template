# adopt-gtm-template

A AdOpt disponibiliza um modelo de tag para dar suporte ao Consent Mode da Google, e para começar a usar o consent mode da Google junto com a AdOpt, é só seguir os próximos passos:
**IMPORTANTE: a instalação e uso do modelo de tag NÃO substitui o aviso da AdOpt que já está instalado no seu site. Tanto o aviso padrão da AdOpt e o modelo de tag devem estar instalados no seu site**

## Instalação do modelo de tag

1 - Importe o modelo da AdOpt. Para isso, você pode importar o nosso mdoelo direto do GitHub, ou pela galeria de modelos do Google Tag Manager

- Pelo GitHub
1. Faça o download do arquivo `./src/template.tpl`
2. Abra o seu **Google Tag Manager** *Web* [Google Tag Manager user interface](https://tagmanager.google.com/) e selecione o container desejado.
3. No GTM, vá até a seção de **Modelos**, e na caixa de **Modelos de tag**, clique no botão azul de **Novo**.
4. No **Editor de modelos**, clique no menu (três pontos na vertical) no canto superior direito e  selecione **Importar**.
5. Selecione o arquivo `template.tpl` que você acabou de fazer o download.
6. Siga os passos indicados. Assim que o processo for concluído, editor de models deve estar exibindo o modelo da AdOptno modo editar.
7. Clique em **Salvar**, e feche o editor de modelo. **Não faça absolutamente nenhuma alteração no código do modelo**.


- Pela galeria de modelos
1. No GTM, vá até a seção de **Modelos**, e na caixa de **Modelos de tag**, clique no botão **Pesquisar na galeria**.
2. Na aba que vai abrir à direita, clique no desenho de **lupa** para pesquisar, e pesquise por "adopt" ou simplesmente role a lista até encontrar a AdOpt.
3. Clique no modelo da AdOpt, e depois clique no botão azul de **Adicionar ao espaço de trabalho**

2 - Instalação da tag do modelo
1. Agora que você já tem o modelo da AdOpt, vá até a seção de **Tags** e clique em **Nova** para criar uma tag nova.
2. Da lista de modelos disponíveis, selecione o modelo **AdOpt** que você acabou de importar.
3. Na parte de configuração da tag, na parte de **Acionamento**, selecione primeiro o **Consent Initialization - All Pages**, pois esse é acionador específico que vai fazer com que o GTM "entenda" que o Consent mode está ativo.
4. Adicione um segundo acionador, do tipo **Evento personalizado**.
    1. Clique no símbolo de "+" para adicionar um novo acionador, e na lista de acionadores, clique novamente no símbolo de "+" para criar um novo acionador.
    2. Clique na caixa de **Configuração do acionador** e na lista que vai abrir à direita, clique no **Evento personalizado**, na seção de **Outros**.
    3. Escolha um nome de sua preferência pra esse acionador, e no **Nome do evento**, digite `adopt-visitor-consent-ready`.
    4. Verifique que a opção de **Todoso os eventos personalizados** esteja selecionada, selecione essa opção se ncessário e clique no botão azul de **Salvar**
    5. De volta à configuração, verifique se os dois acionadores estão configurados, e clique no botão azul de **Salvar**.


## Configurações

Algumas tags, como as do Google Analytics, Google Ads, possuem *Verificações de permissão integradas*. Isso significa que essas tags incluem uma lógica que altera automaticamente o comportamento da tag de acordo com o consentimento do usuário. Nesses casos, não é necessário fazer nenhuma configuração de consentimento.
**IMPORTANTE: Tags que contem Verificações de permissão integradas são carregadas/disparadas independente do consentimento do visitante, dados e informações vão ser transmitidas à Google sem a permissão explícita do mesmo, a diferença é que nesses casos essas tags não gravam cookies no navegador. Caso isso seja um problema, ou é algo preocupante pra você, é recomendado configurar essas tags com *Verificações de permissão adicional*, assim, as tags não serão carregadas/disparadas sem o consentimento explícito.**

Pra configurar essas Verificações, siga os próximos passos.

1. Clique na tag para abrir ela, e clique na caixa de **Configuração da tag**.
2. Clique em **Configurações de permissão** para exibir as opções, e marque opção **Exigir consentimento adicional para disparar a tag**.
3. Clique no botão de **+ Adicionar consentimento obrigatório**, clique no campo que acabou de aparecer, e selecione o tipo de consentimento desejado.
4. Repita o passo 3 para todos os tipos de consentimento que você deseja adicionar.

Caso a tag tenha um acionador simples, como um All Pages, siga esses passos:

1. Clique na caixa de **Acionamento**, e clique no símbolo de "+", e na lista de acionadores disponíveis, clique novamente no símbolo de "+" para configurar um novo acionador.
2. Clique na caixa de "Configuração do acionador", e da lista de tipos disponíveis, selecione o **Evento personalizado**, na seção de **Outros**.
3. No **Nome do evento**, digite `adopt-consent-mode-ready`, e selecione a opção de **Todos os eventos personalizados**, caso ainda essa opção ainda não esteja selecionada, e clique no botão azul de **Salvar**.
4. Verifique se os dois acionadores estão presentes (o acionador antigo que já estava lá e o novo acionador personalizado que você acabou de configurar), e clique no botão azul de **Salvar**
5. Clique no botão azul de **Salvar** no campo superior direito.

Caso a tag tenha outros tipos de acionadores, que dependem de ações do visitante, como clicks, ou outras regras como url específica, siga esses passos (nesse exemplo específico, vamos usar um acionador baseado em cliques):
1. Clique no acionador, para abrir as configurações dele, clique na caixa **Configurações do acionador**, e marque a opção de **Alguns cliques**
2. Nos campos que acabaram de aparecer, no primeiro campo, clique em **Nova variável...**, e novamente na caixa de **Configuração da variável**.
3. Na lista, clique em **Variável JavaScript**.
4. De volta à Configuração da variável, no **Nome da variável global**, digite `adoptConsentModeReady`, escolha um nome para essa variável, e clique no botão azul de **Salvar** no canto superior direito.
5. De volta à **Configuração do acionador**, selecione **contém** no segundo campo, e no terceiro campo, digite novamente `adoptConsentModeReady`.
6. Clique no botão azul de **Salvar** no canto superior direito.
7. Repita esses passos para cada um dos acionadores desse tipo, mas ao invés de criar uma nova variável, apenas selecione a variável que você já criou na primeira vez.

E é isso, não se esqueça de publicar as modificações.
