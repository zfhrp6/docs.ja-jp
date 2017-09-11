---
title: ".NET Framework におけるセキュリティの変更点"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
caps.latest.revision: 52
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b2ee4194f6e6788d99222badeb88e2702247904e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="8b83d-102">.NET Framework におけるセキュリティの変更点</span><span class="sxs-lookup"><span data-stu-id="8b83d-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="8b83d-103">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] のセキュリティにおける最も重要な変更は、厳密な名前付けの変更です。</span><span class="sxs-lookup"><span data-stu-id="8b83d-103">The most important change to security in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is in strong naming.</span></span> <span data-ttu-id="8b83d-104">これらの変更の詳細については、「 [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b83d-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="8b83d-105">.NET Framework は、マネージ アプリケーションに 2 階層のセキュリティ モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="8b83d-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]<span data-ttu-id="8b83d-106"> アプリはリソースへのアクセスを制限する Windows セキュリティ コンテナーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="8b83d-106"> apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="8b83d-107">そのコンテナー内では、マネージ アプリケーションは完全に信頼された状態で実行します。</span><span class="sxs-lookup"><span data-stu-id="8b83d-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="8b83d-108">コード アクセス セキュリティの (CAS) の観点からは、権限を昇格するために開発者が実行できる操作はありません。</span><span class="sxs-lookup"><span data-stu-id="8b83d-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="8b83d-109">Windows で与えられる権限の詳細については、Windows デベロッパー センターの「 [App capability declarations (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=230436) 」 (アプリの機能宣言 (Windows ストア アプリ)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b83d-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="8b83d-110">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリの作成については、「 [C# または Visual Basic を使った初めての Windows ストア アプリの作成](http://go.microsoft.com/fwlink/?LinkId=230461)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b83d-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span></span>

