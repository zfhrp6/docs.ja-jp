---
title: .NET マイクロサービス。 コンテナー化された .NET アプリケーションのアーキテクチャ
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Front Matter'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d4499384d63f11a1d78d0aa84749aed8ea554794
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="8f732-104">.NET マイクロサービス。</span><span class="sxs-lookup"><span data-stu-id="8f732-104">.NET Microservices.</span></span> <span data-ttu-id="8f732-105">コンテナー化された .NET アプリケーションのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="8f732-105">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="8f732-106">次の場所でダウンロードできます: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="8f732-106">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="8f732-107">発行者</span><span class="sxs-lookup"><span data-stu-id="8f732-107">PUBLISHED BY</span></span>

<span data-ttu-id="8f732-108">Microsoft 開発部門、.NET および Visual Studio 製品チーム</span><span class="sxs-lookup"><span data-stu-id="8f732-108">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="8f732-109">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="8f732-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="8f732-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="8f732-110">One Microsoft Way</span></span>

<span data-ttu-id="8f732-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="8f732-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="8f732-112">Copyright © 2017 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="8f732-112">Copyright © 2017 by Microsoft Corporation</span></span>

<span data-ttu-id="8f732-113">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="8f732-113">All rights reserved.</span></span> <span data-ttu-id="8f732-114">本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。</span><span class="sxs-lookup"><span data-stu-id="8f732-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="8f732-115">本書は "現状有姿" で提供され、著者の見解と意見を表しています。</span><span class="sxs-lookup"><span data-stu-id="8f732-115">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="8f732-116">URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="8f732-116">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="8f732-117">ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。</span><span class="sxs-lookup"><span data-stu-id="8f732-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="8f732-118">実在のものとの関連性または関係性は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="8f732-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="8f732-119">http://www.microsoft.com の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。</span><span class="sxs-lookup"><span data-stu-id="8f732-119">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="8f732-120">Mac および macOS は Apple Inc. の商標です。</span><span class="sxs-lookup"><span data-stu-id="8f732-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="8f732-121">Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。</span><span class="sxs-lookup"><span data-stu-id="8f732-121">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="8f732-122">その他のすべてのマークおよびロゴは、該当する各社が所有しています。</span><span class="sxs-lookup"><span data-stu-id="8f732-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="8f732-123">共同作成者:</span><span class="sxs-lookup"><span data-stu-id="8f732-123">Co-Authors:</span></span>

> <span data-ttu-id="8f732-124">**Cesar de la Torre**、Microsoft corp.、.NET 製品チーム、シニア PM</span><span class="sxs-lookup"><span data-stu-id="8f732-124">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="8f732-125">**Bill Wagner**、Microsoft Corp.、C+E、シニア コンテンツ開発者</span><span class="sxs-lookup"><span data-stu-id="8f732-125">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="8f732-126">**Mike Rousos**、Microsoft、DevDiv CAT チーム、主任ソフトウェア エンジニア</span><span class="sxs-lookup"><span data-stu-id="8f732-126">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="8f732-127">編集者:</span><span class="sxs-lookup"><span data-stu-id="8f732-127">Editors:</span></span>

> <span data-ttu-id="8f732-128">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="8f732-128">**Mike Pope**</span></span>
>
> <span data-ttu-id="8f732-129">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="8f732-129">**Steve Hoag**</span></span>

<span data-ttu-id="8f732-130">参加者とレビュー担当者:</span><span class="sxs-lookup"><span data-stu-id="8f732-130">Participants and reviewers:</span></span>

