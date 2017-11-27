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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40bdc27337daae02795137fc3ac67575787018c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
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
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
