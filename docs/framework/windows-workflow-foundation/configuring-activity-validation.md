---
title: "アクティビティ検証の構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d75f03a9af5caa5569cbfd4d1d09cda8936f6562
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="9041c-102">アクティビティ検証の構成</span><span class="sxs-lookup"><span data-stu-id="9041c-102">Configuring Activity Validation</span></span>
<span data-ttu-id="9041c-103">アクティビティの検証を使用すると、アクティビティの作成者とユーザーは、アクティビティを実行する前に、アクティビティの構成エラーを特定および報告できます。</span><span class="sxs-lookup"><span data-stu-id="9041c-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="9041c-104"> には、次に示す 3 種類のアクティビティの検証方法があります:</span><span class="sxs-lookup"><span data-stu-id="9041c-104"> provides the following three types of activity validation:</span></span>  
  
-   <span data-ttu-id="9041c-105">`RequiredArgument` 属性および `OverloadGroup` 属性。</span><span class="sxs-lookup"><span data-stu-id="9041c-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
-   <span data-ttu-id="9041c-106">命令型コードに基づく検証。</span><span class="sxs-lookup"><span data-stu-id="9041c-106">Imperative code-based validation.</span></span>  
  
-   <span data-ttu-id="9041c-107">宣言の制約。</span><span class="sxs-lookup"><span data-stu-id="9041c-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="9041c-108">`RequiredArgument` 属性と `OverloadGroup` 属性は、アクティビティにおける特定の引数が必須であることを示します。</span><span class="sxs-lookup"><span data-stu-id="9041c-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="9041c-109">命令型コードに基づく検証には、アクティビティが自身に関する検証を提供できる単純な方法が用意されています。また、宣言の制約を使用すると、アクティビティとそれを含むワークフローとの関係に関して検証できます。</span><span class="sxs-lookup"><span data-stu-id="9041c-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="9041c-110">検証の要件に従ってアクティビティが正しく構成されていない場合、検証のエラーと警告が返されます。</span><span class="sxs-lookup"><span data-stu-id="9041c-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="9041c-111">包含するワークフローをワークフロー デザイナーを使用して作成する場合、デザイナーには任意の検証のエラーと警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9041c-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="9041c-112">ワークフローをワークフロー デザイナーを使用せずに作成する場合、ワークフローを呼び出すときに任意の検証エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="9041c-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="9041c-113">ワークフローの作成方法にかかわらず、検証エラーを含むワークフローは実行できません。</span><span class="sxs-lookup"><span data-stu-id="9041c-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="9041c-114">ここでは、このようなアクティビティの検証に関する概要と、アクティビティの検証を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9041c-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9041c-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9041c-115">In This Section</span></span>  
 [<span data-ttu-id="9041c-116">必須の引数とオーバーロード グループ</span><span class="sxs-lookup"><span data-stu-id="9041c-116">Required Arguments and Overload Groups</span></span>](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 <span data-ttu-id="9041c-117">検証を実現するために、`RequiredArgument` 属性および `OverloadGroup` 属性を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9041c-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="9041c-118">命令型コードに基づく検証</span><span class="sxs-lookup"><span data-stu-id="9041c-118">Imperative Code-Based Validation</span></span>](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 <span data-ttu-id="9041c-119"><xref:System.Activities.CodeActivity> および <xref:System.Activities.NativeActivity> に基づくアクティビティにコードに基づく検証を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9041c-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="9041c-120">宣言の制約</span><span class="sxs-lookup"><span data-stu-id="9041c-120">Declarative Constraints</span></span>](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 <span data-ttu-id="9041c-121">複雑なアクティビティの検証を実現するために宣言の制約を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9041c-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="9041c-122">アクティビティ検証の呼び出し</span><span class="sxs-lookup"><span data-stu-id="9041c-122">Invoking Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 <span data-ttu-id="9041c-123">アクティビティの検証が自動的に呼び出される場合と、明示的に検証を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9041c-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9041c-124">参照</span><span class="sxs-lookup"><span data-stu-id="9041c-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9041c-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="9041c-125">Related Sections</span></span>
