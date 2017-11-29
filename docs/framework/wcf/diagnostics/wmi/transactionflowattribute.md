---
title: TransactionFlowAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9c8674-29f7-4f14-aa1f-dc2644ca57e4
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2eb7be7fb1acbfb9ccd46aee341e001156795ebc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="transactionflowattribute"></a>TransactionFlowAttribute
TransactionFlowAttribute  
  
## <a name="syntax"></a>構文  
  
```  
class TransactionFlowAttribute : Behavior  
{  
  string TransactionFlowOption;  
};  
```  
  
## <a name="methods"></a>メソッド  
 TransactionFlowAttribute クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 TransactionFlowAttribute クラスには、次のプロパティがあります。  
  
### <a name="transactionflowoption"></a>TransactionFlowOption  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 トランザクションがフローするかどうかを示します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.TransactionFlowAttribute>
