---
title: "メッセージ ベースの非同期通信"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |メッセージ ベースの非同期通信"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: df39771295d12e122edbe27e91cd899e3318e301
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="asynchronous-message-based-communication"></a>メッセージ ベースの非同期通信

非同期メッセージングとイベント ドリブンの通信は、複数の microservices とその関連ドメイン モデル間での変更を反映するときに重要です。 前述のとおり、ディスカッション microservices と範囲指定されたコンテキスト (BCs)、モデル (ユーザー、顧客、製品、アカウントなど) を異なる microservices または BCs 立場に応じてさまざまなを意味します。 を変更した場合は、別のモデル間での変更を調整するために何らかの方法が必要なことを意味します。 ソリューションは、最終的整合性と非同期メッセージングに基づき、イベント ドリブン通信です。

メッセージングを使用して、プロセスは非同期的にメッセージを交換して通信します。 クライアントが、コマンドまたは要求をサービス メッセージを送信しています。 サービスは、返信する必要があります、クライアントにさまざまなメッセージを送信します。 メッセージ ベースの通信のため、クライアントで、応答が受信されず、すぐと、ある可能性がありますいない応答まったくを使用します。

メッセージは、ヘッダー (id やセキュリティ情報などのメタデータ) と本文で構成されます。 通常、メッセージは AMQP のような非同期プロトコルを通じて送信されます。

優先インフラストラクチャ microservices コミュニティでの通信のこの型は、軽量のメッセージ ブローカー、大規模なブローカーと orchestrators SOA で使用されているとは異なります。 軽量のメッセージ ブローカーのインフラストラクチャです通常"、"RabbitMQ や Azure Service Bus のようなクラウドでのスケーラブルな service bus などの単純な実装とのメッセージ ブローカーとしてのみ機能します。 このシナリオで「スマート」考え方のほとんどは従来どおり生成され、メッセージを処理するエンドポイントで、つまり、microservices で。

別の規則に従うと、可能な限りしようとする必要がありますが、内部のサービス間で唯一の非同期メッセージングを使用して、フロント エンド サービス (API ゲートウェイと、最初のレベルには、クライアント アプリケーションからのみ (HTTP など) の同期通信を使用するにはmicroservices)。

非同期メッセージング通信の 2 種類があります。 単一の受信者メッセージ ベースの通信、および複数の受信者メッセージ ベースの通信します。 次のセクションでは、に関する詳細情報を提供します。

## <a name="single-receiver-message-based-communication"></a>単一の受信側メッセージ ベースの通信 

メッセージ ベースの非同期通信を 1 つの受信側では、ただ 1 つのコンシューマー、チャネルから読み取られたことと、メッセージは一度だけ処理するのにメッセージを配信するポイント ツー ポイント通信を意味します。 ただし、特別な状況があります。 インスタンスをエラーから自動的に回復しようとするクラウド システムで、同じメッセージを送信でした複数回です。 により、ネットワークまたはその他のエラーでは、クライアントがメッセージの送信を再試行できるされており、サーバーがべき等になる特定のメッセージを 1 回だけ処理するために、操作を実装する必要です。

単一受信者メッセージ ベースの通信は、1 つのマイクロ サービス間で非同期コマンドを送信するように図 4-18 をこの方法を示していますに特に適しています。

(コマンドまたはイベントのいずれか)、メッセージ ベースの通信の送信を開始すると、同期の HTTP 通信とメッセージ ベースの通信の混在を避ける必要があります。

![](./media/image18.PNG)

**図 4 ~ 18**です。 非同期メッセージを受信する単一のマイクロ サービス

コマンドは、クライアント アプリケーションから取得、ときに実装できる HTTP 同期コマンドとしてに注意してください。 高い拡張性が必要な場合や、メッセージ ベースのビジネス プロセスでは既に、メッセージ ベースのコマンドを使用する必要があります。

## <a name="multiple-receivers-message-based-communication"></a>受信側の複数のメッセージ ベースの通信 