> <span data-ttu-id="8f732-131">**Jeffrey Richter**、Microsoft、Azure チーム、パートナー ソフトウェア エンジニア</span><span class="sxs-lookup"><span data-stu-id="8f732-131">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="8f732-132">**Jimmy Bogard**、Headspring のチーフ アーキテクト</span><span class="sxs-lookup"><span data-stu-id="8f732-132">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="8f732-133">**Udi Dahan**、Particular Software、創設者兼最高経営責任者</span><span class="sxs-lookup"><span data-stu-id="8f732-133">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="8f732-134">**Jimmy Nilsson**、Factor10 の共同創始者兼最高経営責任者</span><span class="sxs-lookup"><span data-stu-id="8f732-134">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="8f732-135">**Glenn Condron**、ASP.NET チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="8f732-135">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="8f732-136">**Mark Fussell**、Microsoft、Azure Service Fabric チーム、プリンシパル PM リーダー</span><span class="sxs-lookup"><span data-stu-id="8f732-136">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="8f732-137">**Diego Vega**、Microsoft、Entity Framework チーム、PM リーダー</span><span class="sxs-lookup"><span data-stu-id="8f732-137">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="8f732-138">**Barry Dorrans**、シニア セキュリティ プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="8f732-138">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="8f732-139">**Rowan Miller**、Microsoft、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="8f732-139">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="8f732-140">**Ankit Asthana**、Microsoft、.NET チーム、主任 PM マネージャー</span><span class="sxs-lookup"><span data-stu-id="8f732-140">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="8f732-141">**Scott Hunter**、Microsoft、.NET チーム、パートナー ディレクター PM</span><span class="sxs-lookup"><span data-stu-id="8f732-141">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="8f732-142">**Dylan Reisenberger**、Polly のアーキテクト兼開発リーダー</span><span class="sxs-lookup"><span data-stu-id="8f732-142">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="8f732-143">**Steve Smith**、ASPSmith Ltd. のソフトウェア設計者兼トレーナー</span><span class="sxs-lookup"><span data-stu-id="8f732-143">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="8f732-144">**Ian Cooper**、Brighter のコーディング アーキテクト</span><span class="sxs-lookup"><span data-stu-id="8f732-144">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="8f732-145">**Unai Zorrilla**、Plain Concepts のアーキテクト兼開発リーダー</span><span class="sxs-lookup"><span data-stu-id="8f732-145">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="8f732-146">**Eduard Tomas**、Plain Concepts の開発リーダー</span><span class="sxs-lookup"><span data-stu-id="8f732-146">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="8f732-147">**Ramon Tomas**、Plain Concepts の開発者</span><span class="sxs-lookup"><span data-stu-id="8f732-147">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="8f732-148">**David Sanz**、Plain Concepts の開発者</span><span class="sxs-lookup"><span data-stu-id="8f732-148">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="8f732-149">**Javier Valero**、Grupo Solutio の最高執行責任者</span><span class="sxs-lookup"><span data-stu-id="8f732-149">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="8f732-150">**Pierre Millet**、Microsoft、シニア コンサルタント</span><span class="sxs-lookup"><span data-stu-id="8f732-150">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="8f732-151">**Michael Friis**、Docker Inc、製品マネージャー</span><span class="sxs-lookup"><span data-stu-id="8f732-151">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="8f732-152">**Charles Lowell**、Microsoft、VS CAT チーム、ソフトウェア エンジニア</span><span class="sxs-lookup"><span data-stu-id="8f732-152">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="8f732-153">はじめに</span><span class="sxs-lookup"><span data-stu-id="8f732-153">Introduction</span></span>

