---
title: Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング
description: コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d1a9f0593b4b84cbe25da9e4164f4ecbe8513831
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="6fdc5-103">Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング</span><span class="sxs-lookup"><span data-stu-id="6fdc5-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="6fdc5-104">Windows コンテナーを使用している場合でも、組織は Azure Vm を使用して、IaaS を処理する場合をまだしています。</span><span class="sxs-lookup"><span data-stu-id="6fdc5-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="6fdc5-105">つまり、インフラストラクチャ操作、VM の OS 修正プログラム、およびインフラストラクチャの複雑さを扱う拡張性の高いアプリケーションの負荷分散インフラストラクチャで複数の Vm を展開する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="6fdc5-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="6fdc5-106">Azure VM で Windows コンテナーを使用するための主なシナリオは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6fdc5-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

-   <span data-ttu-id="6fdc5-107">**開発/テスト環境**: A VM クラウドでは、開発とテスト、クラウド内に最適です。</span><span class="sxs-lookup"><span data-stu-id="6fdc5-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="6fdc5-108">迅速に作成したり、必要に応じて、環境を停止します。</span><span class="sxs-lookup"><span data-stu-id="6fdc5-108">You can rapidly create or stop the environment depending on your needs.</span></span>

-   <span data-ttu-id="6fdc5-109">**小規模および中規模のスケーラビリティが必要な**: シナリオでは、実稼働環境の仮想マシンの 2 回だけを必要があります、Vm の数が少ないを管理する場合があります手頃な価格まで orchestrators と同様より高度な PaaS 環境に移動することができます。</span><span class="sxs-lookup"><span data-stu-id="6fdc5-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

-   <span data-ttu-id="6fdc5-110">**既存の展開ツールを使用して実稼働環境**: Vm または (Puppet などのようなツール) サーバーをベア メタルに複雑な展開を行うためのツールに投資するが、内部設置型環境からを移動する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6fdc5-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="6fdc5-111">実稼働環境の展開の手順に最小限の変更で、クラウドに移動するには、これらのツールを使用して、Azure Vm を展開する続行する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6fdc5-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="6fdc5-112">ただし、配置の単位として配置エクスペリエンスを向上させるために Windows コンテナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="6fdc5-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="6fdc5-113">[前へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[次へ](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="6fdc5-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
