# CrowChat AI — Android

Aplicativo Android nativo em Kotlin + Jetpack Compose, integrado à API OneTag AI.

## Requisitos
- Android Studio recente
- JDK 17
- Android SDK 35
- Chave API OneTag AI e ID de modelo habilitado na sua conta

## Abrir e executar
1. Extraia `CrowChatAI-Android-Source.zip`.
2. Abra a pasta `CrowChatAI` no Android Studio.
3. Aguarde a sincronização do Gradle.
4. Execute em um dispositivo Android ou emulador.
5. Toque na engrenagem e informe a API Key e o ID exato do modelo fornecido pela OneTag.

## Integração
- Endpoint: `https://onetagai.com/v1/chat/completions`
- Header: `Authorization: Bearer SUA_CHAVE`
- Formato: OpenAI Chat Completions
- Streaming: Server-Sent Events (SSE), `stream: true`

## Recursos implementados
- Chat de texto.
- Streaming de respostas, exibidas progressivamente.
- Histórico de conversas persistido localmente.
- Seleção de conversas anteriores.
- Novo chat.
- Configuração local da chave e do identificador do modelo.
- Mensagens de erro HTTP/API.

## Compatibilidade e segurança
A implementação assume que a OneTag oferece streaming SSE compatível com OpenAI Chat Completions. O suporte precisa ser validado com uma chave e modelo reais. O cabeçalho `Origin` incluído é apenas uma tentativa de compatibilidade; ele não contorna políticas de origem nem garante suporte a clientes nativos. Se a OneTag aceitar somente chamadas feitas por um domínio web autorizado, será necessário usar uma integração web oficial ou um backend próprio autorizado pelo provedor.

A chave fica em SharedPreferences nesta versão de desenvolvimento. Não distribua um APK com uma chave pessoal: chaves embutidas podem ser extraídas. Para produção, use um backend com autenticação, limites de uso, controle de custos e armazenamento seguro. Não compartilhe sua chave em conversas ou capturas de tela.

## Limitações atuais
Sem login, sincronização em nuvem, upload de arquivos, imagens, áudio, ferramentas ou publicação na Play Store.

## Gerar APK pelo GitHub Actions (sem Android Studio)

1. Crie uma conta no GitHub e um repositório vazio chamado `CrowChatAI`.
2. Extraia este ZIP e envie **o conteúdo da pasta `CrowChatAI`** para a raiz do repositório (incluindo a pasta oculta `.github`).
3. No GitHub, abra a aba **Actions** e selecione **Build CrowChat AI APK**.
4. Toque em **Run workflow** e confirme em **Run workflow**.
5. Aguarde o trabalho terminar com sucesso. Abra a execução concluída e baixe o artefato **CrowChatAI-debug-apk**.
6. Extraia o artefato e instale `app-debug.apk` no Android. Se solicitado, permita a instalação pelo navegador/gerenciador de arquivos.

O workflow gera um APK de depuração (debug), adequado para teste. Não é uma versão de produção assinada com uma chave própria. A primeira compilação pode demorar alguns minutos.

**Segurança:** não publique sua chave pessoal da OneTag AI no código-fonte nem compartilhe o APK com uma chave já preenchida. Configure a chave no próprio app; para distribuição pública, prefira um backend que proteja a credencial.
