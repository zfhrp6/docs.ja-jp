---
title: Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b7f106e2b79a2c6bb24733debf7f4828505d66a6
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958172"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング

Azure のコンテナー サービスは、Azure の特に人気のオープン ソース ツールとテクノロジの構成を最適化します。 移植性、コンテナーと、アプリケーションの構成の両方を提供する、開いているソリューションが表示されます。 サイズ、ホストの数と、orchestrator ツールを選択します。 Azure のコンテナー サービスは、のインフラストラクチャを処理します。

既にしているオープン ソース orchestrators Kubernetes、Docker Swarm、DC/OS など場合、は、コンテナー ワークロードをクラウドに移動する、既存の管理方法を変更する必要はありません。 慣れているアプリケーションの管理ツールを使用し、任意の orchestrator の標準 API エンドポイントを介して接続します。

これらすべての orchestrators は、Linux Docker コンテナーを使用しているが、Windows コンテナーのプレビュー状態である可能性がありますのみとお考えの場合、完成度の高い環境です。

たとえば、Kubernetes でのサポートのコンテナーはネイティブ (ファーストクラス市民) Kubernetes で Windows コンテナーを使用しても (初期 2018 時点で ACS でのプレビュー) で効果的です。

重要な注意事項: 展開し、"複数 PaaS"バージョンの Kubernetes 用 ACS (Azure コンテナー サービス) AKS (Azure Kubernetes サービス)、ただし、Windows コンテナーはまだサポートされていません Q2 2018 時点では近日サポートされます。

>[!div class="step-by-step"]
[前へ](when-to-deploy-windows-containers-to-service-fabric.md)
[次へ](choosing-azure-compute-options-for-container-based-applications.md)
