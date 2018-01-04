---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e297bfc0499ea3ee8d3dd8395165ca22b2baa1de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>構文  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>メソッド  
 DeliveryRequirementsAttribute クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 DeliveryRequirementsAttribute クラスには、次のプロパティがあります。  
  
### <a name="queueddeliveryrequirements"></a>QueuedDeliveryRequirements  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 サービスのバインドがコントラクトをサポートするかどうかを指定します。  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングが順序付きメッセージをサポートするかどうかを指定します。  
  
### <a name="targetcontract"></a>TargetContract  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 適用先となるコントラクトです。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
