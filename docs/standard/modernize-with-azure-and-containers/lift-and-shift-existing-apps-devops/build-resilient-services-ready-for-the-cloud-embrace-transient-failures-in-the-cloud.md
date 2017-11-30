---
title: "回復力のあるサービス、クラウドの準備ができてをビルドします。 クラウド内の一時的な障害を受け入れる"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |回復力のあるサービス、クラウドの準備ができてをビルドします。 クラウド内の一時的な障害を受け入れる"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 9c21ae37ad2e4fc318eb4b206069db7662bfc5d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>クラウドの準備が整って回復力のあるサービスを構築しますクラウド内の一時的な障害を受け入れる。 

回復性は、障害から回復し、引き続き機能する能力です。 回復性エラーを回避するが、エラーが発生するという事実を受信し、ダウンタイムやデータの損失を回避するように後で対応するのではありません。 回復性の目的は、障害発生後にアプリケーションを完全に機能する状態に戻すことです。

アプリケーションには、少なくともは、ハードウェア ベースのモデルではなく、回復性のソフトウェア ベースのモデルに実装すると、クラウドの準備ができてです。 クラウド アプリケーションには、確実に発生する部分的な障害を採用する必要があります。 設計または部分的に予想される部分的な障害に対する回復力を達成したい場合、アプリケーションをリファクターする必要があります。 これは、一時的なネットワークの停止とノード、または Vm クラウドでクラッシュしたのと同様に、部分的な障害に対処を設計する必要があります。 Orchestrator クラスター内の別のノードに移動するものコンテナーには、アプリケーション内での断続的な短いエラー可能性があります。

## <a name="handling-partial-failure"></a>部分的な障害を処理

クラウド ベースのアプリケーションでは、一部の障害のリスクがないです。 たとえば、1 つの web サイト インスタンスまたはコンテナーが失敗すると、または使用できなくなったり、短い時間があります。 または、1 つの VM またはサーバーがクラッシュする可能性があります。

クライアントとサービスは別のプロセスであるためサービスできないことがあります、クライアントの要求に適切なタイミングで応答します。 サービス可能性があるオーバー ロードされた非常に遅い要求応答することや、単にアクセスできない可能性が短時間ネットワークの問題があるためです。

たとえば、Azure SQL データベースでデータベースにアクセスするモノリシックな .NET アプリケーションがあるとします。 Azure SQL データベースやその他のサード パーティのサービスは、簡単な場合に、応答がない場合 (Azure SQL データベースは、別のノードやサーバーに移動される可能性し、数秒応答していない) に、ユーザーは、操作を行う際に、アプリケーションがクラッシュする可能性がありますと表示w 非常に同時に、例外。

同様のシナリオは、HTTP サービスを使用するアプリで発生する可能性があります。 ネットワークまたはサービス自体できない可能性があります、クラウドで短い、一時的なエラーの際にします。

図 4-9 に示すような回復力のあるアプリケーションでは、アプリケーション リソースの一時的なエラーを処理する機会を提供する「指数バックオフによる再試行」のような技法を実装する必要があります。 また、「ブレーカー」をアプリケーションで使用することも必要があります。 遮断器は、実際には長期的な障害があるときにリソースにアクセスしようとしてからアプリケーションを停止します。 遮断器を使用すると、アプリケーションでは、それ自体にサービス拒否攻撃に富んだで回避できます。

![指数バックオフによる再試行によって処理される部分的な障害](./media/image9.png)

> **図 4-9 です。** 指数バックオフによる再試行によって処理される部分的な障害

HTTP リソースとデータベース リソースの両方には、これらの手法を使用することができます。 図 4-9 では、アプリケーションに基づきます 3 層アーキテクチャでは、これらの手法は、サービス レベル (HTTP) と、データ層のレベル (TCP) 必要があります。 (その他のサービスまたは microservices) は、データベース以外の単一のアプリケーション層のみを使用しているモノリシックなアプリケーション、データベース レベルの接続の一時的なエラー処理があるのに十分な。 このシナリオでは、データベース接続のある特定の構成と通常は単が必要です。

を使用している .NET のバージョンによっては、データベースにアクセスする回復力のある通信を実装するときに非常に単純できます (たとえば、 [Entity Framework 6 以降](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)、構成するだけで済みますが、データベース接続の場合)。 またはのような追加のライブラリを使用する必要があります、 [Transient Fault Handling Application Block](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (以前のバージョンの .NET)、またはでも独自のライブラリを実装します。

使用する、.NET の推奨事項は、HTTP 再試行の回数とブレーカーを実装する場合、[ポリー](https://github.com/App-vNext/Polly)ライブラリで、.NET 4.0、.NET 4.5、および .NET Core のサポートが含まれる .NET 標準 1.1 を対象とします。

クラウドでの部分的な障害を処理するための戦略を実装する方法については、次の参照を参照してください。

### <a name="additional-resources"></a>その他の技術情報

-   **部分的な障害に対処する回復力のある通信を実装します。**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies)

-   **Entity Framework 接続回復性と再試行ロジック (バージョン 6 以降)**

    [https://msdn.microsoft.com/en-us/library/dn456835 (v=vs.113).aspx](https://msdn.microsoft.com/en-us/library/dn456835(v=vs.113).aspx)

-   **Transient Fault Handling Application Block**

<!-- -->

-   [https://msdn.microsoft.com/en-us/library/hh680934 (v=pandp.50).aspx](https://msdn.microsoft.com/en-us/library/hh680934(v=pandp.50).aspx)

-   **回復力のある HTTP 通信のポリー ライブラリ**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
[前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[次へ](modernize-your-apps-with-monitoring-and-telemetry.md)
