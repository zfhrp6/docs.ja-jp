---
title: "Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 6fa7dbde3b7dad24047b31ee708a8a0df2635f09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング

Windows コンテナーを使用している場合でも、組織は Azure Vm を使用して、IaaS を処理する場合をまだしています。 つまり、インフラストラクチャ操作、VM の OS 修正プログラム、およびインフラストラクチャの複雑さを扱う拡張性の高いアプリケーションの負荷分散インフラストラクチャで複数の Vm を展開する必要がある場合。 Azure VM で Windows コンテナーを使用するための主なシナリオは次のとおりです。

-   **開発/テスト環境**: A VM クラウドでは、開発とテスト、クラウド内に最適です。 迅速に作成したり、必要に応じて、環境を停止します。

-   **小規模および中規模のスケーラビリティが必要な**: シナリオでは、実稼働環境の仮想マシンの 2 回だけを必要があります、Vm の数が少ないを管理する場合があります手頃な価格まで orchestrators と同様より高度な PaaS 環境に移動することができます。

-   **既存の展開ツールを使用して実稼働環境**: Vm または (Puppet などのようなツール) サーバーをベア メタルに複雑な展開を行うためのツールに投資するが、内部設置型環境からを移動する可能性があります。 実稼働環境の展開の手順に最小限の変更で、クラウドに移動するには、これらのツールを使用して、Azure Vm を展開する続行する場合があります。 ただし、配置の単位として配置エクスペリエンスを向上させるために Windows コンテナーを使用します。

>[!div class="step-by-step"]
[前へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[次へ](when-to-deploy-windows-containers-to-service-fabric.md)
