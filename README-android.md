
# Setup iOS Android


## Passo 2: Instalar e configurar o Fastlane

Para obter instruções de instalação do fastlane, consulte [Instalando _fastlane_](https://docs.fastlane.tools/getting-started/android/setup/).
É recomendado seguir a instalação via [_Bundler_](https://bundler.io/), além de instalar um gerenciador de versões do Ruby o [_rbenv_](https://github.com/rbenv/rbenv#readme).

## Passo 3: Inserir variáveis de ambiente
Para rodar esse projeto, você vai precisar adicionar as seguintes variáveis de ambiente no seu .env localizado dentro da pasta _fastlane_.

#### Informações do app
* `PACKAGE_NAME`
  > Identifier do app. _Ex.: br.com.example_

#### Assinatura do app
- `STORE_FILE`
  > Caminho para a keystore (.jks) do projeto.

* `STORE_PASSWORD`
  > Senha da Keystore.

* `KEY_ALIAS`
  > Key alias da keystore.

* `KEY_PASSWORD`
  > Key alias password.

* `PLAY_STORE_CONFIG_JSON`
  > Esse arquivo é um token para o CI conseguir submeter versões diretamente na Google Play.
  > Você pode obter essa chave em:  

Aqui está um exemplo:
 ```
{
    "type": "service_account",
    "project_id": "pc-api-5599031065322202413-580",
    "private_key_id": "cf9e2f5b13dda4d90086fdf4ecdf94cb008e1322",
    "private_key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQDjROC/pm1Sf+gE\nyYJYjnSTfaaGJQZmlo+ULRnW+fpz6ZRpagAwkHLY/jyTfL4QoId+cramOMOmdShn\n7lvzDO+S6JAdJP9It4XuIX2qR2/ocTL5AMILGe4mKjjlLlPas7SVLSFR7qc41ax5\nfIQsFpvw43tWdNmes8g80paXHLYsFWyRvrFqZ6bEqFeQUSnk2oIIbRkVGVjzaTS4\nTPuds1+2kGd/Wh9zgd2HS3K8AEYcpUWbhUMDXKwoBic4VdnzStf19s7CluCJqFcf\n4RTmPcENkebCruHTfNuKEN/f2o67hPtBTiOFhPee0iB0VcXmzxOy/Z6BOUC6A3Ll\nhxpA97pRAgMBAAECggEAGYwZk5GawmZcZ4VbYKcK1bWPLY8l7AxKsYZsXC0XiUYd\nh8gBo3PpZRkXKCEioG3bLUyp2X+SBrkuxJgXv/eZSrNX197bz4nJxV4AaU7EdqWa\n7EC4j1Tn32RppuGRTYlb6FT9ZN9l7s6eJ73mgao891Qq/in+eIePH78wbGYu2D+O\nCHkSzrUIVALASCsJUUbNoGCV2oMjugks8NcUIWbxGIQeLVd7LR23Zb85sJ7qW8tP\n6lN7+e49h/PcEJOZ3IMFhNVigWe02yzrQ+QjqwSqWTZNFs/ZayJJmp/lIHxFLV5O\n22bzdqvoAqlRsBPsK/yzvRPZj9KQp3RqsxQqoNhkbQKBgQD3kkB6+p2tFE2O6v9x\n5MSDUMfj6hVMg/FJKrE59ZEMuSJlFVWgzksT98a1Zp7Sdi8gLPYh8d7Bgz+e0EEk\nLWGvSD7QpBc2Nwq+VETbwZh8xNcAOEZJHseoVort2B82ZWZGTjMSXYy7oCxammUg\nn9XQN2lsn8sCNTpu5yUu8WtTGwKBgQDrAa20nrTYrOB9anFBJV41O6+xrBxUiN+u\n4T/74V01FuTLSQ1WfSbI4l/jzn8g6+/0GZ4GtrfuqvtryuKwshuLcR5sLaRi84ON\n2xgwsYsfUJh87s1cuo5TCPALYlhJKdUHqeUj7xtF4OzbutFlp2h4wu8cur/+TQJ8\nax5XaoxTAwKBgQDzUF/i/dBdvKiFH9yyeR3R2WC7VOJd8wb+2+CWkAxgrstpAVDI\n3DbZhxlaS2MogVLLkqTMs8Qz9+RdF1wOTDPHa3+g2sSdWfdLG9MZD+noJiUQaD5b\nus6LWZLtMw1qDro3ur9i+2JHPKKa4UcmizA+xyz+WV7pQKBgCXE\nK0ovhxibD6iYBoNVogIkCWQgKJ1dMbVE9adg3D2/5BzXLJGNo0H9PzO4560+vV0Z\nENA7ZOuyBp2YCT4kIVETaLQx0Y0lXSra3tRUc+sgZKEPL2mLgXvOn+T0dQOs+VM1\n9mED9/oO34GgUC5p7NwbV5niWSBg99lOzZ12vf5JAoGAKZII+DK8jTD0qTRvvy9M\nBuF3O2Wyd9DetnS9jwlwO4SDB5lFn7zK6huRGdeOF1XzHMRrRY+zxpHW8c8iLM4v\nxwLKymJ0RDUfN4q4eZN5lNpCuk9k7Q1AlyCW/I31oB1BWEI/JJ2MdBq2gUSs71dA\nGvOJEkwE9r1mNI/MQqs7ExQ=\n-----END PRIVATE KEY-----\n",
    "client_email": "auth-sp-suite@pc-api-5599031065322202413-999.iam.gserviceaccount.com",
    "client_id": "11414700653889411065607",
    "auth_uri": "https://accounts.google.com/o/oauth2/auth",
    "token_uri": "https://oauth2.googleapis.com/token",
    "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
    "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x798/auth-sp-suite%40pc-api-5599031065322202413-660.iam.gserviceaccount.com"
  }
```
Para obter essa chave, é necessário ser um __administrador__ da conta de desenvolvimento da Google.
Esta opção estará disponível em: App Store Connect -> User and Access -> Keys (Conforme a imagem abaixo).
O arquivo que é gerado é um .p8 que contém um token (É possível abrir em qualquer editor de texto) e é com ele que deverá ser preenchido o atributo ___key___ do JSON acima.
Os outros atributos são preenchidos com os valores obtidos no portal conforme a foto.

<p align="center">
  <img src="images/api_key_location.png" width="600">
</p>

  > ---

#### Variáveis Azure 
 - `URL_DOMAIN`
O valor desta variável pode ser encontrado na url do repositório do projeto (conforme foto abaixo). O valor à ser preenchido deve ser somente a string que sucede o '__@__'.
<p align="center">
  <img src="images/create_url.png" width="600">
</p>
 - `AZURE_TOKEN`
O valor desta variável pode ser encontrado no portal da Azure no caminho ilustrado na imagem abaixo
<p align="center">
  <img src="images/create_token.png" width="400">
</p>

_Exemplo de resultado:_
<p align="center">
  <img src="images/urls_result.png" width="600">
</p>


## Passo 4: Submeter certificados para o git
Ao criar o setup do projeto, deverá ser criado todos os certificados e profiles no portal developer normalmente.
Após isso, será necessário adicionar todos eles em um repositório git (pode ser o mesmo do projeto, ou o mais recomendado, que é criar um um novo só para estes arquivos), para que o fastlane (através do __match__) possa utiliza-los e gerencia-los sempre que necessário.
Para adicionar os certificados no repositório, (já com o ambiente configurado e variáveis de ambiente preenchidas), deverá ser utilizado os seguintes comandos:

```bash
bundle exec fastlane match import --skip_certificate_matching true --type appstore
```

_Obs.: O comando mostrado acima, se aplica apenas para o certificado de distribuição na appstore. O mesmo comando deve ser utilizado para os certificados de __adhoc__ e __development__, substituindo apenas o type para o correspondente._

Ao fazer isso, será necessário passar três arquivos (__.cer__, __.p12__ e __.mobileprovision__) para cada um dos três comandos (--type appstore, --type adhoc e --type development).



## Passo 5: Configurar pipeline

-   #### Preencher variáveis na Azure Dev Ops
	- Deverá ser preenchido o valor de todas as variáveis do projeto no portal da Azure em __Pipelines -> Library__

-   #### Configurar deploy

 ```
	parameters:
		-  	name: softAppDist
			displayName: Upload to Soft App Dist
			type: string
			default: 'Yes'
			values:
			-  'Yes'
			-  'No'

		-  	name: testFlight
			displayName: Upload to TestFlight
			type: string
			default: 'No'
			values:
			-  'Yes'
			-  'No'
```
#####  Criar .env
 ```
-  script:  |
			cd app/ios/fastlane #Caminho para a pasta do fastlane
			echo "URL_DOMAIN=$URL_DOMAIN" > .env
			echo "AZURE_TOKEN=$AZURE_TOKEN" >> .env
			echo "ARTIFACT_PROD_NAME=$ARTIFACT_PROD_NAME" >> .env
			echo "ARTIFACT_DEV_NAME=$ARTIFACT_DEV_NAME" >> .env
			echo "APP_IDENTIFIER=$APP_IDENTIFIER" >> .env
			echo "WORKSPACE=$WORKSPACE" >> .env
			echo "SCHEME=$SCHEME" >> .env
			echo "TEAM_ID=$TEAM_ID" >> .env
			echo "IC_TEAM_ID=$IC_TEAM_ID" >> .env
			echo "MATCH_PASSWORD=$MATCH_PASSWORD" >> .env
			echo "MATCH_KEYCHAIN_PASSWORD=$MATCH_KEYCHAIN_PASSWORD" >> .env
			echo "APP_STORE_CONNECT_APPLE_ID=$APP_STORE_CONNECT_APPLE_ID" >> .env
			echo "AUTH_APP_STORE_CONNECT_API_KEY=$AUTH_APP_STORE_CONNECT_API_KEY" >> .env
	displayName:  '.env fastlane file creation'
```

#####  Gerar .ipa utilizando as funções disponíveis do arquivo FastFile da pasta fastlane
 ```
-  task:  Bash@3
	condition:  eq('${{ parameters.softAppDist }}', 'Yes')
	inputs:
		targetType:  'inline'
		script:  |
			bundle install
			bundle exec fastlane build_distribution
displayName:  'Build iOS'
```
#####  Enviar artefato para o Soft App Dist
 ```
-  task:  deploy-app-binary@0
	condition:  eq('${{ parameters.softAppDist }}', 'Yes')
	inputs:
		projectId:  "ID do projeto"
		apiKey:  "Key do projeto"
		filePath:  app/ios/nomeDoApp.ipa (local do .ipa)
	displayName:  Upload app to App Dist system
```

#####  Enviar artefato para o Test Flight
 ```
-  task:  Bash@3
	condition:  eq('${{ parameters.testFlight }}', 'Yes')
	inputs:
		targetType:  'inline'
		script:  |
			bundle install
			bundle exec fastlane build_appStore
displayName:  'Build iOS'
```

---
 ### Funções disponíveis
 -  __Download project keys__
 Utilizado para baixar e instalar os certificados e profiles existentes no projeto.
```bash
bundle exec fastlane download_keys
```
   - __Build Distribution (AppDist, App center e Firebase)__
Função utilizada para gerar uma compilação (.ipa) do projeto utilizando o certificado de __adHoc__. Esta funcão é utilizada apenas para fazer a compilação e posteriormente ser usada pelo CI (Azure Popelines) para submissão para outras ferramentas (Soft App Distribution e Firebase App Distribution).

  -  __Algumas observações__:
Por padrão a compilação é colocada dentro da pasta do projeto e utiliza a identificação inserida na variável  "_ARTIFACT_DEV_NAME_", que está sendo utilizado no atributo "_output_name_"

```bash
bundle exec fastlane build_distribution
```

* __Build App Store (TestFlight)__
Função utilizada para gerar uma compilação (.ipa) do projeto utilizando o certificado de __appStore__. Está funcão será utilizada pelo CI (Azure DevOps) para gerar o arquivo e envia-lo para o Test Flight.

  * __Algumas observações__:
Não esqueça de versionar o app corretamente antes de submete-lo.
Por padrão a compilação é colocada dentro da pasta do projeto e utiliza a identificação inserida na variável  "_ARTIFACT_PROD_NAME_", que está sendo utilizado no atributo "_output_name_"

```bash
bundle exec fastlane build_appStore
```
## Passo 6: Executar pipeline
Para executar o pipeline, você pode ir até a área "Pipelines" no portal Azure, selecionar a branch e os atributos desejados e executar, conforme a imagem abaixo:
<p align="center">
  <img src="images/execute_pipe.png" width="600">
</p>



## Extra: Configurar projeto no App Dist
Para disponibilizar o app para testes , é necessário que o aplicativo tenha sido criado na plataforma [Soft App Distribution](https://app-dist.softdesign.com.br/) .
Aqui está um exemplo de como criar:
<p align="center">
  <img src="images/app_dist_1.png" width="370">
  <img src="images/app_dist_2.png" width="330">
  <img src="images/app_dist_3.png" width="300">
</p>



_Obs.: Os atributos sublinhados na última imagem, são utilizados na configuração da task "deploy-app-binary@0" da Azure no arquivo de review e deploy (.yaml) do projeto._ 
