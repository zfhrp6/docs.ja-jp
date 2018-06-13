---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 7531cf27aec0ea9a71ee7b1906e8f7cee151695f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485955"
---
# <a name="servicetimeoutsbehavior"></a>ServiceTimeoutsBehavior
ServiceTimeoutsBehavior  
  
## <a name="syntax"></a>構文  
  
```  
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceTimeoutsBehavior クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ServiceTimeoutsBehavior クラスには、次のプロパティがあります。  
  
### <a name="transactiontimeout"></a>TransactionTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 トランザクションを完了しなければならない期間。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