<span data-ttu-id="8f732-154">企業は、コンテナーを使用して、コストの節減、展開の問題の解決、および DevOps と製造作業の向上を実現しつつあります。</span><span class="sxs-lookup"><span data-stu-id="8f732-154">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="8f732-155">Microsoft では、Azure Container Service や Azure Service Fabric などの製品を作成したり、Docker、Mesosphere、Kubernetes などの業界リーダーと提携することで、Windows および Linux 用のコンテナーの新技術をリリースしています。</span><span class="sxs-lookup"><span data-stu-id="8f732-155">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="8f732-156">これらの製品は、企業が使用しているプラットフォームやツールに関係なく、クラウドの速度とスケールでアプリケーションを構築および展開することに役立つコンテナー ソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="8f732-156">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="8f732-157">Docker は、コンテナー業界では事実上の標準になりつつあり、Windows と Linux のエコシステムで最も重要なベンダーでサポートされています </span><span class="sxs-lookup"><span data-stu-id="8f732-157">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="8f732-158">(Microsoft は Docker をサポートする主要なクラウド ベンダーの 1 つです)。将来、Docker は、クラウドまたはオンプレミスのあらゆるデータセンターで広く使用されるようになるでしょう。</span><span class="sxs-lookup"><span data-stu-id="8f732-158">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="8f732-159">さらに、ミッション クリティカルな分散アプリケーションのための重要なアプローチとして、[マイクロサービス](https://martinfowler.com/articles/microservices.html) アーキテクチャが新たに出現しています。</span><span class="sxs-lookup"><span data-stu-id="8f732-159">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="8f732-160">マイクロサービス ベースのアーキテクチャでは、個別に開発、テスト、展開、およびバージョン管理が可能なサービスのコレクションに基づいてアプリケーションが構築されます。</span><span class="sxs-lookup"><span data-stu-id="8f732-160">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="8f732-161">このガイドについて</span><span class="sxs-lookup"><span data-stu-id="8f732-161">About this guide</span></span>

<span data-ttu-id="8f732-162">このガイドでは、マイクロサービス ベースのアプリケーションの開発とコンテナーを使用してこれらを管理する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="8f732-162">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="8f732-163">.NET Core と Docker のコンテナーを使用したアーキテクチャの設計と実装アプローチについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8f732-163">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="8f732-164">コンテナーとマイクロサービスの使用の開始を容易にするため、このガイドでは、ユーザーが探究できる参照コンテナー化されたマイクロサービス ベースのアプリケーションに重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="8f732-164">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="8f732-165">サンプル アプリケーションは、[eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="8f732-165">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="8f732-166">このガイドでは、主に開発環境レベルで、Docker と .NET Core の 2 つのテクノロジに重点を置いた、基本的な開発とアーキテクチャに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="8f732-166">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="8f732-167">このガイドは、運用環境のインフラストラクチャ (クラウドまたはオンプレミス) を重視することなく、アプリケーションの設計について考慮する際にお読みいただくことを意図しています。</span><span class="sxs-lookup"><span data-stu-id="8f732-167">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="8f732-168">インフラストラクチャに関する決定は、後で実稼働可能なアプリケーションを作成するときに行います。</span><span class="sxs-lookup"><span data-stu-id="8f732-168">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="8f732-169">そのため、このガイドは、インフラストラクチャに依存しない、より開発環境中心としたものになることを意図しています。</span><span class="sxs-lookup"><span data-stu-id="8f732-169">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="8f732-170">このガイドで学習したら、次の段階は Microsoft Azure での実稼働可能なマイクロサービスについて学習することです。</span><span class="sxs-lookup"><span data-stu-id="8f732-170">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="8f732-171">このガイドに含まれないもの</span><span class="sxs-lookup"><span data-stu-id="8f732-171">What this guide does not cover</span></span>

<span data-ttu-id="8f732-172">このガイドでは、アプリケーションのライフサイクル、DevOps、CI/CD パイプライン、またはチーム作業については詳しく取り上げません。</span><span class="sxs-lookup"><span data-stu-id="8f732-172">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="8f732-173">これらについては、補完ガイド「[Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル](https://aka.ms/dockerlifecycleebook)」で詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="8f732-173">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="8f732-174">最新のガイドでも、特定のオーケストレーターに関する情報など、Azure インフラストラクチャでの実装の詳細は提供されません。</span><span class="sxs-lookup"><span data-stu-id="8f732-174">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8f732-175">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="8f732-175">Additional resources</span></span>

-   <span data-ttu-id="8f732-176">**Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル** (ダウンロード可能な e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="8f732-176">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="8f732-177">対象読者</span><span class="sxs-lookup"><span data-stu-id="8f732-177">Who should use this guide</span></span>

<span data-ttu-id="8f732-178">このガイドは、Docker ベースのアプリケーションの開発とマイクロサービス ベースのアーキテクチャに詳しくない開発者およびソリューション設計者を対象にしています。</span><span class="sxs-lookup"><span data-stu-id="8f732-178">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="8f732-179">このガイドは、Microsoft 開発テクノロジ (特に .NET Core を中心とした) と Docker コンテナーを使用して、概念実証アプリケーションの設計、デザインおよび実装する方法を学習したい人向けに書かれています。</span><span class="sxs-lookup"><span data-stu-id="8f732-179">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="8f732-180">新しいモダンな分散アプリケーションにどのアプローチを選択するかを決定する前に、アーキテクチャとテクノロジーの概要を必要とする、エンタープライズ アーキテクトなどの技術的意思決定者にもこのガイドは役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8f732-180">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="8f732-181">このガイドの使用方法</span><span class="sxs-lookup"><span data-stu-id="8f732-181">How to use this guide</span></span>

<span data-ttu-id="8f732-182">このガイドの最初の部分では、Docker コンテナーを紹介し、開発フレームワークとして .NET Core または .NET Framework を選択する方法について説明し、マイクロサービスの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="8f732-182">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="8f732-183">このコンテンツは、概要は知りたいが、コード実装の詳細について詳しく知る必要がないアーキテクトおよび技術的意思決定者向けです。</span><span class="sxs-lookup"><span data-stu-id="8f732-183">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="8f732-184">ガイドの 2 番目の部分は、「[Docker ベースのアプリケーションの開発プロセス](#ch_dev_process_for_docker_based_apps)」セクションから始まります。</span><span class="sxs-lookup"><span data-stu-id="8f732-184">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="8f732-185">これは、.NET Core と Docker を使用してアプリケーションを実装するための開発とマイクロ サービスのパターンを中心に説明します。</span><span class="sxs-lookup"><span data-stu-id="8f732-185">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="8f732-186">これは、コード、パターンおよび実装の詳細を重視する開発者やアーキテクトにとって最も関心が高いセクションです。</span><span class="sxs-lookup"><span data-stu-id="8f732-186">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="8f732-187">関連するマイクロサービスとコンテナー ベースの参照アプリケーション: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="8f732-187">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="8f732-188">eShopOnContainers アプリケーションは、.NET Core および Docker コンテナーを使用して展開するように設計されたマイクロサービスのための参照アプリです。</span><span class="sxs-lookup"><span data-stu-id="8f732-188">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="8f732-189">アプリケーションは、いくつかの e ストア UI フロント エンド (Web アプリとネイティブ モバイル アプリ) を含む複数のサブシステムで構成されます。</span><span class="sxs-lookup"><span data-stu-id="8f732-189">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="8f732-190">また、バック エンドのマイクロサービスと必要なサーバー側のすべての操作のためのコンテナーも含まれています。</span><span class="sxs-lookup"><span data-stu-id="8f732-190">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="8f732-191">このマイクロ サービスとコンテナー ベースのアプリケーション ソース コードは、オープン ソースで、[eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="8f732-191">This microservice and container-based application source code is open source and available at the [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="8f732-192">フィードバックをお寄せください。</span><span class="sxs-lookup"><span data-stu-id="8f732-192">Send us your feedback!</span></span>

<span data-ttu-id="8f732-193">このガイドは、コンテナー化されたアプリケーションと .NET のマイクロサービスのアーキテクチャの理解を促進する目的で書かれています。</span><span class="sxs-lookup"><span data-stu-id="8f732-193">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="8f732-194">ガイドと関連する参照アプリケーションは進化していくため、お客様のフィードバックをお待ちしています。</span><span class="sxs-lookup"><span data-stu-id="8f732-194">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="8f732-195">このガイドを改善する方法についてご意見があれば、以下のアドレスに送信してください。</span><span class="sxs-lookup"><span data-stu-id="8f732-195">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
<span data-ttu-id="8f732-196">[次へ] (container-docker-introduction/index.md)</span><span class="sxs-lookup"><span data-stu-id="8f732-196">[Next] (container-docker-introduction/index.md)</span></span>
