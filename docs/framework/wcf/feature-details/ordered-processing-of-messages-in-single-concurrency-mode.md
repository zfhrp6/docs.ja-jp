---
title: "Single 同時実行モードでメッセージを順番に処理する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Single 同時実行モードでメッセージを順番に処理する
WCF では、基になるチャネルがセッションフルでない場合、メッセージを処理する順序については保証されません。たとえば、セッションフル チャネルではない MsmqInputChannel を使用する WCF サービスでは、メッセージを順番に処理できません。開発者には、セッションを使用しないで、順番どおりの処理動作が必要な場合があります。このトピックでは、サービスが Single 同時実行モードで実行されている場合に、この動作を構成する方法について説明します。  
  
## 順番に従ったメッセージの処理  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> という名前の新しい属性が <xref:System.ServiceModel.ServiceBehaviorAttribute> に追加されました。<xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> を true に設定し、<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> を <xref:System.ServiceModel.ConcurrencyMode> に設定すると、サービスに送信されたメッセージは順番に処理されます。次のコード スニペットは、これらの属性の設定方法を示しています。  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
  
```  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> を他の値に設定すると、<xref:System.InvalidOperationException> がスローされます。  
  
## 参照  
 [セッション、インスタンス化、および同時実行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)   
 [同時実行](../../../../docs/framework/wcf/samples/concurrency.md)