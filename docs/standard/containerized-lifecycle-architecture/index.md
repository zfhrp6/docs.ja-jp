---
title: コンテナーと Docker の概要
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 8d1062aaea85cf810fa07b36252974eceb227c43
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="2ed86-103">コンテナーと Docker の概要</span><span class="sxs-lookup"><span data-stu-id="2ed86-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="2ed86-104">コンテナリゼーションは、ソフトウェア開発のアプローチであり、アプリケーションまたはサービス、その依存関係、その構成 (展開マニフェスト ファイルとして抽象化) がコンテナー イメージとしてパッケージ化されます。</span><span class="sxs-lookup"><span data-stu-id="2ed86-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="2ed86-105">次に、コンテナー化アプリケーションをユニットとしてテストし、ホスト オペレーティング システムにコンテナー イメージ インスタンスとして展開することができます。</span><span class="sxs-lookup"><span data-stu-id="2ed86-105">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="2ed86-106">輸送業で使用する標準化されたコンテナーが、内部の貨物に関係なく商品を船舶、列車、またはトラックによって輸送できるのと同様に、ソフトウェア コンテナーは、別のコードと依存関係を含めることができるソフトウェアの標準的なユニットとして機能します。</span><span class="sxs-lookup"><span data-stu-id="2ed86-106">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="2ed86-107">ソフトウェアをコンテナー内に配置することで、開発者や IT プロフェッショナルは、ほとんどまたはまったく変更せずに環境全体にそれらのコンテナーを展開できます。</span><span class="sxs-lookup"><span data-stu-id="2ed86-107">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="2ed86-108">コンテナーは、共有オペレーティング システム (OS) 上で個々のアプリケーションも分離します。</span><span class="sxs-lookup"><span data-stu-id="2ed86-108">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="2ed86-109">コンテナー化アプリケーションは、さらに、OS (Linux または Windows) で実行されているコンテナー ホスト上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="2ed86-109">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="2ed86-110">したがって、コンテナーは、仮想マシン (VM) のイメージよりもフット プリントが大幅に小さくなります。</span><span class="sxs-lookup"><span data-stu-id="2ed86-110">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="2ed86-111">各コンテナーは、図 1-1 に示すように、Web アプリケーションまたはサービスの全体を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="2ed86-111">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="2ed86-112">図 1-1: コンテナー ホストで実行されている複数のコンテナー</span><span class="sxs-lookup"><span data-stu-id="2ed86-112">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="2ed86-113">この例では、Docker ホストが、コンテナー ホストであり、App1、App2、Svc 1、および Svc 2 はコンテナー化アプリケーションまたはサービスです。</span><span class="sxs-lookup"><span data-stu-id="2ed86-113">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="2ed86-114">コンテナリゼーションから得られるもう 1 つの利点はスケーラビリティです。</span><span class="sxs-lookup"><span data-stu-id="2ed86-114">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="2ed86-115">短期的なタスク用の新しいコンテナーを作成することでに簡単にスケール アウトできます。</span><span class="sxs-lookup"><span data-stu-id="2ed86-115">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="2ed86-116">アプリケーションの観点から、*イメージのインスタンス化* (コンテナーの作成) は、サービスまたは Web アプリのようなプロセスのインスタンス化に似ています。</span><span class="sxs-lookup"><span data-stu-id="2ed86-116">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="2ed86-117">ただし、信頼性のために、同じイメージの複数のインスタンスを複数のホスト サーバーで実行するときには通常、各コンテナー (イメージのインスタンス) を異なるフォールト ドメイン内の別のホスト サーバーまたは VM で実行します。</span><span class="sxs-lookup"><span data-stu-id="2ed86-117">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="2ed86-118">つまり、コンテナーには、アプリケーション ライフサイクル ワークフロー全体にわたり、分離、移植性、機敏性、スケーラビリティ、およびコントロールの利点があります。</span><span class="sxs-lookup"><span data-stu-id="2ed86-118">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="2ed86-119">最も重要な利点は、開発と運用間で提供される分離です。</span><span class="sxs-lookup"><span data-stu-id="2ed86-119">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2ed86-120">[Next] (what-is-docker.md)</span><span class="sxs-lookup"><span data-stu-id="2ed86-120">[Next] (what-is-docker.md)</span></span>
