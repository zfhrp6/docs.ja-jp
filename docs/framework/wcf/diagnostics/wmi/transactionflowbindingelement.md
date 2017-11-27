---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c65eb1689d1411cb9083967b9a29c946b7568b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>メソッド  
 TransactionFlowBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 TransactionFlowBindingElement クラスには、次のプロパティがあります。  
  
### <a name="issuedtokens"></a>IssuedTokens  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 発行されるセキュリティ トークン ヘッダー (WS-Trust からの IssuedTokens) の要件を指定します。  
  
### <a name="transactionprotocol"></a>TransactionProtocol  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 トランザクションをフローさせるためにサービスによって使用されるトランザクション プロトコルです。  
  
### <a name="transactions"></a>トランザクション  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 受信トランザクションをサポートするかどうかを示します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
