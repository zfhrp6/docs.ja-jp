---
title: Windows Workflow Foundation の構成スキーマ
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 7ae70357-b150-4342-8f2a-d5eb6f9c6a0d
ms.openlocfilehash: 77c71cd8ebcac91bf48d2e57714d42c7387fed8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352490"
---
# <a name="windows-workflow-foundation-configuration-schema"></a><span data-ttu-id="fc97f-102">Windows Workflow Foundation の構成スキーマ</span><span class="sxs-lookup"><span data-stu-id="fc97f-102">Windows Workflow Foundation Configuration Schema</span></span>
<span data-ttu-id="fc97f-103">Windows Workflow Foundation (WF) の構成要素を使用すると、ワークフロー アプリケーションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="fc97f-103">Windows Workflow Foundation (WF) configuration elements enable you to configure workflow applications.</span></span> <span data-ttu-id="fc97f-104">ワークフロー アプリケーションでは、追跡とトレースを構成できます。</span><span class="sxs-lookup"><span data-stu-id="fc97f-104">For a workflow application, you can configure among other things, tracking and tracing.</span></span> <span data-ttu-id="fc97f-105">追跡とトレースの詳細については、「[ワークフロー追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc97f-105">For more information about tracking and tracing, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="fc97f-106">ワークフロー サービスでは、Windows Communication Foundation (WCF) 構成要素を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="fc97f-106">For workflow services, you can also use Windows Communication Foundation (WCF) configuration elements.</span></span> <span data-ttu-id="fc97f-107">WCF の詳細については、次を参照してください。 [WCF 構成スキーマ](../../../../../docs/framework/configure-apps/file-schema/wcf/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc97f-107">For more details about WCF, see [WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="fc97f-108">構成ファイルは XML として書式設定されているため、テキスト エディターを使用して手動で編集する場合は、XML について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc97f-108">Because configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="fc97f-109">理解しないで編集すると、XML 要素タグや属性が見つからないなどの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fc97f-109">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="fc97f-110">問題の原因は、XML 要素タグと属性が大文字と小文字を区別することによります。</span><span class="sxs-lookup"><span data-stu-id="fc97f-110">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc97f-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fc97f-111">In This Section</span></span>  
 [<span data-ttu-id="fc97f-112">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fc97f-112">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/system-servicemodel-of-workflow.md)  
 <span data-ttu-id="fc97f-113">**ServiceModel** 要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fc97f-113">Describes the **ServiceModel** element.</span></span>
