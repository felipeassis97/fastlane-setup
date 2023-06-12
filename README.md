# Setup iOS Fastlane

Para obter instruções de instalação do fastlane, consulte [Instalando _fastlane_](https://docs.fastlane.tools/getting-started/ios/setup/).
É recomendado seguir a instalação via [_Bundler_](https://bundler.io/), além de instalar um gerenciador de versões do Ruby o [_rbenv_](https://github.com/rbenv/rbenv#readme).

## Fluxo básico

Ao criar o setup do projeto, deverá ser criado todos os certificados e profiles no portal developer normalmente.
Após isso, será necessário adicionar todos eles em um repositório git (pode ser o mesmo do projeto, ou o mais recomendado, que é criar um um novo só para estes arquivos), para que o fastlane (através do __match__) possa utiliza-los e gerencia-los sempre que necessário.
Para adicionar os certificados no repositório, (já com o ambiente configurado e variáveis de ambiente preenchidas), deverá ser utilizado os seguintes comandos:

```bash
bundle exec fastlane match import --skip_certificate_matching true --type appstore
```

_Obs.: O comando mostrado acima, se aplica apenas para o certificado de distribuição na appstore. O mesmo comando deve ser utilizado para os certificados de __adhoc__ e __development__, substituindo apenas o type para o correspondente._

Ao fazer isso, será necessário passar três arquivos (__.cer__, __.p12__ e __.mobileprovision__) para cada um dos três comandos (--type appstore, --type adhoc e --type development).

  
## Variáveis de Ambiente
Para rodar esse projeto, você vai precisar adicionar as seguintes variáveis de ambiente no seu .env localizado dentro da pasta _fastlane_.

#### Informações do app
* `APP_IDENTIFIER`
Identifier do app. _Ex.: br.com.example_

- `SCHEME`
Scheme do app. _Obs.: Em apps Flutter o padrão é Runner._

* `WORKSPACE`
 Workspace do app. _Ex: Runner.xcworkspace._

- `TEAM_ID`
O ID do time pode ser encontrado no  [_Portal Apple Developer_](https://developer.apple.com/account), na sessão __Membership details__.

- `IC_TEAM_ID`
 Essa informação pode ser um pouco difícil de encontrar, mas é possível busca-la neste [_endpoint_](https://appstoreconnect.apple.com/WebObjects/iTunesConnect.woa/ra/user/detail). Para ter acesso, é necessário estar logado na conta.
 _Obs.: A informação deve ser encontrada dentro do atributo __"contentProviderId".__ Você pode utilizar alguma ferramenta para  [_formatar JSON_](https://jsonformatter.curiousconcept.com/) visando facilitar a leitura.


* `ARTIFACT_DEV_NAME`
 Nome do arquivo .ipa de desenvolvimento. _Ex.: __nomeDoAppDev.ipa__. Este nome servirá apenas pra localizar o artefato no diretório e não interfere em nada no nome da aplicação_.

* `ARTIFACT_PROD_NAME`
 Nome do arquivo .ipa de produção. _Ex.: __nomeDoAppProd.ipa__. Este nome servirá apenas pra localizar o artefato no diretório e não interfere em nada no nome da aplicação_.

 > ---
#### Autenticação Apple
- `MATCH_PASSWORD`
Esta senha será usada pelo Fastlane para criptografar todos os certificados antes de salvar no repositório.
_Obs.: Caso o certificado (.p12) tiver uma senha, é recomendado colocar a mesma nesta variável_.

* `MATCH_KEYCHAIN_PASSWORD`
 Esta senha será usada pelo Fastlane para descriptografar quando a nossa ferramenta de CI buscar estes certificados.
  Deve ser a mesma do _MATCH_PASSWORD_

- `APP_STORE_CONNECT_APPLE_ID`
Esta informação pode ser encontrada em: ___App Store Connect > Apps > Meu App > Informações dp App > Apple ID___.

* `AUTH_APP_STORE_CONNECT_API_KEY`
Esta variável de ser preenchida com o caminho do arquivo JSON que deverá ser criado no seguinte formato:
 ```
 {
	"key_id":  "ID DA CHAVE",
	"issuer_id":  "EMISSOR DA CHAVE",
	"key":  "CONTEÚDO DA CHAVE",
	"duration":  1200, //Não é necessário mudar
	"in_house":  false //Não é necessário mudar
}
```
Para obter essa chave, é necessário ser um __administrador__ da conta de desenvolvimento da Apple.
Esta opção estará disponível em: App Store Connect -> User and Access -> Keys (Conforme a imagem abaixo).
O arquivo que é gerado é um .p8 que contém um token (É possível abrir em qualquer editor de texto) e é com ele que deverá ser preenchido o atributo ___key___ do JSON acima.
Os outros atributos são preenchidos com os valores obtidos no portal conforme a foto.

 
  > ---

#### Variáveis Azure 
 - `URL_DOMAIN`
O valor desta variável pode ser encontrado na url do repositório do projeto (conforme foto abaixo). O valor à ser preenchido deve ser somente a string que sucede o '__@__'.

 - `AZURE_TOKEN`
O valor desta variável pode ser encontrado no portal da Azure no caminho ilustrado na imagem abaixo

_Ex.:_

## Funções disponíveis

* __Download project keys__
 Utlizado para baixar e instalar os certificados e profiles existentes no projeto.
```bash
bundle exec fastlane download_keys
```
---
- __Build Distribution (AppDist, App center e Firebase)__
Função utilizada para gerar uma compilação (.ipa) do projeto utilizando o certificado de __adHoc__. Esta funcão é utilizada apenas para fazer a compilação e posteriormente ser usada pelo CI (Azure Popelines) para submissão para outras ferramentas (Soft App Distribution e Firebase App Distribution).

* __Algumas observações__:
Por padrão a compilação é colocada dentro da pasta do projeto e utiliza a identificação inserida na variável  "_ARTIFACT_DEV_NAME_", que está sendo utilizado no atributo "_output_name_"

```bash
bundle exec fastlane build_distribution
```

* __Send Soft App Distribution__
Para enviar para o App Dist, é necessário que o aplicativo tenha sido criado na plataforma [Soft App Distribution](https://app-dist.softdesign.com.br/) .
---

* __Build App Store (TestFlight)__
Função utilizada para gerar uma compilação (.ipa) do projeto utilizando o certificado de __appStore__. Está funcão será utilizada pelo CI (Azure DevOps) para gerar o arquivo e envia-lo para o Test Flight.

* __Algumas observações__:
Não esqueça de versionar o app corretamente antes de submete-lo.
Por padrão a compilação é colocada dentro da pasta do projeto e utiliza a identificação inserida na variável  "_ARTIFACT_PROD_NAME_", que está sendo utilizado no atributo "_output_name_"

```bash
bundle exec fastlane build_appStore
```
---

 



