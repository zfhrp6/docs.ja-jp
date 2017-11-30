---
title: "Docker コンテナーを .NET Framework を選択します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Docker コンテナーを .NET Framework を選択します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1bf1f055f040e7f3dc575b7a04140ebf0c599f98
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Docker コンテナーを .NET Framework を選択します。

.NET Core では、新しいアプリケーションおよびアプリケーションのパターンの重要な利点が用意されています、.NET Framework は引き続きなります多くの既存のシナリオに適してします。

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Windows Server のコンテナーに直接既存のアプリケーションを移行します。

Microservices を作成していない場合でも、だけ展開を簡略化、Docker コンテナーを使用する場合があります。 たとえば、Docker を使用した DevOps ワークフローを向上させたいおそらく — コンテナーがより分離されたテスト環境を移すことができるし、実稼働環境に移動すると、依存関係の欠落による配置の問題を回避できますも。 上記のような場合は、単体のアプリケーションを配置する場合でも理にかなって Docker と Windows コンテナーを使用して、現在の .NET Framework アプリケーション用にします。

このシナリオのほとんどの場合、必要はありません、既存のアプリケーションを .NET Core; を移行するにはDocker コンテナーを含む従来の .NET Framework を使用することができます。 ただし、推奨される方法では、ASP.NET Core で新しいサービスを作成するなど、既存のアプリケーションを拡張するように、.NET Core を使用します。

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>.NET ライブラリのサード パーティ製または NuGet パッケージのない .NET Core を使用します。

サードパーティ製のライブラリが採用すばやく、 [.NET 標準](https://docs.microsoft.com/dotnet/standard/net-standard)コードを .NET Core を含む、すべての .NET フレーバー間で共有できます。 .NET 標準ライブラリ 2.0 以降の API サーフェスさまざまなフレームワークの間で互換性が大きくなり、.NET Core 2.0 のアプリケーションは直接も既存の .NET Framework ライブラリを参照 (を参照してください[compatshim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work))。

ただし、その例外的な進行している .NET 標準 2.0 と .NET Core 2.0 以降を使用する場合でも場合もあります一部の NuGet パッケージが Windows を実行する必要があるし、.NET Core をサポートしていない可能性。 これらのパッケージが、アプリケーションの重要な場合は、Windows コンテナーを .NET Framework を使用する必要があります。

## <a name="usingnet-technologies-not-available-for-net-core"></a>.NET Core では利用できません Using.NET テクノロジ 

一部の .NET Framework テクノロジは、.NET Core (このドキュメントの作成時点でバージョン 2.0) の現在のバージョンでご利用いただけません。 .NET Core の今後のリリースで利用可能なそれらの一部になります (.NET Core 2.x)、その他のユーザーのパターンは、.NET Core の対象となるし、利用できない可能性があります、新しいアプリケーションには適用されません。

.NET Core 2.0 では使用できない、テクノロジのほとんどを次に示します。

-   ASP.NET Web フォームです。 このテクノロジは、.NET Framework をできるだけです。 現時点では、ASP.NET Web フォームを .NET Core で使用できるようにする予定はありません。

-   WCF サービス。 場合でも、 [WCF クライアント ライブラリ](https://github.com/dotnet/wcf).NET Core から WCF サービスを利用することはできます。 mid 2017 時点での WCF サーバーの実装は .NET Framework で使用できるのみです。 このシナリオは、.NET Core の将来のリリースについて検討する可能性があります。

-   ワークフローに関連するサービスです。 Windows Workflow Foundation (WF)、(WCF + 1 つのサービスでの WF) ワークフロー サービスと WCF データ サービス (旧称 ADO.NET Data Services) では、.NET Framework で使用できるのみです。 現在のプランを .NET Core にするためにはありません。

公式に一覧表示、テクノロジだけでなく[.NET Core ロードマップ](https://github.com/aspnet/Home/wiki/Roadmap)、その他の機能は、.NET Core に移植する場合があります。 完全な一覧を参照としてタグ付けされたアイテム[ポートからコア](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core)CoreFX GitHub サイトです。 この一覧は、.NET Core をこれらのコンポーネントをさせる Microsoft からのコミットメントを表さない注: 項目は単に、コミュニティからの要求をキャプチャします。 上に示したコンポーネントについて注意する場合は、自分の声が聞こえるようには、GitHub のディスカッションに参加していることを検討します。 また、何か足りないと感じた場合は、[CoreFX リポジトリで新しい案件を作成](https://github.com/dotnet/corefx/issues/new)してください。

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>プラットフォームまたは .NET Core をサポートしていない API を使用

一部の Microsoft またはサード パーティのプラットフォームでは、.NET Core をサポートしていません。 たとえば、一部の Azure サービスは、されていない .NET Core で利用できるよう SDK を提供します。 これは、機能は、すべての Azure サービスの .NET Core を最終的に使用するため、一時的なです。 など、 [Azure DocumentDB の SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) 2016 年 11 月 16 日でプレビューとしてリリースされましたが安定したバージョンとして一般公開 (GA) ではようになりました。

その間は、任意のプラットフォームまたは Azure のサービスもサポートしていない場合 .NET Core そのクライアント API と、.NET Framework での Azure サービスまたはクライアント SDK から同等の REST API を使用できます。

### <a name="additional-resources"></a>その他の技術情報

-   **.NET core ガイド**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)

-   **.NET Framework から .NET Core への移植**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)

-   **Docker のガイドに .NET framework**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)

-   **.NET コンポーネントの概要**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)




>[!div class="step-by-step"]
[前](net-コア-コンテナーの scenarios.md) [次へ] (コンテナーのフレームワークの選択-factors.md)
