---
title: ".NET Framework におけるセキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, security
- security [.NET Framework], about security
- application development [.NET Framework], security
- security [.NET Framework]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
caps.latest.revision: "37"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d6bf5929466d09b70cb74ffdf6c46d21c6f85ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="security-in-the-net-framework"></a><span data-ttu-id="e0a7e-102">.NET Framework におけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="e0a7e-102">Security in the .NET Framework</span></span>
<span data-ttu-id="e0a7e-103">共通言語ランタイムと .NET Framework には、開発者が安全なコードを簡単に作成したり、システム管理者が保護されたリソースへのアクセスを可能にするコードに付与されたアクセス許可をカスタマイズしたりできるようにするための便利なクラスとサービスが多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-103">The common language runtime and the .NET Framework provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="e0a7e-104">さらに、ランタイムおよび .NET Framework には、暗号とロール ベース セキュリティを簡単に利用できるようにする有用なクラスとサービスも用意されています。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-104">In addition, the runtime and the .NET Framework provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0a7e-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e0a7e-105">In This Section</span></span>  
 [<span data-ttu-id="e0a7e-106">セキュリティの変更</span><span class="sxs-lookup"><span data-stu-id="e0a7e-106">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)  
 <span data-ttu-id="e0a7e-107">.NET Framework セキュリティ システムの重要な変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-107">Describes important changes to the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="e0a7e-108">セキュリティの基本概念</span><span class="sxs-lookup"><span data-stu-id="e0a7e-108">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="e0a7e-109">共通言語ランタイムのセキュリティ機能の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-109">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="e0a7e-110">このセクションは開発者およびシステム管理者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-110">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="e0a7e-111">ロール ベースのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="e0a7e-111">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="e0a7e-112">コード内でロール ベースのセキュリティと対話する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-112">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="e0a7e-113">このセクションは開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-113">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="e0a7e-114">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="e0a7e-114">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="e0a7e-115">.NET Framework によって提供される暗号サービスの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-115">Provides an overview of cryptographic services provided by the .NET Framework.</span></span> <span data-ttu-id="e0a7e-116">このセクションは開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-116">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="e0a7e-117">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="e0a7e-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="e0a7e-118">信頼できる .NET Framework アプリケーションを作成するときの最適な実施方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-118">Describes some of the best practices for creating reliable .NET Framework applications.</span></span> <span data-ttu-id="e0a7e-119">このセクションは開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-119">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="e0a7e-120">アンマネージ コードの安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="e0a7e-120">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="e0a7e-121">アンマネージ コードを呼び出す際のベスト プラクティスとセキュリティに関する注意事項について、いくつか説明します。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-121">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="e0a7e-122">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="e0a7e-122">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="e0a7e-123">アプリケーションでクレーム ベースの ID を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-123">Describes how you can implement claims-based identity in your applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e0a7e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0a7e-124">Related Sections</span></span>  
 [<span data-ttu-id="e0a7e-125">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="e0a7e-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="e0a7e-126">アプリケーションの作成、構成、デバッグ、セキュリティ、配置、および動的プログラミング、相互運用性、拡張性、メモリ管理、スレッド処理に関する情報を含む、アプリケーション開発用の主要な技術領域とタスクのすべてについての手引書です。</span><span class="sxs-lookup"><span data-stu-id="e0a7e-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
