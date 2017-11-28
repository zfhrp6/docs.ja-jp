---
title: "非同期アクティビティ内のエラー処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7606aeeeb3e2e583f9a217b78bcae4aebc6d8662
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling-in-asynchronous-activities"></a>非同期アクティビティ内のエラー処理
<xref:System.Activities.AsyncCodeActivity> でのエラー処理には、アクティビティのコールバック システムを使用したエラーの送信が含まれています。 このトピックでは、SendMail アクティビティのサンプルを使用してホストへ非同期操作でスローされるエラーを取得する方法について説明します。  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>非同期アクティビティでスローされたエラーをホストへ返す  
 SendMail アクティビティ サンプルでの、ホストに返される非同期操作でのエラーのルーティングの手順は次のとおりです。  
  
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
