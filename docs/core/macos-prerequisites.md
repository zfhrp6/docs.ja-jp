---
title: "Mac における .NET Core の前提条件"
description: "macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係。"
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.openlocfilehash: 16f3cfd482bddfff1b9ad56e7ffe58ae2aed4980
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="prerequisites-for-net-core-on-macos"></a>Macos .NET Core の前提条件

この記事では、macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係を示します。 後述のサポート対象 OS のバージョンと依存関係は、Mac で .NET Core アプリを開発する 3 つの方法 ([好きなエディターでコマンド ラインを使用](tutorials/using-with-xplat-cli.md)、[Visual Studio Code を使用](https://code.visualstudio.com/)、および [Visual Studio for Mac を使用](https://www.visualstudio.com/vs/visual-studio-mac/)) に適用されます。

## <a name="supported-macos-versions"></a>サポート対象の macOS のバージョン

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2.x が macOS の次のバージョンでサポートされている .NET core:

* macOS 10.12"Sierra"とそれ以降のバージョン

.NET Core 2.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1.x が macOS の次のバージョンでサポートされている .NET core:

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

.NET Core 1.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。

---

## <a name="net-core-dependencies"></a>.NET Core の依存関係

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

[.NET ダウンロード](https://www.microsoft.com/net/download/core)から .NET Core SDK をダウンロードしてインストールします。 macOS でインストールに関する問題が発生した場合は、[既知の問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)に関するトピックで、インストールされているバージョンに関する記述をご覧ください。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.x**

macOS で実行する場合、.NET Core 1.x には OpenSSL が必要になります。 OpenSSL を取得する簡単な方法は、macOS の [Homebrew ("brew")](https://brew.sh/) パッケージ マネージャーを使用することです。 *brew* をインストールしたら、端末 (コマンド) プロンプトで次のコマンドを実行して OpenSSL をインストールします。

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

[.NET ダウンロード](https://www.microsoft.com/net/download/core)から .NET Core SDK をダウンロードしてインストールします。 macOS でインストールに関する問題が発生した場合は、「[1.0.0 Known Issues (1.0.0 の既知の問題)](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)」と「[1.0.1 Known Issues (1.0.1 の既知の問題)](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)」のトピックをご覧ください。

---

## <a name="increase-the-maximum-open-file-limit"></a>開いているファイルの最大制限を増やす

既定のファイルを開く上限 macOS いないプロジェクトを復元するか、単体テストの実行など、一部の .NET Core ワークロードのための十分な場合があります。

この制限は、次の手順を向上させることができます。

1. 新しいファイルを作成、テキスト エディターを使用して_/Library/LaunchDaemons/limit.maxfiles.plist_、このコンテンツを含む、ファイルを保存します。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>limit.maxfiles</string>
    <key>ProgramArguments</key>
    <array>
      <string>launchctl</string>
      <string>limit</string>
      <string>maxfiles</string>
      <string>2048</string>
      <string>4096</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>ServiceIPC</key>
    <false/>
  </dict>
</plist>
```

2. ターミナル ウィンドウで、次のコマンドを実行します。

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. これらの設定を適用する Mac を再起動します。

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。 ただし、Mac 上の統合開発環境で .NET Core アプリケーションを開発する場合には、[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/) を使用できます。 

macOS 上で Visual Studio for Mac を使用して .NET Core で開発を行うには、以下のものが必要です。

* サポートされているバージョンの macOS オペレーティング システム
* OpenSSL (.NET Core 1.x のみ。NET Core 2.x では、macOS でネイティブ利用できるセキュリティ サービスが利用されます。)
* .NET Core SDK for Mac
* [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)
