---
title: Docker アプリの開発環境
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ddd1006c8c6728d4d315442f409f8fa33e54f9a3
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="development-environment-for-docker-apps"></a>Docker アプリの開発環境

## <a name="development-tools-choices-ide-or-editor"></a>開発ツールの選択: IDE またはエディター

かにかかわらずする場合、完全かつ強力な IDE または軽量とアジャイル エディターでは、Microsoft に対応する際に Docker アプリケーションを開発します。

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code と Docker CLI (Mac、Linux、および Windows 用のクロスプラット フォーム ツール)

任意の開発言語をサポートする、軽量のクロスプラット フォーム エディターを使用する場合は、Visual Studio Code と Docker CLI を使用できます。 これらの製品では、簡単かつ堅牢なエクスペリエンスを合理化開発者ワークフローにとって重要となるを提供します。 "Docker の Mac"または"Docker for Windows の"(開発環境) をインストールすると、Docker の開発者は、Windows または Linux (ランタイム環境) の両方のアプリをビルドするのに 1 つの Docker CLI を使用できます。 さらに、Visual Studio Code エディターから Docker コマンドを実行するには、Dockerfile とショートカット タスク用の IntelliSense と Docker の拡張機能をサポートしています。

> [!NOTE]
> Visual Studio のコードをダウンロードするには<https://code.visualstudio.com/download>します。

Mac および Windows の Docker をダウンロードするには<http://www.docker.com/products/docker>します。

### <a name="visual-studio-with-docker-tools"></a>Docker ツールと visual Studio

Visual Studio 2015 を使用している場合は、"Docker Tools for Visual Studio です"のアドオン ツールをインストールすることができます。 Visual Studio 2017 の Docker ツールに付属でビルドされた既にです。 どちらの場合に、開発し、実行、および選択した Docker 環境内で直接、アプリケーションを検証することができます。 F5 キーを押して、Docker に直接、アプリケーション (1 つのコンテナーまたは複数のコンテナー) はデバッグは、ホストまたは Ctrl + f5 キーを押して編集し、コンテナーを再構築しなくてもアプリを更新します。 これは、Linux または Windows の Docker コンテナーを作成する Windows 開発者にとって最も簡単で強力な選択肢です。

> [!NOTE]
> Visual Studio の Docker のツールをダウンロードするには<https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>します。

## <a name="language-and-framework-choices"></a>言語やフレームワークの選択

Docker のアプリケーションと最近のほとんどの言語で Microsoft のツールを開発することができます。 最初の一覧を次に示しますが、これに限定されません。

-   .NET core と ASP.NET Core

-   Node.js

-   Golang

-   Java

-   Ruby

-   Python

基本的には、Linux または Windows で Docker でサポートされている最新の言語を使用することができます。


>[!div class="step-by-step"]
[前] (調整-高-スケーラビリティ-availability.md) [次へ] (docker-アプリ-内側のループ-workflow.md)
