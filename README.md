# Template CI/CD

# Descrição
Este é um template de exemplo inicial para colocar nos projetos, com alguns ajustes e o CI/CD já estará funcionando.


# Setup
Para rodar o CI/CD em seu projeto esse template utiliza 6 arquivos que vai rodar comandos para garantir a qualidade do seu código, sendo estes:


* cd.yml
* ci.yml
* dart_package.yml
* flutter_package.yml
* dartcodemetrics.yml
* semantic_pull_request.yml


# Função dos arquivos
## CD
* cd.yml - Este arquivo é responsável por fazer o Build do Android e do IOS, nele contém as configurações necessárias para fazer os Builds. Mais caso queira modificar alguma configuração aqui está a documentação desta Action:
[Flutter Action](https://github.com/marketplace/actions/flutter-action)


## CI
* ci.yml - Este arquivo é responsável por informar o caminho da pasta do App e dos packages caso haja, nele pode-se setar a versão do Dart/Flutter que cada package está utilizando e indicar o arquivo que irá analisar cada um, também é possível indicar quando ira rodar o CI e em qual branch como no exemplo abaixo:
```yml
 on:
  pull_request:
  push:
    branches:
      - main
```


## Dart Package
* dart_package.yml - Este arquivo é responsável por rodar todos os comandos e analisar os packages, este também contem os comandos necessario para fazer uma analise completa e garantir a qualidade do código, porém é possivel adicionar outras configurações e para mais informações sobre aqui está a documentação desta Action: [Setup Dart SDK](https://github.com/marketplace/actions/setup-dart-sdk)


## Flutter Package
* flutter_package.yml - Este arquivo é responsável por rodar os comandos e analisar o App na parte do Flutter, por padrão ele também contem as configurações essenciais para fazer uma analise completa do código, porém é possivel adicionar novas Action e outros comandos para uma analise mais completa através da documentação: [Flutter Action](https://github.com/marketplace/actions/flutter-action)


## Dart Code Metrics
* dartcodemetrics.yml - Este arquivo é responsável por fazer a análise estática que ajuda você a analisar e melhorar a qualidade do seu código, as configurações utilizada são as essenciais porém caso queira adicionar novos comandos segue a documentação: [Dart Code Metrics Action](https://github.com/marketplace/actions/dart-code-metrics-action)


## Semantic Pull Request
* semantic_pull_request.yml - Este arquivo é responsável por validar os títulos de RP e se corresponde às especificações de Commits convencionais. Para mais informações sobre está Action de uma conferida na documentação: [semantic-pull-request](https://github.com/marketplace/actions/semantic-pull-request)


# Como usar os arquivos
  O arquivo que tem mais configuração manual é o de CI pois o usuário deve passar os caminhos e o nome das pastas no qual ele vai querer que o CI analise, os demais arquivos poderão ser alterados mais não é necessário, tem comentário nos arquivos onde deve ser configurado versão que está sendo utilizado no App da SDK do Flutter e do Dart, e o nome das pasta do package assim como no exemplo abaixo:
  ``` yml
  check-app:
    # Passar o nome do arquivo que vai rodar os comandos do CI
    uses: ./.github/workflows/flutter_package.yml
    with:
      # Setar versão que o App está utilizando
      flutter_version: "3.3.9"
      # Nome da pasta do App
      working_directory: app_exemple
  ```