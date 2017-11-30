---
title: "Docker コンテナーを .NET Core を選択します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Docker コンテナーを .NET Core を選択します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b7e2322bab7937c41d4659fefef11c8937d5eae7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Docker コンテナーを .NET Core を選択します。

.NET Core のモジュール性および軽量な性質により、コンテナーに最適です。 展開コンテナーを開始すると、そのイメージがよりも .NET Framework での .NET Core とはるかに小さくなります。 これに対しをコンテナーには、.NET Framework を使用して、行う必要があります、イメージは、Windows Nano Server または Linux イメージを .NET core を使用するよりもずっと高い負荷に対応する Windows Server Core イメージにします。

さらに、.NET Core はプラットフォーム間は、Linux または Windows のコンテナー イメージとサーバー アプリケーションを展開することができます。 ただし、従来の .NET Framework を使用している場合は、Windows Server Core のベース イメージをのみ展開できます。

.NET Core を選択する理由の詳細な説明を次に示します。

## <a name="developing-and-deploying-cross-platform"></a>開発およびクロス プラットフォームを展開します。

明らか、してが目的の場合は、.NET Framework には、Windows のみがサポートされるため、最適な選択肢を Docker (Linux と Windows 用) でサポートされている複数のプラットフォームで実行できるアプリケーション (web アプリケーションまたはサービス) .NET Core です。

.NET core は、開発プラットフォームとしても macOS をサポートします。 ただし、Docker ホストにコンテナーを展開するときにホストする必要があります (現在) に基づいて Linux または Windows です。 たとえば、開発環境でする可能性がありますを使用して mac で実行されている Linux VM

[Visual Studio](https://www.visualstudio.com/) Windows の統合開発環境 (IDE) を提供し、Docker の開発をサポートします。 

[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/) macOS で実行されている、Xamarin Studio の進展、IDE は 2017 中旬以降 Docker をサポートしています。

使用することも[Visual Studio Code](https://code.visualstudio.com/) (VS Code) macOS、Linux、および Windows にします。 VS コードは、.NET Core、IntelliSense などのデバッグを完全にサポートします。 VS Code は軽量のエディターであるためには Docker CLI と組み合わせて、Mac 上のコンテナー化アプリケーションを開発するを使用できる、 [.NET Core コマンド ライン インターフェイス (CLI) ツール](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x)です。 .NET Core は Sublime テキスト、Emacs、vi、.NET 言語の IntelliSense サポートを提供した、オープン ソース OmniSharp プロジェクトなどのサードパーティ製エディターで対象することもできます。 Ide およびエディターで、に加えては、サポートされているすべてのプラットフォームの .NET Core CLI を使用できます。

## <a name="using-containers-for-new-green-field-projects"></a>(「緑フィールド」) の新しいプロジェクトのコンテナーの使用

コンテナーは containerize web アプリまたはアーキテクチャのパターンに準拠するサービスを使用することもできますが、一般的 microservices アーキテクチャと組み合わせて使用します。 Windows コンテナーは、モジュールで .NET Framework を使用することができ、.NET Core の軽量な性質により、コンテナーおよび microservices アーキテクチャに最適です。 作成して、コンテナーを展開するときに、そのイメージよりも .NET Framework での .NET Core のはるかに小さくなります。

## <a name="creating-and-deploying-microservices-on-containers"></a>作成とコンテナーの microservices の展開

(コンテナー) なし microservices ベースのアプリケーションを構築するには、標準のプロセスを使用して、従来の .NET Framework を使用する可能性があります。 こうすれば、.NET Framework が既にインストールされ、プロセス間で共有されるのでプロセス薄い高速なを開始します。 ただし、コンテナーを使用している場合、従来の .NET Framework 用の画像もに基づいて Windows Server Core とをなります microservices-コンテナーのアプローチの大きなです。

これに対し、.NET Core は軽量なため、コンテナーに基づいている microservices 指向のシステムを採用は場合に、.NET Core は最適な候補です。 さらに、Linux イメージまたは Windows Nano イメージのいずれか、関連するコンテナー イメージは、リーンと小さいコンテナーのライトを行う起動を高速です。

できるだけ小さくするものでは、マイクロ サービス: 明るい色にする回転しているときに、小さな範囲指定されたコンテキストに関連する要素の小さい領域を表すため、開始し、停止を高速にできるようにして、小さなフット プリントにします。 要件については、.NET Core コンテナー イメージのように小規模で高速のインスタンスのコンテナー イメージを使用するされます。

Microservices アーキテクチャを使用すると、サービス境界を越えてテクノロジを混在させることもできます。 これにより、他の microservices または Node.js、Python、Java、GoLang、またはその他のテクノロジで開発したサービスとの連携を新しい microservices の .NET Core を段階的な移行できます。

## <a name="deploying-high-density-in-scalable-systems"></a>スケーラブルなシステムで高密度を展開します。

コンテナー ベースのシステムには、最適な密度、粒度、およびパフォーマンスが必要がある、.NET Core と ASP.NET Core は、最適なオプションです。 ASP.NET Core は、従来の .NET Framework には、ASP.NET よりも最大でその 10 倍高速と microservices、Java サーブレット、移動、および Node.js などの他の一般的な業界テクノロジを説明します。

これは特に microservices アーキテクチャでは、数百台 microservices (コンテナー) を実行しているがある可能性があります。 ASP.NET Core のイメージ (.NET Core ランタイムに基づく) では、Linux または Windows Nano 程度の数を減らすサーバーまたは Vm、最終的にはインフラストラクチャのコストを保存して、ホスティングを使用してシステムを実行することができます。


>[!div class="step-by-step"]
[前]([全般] guidance.md) [次へ] (net-framework ・ コンテナー ・ scenarios.md)
