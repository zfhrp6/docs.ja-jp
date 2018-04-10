---
title: .NET Framework 4.7、4.6、および 4.5
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 34402e74bb0cb560d213760c38ce4b936d712eb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-guide"></a><span data-ttu-id="2fa88-102">.NET Framework ガイド</span><span class="sxs-lookup"><span data-stu-id="2fa88-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="2fa88-103">この .NET Framework コンテンツ セットには .NET Framework バージョン 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7 および 4.7.1 に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2fa88-103">This .NET Framework content set includes information for .NET Framework versions 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, and 4.7.1.</span></span> <span data-ttu-id="2fa88-104">.NET Framework をダウンロードするには、「[.NET Framework のインストール](../../docs/framework/install/guide-for-developers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa88-104">To download the .NET Framework, see [Installing the .NET Framework](../../docs/framework/install/guide-for-developers.md).</span></span> <span data-ttu-id="2fa88-105">NET Framework 4.5、[!INCLUDE[net_v46](../../includes/net-v46-md.md)]、これらのポイント リリース、および .NET Framework 4.7 および 4.7.1 の新機能と変更点については、「[.NET Framework の新機能](../../docs/framework/whats-new/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2fa88-105">For a list of new features and changes in the NET Framework 4.5, the [!INCLUDE[net_v46](../../includes/net-v46-md.md)], their point releases, and the .NET Framework 4.7 and 4.7.1, see [What's New in the .NET Framework](../../docs/framework/whats-new/index.md).</span></span> <span data-ttu-id="2fa88-106">サポートされているプラットフォームについては、「[.NET Framework のシステム要件](../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa88-106">For a list of supported platforms, see [.NET Framework System Requirements](../../docs/framework/get-started/system-requirements.md).</span></span> 

<span data-ttu-id="2fa88-107">.NET Framework は、Web、Windows、Windows Phone、Windows Server、および Microsoft Azure 用のアプリを作成するための開発プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="2fa88-107">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="2fa88-108">共通言語ランタイム (CLR) と .NET Framework クラス ライブラリで構成され、さまざまな機能を含み、さまざまな業界標準をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2fa88-108">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="2fa88-109">.NET Framework は、メモリ管理、型とメモリの安全性、セキュリティ、ネットワーク、およびアプリケーションの展開など、多くのサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2fa88-109">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="2fa88-110">使いやすいデータ構造と下位レベルの Windows オペレーティング システムを抽象化する API を提供します。</span><span class="sxs-lookup"><span data-stu-id="2fa88-110">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="2fa88-111">.NET Framework では、C#、F#、Visual Basic を含む、さまざまなプログラミング言語を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2fa88-111">You can use a variety of programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>  

<span data-ttu-id="2fa88-112">ユーザーと開発者のための .NET Framework の概要については、「[.NET Framework の概要](../../docs/framework/get-started/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa88-112">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](../../docs/framework/get-started/index.md).</span></span> <span data-ttu-id="2fa88-113">.NET Framework のアーキテクチャおよび主要機能の概要については、[「.NET Framework overview の概要」](../../docs/framework/get-started/overview.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa88-113">For an introduction to the architecture and key features of the .NET Framework, see the [overview](../../docs/framework/get-started/overview.md).</span></span>  

<span data-ttu-id="2fa88-114">.NET Framework は、Docker との併用および [Windows コンテナー](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview)との併用が可能です。</span><span class="sxs-lookup"><span data-stu-id="2fa88-114">The .NET Framework can be used with Docker and with [Windows Containers](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).</span></span> <span data-ttu-id="2fa88-115">Docker コンテナーでアプリケーションを実行する方法については、「[Deploying .NET Framework applications with Docker](./docker/index.md)」 (Docker を使用して .NET Framework アプリケーションを配置する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa88-115">See [Deploying .NET Framework applications with Docker](./docker/index.md) to learn how to run your applications in Docker containers.</span></span>

## <a name="installation"></a><span data-ttu-id="2fa88-116">インストール</span><span class="sxs-lookup"><span data-stu-id="2fa88-116">Installation</span></span>

<span data-ttu-id="2fa88-117">.NET Framework は、Windows に付属しているので .NET Framework アプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2fa88-117">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="2fa88-118">Windows に付属しているバージョンよりも、新しいバージョンの .NET Framework が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="2fa88-118">You may need a later version of the .NET Framework than comes with your Windows version.</span></span> <span data-ttu-id="2fa88-119">詳細については、「[Windows への .NET Framework のインストール](./install/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa88-119">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="2fa88-120">.NET Framework をインストールするときにエラーが発生する場合に .NET Framework のインストールを修復する方法については、「[Repair the .NET Framework](./install/repair.md)」(.NET Framework を修復する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa88-120">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you are experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="2fa88-121">.NET Framework のダウンロードの詳細については、「[開発者向けの .NET Framework のインストール](../../docs/framework/install/guide-for-developers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fa88-121">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](../../docs/framework/install/guide-for-developers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2fa88-122">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2fa88-122">In This Section</span></span>

[<span data-ttu-id="2fa88-123">新機能</span><span class="sxs-lookup"><span data-stu-id="2fa88-123">What's New</span></span>](../../docs/framework/whats-new/index.md)  
<span data-ttu-id="2fa88-124">最新バージョンの .NET Framework の主要な新機能と変更点について説明します。</span><span class="sxs-lookup"><span data-stu-id="2fa88-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="2fa88-125">現在使用されていない型とメンバーのリストを示し、.NET Framework の以前のバージョンからアプリケーションを移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2fa88-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>  
  
[<span data-ttu-id="2fa88-126">はじめに</span><span class="sxs-lookup"><span data-stu-id="2fa88-126">Getting Started</span></span>](../../docs/framework/get-started/index.md)  
<span data-ttu-id="2fa88-127">.NET Framework の包括的な概要と、追加リソースへのリンクを説明します。</span><span class="sxs-lookup"><span data-stu-id="2fa88-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
<span data-ttu-id="2fa88-128">[移行ガイド](../../docs/framework/migration-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2fa88-128">[Migration Guide](../../docs/framework/migration-guide/index.md) </span></span>  
<span data-ttu-id="2fa88-129">アプリケーションを新しいバージョンの .NET Framework に移行する場合に検討する必要のあるリソースと変更の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="2fa88-129">Provides resources and a list of changes you need to consider  if you're migrating your application to a new version of the .NET Framework.</span></span>  
  
[<span data-ttu-id="2fa88-130">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="2fa88-130">Development Guide</span></span>](../../docs/framework/development-guide.md)  
<span data-ttu-id="2fa88-131">アプリケーションの作成、構成、デバッグ、セキュリティ、配置、および動的プログラミング、相互運用性、拡張性、メモリ管理、スレッド処理に関する情報を含む、アプリケーション開発用の主要な技術領域とタスクのすべてについての手引書です。</span><span class="sxs-lookup"><span data-stu-id="2fa88-131">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
[<span data-ttu-id="2fa88-132">ツール</span><span class="sxs-lookup"><span data-stu-id="2fa88-132">Tools</span></span>](../../docs/framework/tools/index.md)  
<span data-ttu-id="2fa88-133">.NET Framework テクノロジを使ってアプリケーションを開発、構成、配置するのに役立つツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2fa88-133">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>  
  
<span data-ttu-id="2fa88-134">[.NET Framework クラス ライブラリ](/dotnet/api/?view=netframework-4.7.1) </span><span class="sxs-lookup"><span data-stu-id="2fa88-134">[.NET Framework Class Library](/dotnet/api/?view=netframework-4.7.1) </span></span>  
<span data-ttu-id="2fa88-135">.NET Framework の名前空間に含まれる各クラスの構文、コード例、および関連情報を記載しています。</span><span class="sxs-lookup"><span data-stu-id="2fa88-135">Supplies syntax, code examples, and related information for each class contained in the .NET Framework namespaces.</span></span>  
  
[<span data-ttu-id="2fa88-136">追加のクラス ライブラリおよび API</span><span class="sxs-lookup"><span data-stu-id="2fa88-136">Additional Class Libraries and APIs</span></span>](../../docs/framework/additional-apis/index.md)  
<span data-ttu-id="2fa88-137">アウト オブ バンド (OOB) のリリースに含まれるクラスと、特定のプラットフォームまたは .NET Framework の実装を対象としたクラスに関するドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="2fa88-137">Provides documentation for classes contained in out-of-band (OOB) releases, as well as for classes that target specific platforms or implementations of the .NET Framework.</span></span>
