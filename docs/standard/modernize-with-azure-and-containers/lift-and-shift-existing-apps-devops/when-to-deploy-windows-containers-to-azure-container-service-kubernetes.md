---
title: "Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: f5ba7aa2cf14e7ca9f3a1f3eb12bbe236dca7e97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング

Azure のコンテナー サービスは、Azure の特に人気のオープン ソース ツールとテクノロジの構成を最適化します。 移植性、コンテナーと、アプリケーションの構成の両方を提供する、開いているソリューションが表示されます。 サイズ、ホストの数と、orchestrator ツールを選択します。 Azure のコンテナー サービスは、のインフラストラクチャを処理します。

既にしているオープン ソース orchestrators Kubernetes、Docker Swarm、DC/OS など場合、は、コンテナー ワークロードをクラウドに移動する、既存の管理方法を変更する必要はありません。 既にに精通して任意の orchestrator の標準 API エンドポイントを介して接続する、アプリケーションの管理ツールを使用します。

これらすべての orchestrators は、使用する場合があっての Linux Docker コンテナーもサポート Windows コンテナー 2017 (前、最近では、orchestrator によって異なります) のように完成度の高い環境が。

たとえば、Kubernetes でのサポートのコンテナーは Kubernetes で Windows コンテナーを使用してネイティブ (ファーストクラス市民) では非常に効率的かつ信頼性の高いも (までプレビュー早期分類 2017)。

>[!div class="step-by-step"]
[前へ](when-to-deploy-windows-containers-to-service-fabric.md)
[次へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
