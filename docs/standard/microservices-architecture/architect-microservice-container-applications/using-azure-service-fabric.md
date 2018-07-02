---
title: Azure Service Fabric の使用
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | Azure Service Fabric の使用
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 5058023aa7cbb42bcf39d061a3273b30e0e9b74c
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105821"
---
# <a name="using-azure-service-fabric"></a>Azure Service Fabric の使用

Azure Service Fabric は、一般的にモノリシックなスタイルのボックス製品の提供からサービスの提供へというマイクロソフトの変換から生まれました。 Azure SQL データベース、Azure Cosmos DB、Azure Service Bus、Cortana のバックエンド、成形された Service Fabric. などの規模なサービスの構築と運用の経験。 プラットフォームは時間をかけてより多くのサービスを採用するように進化しました。 重要なのは、Service Fabric は、Azure 内だけでなく、スタンドアロン Windows Server の展開でも実行する必要があることです。

Service Fabric の目的は、サービスの構築と実行、インフラストラクチャ リソースの効率的な使用に関連する困難な問題を解決し、チームがマイクロサービス アプローチを使用してビジネスの問題を解決できるようにすることです。

Service Fabric は、マイクロサービス アプローチを使用するアプリケーションの構築に役立つ 2 つの広範な領域を提供します。

-   展開、拡張、アップグレード、検出のためのシステム サービス、失敗したサービスの再起動、サービスの場所の検出、状態の管理、正常性の監視を提供するプラットフォーム。 これらのシステム サービスによって、前に説明したマイクロサービスの特性の多くが実質的に有効になります。

-   アプリケーションをマイクロサービスとして構築するために役立つプログラミング API またはフレームワーク: [Reliable Actors と Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)。 もちろん、マイクロサービスを構築するための任意のコードを選択できますが、これらの API によってジョブがさらにわかりやすくなり、より深いレベルでプラットフォームと統合されます。 この方法で正常性情報と診断情報を取得し、信頼できる状態管理を利用することができます。

Service Fabric は、サービスの構築方法に依存しないので、任意のテクノロジを使用することができます。 ただし、マイクロサービスをビルドしやすくする組み込みのプログラミング API を提供します。

図 4-26 に示すように、単純なプロセスまたは Docker コンテナーとして、Service Fabric 内でマイクロサービスを作成して実行することができます コンテナーベースのマイクロサービスとプロセッサーベースのマイクロサービスを同じ Service Fabric クラスター内に混在させることもできます。

![](./media/image30.png)

**図 4-26** Azure Service Fabric 内のプロセッサーまたはコンテナーとしてマイクロサービスを展開する

Linux と Windows のホストに基づく Service Fabric クラスターは、Docker Linux コンテナーと Windows コンテナーをそれぞれ実行することができます。

Azure Service Fabric でのコンテナーのサポートの最新情報については、「[Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)」を参照してください。

