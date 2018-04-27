---
title: Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング
description: コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cccf78ef5b7683a2eefa3efab50a7bbe1bffda18
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング

Azure のコンテナー サービスは、Azure の特に人気のオープン ソース ツールとテクノロジの構成を最適化します。 移植性、コンテナーと、アプリケーションの構成の両方を提供する、開いているソリューションが表示されます。 サイズ、ホストの数と、orchestrator ツールを選択します。 Azure のコンテナー サービスは、のインフラストラクチャを処理します。

既にしているオープン ソース orchestrators Kubernetes、Docker Swarm、DC/OS など場合、は、コンテナー ワークロードをクラウドに移動する、既存の管理方法を変更する必要はありません。 既にに精通して任意の orchestrator の標準 API エンドポイントを介して接続する、アプリケーションの管理ツールを使用します。

これらすべての orchestrators は、使用する場合があっての Linux Docker コンテナーもサポート Windows コンテナー 2017 (前、最近では、orchestrator によって異なります) のように完成度の高い環境が。

たとえば、Kubernetes でのサポートのコンテナーは Kubernetes で Windows コンテナーを使用してネイティブ (ファーストクラス市民) では非常に効率的かつ信頼性の高いも (までプレビュー早期分類 2017)。

>[!div class="step-by-step"]
[前へ](when-to-deploy-windows-containers-to-service-fabric.md)
[次へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
