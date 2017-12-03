---
title: "COM+ と ServiceModel でのトランザクションの比較"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5229c872c4843df916cf538b7f2e88e451dc6b9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>COM+ と ServiceModel でのトランザクションの比較
このトピックでは、トランザクション COM+ サービスの動作を、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 名前空間で定義された <xref:System.ServiceModel> 属性を使用してシミュレートする方法について説明します。  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>ServiceModel 属性を使った COM+ のエミュレート  
 次の表では、<xref:System.EnterpriseServices.TransactionOption> トランザクションの生成に使用される `EnterpriseServices` 列挙体の各値を比較し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 名前空間で定義された <xref:System.ServiceModel> 属性との関連を示します。  
  
|COM+ 属性|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 属性|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> に設定されます。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `true` です。<br /><br /> バインド要素の `TransactionFlow` 属性は `false` です。|  
|必須|<xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.TransactionFlowOption.Allowed> に設定されます。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `true` です。<br /><br /> バインド要素の `TransactionFlow` 属性は `true` です。|  
|サポート状況|同等の属性はありません。 一般に、`Required` を指定した場合の動作を採用することをお勧めします。|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `false` です。<br /><br /> バインド要素の `TransactionFlow` 属性は `false` です。|  
|Disabled|同等の属性はありません。 一般に、`NotSupported` を指定した場合の動作を採用することをお勧めします。|
