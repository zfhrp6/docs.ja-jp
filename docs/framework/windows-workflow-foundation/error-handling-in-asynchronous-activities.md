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
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="3755f-102">非同期アクティビティ内のエラー処理</span><span class="sxs-lookup"><span data-stu-id="3755f-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="3755f-103"><xref:System.Activities.AsyncCodeActivity> でのエラー処理には、アクティビティのコールバック システムを使用したエラーの送信が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3755f-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="3755f-104">このトピックでは、SendMail アクティビティのサンプルを使用してホストへ非同期操作でスローされるエラーを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3755f-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="3755f-105">非同期アクティビティでスローされたエラーをホストへ返す</span><span class="sxs-lookup"><span data-stu-id="3755f-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="3755f-106">SendMail アクティビティ サンプルでの、ホストに返される非同期操作でのエラーのルーティングの手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3755f-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
-   <span data-ttu-id="3755f-107">Exception プロパティを `SendMailAsyncResult` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="3755f-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
-   <span data-ttu-id="3755f-108">スローされたエラーを `SendCompleted` イベント ハンドラー内でそのプロパティにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3755f-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
-   <span data-ttu-id="3755f-109">`EndExecute` イベント ハンドラー内で例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3755f-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="3755f-110">結果として得られるコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3755f-110">The resulting code is as follows.</span></span>  
  
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
