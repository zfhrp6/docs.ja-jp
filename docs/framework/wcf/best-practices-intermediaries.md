---
title: "ベスト プラクティス: 中継局 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# ベスト プラクティス: 中継局
サービス側のチャネルが正常閉じられていることを確認するために中継局を呼び出すときには、例外処理が正しく行われることに注意が必要です。  
  
 次のようなシナリオがあるとします。クライアントは、バックエンド サービスを呼び出す中継局を呼び出します。バックエンド サービスは、エラー コントラクトを定義しません。したがって、そのサービスからスローされたエラーは型指定されていないエラーとして扱われます。バックエンド サービスは <xref:System.ApplicationException> をスローし、WCF サービス側のチャネルを中止します。<xref:System.ApplicationException> は、中継局へスローされる <xref:System.ServiceModel.FaultException> として表示されます。中継局は <xref:System.ApplicationException> を再スローします。WCF はこれを中継局からの型指定されていないエラーとして解釈し、クライアントに転送します。エラーを受け取ると、中継局とクライアントは、クライアント側のチャネルをエラーにします。ただし、WCF はそのエラーが致命的であると認知しないため、中間サービス側のチャネルは開いたままとなります。  
  
 このシナリオのベスト プラクティスは、サービスからのエラーを致命的であるかどうかを検出し、エラーである場合は、次のコード スニペットに示すように、中継局がそのサービス側のチャネルをエラーとします。  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
  
```  
  
## 参照  
 [WCF エラー処理](../../../docs/framework/wcf/wcf-error-handling.md)   
 [コントラクトおよびサービスのエラーの指定と処理](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)