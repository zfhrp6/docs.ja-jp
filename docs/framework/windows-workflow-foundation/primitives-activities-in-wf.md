---
title: "WF 内のプリミティブ アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e411d922577dcb9d3ca322d61c0e10911a006027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="c47a0-102">WF 内のプリミティブ アクティビティ</span><span class="sxs-lookup"><span data-stu-id="c47a0-102">Primitives Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="c47a0-103"> には、共通のタスクを実行する便利な機構を提供する、システムによって提供されるアクティビティがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="c47a0-103"> provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="c47a0-104">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="c47a0-104">Activity</span></span>|<span data-ttu-id="c47a0-105">説明</span><span class="sxs-lookup"><span data-stu-id="c47a0-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="c47a0-106">現在のスコープで、変数に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c47a0-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="c47a0-107">1 つの実行パスをアイドル状態にして、場合によってはワークフローをアンロードできるようにします。</span><span class="sxs-lookup"><span data-stu-id="c47a0-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="c47a0-108"><xref:System.Activities.ActivityDelegate> から派生し、プロパティとして公開されるデリゲートを実行します。</span><span class="sxs-lookup"><span data-stu-id="c47a0-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="c47a0-109">CLR オブジェクトのパブリック メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c47a0-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="c47a0-110">指定した文字列を、コンソールまたは指定した <xref:System.IO.TextWriter> オブジェクトに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="c47a0-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
