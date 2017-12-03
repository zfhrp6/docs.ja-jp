---
title: "カスタム アクティビティの設計と実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 944f8d7c015d2522ae4fb8f0805ca6a40d494a75
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="d1d9c-102">カスタム アクティビティの設計と実装</span><span class="sxs-lookup"><span data-stu-id="d1d9c-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="d1d9c-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] のカスタム アクティビティを作成するには、システム標準アクティビティを複合アクティビティにアセンブルするか、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、または <xref:System.Activities.NativeActivity> から派生する新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="d1d9c-104">ここでは、いずれかのメソッドを使用してカスタム アクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1d9c-105">既定では、カスタム アクティビティは、ワークフロー デザイナー内で、アクティビティ名を含む単純な四角形として表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="d1d9c-106">ワーク フロー デザイナーでアクティビティのカスタム ビジュアル表現を指定するには、カスタム デザイナーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="d1d9c-107">[カスタム アクティビティ デザイナーおよびテンプレートを使用して](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)です。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-107"> [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1d9c-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d1d9c-108">In This Section</span></span>  
 [<span data-ttu-id="d1d9c-109">アクティビティ作成オプション</span><span class="sxs-lookup"><span data-stu-id="d1d9c-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="d1d9c-110">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] で使用できる作成スタイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="d1d9c-111">カスタム アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="d1d9c-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="d1d9c-112">ワークフロー プロジェクトにカスタム アクティビティを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="d1d9c-113">非同期アクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="d1d9c-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="d1d9c-114">非同期アクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="d1d9c-115">アクティビティ検証の構成</span><span class="sxs-lookup"><span data-stu-id="d1d9c-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="d1d9c-116">アクティビティの検証を使用して、アクティビティを実行する前にその構成エラーを特定および報告する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="d1d9c-117">実行時におけるアクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="d1d9c-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="d1d9c-118"><xref:System.Activities.DynamicActivity> を使用して実行時にアクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="d1d9c-119">ワークフロー実行プロパティ</span><span class="sxs-lookup"><span data-stu-id="d1d9c-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="d1d9c-120">ワークフロー実行プロパティを使用して、アクティビティの環境にコンテキスト固有のプロパティを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="d1d9c-121">アクティビティ デリゲートの使用</span><span class="sxs-lookup"><span data-stu-id="d1d9c-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="d1d9c-122">アクティビティ デリゲートを含むアクティビティを作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-122">Discusses how to author and use activities that contain activity delegates.</span></span>  
  
 [<span data-ttu-id="d1d9c-123">アクティビティのローカライズ</span><span class="sxs-lookup"><span data-stu-id="d1d9c-123">Activity Localization</span></span>](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 <span data-ttu-id="d1d9c-124">アクティビティの文字列リソースのローカライズを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-124">Describes how to use localization of string resources in activities.</span></span>  
  
 [<span data-ttu-id="d1d9c-125">アクティビティ拡張機能の使用</span><span class="sxs-lookup"><span data-stu-id="d1d9c-125">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="d1d9c-126">アクティビティ拡張機能を作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-126">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="d1d9c-127">ワークフローからの OData フィードの利用</span><span class="sxs-lookup"><span data-stu-id="d1d9c-127">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="d1d9c-128">ワークフローから WCF Data Service を呼び出すためのいくつかの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-128">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="d1d9c-129">アクティビティ定義のスコープ設定と表示</span><span class="sxs-lookup"><span data-stu-id="d1d9c-129">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="d1d9c-130">アクティビティのデータのスコープとメンバーの参照範囲を定義するためのオプションおよび規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d9c-130">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
