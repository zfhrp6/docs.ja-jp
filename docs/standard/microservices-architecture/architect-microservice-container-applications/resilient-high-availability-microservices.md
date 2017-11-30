---
title: "回復性と microservices での高可用性"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |回復性と microservices での高可用性"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 149e28ac7bd7383e4e960ed8a226943e2b9bdaa1
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="resiliency-and-high-availability-in-microservices"></a>回復性と microservices での高可用性

予期しない障害を処理する場合は、解決するため、特に、分散システムで最も困難な問題の 1 つです。 例外の処理、多くの開発者が記述するコードでは、これもテストで最も多くの時間がかかった箇所。 問題は、エラーを処理するコードを記述するよりも複雑です。 新機能は、マイクロ サービスを実行しているコンピューターが失敗した場合にどうなりますか。 このマイクロ サービス障害 (ハード問題自体) を検出する必要がありますだけでなく、マイクロ サービスを再起動するものをも必要です。

マイクロ サービスに障害に対する回復力と可用性のための別のコンピューターで多くの場合、再起動する必要があります。 この回復性もは、マイクロ サービスが、この状態を回復し、マイクロ サービスを正常に再起動できるかどうか、マイクロ サービスに代わって保存された状態にします。 つまり、する必要があります (プロセスはいつでも再起動できます)、コンピューティング機能のレジリエンシー状態またはデータ (データ損失なし、および一貫性のあるデータは、その) からの復元力とします。

アプリケーションのアップグレード中にエラーが発生したときなど、他のシナリオの中には、回復性の問題が複雑化します。 配置システムの操作、マイクロ サービスは、新しいバージョンに進むまたは代わりに一貫性のある状態を維持するために以前のバージョンにロールバックを続行するかどうかを決定する必要があります。 十分なマシンを前方移動を使用できるかどうかや、マイクロ サービスの以前のバージョンを回復する方法などの質問は、考慮する必要があります。 これには、アプリケーション全体と orchestrator がこれらの決定を行うこと、正常性に関する情報を出力するマイクロ サービスが必要です。

