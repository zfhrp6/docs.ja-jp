---
title: "Azure Service Fabric を使用します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Azure Service Fabric を使用します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: aa15f9cf9bc60e9e70607da921f2ce2c75e39ec2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="using-azure-service-fabric"></a>Azure Service Fabric を使用します。

サービスを提供することをスタイルで通常モノリシック個、ボックス製品を提供するから移行する Microsoft の azure Service Fabric が発生しました。 構築し、規模では、Azure SQL Database、Azure Cosmos DB、Azure Service Bus、Cortana のバックエンドなどの大規模なサービスを運用環境では、Service Fabric を形です。 プラットフォームはますます多くのサービスで採用して時間の経過と共に進歩しました。 重要なは、Service Fabric は、Azure では、スタンドアロン Windows Server の展開でもを実行する必要があります。

Service Fabric の目的は、チームが microservices アプローチを使用するビジネス上の問題を解決できるようにを構築およびサービスを実行してインフラストラクチャ リソースを効率的に活用して困難な問題を解決するために、します。

Service Fabric は、microservices アプローチを使用するアプリケーションを構築するための 2 つの広範な領域を提供します。

-   システム サービスを展開、拡張、アップグレード、検出すると、および失敗したサービスを再起動して、サービスの場所を検出、状態を管理、および正常性を監視を提供するプラットフォームです。 有効で、これらのシステム サービスでは、前に説明した microservices の特性を数多く有効にします。

-   プログラミング Api、またはフレームワーク、microservices としてアプリケーションを構築できるようにする:[信頼性の高いアクターと信頼性の高いサービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)です。 もちろん、マイクロ サービスを構築するためのコードを選択できますが、これらの Api ジョブさらにわかりやすい行い深いレベルでプラットフォームと統合します。 正常性と診断情報を取得するこの方法では、信頼性の高い状態管理を利用できます。

Service Fabric は、サービスを構築する方法に関して依存しないと、任意のテクノロジを使用することができます。 ただし、microservices をビルドしやすく組み込みのプログラミング Api を提供します。

図 4-26 を示すようにすることができますで作成および実行 microservices Service Fabric 簡単なプロセス、または Docker のコンテナーとして。 同じ Service Fabric クラスター内のプロセスに基づく microservices でコンテナー ベース microservices を混在させることもできます。

![](./media/image30.png)

**図 4-26**です。 プロセス、または Azure Service Fabric 内のコンテナーとして microservices を展開します。

Linux と Windows のホストに基づいて Service Fabric クラスター Docker Linux コンテナーと Windows コンテナーをそれぞれ実行することができます。

Azure Service Fabric でのコンテナーのサポートの最新の状態については、次を参照してください。 [Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)です。

