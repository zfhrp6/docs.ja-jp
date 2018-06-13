---
title: COM+ と ServiceModel でのトランザクションの比較
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 4a47fe1686dff2e705b06b001d7d5e4ea6e8c5f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488648"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>COM+ と ServiceModel でのトランザクションの比較
このトピックで、トランザクション COM + サービスの Windows Communication Foundation (WCF) 属性を使用して動作をシミュレートする方法について説明します、<xref:System.ServiceModel>名前空間を提供します。  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>ServiceModel 属性を使った COM+ のエミュレート  
 比較を次の表、<xref:System.EnterpriseServices.TransactionOption>を作成するための列挙、`EnterpriseServices`トランザクションおよび関連 WCF 属性を<xref:System.ServiceModel>名前空間を提供します。  
  
|COM+ 属性|WCF 属性|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> に設定されます。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `true` です。<br /><br /> バインド要素の `TransactionFlow` 属性は `false` です。|  
|必須|<xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.TransactionFlowOption.Allowed> に設定されます。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `true` です。<br /><br /> バインド要素の `TransactionFlow` 属性は `true` です。|  
|サポート状況|同等の属性はありません。 一般に、`Required` を指定した場合の動作を採用することをお勧めします。|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `false` です。<br /><br /> バインド要素の `TransactionFlow` 属性は `false` です。|  
|Disabled|同等の属性はありません。 一般に、`NotSupported` を指定した場合の動作を採用することをお勧めします。|
