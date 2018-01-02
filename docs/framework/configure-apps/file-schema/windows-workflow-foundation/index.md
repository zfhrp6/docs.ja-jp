---
title: "Windows Workflow Foundation の構成スキーマ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7ae70357-b150-4342-8f2a-d5eb6f9c6a0d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: baa8846d339e87c121ece2678157c132035db07f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-workflow-foundation-configuration-schema"></a><span data-ttu-id="f1bdf-102">Windows Workflow Foundation の構成スキーマ</span><span class="sxs-lookup"><span data-stu-id="f1bdf-102">Windows Workflow Foundation Configuration Schema</span></span>
[!INCLUDE[wf](../../../../../includes/wf-md.md)]<span data-ttu-id="f1bdf-103"> の構成要素を使用して、ワークフロー アプリケーションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="f1bdf-103"> configuration elements enable you to configure workflow applications.</span></span> <span data-ttu-id="f1bdf-104">ワークフロー アプリケーションでは、追跡とトレースを構成できます。</span><span class="sxs-lookup"><span data-stu-id="f1bdf-104">For a workflow application, you can configure among other things, tracking and tracing.</span></span> <span data-ttu-id="f1bdf-105">追跡とトレースの詳細については、「[ワークフロー追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1bdf-105">For more information about tracking and tracing, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="f1bdf-106">ワークフロー サービスでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] の構成要素も使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1bdf-106">For workflow services, you can also use [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] configuration elements.</span></span> <span data-ttu-id="f1bdf-107">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の詳細については、「[WCF 構成スキーマ](../../../../../docs/framework/configure-apps/file-schema/wcf/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1bdf-107">For more details about [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], see [WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="f1bdf-108">構成ファイルは XML として書式設定されているため、テキスト エディターを使用して手動で編集する場合は、XML について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bdf-108">Because configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="f1bdf-109">理解しないで編集すると、XML 要素タグや属性が見つからないなどの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f1bdf-109">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="f1bdf-110">問題の原因は、XML 要素タグと属性が大文字と小文字を区別することによります。</span><span class="sxs-lookup"><span data-stu-id="f1bdf-110">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1bdf-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f1bdf-111">In This Section</span></span>  
 [<span data-ttu-id="f1bdf-112">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f1bdf-112">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/system-servicemodel-of-workflow.md)  
 <span data-ttu-id="f1bdf-113">**ServiceModel** 要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1bdf-113">Describes the **ServiceModel** element.</span></span>
