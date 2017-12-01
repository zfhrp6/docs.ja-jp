---
title: "スレッドの破棄"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a41dce5db707d0be49c283256de665d316e1a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="destroying-threads"></a>スレッドの破棄
<xref:System.Threading.Thread.Abort%2A>マネージ スレッドを完全に停止するメソッドを使用します。 呼び出すと<xref:System.Threading.Thread.Abort%2A>、共通言語ランタイムをスロー、<xref:System.Threading.ThreadAbortException>対象のスレッドにキャッチできる対象のスレッドにします。 詳細については、「<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>」を参照してください。  
  
> [!NOTE]
>  スレッドが実行されている場合は、アンマネージ コードの場合にその<xref:System.Threading.Thread.Abort%2A>メソッドが呼び出されると、ランタイムのマークが付け<xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>。 スレッドがマネージ コードに戻ると、例外がスローされます。  
  
 スレッドが中止されると、一度を再起動することはできません。  
  
 <xref:System.Threading.Thread.Abort%2A>メソッドは行われません、スレッドが、すぐに中止する対象のスレッドにキャッチできるため、<xref:System.Threading.ThreadAbortException>内のコードの任意の量を実行し、`finally`ブロックします。 呼び出すことができます<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>スレッドが終了するまで待機する必要がある場合。 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>ブロッキング呼び出しではスレッドの実行が実際に停止されるまで返されないか、オプションのタイムアウト間隔が経過しました。 中止されたスレッドを呼び出すことが、<xref:System.Threading.Thread.ResetAbort%2A>メソッドで無限の処理を実行したり、`finally`ブロックにあるため、タイムアウト時間を指定しないと場合、待機が終了とは限りません。  
  
 呼び出しで待機しているスレッド、<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>メソッドを呼び出す他のスレッドを中断できる<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>です。  
  
## <a name="handling-threadabortexception"></a>ThreadAbortException の処理  
 呼び出しの結果として、中止するスレッドが予想される場合<xref:System.Threading.Thread.Abort%2A>またはスレッドが実行されているアプリケーション ドメインをアンロードした結果として、自分のコードから (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>使用<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>スレッドを終了する)、スレッドを処理する必要があります<xref:System.Threading.ThreadAbortException>での最終処理を実行し、`finally`句、次のコードに示すようにします。  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 クリーンアップ コードがである必要があります、`catch`句または`finally`句、ため、<xref:System.Threading.ThreadAbortException>の最後に、システムによって再スロー、`finally`句、またはの最後に、`catch`句がある場合にない`finally`句。  
  
 システムから呼び出すことによって、例外を再スローすることができなくことができます、<xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>メソッドです。 ただし、行う必要がある場合のみ、この独自のコードの原因となった、<xref:System.Threading.ThreadAbortException>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [スレッドの使用とスレッド処理](../../../docs/standard/threading/using-threads-and-threading.md)
