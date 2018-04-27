---
title: ワークフロー デザイン操作のカスタマイズ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ee64ae3db9dbf98f2a62397075406c118a867bb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="8eb48-102">ワークフロー デザイン操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="8eb48-102">Customizing the Workflow Design Experience</span></span>
<span data-ttu-id="8eb48-103">[!INCLUDE[wfd1](../../../includes/wfd1-md.md)] では、カスタム アクティビティを設計するシナリオや [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]を再ホストするシナリオが大幅に簡略化されました。</span><span class="sxs-lookup"><span data-stu-id="8eb48-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="8eb48-104">開発も配置も簡単になり、柔軟性も向上しました。</span><span class="sxs-lookup"><span data-stu-id="8eb48-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="8eb48-105">キーのインフラストラクチャの変更は、こと、新しいアクティビティ デザイナー プログラミング モデルが構築された時に Windows Presentation Foundation (WPF) です。</span><span class="sxs-lookup"><span data-stu-id="8eb48-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="8eb48-106">そのため、アクティビティ デザイナーを宣言によって定義することや、他のアプリケーションに[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]を再ホストすることが比較的簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="8eb48-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="8eb48-107">再ホストするときに、カスタム式エディターを開発して、IntelliSense や簡略化された式ドメインをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="8eb48-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="8eb48-108">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] との統合は、ワークフロー サービスを使用することで、よりシームレスになっています。</span><span class="sxs-lookup"><span data-stu-id="8eb48-108">The integration with [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] has become more seamless with use of workflow services.</span></span> <span data-ttu-id="8eb48-109">カスタム アクティビティ デザイナーおよびモデル アイテム ツリーを使用して、再ホストされたワークフロー デザイナーのデザイン時の操作を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="8eb48-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8eb48-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8eb48-110">In This Section</span></span>  
 [<span data-ttu-id="8eb48-111">カスタム アクティビティ デザイナーおよびテンプレートの使用</span><span class="sxs-lookup"><span data-stu-id="8eb48-111">Using Custom Activity Designers and Templates</span></span>](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)  
 <span data-ttu-id="8eb48-112">新しいカスタム アクティビティ デザイナーおよびテンプレートを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8eb48-112">Describes how to create new custom activity designers and templates.</span></span>  
  
 [<span data-ttu-id="8eb48-113">ワークフロー デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="8eb48-113">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 <span data-ttu-id="8eb48-114">[!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 以外に [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]を再ホストする方法および検証エラーを表示する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8eb48-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] and how to display validation errors.</span></span>  
  
 [<span data-ttu-id="8eb48-115">カスタム式エディターの使用</span><span class="sxs-lookup"><span data-stu-id="8eb48-115">Using a Custom Expression Editor</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)  
 <span data-ttu-id="8eb48-116">[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 以外で再ホストされたワークフロー デザイナーで使用するカスタム式エディターの実装方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8eb48-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8eb48-117">参照</span><span class="sxs-lookup"><span data-stu-id="8eb48-117">Reference</span></span>  
 <xref:System.Activities.Presentation.ActivityDesigner>  
  
## <a name="see-also"></a><span data-ttu-id="8eb48-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8eb48-118">See Also</span></span>  
 [<span data-ttu-id="8eb48-119">Windows Workflow Foundation の拡張</span><span class="sxs-lookup"><span data-stu-id="8eb48-119">Extending Windows Workflow Foundation</span></span>](../../../docs/framework/windows-workflow-foundation/extend.md)  
 [<span data-ttu-id="8eb48-120">デザイナー</span><span class="sxs-lookup"><span data-stu-id="8eb48-120">Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer.md)  
 [<span data-ttu-id="8eb48-121">カスタム アクティビティ デザイナー</span><span class="sxs-lookup"><span data-stu-id="8eb48-121">Custom Activity Designers</span></span>](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)  
 [<span data-ttu-id="8eb48-122">デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="8eb48-122">Designer ReHosting</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)
