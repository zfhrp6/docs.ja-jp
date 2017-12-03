---
title: "WF 内のエラー処理アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8b7ed6837e9ee88e85324ed5d7a2b9ff3e419a9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="error-handling-activities-in-wf"></a>WF 内のエラー処理アクティビティ
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、エラーの処理および回復を実装するためのシステム標準のアクティビティが用意されています。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][例外](../../../docs/framework/windows-workflow-foundation/exceptions.md)です。  
  
## <a name="error-handling-activities"></a>エラー処理アクティビティ  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|`TryCatch` アクティビティ内からスローされた最後の例外を再スローします。|  
|<xref:System.Activities.Statements.Throw>|例外をスローします。|  
|<xref:System.Activities.Statements.TryCatch>|例外処理を実装します。|
