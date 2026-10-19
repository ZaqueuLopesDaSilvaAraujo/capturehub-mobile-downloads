# CaptureHub Mobile

O CaptureHub Mobile é um painel sobre o emulador oficial do Google para testar
apps Android no PC, sem o Android Studio, com a evidência no padrão do
CaptureHub: prints, gravações, os passos de cada toque, o relatório HTML e a
apresentação PowerPoint.

Este repositório guarda só os downloads. O produto, com planos, conta e
perguntas frequentes, fica em [capturehub.com.br](https://capturehub.com.br).

## Requisitos

- Windows 10 versão 2004 ou superior, ou Windows 11, de 64 bits
- A virtualização ligada no processador: se faltar, o app mostra o passo a passo
- Espaço livre: o app ocupa uns 280 MB, a primeira execução baixa 2,6 GB do
  Google, e cada aparelho pode chegar a 7 GB depois de usado

## Como baixar

Abra a página [Releases](https://github.com/ZaqueuLopesDaSilvaAraujo/capturehub-mobile-downloads/releases/latest)
e, em **Assets**, escolha uma das duas formas. Os nomes dos arquivos trazem o
número da versão, que muda a cada publicação.

### Instalador

1. Baixe o arquivo terminado em `-instalador.exe`.
2. Execute e siga o assistente. Ele instala só para você, sem pedir
   administrador.
3. O CaptureHub Mobile passa a abrir pelo menu Iniciar.

### Pacote portátil, sem instalar

1. Baixe o arquivo terminado em `.zip`.
2. Extraia todo o conteúdo para uma pasta sua.
3. Abra `CaptureHub.Mobile.exe`, na pasta extraída.

> Não execute o aplicativo de dentro do ZIP. Extraia todos os arquivos antes de
> abrir.

## Conferir o que você baixou

Cada arquivo tem um `.sha256` ao lado, na mesma release. Conferir leva um
segundo e prova que o arquivo que chegou é o mesmo que saiu daqui.

Baixe o `.sha256` junto do arquivo, abra o PowerShell na pasta onde os dois
estão e cole:

```powershell
Get-ChildItem CaptureHubMobile-*.sha256 | ForEach-Object { $esperado = (Get-Content $_).Split()[0]; $arquivo = $_.FullName.Substring(0, $_.FullName.Length - 7); $obtido = (Get-FileHash $arquivo -Algorithm SHA256).Hash; '{0}: {1}' -f (Split-Path $arquivo -Leaf), $(if ($obtido -eq $esperado) { 'confere' } else { 'NAO CONFERE' }) }
```

Se aparecer `NAO CONFERE`, apague o arquivo e baixe de novo.

## Primeiro uso

O pacote ainda não tem assinatura digital. Se o Windows disser "O Windows
protegeu o computador":

1. Clique em **Mais informações**.
2. Confira se o arquivo aberto é o pacote do CaptureHub Mobile que você baixou.
3. Clique em **Executar assim mesmo**.

Com o **Controle Inteligente de Aplicativos** ligado, o Windows bloqueia o
instalador sem essa opção. Nesse caso, use o ZIP.

Enquanto não há assinatura, a conferência do SHA-256 acima é o que prova a
procedência do arquivo.

Na primeira execução, depois que você aceitar a licença do Google, o app baixa
o emulador e o Android 17 e cria um celular e um tablet. Ele só para para
pedir o que é seu: a licença do Google, a Plataforma do Hipervisor do Windows,
que pede a confirmação do Windows e um reinício, e, se for o caso, a
virtualização na BIOS.

## Atalhos principais

| Atalho | Ação |
|---|---|
| Ctrl+Shift+1 | Capturar uma imagem do aparelho |
| Ctrl+Shift+2 | Iniciar ou parar uma gravação |
| Ctrl+Shift+3 | Pausar ou retomar a gravação |
| Ctrl+Shift+M | Marcar um momento da gravação |

## Onde ficam as coisas

| O quê | Onde |
|---|---|
| Evidências | `Documentos\CaptureHub Mobile` |
| Dados do app | `%LOCALAPPDATA%\CaptureHub Mobile` |
| Emulador e versões do Android | `%LOCALAPPDATA%\Android\Sdk` |
| Aparelhos | `%USERPROFILE%\.android\avd` |

A desinstalação, pelo Windows em Aplicativos instalados, nunca apaga as
evidências.
