---
title: "カスタム追跡レコード"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a459e6df0e030f4e17bb73461d8fa790a61787e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="custom-tracking-records"></a>カスタム追跡レコード
このトピックではカスタム追跡レコードを作成し、出力されたデータをレコードと一緒に読み込む方法を示します。  
  
## <a name="emitting-custom-tracking-records"></a>カスタム追跡レコードの出力  
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
  
 <xref:System.Activities.Tracking.CustomTrackingRecord> 上で <xref:System.Activities.NativeActivityContext.Track%2A> メソッドを呼び出すことで、`ActvityContext` をコード アクティビティに出力できます。  
  
## <a name="see-also"></a>関連項目  
 [Windows Server App Fabric の監視](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [アプリケーション App Fabric の監視](http://go.microsoft.com/fwlink/?LinkId=201275)
