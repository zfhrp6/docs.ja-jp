---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 480670f19407321eb0928d07752936b2ece1f7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484189"
---
# <a name="activitytransfer"></a>ActivityTransfer
アクティビティ転送イベント  
  
## <a name="syntax"></a>構文  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ActivityTransfer クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ActivityTransfer クラスには次のプロパティがあります。  
  
### <a name="activityid"></a>ActivityID  
  
-   データ型: object  
    アクセスの種類 : 読み取り専用  
  
-   アクティビティ ID  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
-   データ型: object  
    アクセスの種類 : 読み取り専用  
  
-   関連アクティビティ ID  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|
