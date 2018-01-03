---
title: illegalPrepareConstrainedRegion MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b739cb76827a12a9928e0268e5e2cb8be686479
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
`illegalPrepareConstrainedRegion` マネージ デバッグ アシスタント (MDA) は、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> メソッドの呼び出しが、例外ハンドラーの `try` ステートメントの直前にない場合にアクティブ化されます。 この制限は、MSIL レベルであり、呼び出しと `try` の間でコメントなどのコードを生成しないソースの使用が許可されます。  
  
## <a name="symptoms"></a>症状  
 そのように扱われず、単純な例外処理ブロック (`finally` または `catch`) として扱われる制約された実行領域 (CER)。 その結果、メモリ不足の状態やスレッドの中止のときには領域は実行されません。  
  
## <a name="cause"></a>原因  
 CER の準備パターンが正しく実行されません。  エラー イベントが発生します。 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>例外ハンドラーとしての CER の概要を示すために使用されるメソッドの呼び出し、 `catch` / `finally` / `fault` / `filter`直前のブロックを使用する必要があります、`try`ステートメントです。  
  
## <a name="resolution"></a>解像度  
 `try`ステートメントの直前に <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> の呼び出しがあることを確認します。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 この MDA は CLR に影響しません。  
  
## <a name="output"></a>出力  
 MDA は、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> メソッドの呼び出し元の名前、MSIL のオフセット、および呼び出しが try ブロックの先頭の直前にないことを示すメッセージを表示します。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>例  
 次のコード例では、この MDA のアクティブ化の原因となるパターンを示します。  
  
```  
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
