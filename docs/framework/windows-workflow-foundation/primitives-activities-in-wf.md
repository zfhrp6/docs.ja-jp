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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0bd34984b421f353c53da8c97533b396a49751d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="primitives-activities-in-wf"></a>WF 内のプリミティブ アクティビティ
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] には、共通のタスクを実行する便利な機構を提供する、システムによって提供されるアクティビティがいくつか用意されています。  
  
|アクティビティ|説明|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|現在のスコープで、変数に値を割り当てます。|  
|<xref:System.Activities.Statements.Delay>|1 つの実行パスをアイドル状態にして、場合によってはワークフローをアンロードできるようにします。|  
|<xref:System.Activities.Statements.InvokeDelegate>|<xref:System.Activities.ActivityDelegate> から派生し、プロパティとして公開されるデリゲートを実行します。|  
|<xref:System.Activities.Statements.InvokeMethod>|CLR オブジェクトのパブリック メソッドを実行します。|  
|<xref:System.Activities.Statements.WriteLine>|指定した文字列を、コンソールまたは指定した <xref:System.IO.TextWriter> オブジェクトに書き込みます。|
