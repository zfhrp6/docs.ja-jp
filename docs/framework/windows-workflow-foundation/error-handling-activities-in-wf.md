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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bcb006f649fe0d2a92b4c789c435ba33916d140f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling-activities-in-wf"></a>WF 内のエラー処理アクティビティ
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、エラーの処理および回復を実装するためのシステム標準のアクティビティが用意されています。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][例外](../../../docs/framework/windows-workflow-foundation/exceptions.md)です。  
  
## <a name="error-handling-activities"></a>エラー処理アクティビティ  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|`TryCatch` アクティビティ内からスローされた最後の例外を再スローします。|  
|<xref:System.Activities.Statements.Throw>|例外をスローします。|  
|<xref:System.Activities.Statements.TryCatch>|例外処理を実装します。|