回復性がさらに、関連するクラウド ベースのシステムを動作する必要があります。 前述のように、クラウド ベースのシステムの障害を受け入れる必要があります。. から自動的に回復を試みる必要があります。 たとえば、ネットワークまたはコンテナーの障害が発生した場合クライアント アプリまたはクライアント サービスが必要メッセージの送信を再試行するか、多くの場合は、クラウド内の障害は部分的なので、要求を再試行する戦略です。 [回復力のあるアプリケーションの実装](#implementing_resilient_apps)このガイドのセクションでは、部分的な障害に対処する方法を説明します。 ようなライブラリを使用して指数バックオフまたは .NET Core で遮断器パターンでの再試行のような手法について説明[ポリー](https://github.com/App-vNext/Polly)、大規模なさまざまなこの件名を処理するためのポリシーを提供します。

## <a name="health-management-and-diagnostics-in-microservices"></a>正常性の管理と microservices での診断

当然のこと、およびこれは、見落とされがちが、マイクロ サービスは、その正常性と診断を報告する必要があります。 それ以外の場合、操作の観点からほとんどの洞察がありません。 独立したサービスのセット間の診断イベントを関連付けることと、イベントの順序を理解することのコンピューター クロックのずれを処理するには、困難です。 同じ方法で合意プロトコルとデータ形式をマイクロ サービスを操作する必要があるヘルスおよびクエリを実行して表示するため、イベント ストアで最終的に終了する診断のイベント ログに記録する方法を標準化します。 キーである、microservices 的に異なるチームが、1 つのログ ファイル形式に同意します。 アプリケーションの診断イベントの表示を一貫した方法が必要です。

### <a name="health-checks"></a>正常性チェック

正常性は、診断と異なります。 正常性は適切なアクションを実行する現在の状態を報告マイクロ サービスです。 良い例は、可用性を維持するためにアップグレードし、展開のメカニズムと連携します。 サービスが現在プロセスのクラッシュのため異常であるコンピューターの再起動をまたはサービスを運用可能性があります。 最後にする必要がありますに、この悪化アップグレードの実行を開始します。 最良の手法は、最初に調査を行うには、マイクロ サービスを回復する時間を許可するか。 マイクロ サービスからの正常性イベントにご協力を下すし、実際には、自己回復サービスの作成に役立ちます。

実装で正常性チェックこのガイドの ASP.NET Core services セクションで適切なアクションを実行する監視サービスの状態を報告することができますので、microservices 内の新しい ASP.NET HealthChecks ライブラリを使用する方法について説明します。

### <a name="using-diagnostics-and-logs-event-streams"></a>診断とログのイベント ストリームを使用します。

ログは、どのアプリケーションまたはサービスが実行されている、例外、警告、および単純な情報メッセージを含むに関する情報を提供します。 通常、例外は、複数の行、スタック トレースを表示する場合もありますが、各ログは、イベントごとに 1 行のテキスト形式でです。

モノリシックのサーバー ベースのアプリケーションでは、単にログ ファイルを書き込む (ログ ファイル) をディスク上し、任意のツールと分析できます。 アプリケーションの実行は、固定サーバー ロールまたは VM に制限されているため、通常は複雑すぎるため、イベントのフローを分析 、Orchestrator クラスター内の多数のノード間で複数のサービスを実行する場所、分散アプリケーションに分散型のイベントを関連付けることが困難です。

マイクロ サービス ベースのアプリケーションは、自体は、イベント、またはログ ファイルの出力ストリームを保存しようとしていない必要がありますであっても、一元的にイベントのルーティングを管理しようとすることがします。 透過的な場合の下を実行している環境を実行するためのインフラストラクチャによって収集される標準出力に場合、各プロセスでだけ、イベント ストリームを書き込むことを意味がある場合があります。 これらのイベント ストリーム ルーターの例は[Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow)、複数のソースからイベント ストリームを収集し、システムを出力する公開します。 開発環境用の単純な標準出力が含まれますかなどのクラウド システム[Application Insights](https://azure.microsoft.com/services/application-insights/)、 [OMS](https://github.com/Azure/diagnostics-eventflow#oms-operations-management-suite) (アプリケーションについては、内部設置型)、および[Azure 診断](https://docs.microsoft.com/azure/monitoring-and-diagnostics/azure-diagnostics). ある優れたサード パーティ製のログ分析プラットフォームとツールで検索する、アラート、レポート、およびなどのリアルタイムであっても、モニターのログ[Splunk](http://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA)です。

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orchestrators 健全性と診断情報を管理します。

マイクロ サービス ベースのアプリケーションを作成するときに、複雑さを処理する必要があります。 もちろん、単一のマイクロ サービスを扱う、単純なは数十または数百の種類と数千 microservices のインスタンスの複雑な問題です。 これはほぼビルドされません、マイクロ サービス アーキテクチャ — 必要もあります高可用性、addressability、回復性、ヘルス、および診断システム安定性と統一する場合。

![](./media/image22.png)

**図 4-22**です。 マイクロ サービス プラットフォームは、アプリケーションの正常性の管理の基本的です

図 4-22 を示す複雑な問題は、自分で解決するために非常に困難です。 開発チームは、ビジネス上の問題を解決し、マイクロ サービス ベースのアプローチでカスタム アプリケーションを構築に集中する必要があります。 複雑なインフラストラクチャの問題を解決するのには重点必要があります。起きている場合は、任意のマイクロ サービス ベースのアプリケーションのコストは大幅になります。 したがってはマイクロ サービス指向プラットフォームでは、orchestrators またはを構築およびサービスを実行してインフラストラクチャ リソースを効率的に使用するハードの問題を解決しようとしたマイクロ サービス クラスターと呼ばれます。 これにより、microservices アプローチを使用するアプリケーションの構築の複雑な作業が軽減されます。

異なる orchestrators と同様に、音の可能性がありますが、次のセクションで説明したようの機能と、OS のプラットフォームによっても、成熟度の状態で、診断とそれらの各によって提供される正常性チェックが異なります。

## <a name="additional-resources"></a>その他の技術情報

-   **12 係数アプリです。XI です。ログ: イベントのストリームとしてのログの処理**
    [*https://12factor.net/logs*](https://12factor.net/logs)

-   **Microsoft 診断 EventFlow ライブラリです。** GitHub のリポジトリ。

    [*https://github.com/Azure/diagnostics-eventflow*](https://github.com/Azure/diagnostics-eventflow)

-   **Azure 診断は**
    [*https://docs.microsoft.com/azure/azure-diagnostics*](https://docs.microsoft.com/azure/azure-diagnostics)

-   **Windows コンピューターで、Azure ログ分析サービスを接続**
    [*https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents*](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents)

-   **平均値をどのようなログ記録: セマンティック ログ アプリケーション ブロックを使用して**
    [*https://msdn.microsoft.com/library/dn440729 (v=pandp.60).aspx*](https://msdn.microsoft.com/library/dn440729(v=pandp.60).aspx)

-   **Splunk です。** 公式サイト。
    [*http://www.splunk.com*](http://www.splunk.com)

-   **EventSource クラス**です。 API tracing for Windows (ETW) イベントを[ *https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource*](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource)




>[!div class="step-by-step"]
[前](microservice-based-composite-ui-shape-layout.md) [次へ] (scalable-available-multi-container-microservice-applications.md)
