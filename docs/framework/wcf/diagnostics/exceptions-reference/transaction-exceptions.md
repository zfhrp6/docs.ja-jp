---
title: "トランザクションの例外"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be53af47aef4d42ddd2c77fbd29c8c9e9961c47b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-exceptions"></a>トランザクションの例外
ここでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] トランザクションによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|メタデータからインポートされたポリシー情報により、TransactionProtocol に操作間で異なる値が指定されました。 各エンドポイントでサポートされる TransactionProtocol は 1 つに限られます。|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete は、サービスの InstanceContextMode が PerSession にならない限り、false にはなりません。 指定したコントラクトと操作の実装でエラーが発生しました。|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete は、TransactionAutoComplete が false に設定され、TransactionScopeRequired が true に設定されている場合にのみ、操作から呼び出すことができます。 これは無効なシナリオであり、現在のトランザクションは終了しました。|  
|TransactionFlowRequiredIssuedTokens|トランザクションをフローさせるには、発行済みトークンのフローもサポートされる必要があります。|  
|TrustDriverVersionDoesNotSupportIssuedTokens|構成されたバージョンの Trust では、発行済みトークンがサポートされません。 WSTrustFeb2005 またはそれ以降を使用してください。|
