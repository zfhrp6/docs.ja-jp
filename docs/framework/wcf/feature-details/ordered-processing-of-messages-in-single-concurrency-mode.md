---
title: "Single 同時実行モードでメッセージを順番に処理する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a1acf4c3edb51500c2ead2e4ba33c6d3cc9c953f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Single 同時実行モードでメッセージを順番に処理する
基になるチャネルがセッションフルでない限り、WCF は、メッセージが処理される順序に関する保証はありません。  インスタンスの順序でメッセージを処理する、セッションの多いチャネルではない MsmqInputChannel を使用する WCF サービスは失敗します。 状況によっては、開発者可能性があります順番に処理動作をしますが、セッションを使用するには。 このトピックでは、サービスが Single 同時実行モードで実行されている場合にこの動作を構成する方法について説明します。  
  
## <a name="in-order-message-processing"></a>順番に従ったメッセージの処理  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> という名前の新しい属性が <xref:System.ServiceModel.ServiceBehaviorAttribute> に追加されました。 <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> を true に設定し、<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> を <xref:System.ServiceModel.ConcurrencyMode.Single> に設定すると、サービスに送信されたメッセージは順番に処理されます。 次のコードは、これらの属性の設定方法を示しています。  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> をその他の値に設定すると、<xref:System.InvalidOperationException> がスローされます。  
  
## <a name="see-also"></a>関連項目  
 [セッション、インスタンス化、および同時実行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [同時実行](../../../../docs/framework/wcf/samples/concurrency.md)
