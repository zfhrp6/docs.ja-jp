---
title: "マイクロサービス アーキテクチャ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Microservices アーキテクチャ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5ede1f0ad19270ca6b7556ff1bb7e4cf8ccf7cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="microservices-architecture"></a>マイクロサービス アーキテクチャ

名前からわかるように、microservices アーキテクチャは、一連の小さなサービスとしてのサーバー アプリケーションを構築する方法です。 各サービスが、独自のプロセスで実行され、HTTP、HTTPS、Websocket などのプロトコルを使用して他のプロセスと通信するか、 [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)です。 各マイクロ サービスは、特定のエンド ツー エンドのドメインまたは特定のコンテキストの境界内でのビジネス機能を実装および各自律的に開発する必要があります個別に配置されます。 最後に、各マイクロ サービスでは、その関連するドメインのデータ モデルと別のデータ記憶域テクノロジ (SQL、NoSQL) と異なるプログラミング言語に基づくドメイン ロジック (に対しておよび分散データ管理) を所有する必要があります。

どのようなサイズ、マイクロ サービスべきでしょうか。 マイクロ サービスを開発するときに、サイズは、重要なポイントにすることはできません。 代わりに、重要な点は、疎を作成するにはサービスを開発、配置、および各サービスのスケールの自律性があるように結合する必要があります。 もちろんとを識別する microservices を設計、、ようにできるだけ小さくとその他の microservices が多すぎます直接的な依存関係があるない限り、しようとする必要があります。 ほど重要、マイクロ サービスのサイズは必要があります内部凝集度とその他のサービスから独立します。

なぜ microservices アーキテクチャしますか? つまり、長期的な機敏性を提供します。 Microservices は、細かいおよび自律的なライフ サイクルがあるとは別に配置可能なサービスの多くに基づくアプリケーションを作成することで複雑な大規模な拡張性の高いシステムで保守性の向上を有効にします。

追加のメリットとして microservices ことができますを個別に拡張します。 単位としてスケール アウトする必要がありますを単一のモノリシックなアプリケーションはなく、代わりにスケール アウトできます microservices を特定します。 このようにより多くの処理電源やネットワーク帯域幅のスケール アウトを拡張する必要がないアプリケーションの他の領域ではなく、要求をサポートするために必要な機能領域だけを拡張できます。 コストの節約は、ハードウェアが必要なのでを意味します。

![](./media/image6.png)

**図 4. ~ 6.**です。 モノリシックな展開と microservices アプローチ

図 4 ~ 6 に示す microservices アプローチで複雑な大規模なおよびスケーラブルなアプリケーションの特定、小さな領域を変更できるためアジャイル変更し、各マイクロ サービスの迅速な反復処理ができます。

粒度の細かい microservices ベースのアプリケーションで有効に継続的インテグレーションと継続的配信のプラクティスを構築します。 また、アプリケーションに新しい関数の配信も向上します。 アプリケーションの粒度の細かいコンポジションを実行し、分離で microservices をテストして、それらの間のクリアのコントラクトを維持しながら自律的に進化させることができます。 インターフェイスまたはコントラクトを変更しない限り、任意のマイクロ サービスの内部実装を変更したりその他の microservices を分断することがなく新しい機能を追加できます。

Microservices ベースのシステムで実稼働に移行の成功を有効にする重要な側面を次に示します。

-   サービスとインフラストラクチャの監視および正常性チェックします。

-   (つまり、クラウド、orchestrators) サービスのスケーラブルなインフラストラクチャです。

-   セキュリティの設計と実装を複数のレベルで: 認証、承認、機密情報の管理、セキュリティで保護された通信などです。

-   通常はチームごとに異なる microservices に焦点を当てたと共にアプリケーションの迅速な配信します。

-   DevOps と CI/CD のプラクティスおよびインフラストラクチャです。

、これらの最初の 3 つのみが対象か、このガイドで導入されました。 最後の 2 つのポイントは、アプリケーションのライフ サイクルに関連する、については、「その他[Microsoft プラットフォームとツールと Docker アプリケーションのライフ サイクルのコンテナー](https://aka.ms/dockerlifecycleebook)電子書籍します。

## <a name="additional-resources"></a>その他の技術情報

-   **Mark Russinovich です。Microservices: アプリケーション revolution クラウドから電力を得て**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)

-   **Martin Fowler。Microservices**
    [*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)

-   **Martin Fowler。マイクロ サービスの前提条件**
    [*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)

-   **Jimmy Nilsson。チャンクのクラウド コンピューティング**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)

-   **Cesar de la Torre。Microsoft プラットフォームとツールのアプリケーションのライフ サイクルの Docker のコンテナー** (ダウンロード可能な電子書籍) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)




>[!div class="step-by-step"]
[前](サービス-指向-architecture.md) [次へ] (データ-に対して-あたり-microservice.md)
