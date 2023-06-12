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

### Autenticação App Store
* `APPLE_ID`
> Apple id de um perfil com permissão de submissão na app store. _Ex.: fulano@email.com_

- `FASTLANE_PASSWORD`
> Senha de acesso à app store. _Obs.: Caso utilizado este método de autenticação, esta senha deve estar setada como uma secret na configuração do pipeline Azure._

* `FASTLANE_SESSION`
> Utilizado para recuperar a sessão ativa ao executar via CI (Azure DevOps). Para obter uma chave de sessão, executar:
```bash
bundle exec fastlane spaceauth -u youremail@email.com
```
- `FASTLANE_APPLE_APPLICATION_SPECIFIC_PASSWORD`
> Quando utilizado autenticação com e-mail e senha, é necessário informar uma senha especifica de aplicativos, que pode ser gerada no portal [_Apple_](https://appleid.apple.com).

 
### Informações do app
- `APP_STORE_CONNECT_APPLE_ID`
> ID do aplicativo que pode ser encontrado em _App Store Connect > Apps > App > Info > Apple ID_.

* `TEAM_ID`
> App Store Connect Team ID que pode ser encontrado no portal Developer.

- `IC_TEAM_ID`
> CHANGE: Update docs (module code remains unchanged)

* `APP_IDENTIFIER`
> Bundle identifier do projeto. _Ex.: br.com.softdesign.quickstartFlutter_

- `SCHEME`
> Scheme do app iOS (Em apps flutter, o padrão é _Runner_).

* `WORKSPACE`
> Geralmente é formado por SchemeName.xcworkspace. _Ex.: Runner.xcworkspace_

- `MATCH_PASSWORD`
> Esta senha será usada pelo fastlane quando os certificados forem criptografados para salvar no repositório.

* `MATCH_KEYCHAIN_PASSWORD`
> Esta senha será usada pelo fastlane para descriptografar quando a nossa ferramenta de CI buscar estes certificados.

  
  

### Firebase App Distribution (Opcional)
_Utilizar apenas se o app for distribuido no app distribution_

* `FIREBASE_DIST_SERVICE_ACCOUNT_FILE`
> Certificado utilizado para autenticação com o firebase. Pode ser gerado em [_Google Cloud Plataform_](console.cloud.google.com/) na aba KEYS.

- `FIREBASE_APP_ID`
> ID do app encontrado no console do Firebase.

* `FIREBASE_TEST_GROUP`
> Nome dogrupo que será distribuído o app.

  
  
  

## Funções disponíveis




* __Download project keys__
> Utlizado para baixar e instalar os certificados e profiles existentes no projeto.
```bash
bundle exec fastlane download_keys
```

---
- __Build Distribution (AppDist, App center e Firebase)__
> Função utilizada para gerar uma compilação (.ipa) do projeto utilizando o certificado de __adHoc__. Esta funcão é utilizada apenas para fazer a compilação e posteriormente ser usada pelo CI (Azure Popelines) para submissão para outras ferramentas (Soft App Distribution e Firebase App Distribution).

* __Algumas observações__:
- Caso você queira rodar a função na sua máquina, é necessário alterar a função no arquivo _FastFile_, onde o match gerencia os certificados, substituíndo o atributo __readonly__ de _is_ci_ para _true_.

- Por padrão a compilação é colocada dentro da pasta do projeto e utiliza a identicação inserida na variável  "_ARTIFACT_DEV_NAME_", que está sendo utilizado no atributo "_output_name_"

```bash
bundle exec fastlane build_distribution
```


---

* __Build App Store (TestFlight)__

> Função utilizada para gerar uma compilação (.ipa) do projeto utilizando o certificado de __appStore__. Está funcão será utilizadda pelo CI (Azure DevOps) para gerar o arquivo que posteriormente será enviado para o Test Flight.

* __Algumas observações__:
- Caso você queira rodar a função na sua máquina, é necessário alterar a função no arquivo _FastFile_, onde o match gerencia os certificados, substituíndo o atributo __readonly__ de _is_ci_ para _true_.

- Por padrão a compilação é colocada dentro da pasta do projeto e utiliza a identicação inserida na variável  "_ARTIFACT_PROD_NAME_", que está sendo utilizado no atributo "_output_name_"

```bash
bundle exec fastlane build_appStore
```
---

  

* __Send Soft App Distribution__
> Para enviar para o App Dist, é necessário que o aplicativo tenha sido criado na plataforma [Soft App Distribution](https://app-dist.softdesign.com.br/) .



---

  

- __Automatic upload to Test Flight__

> CHANGE: Update docs (module code remains unchanged)
