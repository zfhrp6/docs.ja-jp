---
title: 実行可能インスタンス検出期間
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: 7b12353c3bd18367618825d22d020391b14ec3f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513238"
---
# <a name="runnable-instances-detection-period"></a><span data-ttu-id="74ee3-102">実行可能インスタンス検出期間</span><span class="sxs-lookup"><span data-stu-id="74ee3-102">Runnable Instances Detection Period</span></span>
<span data-ttu-id="74ee3-103">SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、実行可能またはアクティブ化可能なインスタンスを永続性データベースで検出します。</span><span class="sxs-lookup"><span data-stu-id="74ee3-103">The SQL Workflow Instance Store runs an internal task that periodically wakes up and detects runnable or activatable instances in the persistence database.</span></span> <span data-ttu-id="74ee3-104">**実行可能インスタンス検出期間**SQL Workflow Instance Store のプロパティを SQL Workflow Instance Store が実行可能またはアクティブ化可能なワークフローを検出する検出タスクを実行するまでの期間を指定します前回の検出サイクルの後に、永続性データベースでのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="74ee3-104">The **Runnable Instances Detection Period** property of the SQL Workflow Instance Store specifies the time period after which the SQL Workflow Instance Store runs a detection task to detect any runnable or activatable workflow instances in the persistence database after the previous detection cycle.</span></span>  
  
 <span data-ttu-id="74ee3-105">このプロパティの間隔を短く設定すると、ワークフロー インスタンスに関連付けられたタイマーの期限切れと、イベントのシグナリングおよび後続のインスタンスの読み込みの間の時間が短くなります。</span><span class="sxs-lookup"><span data-stu-id="74ee3-105">Setting a shorter interval for this property reduces the time between the expiration of a timer associated with a workflow instance and the signaling of the event and subsequent loading of the instance.</span></span> <span data-ttu-id="74ee3-106">ただし、ホストにかかる処理の負荷も増えるため、永続的なタイマーやホスト エラーがまれなシナリオでは望ましくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="74ee3-106">However, it also increases the processing load on a host and may not be desirable in scenarios where durable timers and/or host failures are rare.</span></span> <span data-ttu-id="74ee3-107">プロパティの型は TimeSpan で、プロパティの値は hh:mm:ss の形式です。</span><span class="sxs-lookup"><span data-stu-id="74ee3-107">The type of the property is TimeSpan and the value of the property follows the format: hh:mm:ss.</span></span> <span data-ttu-id="74ee3-108">このプロパティの最小値は 00:00:01 です。</span><span class="sxs-lookup"><span data-stu-id="74ee3-108">The minimum value for this property is 00:00:01.</span></span> <span data-ttu-id="74ee3-109">プロパティの既定値は 00:00:05 です。</span><span class="sxs-lookup"><span data-stu-id="74ee3-109">The default value for the property is 00:00:05.</span></span>  
  
 <span data-ttu-id="74ee3-110">詳細については検出とアクティブ化可能な実行可能なワークフロー インスタンスをアクティブ化を参照してください[インスタンスのアクティブ化](../../../docs/framework/windows-workflow-foundation/instance-activation.md)です。</span><span class="sxs-lookup"><span data-stu-id="74ee3-110">For more information detecting and activating runnable and activatable workflow instances, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span>
