---
title: 共通のコンテナー デザインの原則
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: d3ae0c05a7e94d739a3442ecdb11564a70567963
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071176"
---
# <a name="common-container-design-principles"></a>共通のコンテナー デザインの原則

事前に、開発プロセスを取得するはすコンテナーを使用する方法に関していくつかの基本的な概念です。

## <a name="container-equals-a-process"></a>コンテナーには、プロセスと等しい

コンテナー モデルでは、コンテナーは、1 つのプロセスを表します。 コンテナーを定義すると、プロセス境界として、スケール、またはバッチ オフ、プロセスに使用されるプリミティブの作成を開始します。 Docker コンテナーを実行すると表示されます、 [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint)定義します。 これは、プロセス、およびコンテナーの有効期間を定義します。 プロセスが完了したら、コンテナーのライフ サイクルが終了します。 Web サーバー、および Microsoft Azure として実装されていますが、バッチ ジョブなどの有効期間が短いプロセスなどの実行時間の長いプロセスが[WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/)です。 プロセスが失敗した場合、コンテナーが終了し、Orchestrator が引き継ぎます。 Orchestrator が実行されている 5 つのインスタンスを保持するように指示しました、1 つが失敗した場合は、orchestrator は、失敗した処理を置換する別のコンテナーを作成します。 バッチ ジョブで、プロセスはパラメーターを指定して開始されます。 プロセスが完了すると、作業が完了します。

複数のプロセスが 1 つのコンテナーで実行するシナリオがあります。 任意のアーキテクチャのドキュメントではありません、"never、"は常にも、「常にします」。 複数のプロセスを必要とするシナリオで一般的なパターンでは、使用する[スーパーバイザー](http://supervisord.org/)です。


>[!div class="step-by-step"]
[前へ](design-docker-applications.md)
[次へ](monolithic-applications.md)