Service Fabric は、「[論理アーキテクチャと物理アーキテクチャ](#logical-architecture-versus-physical-architecture)」のセクションで紹介されている物理的な実装とは異なる論理アーキテクチャ (ビジネス マイクロサービスまたは境界指定されたコンテキスト) を定義できるプラットフォームの良い例です。 たとえば、後で「[ステートレス マイクロサービスとステートフル マイクロサービスの比較](#stateless-versus-stateful-microservices)」で紹介する [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) で[ステートフル Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) を実装する場合、複数の物理的なサービスと共にビジネス マイクロサービスの概念を使用できます。

図 4-27 に示すように、論理的/ビジネス マイクロサービスの観点から考えると、Service Fabric ステートフル Reliable Service を実装するときには、通常 2 層のサービスを実装する必要があります。 1 つ目は、バックエンド ステートフル Reliable Service で、複数のパーティションを処理します (各パーティションはステートフル サービスです)。 2 つ目は、フロントエンド サービスまたはゲートウェイ サービスで、複数のパーティションまたはステートフル サービス インスタンス間のルーティングとデータの集計を担当します。 そのゲートウェイ サービスは、バックエンド サービスにアクセスする際の再試行のループを含むクライアント側の通信を処理します。
カスタム サービスを実装している場合は、ゲートウェイ サービスと呼ばれます。または、すぐに利用できる Service Fabric である[リバース プロキシ サービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)を使用することもできます。

![](./media/image31.png)

**図 4-27** いくつかのステートフルなサービス インスタンスとカスタム ゲートウェイ フロントエンドを含むビジネス マイクロサービス

いずれの場合でも、Service Fabric ステートフル Reliable Services を使用する場合、通常は複数の物理サービスで構成される論理的/ビジネス マイクロサービス (境界指定されたコンテキスト) も使用できます。 図 4-26 に示すように、それぞれにゲートウェイ サービスおよびパーティションのサービスを ASP.NET Web API サービスとして実装できます。

Service Fabric では、サービスをグループ化して、サービスのグループを [Service Fabric アプリケーション](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)として展開することができます。これは、オーケストレーターおよびクラスター用のパッケージ化および展開の単位です。 そのため、Service Fabric アプリケーションをこの自律的なビジネスおよび論理マイクロサービス境界または境界指定されたコンテキストにマッピングすることができ、さらにこれらのサービスを自律的に展開することもできます。

## <a name="service-fabric-and-containers"></a>Service Fabric とコンテナー

Service Fabric 内のコンテナーに関して、Service Fabric クラスター内のコンテナー イメージにサービスを展開することもできます。 図 4-28 に示すように、ほとんどの場合、サービスごとに 1 つのコンテナーのみがあります。

![](./media/image32.png)

**図 4-28** Service Fabric 内に複数のサービス (コンテナー) を持つビジネス マイクロサービス

ただし、いわゆる "サイドカー" コンテナー (論理サービスの一部としてまとめて展開する必要がある 2 つのコンテナー) は Service Fabric でも可能です。 重要な点は、ビジネス マイクロサービスが、いくつかのまとまりのある要素を囲む論理的な境界であることです。 多くの場合、1 つのデータ モデルを含む 1 つのサービスかもしれませんが、場合によっては物理的な複数のサービスも含まれます。

2017 の中間時点で、Service Fabric では、SF Reliable ステートフル サービスをコンテナー上に展開することができません。ステートレス サービスおよびアクター サービスのみをコンテナーに展開できます。 図 4-29 に示すように、同じ Service Fabric アプリケーションにプロセス内のサービスとコンテナー内のサービスを混在させることができることに注意してください。

![](./media/image33.png)

**図 4-29** コンテナーとステートフル サービスを含む Service Fabric アプリケーションにマップされているビジネス マイクロサービス

Azure Service Fabric でのコンテナーのサポートの詳細については、「[Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)」を参照してください。

## <a name="stateless-versus-stateful-microservices"></a>ステートレス マイクロサービスとステートフル マイクロサービスの比較

前述のように、各マイクロサービス (論理的な境界指定されたコンテキスト) は、ドメイン モデル (データとロジック) を所有している必要があります。 ステートレス マイクロ サービスの場合、データベースはサービス外部に用意することになります。このデータベースは、SQL Server などのリレーショナル データベースでも、MongoDB、Azure Cosmos DB などの NoSQL データベースでもかまいません。

Service Fabric でサービス自体もステートフルにして、データをマイクロサービス内に常駐させることもできます。 このデータは、同じサーバー上に存在できるだけでなく、マイクロサービスのプロセス内であれば、メモリ内に存在することも、ハード ドライブに保存することも、他のノードにレプリケートすることもできます。 図 4-30 では、別の方法を示します。

![](./media/image34.png)

**図 4-30** ステートレス マイクロサービスとステートフル マイクロサービスの比較

ステートレス アプローチは、完全に有効で、従来の既知のパターンに似ているので、ステートフルなマイクロサービスよりも容易に実装できます。 ステートレス マイクロサービスは、プロセスおよびデータ ソース間の遅延を強制します。 追加のキャッシュとキューを使用してパフォーマンスを改善しようとしている場合は、含まれる移動する部分が増加します。 結果として、階層の数が多すぎる複雑なアーキテクチャになる可能性があります。

一方、[ステートフルなマイクロサービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)は、ドメイン ロジックとデータの間に遅延が生じないため、高度なシナリオに優れています。 負荷の高いデータ処理、ゲームのバックエンド、サービスとしてのデータベースなど、あまり遅延が許されないシナリオでは、ローカルな状態で高速にアクセスできるステートフル サービスのメリットを生かすことができます。

ステートレス サービスおよびステートフル サービスは相互に補完します。 たとえば、図 4-30 でわかるように、右側の図では、ステートフル サービスを複数のパーティション分割することができます。 それらのパーティションにアクセスするには、パーティション キーに基づく各パーティションへのアドレス指定方法を知っているゲートウェイ サービスとして、ステートレス サービスが動作する必要があります。

ステートフル サービスには欠点があります。 スケール アウト可能なある程度の複雑さを強制します。通常外部データベース システムによって実装される機能は、ステートフル マイクロサービスにまたがるレプリケーションや、データのパーティション分割などの機能として対処する必要があります。 ただし、[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) などのオーケストレーターとその[ステートフル Reliable Service](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) が最も役立つ領域の 1 つです。これにより、[Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) と [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction) を使用するステートフル マイクロサービスの開発とライフサイクルが簡素化されます。

ステートフル サービスを許可し、Actor パターンをサポートし、ビジネス ロジックとデータ間のフォールト トレランスと遅延を改善する他のマイクロサービス フレームワークは、Microsoft [Orleans](https://github.com/dotnet/orleans)、Microsoft Research、および [Akka.NET](https://getakka.net/) です。 両方のフレームワークは、現在 Docker のサポートを向上させています。

Docker コンテナーはそれ自身ステートレスなことに注意してください。 ステートフル サービスを実装する場合は、前に説明した追加の規範的で高度なフレームワークの 1 つが必要です。 

>[!div class="step-by-step"]
[前へ](scalable-available-multi-container-microservice-applications.md)
[次へ](../docker-application-development-process/index.md)
