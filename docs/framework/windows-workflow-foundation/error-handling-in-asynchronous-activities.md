---
title: "非同期アクティビティ内のエラー処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 非同期アクティビティ内のエラー処理
<xref:System.Activities.AsyncCodeActivity> でのエラー処理には 、アクティビティのコールバック システムを使用したエラーの送信が含まれています。このトピックでは、SendMail アクティビティのサンプルを使用してホストへ非同期操作でスローされる エラーを取得する方法について説明します。  
  
## 非同期アクティビティでスローされたエラーをホストへ返す  
 SendMail アクティビティ サンプルにある、ホストに返される非同期操作でのエラー送信には、次の手順が含まれています。:  
  
-   Exception プロパティを `SendMailAsyncResult` クラスに追加します。  
  
-   スローされたエラーを `SendCompleted` イベント ハンドラー内でそのプロパティにコピーします。  
  
-   `EndExecute` イベント ハンドラー内で例外をスローします。  
  
 結果として得られるコードは次のようになります。  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }   
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;   
        }  
    }  
  
```