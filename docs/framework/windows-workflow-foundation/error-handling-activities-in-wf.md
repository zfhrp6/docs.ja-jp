---
title: WF 内のエラー処理アクティビティ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1c0459dd562f6292a8fe9a42f8b1b48cd175516a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="error-handling-activities-in-wf"></a>WF 内のエラー処理アクティビティ
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、エラーの処理および回復を実装するためのシステム標準のアクティビティが用意されています。 詳細については、次を参照してください。[例外](../../../docs/framework/windows-workflow-foundation/exceptions.md)です。  
  
## <a name="error-handling-activities"></a>エラー処理アクティビティ  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|`TryCatch` アクティビティ内からスローされた最後の例外を再スローします。|  
|<xref:System.Activities.Statements.Throw>|例外をスローします。|  
|<xref:System.Activities.Statements.TryCatch>|例外処理を実装します。|
