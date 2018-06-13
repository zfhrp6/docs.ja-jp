---
title: コンテナー ベース アプリケーション用の Azure のコンピューティング プラットフォームを選択します。
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |コンテナー ベース アプリケーション用の Azure のコンピューティング プラットフォームを選択します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958012"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>コンテナー ベース アプリケーション用の Azure のコンピューティング プラットフォームを選択します。

お気付きに前のセクションを読んだ後、Azure は複数の選択肢を提供する、開いているクラウドです。 ニーズに最適値を使用するもには、コンテナー化アプリケーションを使用する製品/テクノロジに関する質問を明らかにただし、します。

として、*既定*このガイドで推奨されている主な条件、推奨事項を次に示します。

  - **1 つのモノリシック アプリ:** Azure App Service の選択
  - **N 層アプリケーション:** orchestrators Azure Kubernetes サービス (AKS)、Service Fabric (SF) またはアプリ サービスなどを選択して、1 つまたはいくつかのバックエンド サービスがある場合
  - **Linux microservices:** AKS/Kubernetes の選択
  - **Windows microservices:** Service Fabric の選択
  - **サーバーなしの関数とイベント ハンドラー:** Azure 関数の選択
  - **大規模なバッチ:** Azure Batch の選択

ただし、製品の選択は、特定のアプリケーションのニーズと特性に依存するの salt、ピンチ操作でこの推奨事項を実行してください。 すべてのアプリケーションは、最初に類似した種類を検索する場合があるときでも同じです。

アプリケーションのニーズの詳細な分析の後は、選択されている製品が異なる可能性があります。 開始点としてお勧めして、初期のガイダンスの評価を開始することができ、特定の優先順位に基づくテストします。

次の図に、詳細な意思決定テーブル中にグローバルよりを分析できます。

![](./media/image8.5.png)

通知方法 (Windows と OS の基になります。Linux) では、いくつか orchestrators が成熟 Linux コンテナーと Windows コンテナーの その他、決定要因こともできます。 たとえば、Linux コンテナーは、小さい Service Fabric で完成度の高い、非常に成熟 Kubernetes (Azure で AKS) です。 その一方で、Windows コンテナーは、(2017 年 1 月リリース) Service Fabric で完成度の高い小さい AKS で完成度の高い。

ただし、成熟度の OS でそれらの相違点は自動的に後で複数のプラットフォームは比較可能な OS 成熟度および意思決定が、アプリケーションが必要になるまたは各プラットフォームのエコシステムに基づく特定の機能に基づいた環境設定でさらにレイアウト理由があります。


>[!div class="step-by-step"]
[前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[次へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
