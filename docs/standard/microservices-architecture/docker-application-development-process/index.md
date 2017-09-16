---
title: "Docker ベースのアプリケーションの開発プロセス"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker ベースのアプリケーションの開発プロセス"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: f4c241f463ff1270037c7d66ba39409ca5d9e728
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---
# <a name="development-process-for-docker-based-applications"></a>Docker ベースのアプリケーションの開発プロセス

*Visual Studio と Visual Studio Tools for Docker を使用して IDE に重点を置くか、Docker CLI と Visual Studio Code を使用して CLI/エディターに重点を置くか、好みの方法でコンテナー化された .NET アプリケーションを開発します。*

## <a name="development-environment-for-docker-apps"></a>Docker アプリの開発環境

### <a name="development-tool-choices-ide-or-editor"></a>開発ツールの選択: IDE またはエディター

完全で強力な IDE または軽量でアジャイルなエディターのどちらを選んでも、Microsoft では Docker アプリケーションの開発に使用できるツールが用意されています。

**Visual Studio と Tools for Docker**。 Visual Studio 2015 を使用している場合は、[Visual Studio Tools for Docker](https://marketplace.visualstudio.com/items?itemName=MicrosoftCloudExplorer.VisualStudioToolsforDocker-Preview) アドインをインストールできます。 Visual Studio 2017 を使用している場合は、Tools for Docker が既に組み込まれています。 いずれの場合も、Tools for Docker を使用して、ターゲットの Docker 環境で直接アプリケーションの開発、実行、および検証ができます。 F5 キーを押すと、Docker ホスト内で直接アプリケーション (1 つのコンテナー、または複数のコンテナー) を実行してデバックできます。または、CTRL キーを押しながら F5 キーを押すと、コンテナーを再構築しなくても、アプリケーションを編集して更新できます。 これは、Linux または Windows の Docker コンテナーをターゲットとする Windows 開発者にとって最も簡単で最も強力な選択肢です。

**Visual Studio Code と Docker CLI**。 任意の開発言語をサポートする軽量なクロスプラット フォーム エディターを選択すると、Microsoft Visual Studio Code (VS Code) と Docker CLI を使用することができます。 これは、Mac、Linux、および Windows のクロスプラット フォーム開発アプローチです。

これらの製品は、開発者のワークフローを効率化する、単純ながらも信頼性の高いエクスペリエンスを提供します。 [Docker Community Edition (CE)](https://www.docker.com/community-edition) ツールをインストールすることで、1 つの Docker CLI を使用して Windows と Linux の両方のアプリを構築することができます。 さらに、Visual Studio Code は、Dockerfiles の IntelliSense などの Docker の拡張機能や、エディターから Docker コマンドを実行するショートカット タスクをサポートします。

### <a name="additional-resources"></a>その他の技術情報

-   **Visual Studio Tools for Docker**
    [*https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4*](https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4)

-   **Visual Studio Code**。 公式サイト。
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   **Mac および Windows の Docker Community Edition (CE)**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>.NET 言語および Docker コンテナーのフレームワーク

このガイドの前のセクションで触れたように、Docker コンテナー化された NET アプリケーションを開発する際に、.NET Framework、.NET Core、またはオープン ソースの Mono プロジェクトを使用できます。 Linux または Windows コンテナーをターゲットにする場合、使用している .NET Framework に応じて、C\#、F\#、または Visual Basic で開発できます。 .NET 言語の詳細については、ブログ投稿「[The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/)」 (.NET 言語戦略) を参照してください。


>[!div class="step-by-step"]
[前へ] (../architect-microservice-container-applications/using-azure-service-fabric.md) [次へ] (docker-app-development-workflow.md)