、、より柔軟なアプローチとして、送信者からの通信を使用できるは、追加サブスクライバー microservices または外部アプリケーションにできるように、パブリッシュ/サブスクライブのメカニズムを使用することがもできます。 したがってに利用するに従って、[原則を開く/閉じる](https://en.wikipedia.org/wiki/Open/closed_principle)送信側のサービスでします。 ようにして、将来的に送信側サービスを変更する必要がないその他のサブスクライバーを追加できます。

パブリッシュ/サブスクライブの通信を使用する場合は、任意のサブスクライバーにイベントを公開するイベント バス インターフェイスを使用する可能性があります。

## <a name="asynchronous-event-driven-communication"></a>イベント ドリブンの非同期通信

イベント ドリブンの非同期通信を使用する場合、マイクロ サービスは、そのドメイン内で何かが発生し、別マイクロ サービスは、製品カタログ マイクロ サービスの価格変更と同様に、対応する必要があるときに、統合イベントを公開します。 追加 microservices は、それらを非同期的に受信できるように、イベントをサブスクライブします。 発生したときに、受信側は、独自のドメイン エンティティが公開する複数の統合イベントが発生することができますを更新可能性があります。 このパブリッシュ/サブスクライブ システムは通常、イベント バスの実装を使用して実行されます。 イベント バスは、抽象またはインターフェイスをサブスクライブまたはイベントをアンサブスク ライブして、イベントを発行するために必要な api として設計できます。 イベント バスできますも 1 つまたは複数の実装は、メッセージング キューまたはサービス バスの非同期通信と、パブリッシュ/サブスクライブ モデルをサポートするように、プロセス間およびメッセージング ブローカーに基づきます。

システムでは、統合イベントによって最終的整合性を使用する場合は、この方法をエンドユーザーに完全に消えて行われることをお勧めします。 システムは、SignalR クライアントからのポーリング システムなどの統合イベントを模倣するアプローチを使用しないでください。 エンドユーザーとビジネス所有者を明示的にシステムの最終的整合性を採用し、これは、明示的な限り多くの場合、ビジネスがないことには、この方法は、何か問題ことに注意してあります。

前に説明したとおり、[に関する課題とソリューションの分散データ管理](#challenges-and-solutions-for-distributed-data-management) セクションで、複数の microservices にまたがるビジネス タスクを実装する統合イベントを使用することができます。 したがって、サービス間で最終的整合性をがあります。 最終的に一貫性のあるトランザクションは分散アクションのコレクションで構成をされます。 各アクションには、関連マイクロ サービスは、ドメイン エンティティを更新し、同じエンド ツー エンドのビジネス タスク内で次のアクションを発生させているもう 1 つの統合イベントを発行します。

重要な点は、可能性がある、同じイベントにサブスクライブされる複数の microservices と通信します。 パブリッシュ/サブスクライブを行うこともできますメッセージングに基づくイベント ドリブンの通信では、図 4-19 に示すようにします。 このパブリッシュ/サブスクライブ メカニズムがマイクロ サービス アーキテクチャに排他的ではないです。 同様の方法である[コンテキストの境界を付けられた](http://martinfowler.com/bliki/BoundedContext.html)で DDD が通信する必要があります、または、書き込み可能なデータベースからの読み取りのデータベースへの更新を伝達する方法を[コマンドと Query Responsibility Segregation (CQRS)](http://martinfowler.com/bliki/CQRS.html)アーキテクチャ パターン。 目標は、分散システム全体で複数のデータ ソース間で最終的整合性にです。

![](./media/image19.png)

**図 4-19**です。 非同期イベント駆動型メッセージ通信

実装では、イベント ドリブン、メッセージ ベースの通信に使用するプロトコルを決定します。 [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)キューに置かれた通信の信頼性を実現するのに役立てることができます。

イベント バスを使用する場合と同様に、メッセージ ブローカーから API を使用してコードでクラスに関連する実装に基づいた (イベント バス インターフェイス) のような抽象化レベルを使用する可能性があります[RabbitMQ](https://www.rabbitmq.com/)やのようにservicebus[Azure Service Bus のトピックを参照](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)です。 また、明確に示す、イベント バスやシステムのパブリッシュ/サブスクライブに NServiceBus、MassTransit、Brighter などの上位レベルのサービス バスを使用することができます。

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>メッセージング テクノロジを運用システムに関する注意事項

抽象イベント バスを実装するために利用できるメッセージング テクノロジは、さまざまなレベルでです。 たとえば、RabbitMQ (メッセージング ブローカー トランスポート) と Azure Service Bus などの製品の前に座って、またはより低いレベルの他の製品と同様に、NServiceBus、MassTransit、Brighter、RabbitMQ と Azure Service Bus の上に動作することができます。 選択は、アプリケーション レベルと既定のスケーラビリティがアプリケーションに必要な数の豊富な機能によって異なります。 開発環境に合わせて、概念実証のイベント バスだけを実装するため eShopOnContainers サンプルでは、作業が完了する Docker コンテナーで実行されている RabbitMQ 上に簡単な実装ではあります十分です。

ただし、ミッション クリティカル運用システム ハイパー スケーラビリティが必要では、Azure Service Bus を評価する必要があります。 高度な抽象化と分散アプリケーションの開発を容易にする機能は、NServiceBus、MassTransit、Brighter など他の商用およびオープン ソースのサービス バスを評価することをお勧めします。 もちろん、RabbitMQ と Docker のような下位レベルのテクノロジの上に独自のサービス バス機能をビルドすることができます。 その組み込み作業可能性がありますコスト、カスタムのエンタープライズ アプリケーションには多すぎます。

## <a name="resiliently-publishing-to-the-event-bus"></a>イベント バスに発行弾性的

複数 microservices 間で、イベント ドリブンのアーキテクチャを実装する際の課題はアトミックに弾性的に基づいて何らかの理由で、イベント バスに、関連する統合イベントの発行中に元のマイクロ サービスの状態を更新する方法トランザクション。 次に示します、これを実現する方法はいくつか追加の方法があります。

-   MSMQ などのトランザクション (DTC ベース) のキューを使用します。 (ただし、これは、従来のアプローチ) です。

-   使用して[トランザクション ログ マイニング](http://www.scoop.it/t/sql-server-transaction-log-mining)です。

-   使用して完全[イベント調達](https://msdn.microsoft.com/en-us/library/dn589792.aspx)パターン。

-   使用して、[送信トレイ パターン](http://gistlabs.com/2014/05/the-outbox/): イベントを作成し、発行されるイベント作成者コンポーネントの基本となる、メッセージ キューとトランザクションのデータベース テーブルです。

メッセージべき等性とメッセージの重複除去は、非同期通信を使用する際に考慮するその他のトピックです。 これらのトピックのセクションで説明されて[microservices (統合イベント) の間でイベント ベースの通信を実装する](#implementing_event_based_comms_microserv)このガイドで後述します。

## <a name="additional-resources"></a>その他の技術情報

-   **イベント ドリブン メッセージング**
    [*http://soapatterns.org/design\_パターン/イベント\_ドリブン\_メッセージング*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **チャネルのパブリッシュ/サブスクライブ**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Udi Dahan です。CQRS が明確にされました**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **コマンドおよび責任 Segregation (CQRS) をクエリ**
    [*https://docs.microsoft.com/azure/architecture/patterns/cqrs*](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

-   **コンテキスト間の通信範囲指定された**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **最終的整合性**
    [*https://en.wikipedia.org/wiki/Eventual\_整合性*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Jimmy Bogard。に対する回復力のリファクタリング: 結合の評価**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)


>[!div class="step-by-step"]
[前](通信-で-マイクロ サービス-architecture.md) [次へ] (管理-マイクロ サービス-apis.md)
