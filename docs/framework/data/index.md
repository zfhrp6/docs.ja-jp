---
title: ".NET Framework におけるデータとモデリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, data access
- data access [.NET Framework], about .NET Framework data access
- data [.NET Framework], accessing
ms.assetid: 8c37635d-e2c1-4b64-a258-61d9e87405e6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfeacc0d4fb736c523538896246b0f406f995fa7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="data-and-modeling-in-the-net-framework"></a><span data-ttu-id="c08d9-102">.NET Framework におけるデータとモデリング</span><span class="sxs-lookup"><span data-stu-id="c08d9-102">Data and Modeling in the .NET Framework</span></span>
<span data-ttu-id="c08d9-103">ここでは、ADO.NET、統合言語クエリ (LINQ: Language-Integrated Query)、WCF Data Services、および XML を使用してデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c08d9-103">This section provides information on how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c08d9-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c08d9-104">In This Section</span></span>  
 [<span data-ttu-id="c08d9-105">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c08d9-105">ADO.NET</span></span>](../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="c08d9-106">ADO.NET のアーキテクチャについて説明します。また、ADO.NET のクラスを使用してアプリケーション データを管理し、データ ソース (Microsoft SQL Server、OLE DB データ ソース、および XML を含む) とやり取りする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="c08d9-106">Describes the ADO.NET architecture and how to use the ADO.NET classes to manage application data and interact with data sources, including Microsoft SQL Server, OLE DB data sources, and XML.</span></span>  
  
 [<span data-ttu-id="c08d9-107">LINQ ポータル</span><span class="sxs-lookup"><span data-stu-id="c08d9-107">LINQ Portal</span></span>](http://msdn.microsoft.com/library/6eb15c76-4ee6-4146-981e-b3429a945e6f)  
 <span data-ttu-id="c08d9-108">統合言語クエリ (LINQ) に関連するドキュメントへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="c08d9-108">Provides links to relevant documentation for Language Integrated Query (LINQ).</span></span>  
  
 [<span data-ttu-id="c08d9-109">トランザクション処理</span><span class="sxs-lookup"><span data-stu-id="c08d9-109">Transaction Processing</span></span>](../../../docs/framework/data/transactions/index.md)  
 <span data-ttu-id="c08d9-110">.NET Framework におけるトランザクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c08d9-110">Discusses the .NET Framework support for transactions.</span></span>  
  
 [<span data-ttu-id="c08d9-111">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="c08d9-111">WCF Data Services 4.5</span></span>](../../../docs/framework/data/wcf/index.md)  
 <span data-ttu-id="c08d9-112">WCF Data Services を使用して Web やイントラネットにデータ サービスを配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c08d9-112">Provides information about how to use WCF Data Services to deploy data services on the Web or an intranet.</span></span>  
  
 [<span data-ttu-id="c08d9-113">XML ドキュメントと XML データ</span><span class="sxs-lookup"><span data-stu-id="c08d9-113">XML Documents and Data</span></span>](../../../docs/standard/data/xml/index.md)  
 <span data-ttu-id="c08d9-114">.NET Framework で XML ドキュメントおよびデータを処理するための、統合された包括的な一連のクラスについて概説します。</span><span class="sxs-lookup"><span data-stu-id="c08d9-114">Provides an overview to a comprehensive and integrated set of classes that work with XML documents and data in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="c08d9-115">XML 標準のリファレンス</span><span class="sxs-lookup"><span data-stu-id="c08d9-115">XML Standards Reference</span></span>](http://msdn.microsoft.com/library/79c78508-c9d0-423a-a00f-672e855de401)  
 <span data-ttu-id="c08d9-116">Microsoft がサポートする XML 標準に関するリファレンス情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c08d9-116">Provides reference information on XML standards that Microsoft supports.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c08d9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c08d9-117">Related Sections</span></span>  
 [<span data-ttu-id="c08d9-118">Microsoft SQL Server のモデリング テクノロジー</span><span class="sxs-lookup"><span data-stu-id="c08d9-118">Microsoft SQL Server Modeling Technologies</span></span>](http://go.microsoft.com/fwlink/?LinkId=193039)  
 <span data-ttu-id="c08d9-119">データに基づくアプリケーションをカスタム方式で迅速に設計および開発することを可能にする一連のテクノロジについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c08d9-119">Describes a set of technologies that enable rapid and customized data-based application design and development.</span></span>  
  
 [<span data-ttu-id="c08d9-120">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="c08d9-120">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="c08d9-121">アプリケーションの作成、構成、デバッグ、セキュリティ、配置、および動的プログラミング、相互運用性、拡張性、メモリ管理、スレッド処理に関する情報を含む、アプリケーション開発用の主要な技術領域とタスクのすべてについての手引書です。</span><span class="sxs-lookup"><span data-stu-id="c08d9-121">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
 [<span data-ttu-id="c08d9-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c08d9-122">Security</span></span>](../../../docs/standard/security/index.md)  
 <span data-ttu-id="c08d9-123">共通言語ランタイムおよび .NET Framework において安全なアプリケーションの開発を促進するクラスおよびサービスに関する情報へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="c08d9-123">Provides links to more information on the classes and services in the common language runtime and the .NET Framework that facilitate secure application development.</span></span>
