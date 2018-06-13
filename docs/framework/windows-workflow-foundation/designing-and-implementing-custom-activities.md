---
title: カスタム アクティビティの設計と実装
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 2ed80b5cbb27c6647053ee9b8f4cd2bedb0c6cde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513820"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="cf283-102">カスタム アクティビティの設計と実装</span><span class="sxs-lookup"><span data-stu-id="cf283-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="cf283-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] のカスタム アクティビティを作成するには、システム標準アクティビティを複合アクティビティにアセンブルするか、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、または <xref:System.Activities.NativeActivity> から派生する新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="cf283-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="cf283-104">ここでは、いずれかのメソッドを使用してカスタム アクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cf283-105">既定では、カスタム アクティビティは、ワークフロー デザイナー内で、アクティビティ名を含む単純な四角形として表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf283-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="cf283-106">ワーク フロー デザイナーでアクティビティのカスタム ビジュアル表現を指定するには、カスタム デザイナーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf283-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="cf283-107">詳細については、次を参照してください。[を使用してカスタム アクティビティ デザイナーおよびテンプレート](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)です。</span><span class="sxs-lookup"><span data-stu-id="cf283-107">For more information, see [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf283-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="cf283-108">In This Section</span></span>  
 [<span data-ttu-id="cf283-109">アクティビティ作成オプション</span><span class="sxs-lookup"><span data-stu-id="cf283-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="cf283-110">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] で使用できる作成スタイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="cf283-111">カスタム アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="cf283-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="cf283-112">ワークフロー プロジェクトにカスタム アクティビティを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="cf283-113">非同期アクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="cf283-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="cf283-114">非同期アクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="cf283-115">アクティビティ検証の構成</span><span class="sxs-lookup"><span data-stu-id="cf283-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="cf283-116">アクティビティの検証を使用して、アクティビティを実行する前にその構成エラーを特定および報告する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="cf283-117">実行時におけるアクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="cf283-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="cf283-118"><xref:System.Activities.DynamicActivity> を使用して実行時にアクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="cf283-119">ワークフロー実行プロパティ</span><span class="sxs-lookup"><span data-stu-id="cf283-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="cf283-120">ワークフロー実行プロパティを使用して、アクティビティの環境にコンテキスト固有のプロパティを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="cf283-121">アクティビティ デリゲートの使用</span><span class="sxs-lookup"><span data-stu-id="cf283-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="cf283-122">アクティビティ デリゲートを含むアクティビティを作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-122">Discusses how to author and use activities that contain activity delegates.</span></span>  
  
 [<span data-ttu-id="cf283-123">アクティビティのローカライズ</span><span class="sxs-lookup"><span data-stu-id="cf283-123">Activity Localization</span></span>](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 <span data-ttu-id="cf283-124">アクティビティの文字列リソースのローカライズを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-124">Describes how to use localization of string resources in activities.</span></span>  
  
 [<span data-ttu-id="cf283-125">アクティビティ拡張機能の使用</span><span class="sxs-lookup"><span data-stu-id="cf283-125">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="cf283-126">アクティビティ拡張機能を作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-126">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="cf283-127">ワークフローからの OData フィードの利用</span><span class="sxs-lookup"><span data-stu-id="cf283-127">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="cf283-128">ワークフローから WCF Data Service を呼び出すためのいくつかの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-128">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="cf283-129">アクティビティ定義のスコープ設定と表示</span><span class="sxs-lookup"><span data-stu-id="cf283-129">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="cf283-130">アクティビティのデータのスコープとメンバーの参照範囲を定義するためのオプションおよび規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf283-130">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
