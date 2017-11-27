---
title: "WF のランタイム アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3aca3fcdd4fa8d73bf3412d7c20697847d0a699
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="52fcc-102">WF のランタイム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="52fcc-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="52fcc-103"> には、永続化や終了などのワークフロー ランタイムの機能にアクセスするために、システムによって提供されるアクティビティがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="52fcc-103"> provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="52fcc-104">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="52fcc-104">Activity</span></span>|<span data-ttu-id="52fcc-105">説明</span><span class="sxs-lookup"><span data-stu-id="52fcc-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="52fcc-106">ワークフローがその状態を永続化するように明示的に要求します。</span><span class="sxs-lookup"><span data-stu-id="52fcc-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="52fcc-107">実行中のワークフロー インスタンスを終了します。</span><span class="sxs-lookup"><span data-stu-id="52fcc-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="52fcc-108">子アクティビティの永続化を防ぐコンテナー アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="52fcc-108">A container activity that prevents child activities from persisting.</span></span>|