Service Fabric は、プラットフォームの良い例は異なる論理アーキテクチャ (ビジネス microservices または範囲指定されたコンテキスト) で導入された物理的な実装を定義することができます、[物理と論理アーキテクチャアーキテクチャ](#logical-architecture-versus-physical-architecture)セクションです。 実装する場合など、[ステートフル Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)で[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)のセクションで導入されたを[ステートレスとステートフル microservices](#stateless-versus-stateful-microservices)後で、複数の物理サービスを含むビジネス マイクロ サービスの概念ことができます。

図 4-27、および Service Fabric ステートフルの信頼性の高いサービスを実装する場合、論理/ビジネス マイクロ サービスの観点から考えることに示す、通常必要がありますを 2 層のサービスを実装します。 最初は、バック エンド ステートフルな信頼性の高いサービス、(各パーティションは、ステートフルなサービスを) 複数のパーティションを処理します。 2 つ目は、フロント エンド サービスは、または複数のパーティションまたはステートフルなサービス インスタンス間のルーティングとデータの集計を担当する、ゲートウェイ サービスです。 そのゲートウェイ サービスは、再試行のループがバックエンド サービスにアクセスするクライアント側の通信を処理します。
カスタム サービス、またはボックスの Service Fabric を使用することもできます。 alternatevely を実装する場合に、ゲートウェイ サービスが呼び出された[リバース プロキシ サービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)です。

![](./media/image31.png)

**図 4-27**です。 いくつかのステートフルなサービス インスタンスとフロント エンドのカスタムのゲートウェイのビジネス マイクロ サービス

いずれの場合は、Service Fabric ステートフル Reliable Services を使用する場合もがある場合、論理またはビジネス マイクロ サービス (範囲指定されたコンテキスト) 複数の物理サービスで構成される通常します。 それぞれに、ゲートウェイ サービスおよびパーティションのサービスのアドレスは、図 4-26 を示すように、ASP.NET Web API サービスとして実装できます。

Service Fabric でグループ化し、としてのサービスのグループを展開、 [Service Fabric アプリケーション](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)、これはパッケージ化と、orchestrator またはクラスターの配置の単位。 そのため、Service Fabric アプリケーション マップすることもこの自律的なビジネスおよび論理マイクロ サービス境界または範囲指定のコンテキストでは、同様に、ため、これらのサービスは自律的に展開する可能性があります。

## <a name="service-fabric-and-containers"></a>Service Fabric とコンテナー

サービス ファブリック内のコンテナー、に関して、Service Fabric クラスター内のコンテナー イメージのサービスを展開することもできます。 図 4-28 では、ほとんどの場合のみありますサービスごとの 1 つのコンテナー。

![](./media/image32.png)

**図 4-28**です。 Service Fabric でいくつかのサービス (コンテナー) を使ってビジネス マイクロ サービス

ただし、いわゆる「サイドカー」コンテナー (論理サービスの一部としてまとめて配置する必要のある 2 つのコンテナー) が Service Fabric 可能もです。 重要な点は、ビジネス マイクロ サービスがいくつかのまとまりのある要素を囲む論理的な境界でことです。 多くの場合、1 つのデータ モデルを含む 1 つのサービスかもしれませんが、場合によっては他の物理的ないくつかのサービスもする必要があります。

Mid 2017 時点で Service Fabric でできませんサービスを配置する SF 信頼性の高いステートフル コンテナーに対する — ステートレスなサービスとアクター サービス コンテナーにのみ展開できます。 図 4-29 のように、同じ Service Fabric アプリケーション内のコンテナーでのプロセスでのサービスとサービスを混在させることがある注意してください。

![](./media/image33.png)

**図 4-29**です。 コンテナーとステートフル サービスの Service Fabric アプリケーションにマップされているビジネス マイクロ サービス

Azure Service Fabric でのコンテナーのサポートの詳細については、次を参照してください。 [Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)です。

## <a name="stateless-versus-stateful-microservices"></a>ステートレスとステートフル microservices

前述のように、各マイクロ サービス (論理範囲指定されたコンテキスト) は、ドメイン モデル (データとロジック) を所有する必要があります。 ステートレス microservices の場合、データベースは、外部、SQL Server のようなリレーショナル オプションまたは MongoDB や Azure Cosmos DB などの NoSQL オプションを採用することになります。

サービス自体は、マイクロ サービス内でデータが格納されていることを意味する Service Fabric でステートフルなすることもできます。 このデータはだけでなく、同じサーバーがメモリ内のマイクロ サービス プロセス内で可能性がありますが存在してハード ドライブ上に保存し、その他のノードにレプリケートします。 図 4-30 では、別の方法を示します。

![](./media/image34.png)

**図 4-30**します。 ステートレスとステートフル microservices

ステートレスな方法は、完全に有効なアプローチは、従来の既知のパターンに似ていますので、ステートフルの microservices よりも実装する方が簡単。 ステートレス microservices プロセスおよびデータ ソース間の待機時間を強制します。 それに伴うより移動の個追加のキャッシュとキューのパフォーマンスを改善しようとします。 結果は、多数の階層のある複雑なアーキテクチャを持つ終了できます。

これに対し、[ステートフル microservices](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)ドメイン ロジックとデータ間の待機時間がないために、高度なシナリオは、excel ことができます。 大量のデータ処理、戻るゲームが終了をサービスとしてのデータベースとすべて他の低待機時間シナリオがステートフルなサービスは、ローカル アクセスの状態を高速化を有効に活用できます。

ステートレスおよびステートフルなサービスは、相互に補完します。 たとえば、ステートフルなサービスに複数のパーティション分割することで右側の図では、図 4-30 を確認できます。 それらのパーティションにアクセスするには、パーティション キーに基づく各パーティションに対処する方法を知っているゲートウェイ サービスとして動作するステートレスなサービスを必要があります。

ステートフルなサービスでは、欠点がします。 スケール アウトでは、複雑さのレベルをかけます。外部データベース システムで実装する場合と通常の機能は、ステートフルな microservices とデータのパーティション分割の間でデータのレプリケーションなどのタスクの対処をする必要があります。 ただし、これは、orchestrator のような領域の 1 つ[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture)でその[ステートフルな信頼性の高いサービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)最も役立つことができます: 開発とステートフルのライフ サイクルを簡略化microservices を使用して、 [Services API の信頼性の高い](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections)と[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)です。

他のステートフルなサービス、Actor パターンをサポートして、フォールト トレランスとビジネス ロジックとデータ間の待機時間を向上できるようにするマイクロ サービス フレームワークは Microsoft [Orleans](https://github.com/dotnet/orleans)、Microsoft Research とから[Akka.NET](http://getakka.net/)です。 両方のフレームワークは、現在 Docker のサポートを向上させます。

Docker コンテナーは自身のステートレスなことに注意してください。 ステートフルなサービスを実装する場合は、前に説明した追加の規範的な高度なフレームワークの 1 つ必要があります。 

>[!div class="step-by-step"]
[前](scalable-available-multi-container-microservice-applications.md) [次へ] (../docker-application-development-process/index.md)
