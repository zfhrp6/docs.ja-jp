---
title: "Windows Workflow Foundation で使用されない型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 422e95a105978749cc56dfe6601fb4518cc11509
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="f5125-102">Windows Workflow Foundation で使用されない型</span><span class="sxs-lookup"><span data-stu-id="f5125-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="f5125-103">.NET 4 の段階で、ワークフロー チームは、<xref:System.Activities> 名前空間のまったく新しいワークフロー エンジンをリリースしました。</span><span class="sxs-lookup"><span data-stu-id="f5125-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="f5125-104">.NET 4.5 ベータ版のリリースでは、"WF 3"で型の大部分のマークを付けるおは<xref:System.Workflow.Activities>、 <xref:System.Workflow.ComponentModel>、および<xref:System.Workflow.Runtime>不使用と名前空間。</span><span class="sxs-lookup"><span data-stu-id="f5125-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="f5125-105">旧式の名前空間とツール</span><span class="sxs-lookup"><span data-stu-id="f5125-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="f5125-106">次のアセンブリには、今後使用を推奨されなくなるパブリック型が 1 つ以上含まれています。</span><span class="sxs-lookup"><span data-stu-id="f5125-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
-   <span data-ttu-id="f5125-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="f5125-107">System.Workflow.Activities.dll</span></span>  
  
-   <span data-ttu-id="f5125-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="f5125-108">System.Workflow.ComponentModel.dll</span></span>  
  
-   <span data-ttu-id="f5125-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="f5125-109">System.Workflow.Runtime.dll</span></span>  
  
-   <span data-ttu-id="f5125-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="f5125-110">System.WorkflowServices.dll</span></span>  
  
-   <span data-ttu-id="f5125-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="f5125-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
-   <span data-ttu-id="f5125-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="f5125-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
-   <span data-ttu-id="f5125-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="f5125-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="f5125-114">その結果、推奨されなくなった WF 3 API を今後使用すると、ビルド時に警告が発生し、次のようなメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f5125-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="f5125-115">**警告 bc 40000: X が廃止されています: WF 3 の型は使用されなくなりました。代わりに WF 4 を使用してください。**</span><span class="sxs-lookup"><span data-stu-id="f5125-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="f5125-116">WF 3 の型は .NET Framework の将来のリリースで削除されますが、実際の削除時期はまだ未定です (4.5 では行われません)。</span><span class="sxs-lookup"><span data-stu-id="f5125-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="f5125-117">この段階的な変更は、今後の方向性を示し、お客様が WF 4 モデルに余裕をもって移行するための期間を確保するためのものです。</span><span class="sxs-lookup"><span data-stu-id="f5125-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="f5125-118">、当然ながら、引き続きこれら WF 3 の型をサポートするために、[マイクロソフト サポート ライフ サイクル ポリシー](http://aka.ms/MicrosoftSupportLifecycle)です。</span><span class="sxs-lookup"><span data-stu-id="f5125-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](http://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="f5125-119">既存の WF 3 アプリケーションは .NET 4.5 でも問題なく動作します。また、WF 3 ベースの新規および既存ソリューションは [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] でもサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f5125-119">Existing WF3 applications will run without issue on .NET 4.5, and [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="f5125-120"><xref:System.Workflow.Activities.Rules> 名前空間に含まれるルール関連の型については、WF 4.5 には相当する型がないため、非推奨扱いにはなりません。</span><span class="sxs-lookup"><span data-stu-id="f5125-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="f5125-121">WF 4 にアプリケーションを移行する顧客にとってはのヘルプを検索、[ワークフロー 4 移行のガイダンス](migration-guidance.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5125-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
