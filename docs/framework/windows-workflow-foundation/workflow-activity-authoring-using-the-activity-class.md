---
title: アクティビティ クラスを使用したワークフロー アクティビティの作成
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 517e646c8a84ed4374c01da974d952d4f50a4e22
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="2cb6b-102">アクティビティ クラスを使用したワークフロー アクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="2cb6b-102">Workflow Activity Authoring Using the Activity Class</span></span>
<span data-ttu-id="2cb6b-103">最も基本的な方法で Windows Workflow Foundation (WF) を使用してアクティビティを作成する[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]から継承するクラスを作成するのには、<xref:System.Activities.Activity>を作成する機能をまとめることでカスタム アクティビティまたはアクティビティから、[組み込みアクティビティ ライブラリ](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)です。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-103">The most basic way to create an activity using Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="2cb6b-104">ここでは、2 つのメッセージをコンソールに書き込むアクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-104">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="2cb6b-105">アクティビティ デザイナーを使ってカスタム アクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="2cb6b-105">To create a custom Activity using the activity designer</span></span>  
  
1.  <span data-ttu-id="2cb6b-106">[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-106">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="2cb6b-107">[ファイル]、[新規作成]、[プロジェクト] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-107">Select File, New, Project.</span></span> <span data-ttu-id="2cb6b-108">選択**Workflow 4.0**  **Visual c#** で、**プロジェクトの種類**ウィンドウ、および選択、 **v2010**ノード。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-108">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="2cb6b-109">選択**アクティビティ ライブラリ**で、**テンプレート**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-109">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="2cb6b-110">新しいプロジェクトに HelloActivity という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-110">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="2cb6b-111">新しいアクティビティを開きます。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-111">Open the new activity.</span></span>  <span data-ttu-id="2cb6b-112"><xref:System.Activities.Statements.Sequence> アクティビティをツールボックスからデザイナー画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-112">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>  
  
4.  <span data-ttu-id="2cb6b-113"><xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-113">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="2cb6b-114">入力`"Hello World"`(引用符を含む) に、**テキスト**フィールドです。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-114">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>  
  
5.  <span data-ttu-id="2cb6b-115">2 つ目の <xref:System.Activities.Statements.WriteLine> アクティビティを、1 つ目の下にある <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-115">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="2cb6b-116">入力`"Goodbye"`(引用符を含む) に、**テキスト**フィールドです。</span><span class="sxs-lookup"><span data-stu-id="2cb6b-116">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
