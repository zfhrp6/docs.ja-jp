---
title: "Mac における .NET Core の前提条件 | Microsoft Docs"
description: "macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係。"
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 03/16/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: ff143583ba62fc1d82561e739a75107e50ebee88
ms.openlocfilehash: da75f5fd56b7ce66b2c46ef488e6e26c55a63ee2
ms.lasthandoff: 03/20/2017

---

# <a name="prerequisites-for-net-core-on-mac"></a>Mac における .NET Core の前提条件

この記事では、macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係を示します。 後述のサポート対象 OS のバージョンと依存関係は、Mac で .NET Core アプリを開発する 3 つの方法 ([好きなエディターでコマンド ラインを使用](tutorials/using-with-xplat-cli.md)、[Visual Studio Code (VS Code) を使用](https://code.visualstudio.com/)、および [Visual Studio for Mac を使用](https://www.visualstudio.com/vs/visual-studio-mac/)) に適用されます。

## <a name="supported-macos-versions"></a>サポート対象の macOS のバージョン

.NET Core は、macOS の次のバージョンでサポートされています。

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

サポート対象のオペレーティング システムの完全なリストは、[.NET Core のリリース ノート](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md)で確認してください。

## <a name="net-core-dependencies"></a>.NET Core の依存関係

macOS で実行する場合、.NET Core には OpenSSL が必要になります。 OpenSSL を取得する簡単な方法は、macOS の [Homebrew ("brew")](http://brew.sh/) パッケージ マネージャーを使用することです。 *brew* をインストールしたら、端末 (コマンド) プロンプトで次のコマンドを実行して OpenSSL をインストールします。

```Terminal
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

OpenSSL をインストールしたら、公式の [.NET Core SDK for Mac インストーラー](https://go.microsoft.com/fwlink/?linkid=843444)を取得します。 .NET Core 1.1.1 が最新バージョンです。 長期サポート バージョンとその他のダウンロードについては、「[.NET Downloads: All downloads](https://www.microsoft.com/net/download/core)」 (.NET ダウンロード: すべてのダウンロード) を参照してください。 macOS でインストールに関する問題が発生した場合は、「[Known issues & workarounds](https://github.com/dotnet/core/blob/master/cli/known-issues.md)」 (既知の問題と回避策) を参照してください。

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

macOS 上で Visual Studio for Mac を使用して .NET Core で開発を行うには、以下のものが必要です。

* サポートされているバージョンの macOS オペレーティング システム
* Openssl
* .NET Core SDK for Mac
* [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

