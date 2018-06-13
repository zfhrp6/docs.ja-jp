---
title: Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 7472745577f414062b460fd71ab45bae85d7a62e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958022"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング

Windows コンテナーを使用している場合でも、組織は Azure Vm を使用して、IaaS を処理する場合をまだしています。 つまり、インフラストラクチャ操作、VM の OS 修正プログラム、およびインフラストラクチャの複雑さを扱う拡張性の高いアプリケーションの負荷分散インフラストラクチャで複数の Vm を展開する必要がある場合。 Azure VM で Windows コンテナーを使用するための主なシナリオは次のとおりです。

-   **開発/テスト環境**: A VM クラウドでは、開発とテスト、クラウド内に最適です。 迅速に作成したり、必要に応じて、環境を停止します。

-   **小規模および中規模のスケーラビリティが必要な**: シナリオでは、実稼働環境の仮想マシンの 2 回だけを必要があります、Vm の数が少ないを管理する場合があります手頃な価格まで orchestrators と同様より高度な PaaS 環境に移動することができます。

-   **既存の展開ツールを使用して実稼働環境**: Vm または (Puppet などのようなツール) サーバーをベア メタルに複雑な展開を行うためのツールに投資するが、内部設置型環境からを移動する可能性があります。 実稼働環境の展開の手順に最小限の変更で、クラウドに移動するには、これらのツールを使用して、Azure Vm を展開する続行する場合があります。 ただし、配置の単位として配置エクスペリエンスを向上させるために Windows コンテナーを使用します。

>[!div class="step-by-step"]
[前へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[次へ](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
