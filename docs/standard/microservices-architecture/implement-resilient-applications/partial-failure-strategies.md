---
title: "部分的な障害を処理するための戦略"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |部分的な障害を処理するための戦略"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ff3bed530b13a9b1822c7cccf5a4d47df6fc6239
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="strategies-for-handling-partial-failure"></a>部分的な障害を処理するための戦略

部分的な障害を処理するための戦略には、次の項目が含まれます。

**内部 microservices 間で非同期通信 (たとえば、メッセージ ベースの通信) を使用して**です。 その正しくないデザインは不適切な停止の主な原因を最終的になるために、内部 microservices 間で同期の HTTP 呼び出しの長いチェーンを作成するには、いないことを強く勧めします。 反対に、クライアント アプリケーションと microservices や粒度の細かい API ゲートウェイの最初のレベル間フロント エンドの通信を除くをお勧め通信を使用するのみ非同期 (メッセージに基づく)、最初の要求の 1 回を超えて/内部 microservices 間での応答のサイクルです。 最終的整合性およびイベント ドリブンのアーキテクチャは、ripple 影響を最小限に抑えるに役立ちます。 これらの方法はマイクロ サービスの自律性の高いレベルを適用して、ここに記載されている問題を防止するため。

**指数バックオフによる再試行を使用して**です。 この手法の回避に役立ちます短いと、サービスが短時間に対してのみ使用可能な場合に呼び出しを実行することによって断続的なエラー再試行する回数だけ、します。 これは、断続的なネットワークの問題により、またはマイクロ サービス/コンテナーがクラスター内の異なるノードに移動したときに発生する可能性があります。 ただし、これらの再試行がブレーカーを正しく設計されていません場合、そのことができますを悪化させること波及効果、最終的にも発生する[サービス拒否 (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack)です。

**ネットワークのタイムアウトを回避する**です。 一般に、クライアントは、応答を待機しているときに常にタイムアウトを使用して無期限にブロックを設計する必要があります。 タイムアウトを使用しているリソースは決して関連付けられています無期限にことを確認します。

**遮断器パターンを使用して**です。 この方法では、クライアント プロセスは、失敗した要求の数を追跡します。 場合はエラー率は、再試行はすぐに失敗できるように構成されている制限値は、「遮断器」トリップを超えています。 (大量の要求が失敗する場合を提案する、サービスが使用できないと、要求を送信することは、無意味です。)タイムアウト期間後にクライアント必要がありますもう一度やり直してくださいし、新しい要求が成功すると、遮断器を閉じます。

**フォールバックを提供**です。 この方法では、クライアント プロセスは、要求が失敗した場合に、キャッシュされたデータまたは既定値を返すなどに、フォールバック ロジックを実行します。 これはクエリでは、適切なアプローチであり、更新プログラムやコマンドにより複雑なは。

**キューに置かれた要求の数を制限**です。 クライアントは、クライアント マイクロ サービスを特定のサービスに送信できる未処理の要求の数に上限を課すもする必要があります。 制限に達している場合は、おそらく他の要求を行うことも意味がなく、再試行回数が即座に失敗します。 実装では、ポリーの観点から[バルクヘッド分離](https://github.com/App-vNext/Polly/wiki/Bulkhead)ポリシーは、この要件を受け付けますを使用することができます。 並列化スロットル本質的には、この方法は[SemaphoreSlim](https://docs.microsoft.com/dotnet/api/system.threading.semaphoreslim?view=netcore-1.1)として実装します。 バルクヘッド外"queue"をこともできます。 (たとえば、容量には、すべてのものと見なされます) ため能動的に実行する前に余分な負荷かアドバイスことができます。 これにより、特定の障害シナリオへの応答、遮断器である場合は、障害の遮断器が待機するためのより高速化します。 ポリーで BulkheadPolicy オブジェクトがどの程度のバルクヘッドを公開およびキューは、オーバーフローについて提供イベントのでこともできますを水平方向の自動スケーリングを実行します。

## <a name="additional-resources"></a>その他の技術情報

-   **回復力のパターン**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **回復力を追加して、パフォーマンスを最適化する**
    [*https://msdn.microsoft.com/en-us/library/jj591574.aspx*](https://msdn.microsoft.com/en-us/library/jj591574.aspx)

-   **バルクヘッドです。** GitHub のリポジトリ。 ポリー ポリシーを使用して実装します \。
    [*https://github.com/App-vNext/Polly/wiki/Bulkhead*](https://github.com/App-vNext/Polly/wiki/Bulkhead)

-   **Azure の回復力のあるアプリケーションの設計**
    [*https://docs.microsoft.com/azure/architecture/resiliency/*](https://docs.microsoft.com/azure/architecture/resiliency/)

-   **一時的なエラー処理**
    <https://docs.microsoft.com/azure/architecture/best-practices/transient-faults>


>[!div class="step-by-step"]
[前](ハンドル-部分的-failure.md) [次へ] (実装の再試行-指数-backoff.md)
