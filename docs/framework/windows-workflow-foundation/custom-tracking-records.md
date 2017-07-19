---
title: "カスタム追跡レコード | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# カスタム追跡レコード
このトピックではカスタム追跡レコードを作成し、出力されたデータをレコードと一緒に読み込む方法を示します。  
  
## カスタム追跡レコードの出力  
 次の例に示すように、カスタム追跡レコードはコード アクティビティから出力できます。  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 `ActvityContext` 上で <xref:System.Activities.NativeActivityContext.Track%2A> メソッドを呼び出すことで、<xref:System.Activities.Tracking.CustomTrackingRecord> をコード アクティビティに出力できます。  
  
## 参照  
 [Windows Server App Fabric の監視](http://go.microsoft.com/fwlink/?LinkId=201273)   
 [App Fabric を使用したアプリケーションの監視](http://go.microsoft.com/fwlink/?LinkId=201275)