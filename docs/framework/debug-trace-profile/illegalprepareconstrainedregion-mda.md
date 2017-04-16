---
title: "illegalPrepareConstrainedRegion MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "PrepareConstrainedRegions method"
  - "managed debugging assistants (MDAs), illegal PrepareConstrainedRegions"
  - "try/catch exception handling, managed debugging assistants"
  - "IllegalPrepareConstrainedRegions MDA"
  - "MDAs (managed debugging assistants), illegal PrepareConstrainedRegions"
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# illegalPrepareConstrainedRegion MDA
`illegalPrepareConstrainedRegion` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=fullName> メソッド呼び出しが例外ハンドラーの `try` ステートメントの直前にない場合にアクティブになります。  この制限は MSIL レベルであるため、呼び出しと `try` の間にコード生成されないソース \(コメントなど\) がある場合は問題ありません。  
  
## 症状  
 制約された実行領域 \(CER\) が制約された状態として扱われず、簡単な例外処理ブロック block \(`finally` または `catch`\) として扱われる。  結果として、メモリが不足している場合やスレッドが中止された場合に、領域が実行されません。  
  
## 原因  
 CER の準備パターンが正しく続いていません。エラー イベントが発生します。  `catch`\/`finally`\/`fault`\/`filter` ブロック内で CER の導入として例外ハンドラーをマークするために使用される <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> メソッドは、`try` ステートメントの直前で使用する必要があります。  
  
## 解決策  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> への呼び出しが `try` `` ステートメントの直前に行われるようにします。  
  
## ランタイムへの影響  
 この MDA は、CLR への影響はありません。  
  
## 出力  
 MDA は、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> メソッドの呼び出し元メソッドの名前、MSIL オフセット、および呼び出しが try ブロックの先頭の直前で行われていないことを示すメッセージを表示します。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 この MDA がアクティブになるパターンのコード例を次に示します。  
  
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
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)