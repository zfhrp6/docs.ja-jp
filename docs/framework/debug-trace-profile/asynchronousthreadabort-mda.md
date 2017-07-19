---
title: "asynchronousThreadAbort MDA | Microsoft Docs"
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
  - "asynchronous thread aborts"
  - "AsynchronousThreadAbort MDA"
  - "managed debugging assistants (MDAs), asynchronous thread aborts"
  - "threading [.NET Framework], managed debugging assistants"
  - "MDAs (managed debugging assistants), asynchronous thread aborts"
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# asynchronousThreadAbort MDA
`asynchronousThreadAbort` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、スレッドが別のスレッドに非同期の中止処理を適用しようとするとアクティブになります。  同期のスレッド中止では、`asynchronousThreadAbort` MDA はアクティブになりません。  
  
## 症状  
 メインのアプリケーション スレッドが中止されると、アプリケーションは未処理の <xref:System.Threading.ThreadAbortException> でクラッシュします。  もしもアプリケーションが実行を続けると、アプリケーションがクラッシュした場合よりも悪い結果を招き、データ破損が続くなどの状況になる恐れがあります。  
  
 分割できない操作が部分的に完了した後で中断された可能性があり、アプリケーション データは予測不可能な状態のままになりました。  <xref:System.Threading.ThreadAbortException> は、コード実行中、見かけ上はランダムなポイントから生成でき、例外が発生するとは予期していない場所で生成されることもよくあります。  コードは例外などを処理できず、破損した状態になります。  
  
 問題には偶然性が伴うため、症状は非常に多岐にわたります。  
  
## 原因  
 あるスレッドのコードが、対象スレッド上の <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> メソッドを呼び出し、非同期のスレッド中止を招きました。  <xref:System.Threading.Thread.Abort%2A> への呼び出しを実行するコードは、中止操作の対象スレッドとは異なるため、スレッド中止は非同期になります。  同期のスレッド中止の場合、<xref:System.Threading.Thread.Abort%2A> を実行するスレッドがこの操作を実行するのは、アプリケーション状態に一貫性がある安全なチェックポイントだけなので、問題になりません。  
  
 非同期のスレッド中止は、対象スレッドの実行中に予期しないポイントで実行されるため、問題になります。  これを回避するには、この方法で中断される可能性のあるスレッドで実行するコードでは、ほとんどすべてのコード行で <xref:System.Threading.ThreadAbortException> を処理して、アプリケーション データが一貫性のある状態へ戻すことができるように気を付ける必要があります。  コードがこの問題に備えて作成されることを想定したり、起こりうるすべての状況に対処するコードを作成したりすることは、現実的ではありません。  
  
 アンマネージ コードの呼び出しと `finally` ブロックは非同期に中止されませんが、これらのいずれかから終了すると、即座に中止されます。  
  
 問題には偶然性が伴うため、原因を特定することは困難な場合があります。  
  
## 解決策  
 非同期のスレッド中止を使用しなければならないコード設計を避けます。  対象スレッドが <xref:System.Threading.Thread.Abort%2A> の呼び出しを必要としない場合に、その対象スレッドを中断するのに適した方法はいくつかあります。  最も安全な方法は、対象スレッドが中断を要求していることを示すシグナルとなる、共通プロパティなどの機構を導入することです。  対象スレッドは、特定の安全なチェックポイントで、シグナルをチェックします。  中断が要求されたことが示されている場合は、適切にシャットダウンできます。  
  
## ランタイムへの影響  
 この MDA は、CLR への影響はありません。  非同期のスレッド中止に関するデータを報告するだけです。  
  
## 出力  
 MDA は、中止を実行するスレッドの ID、および中止の対象となるスレッドの ID を報告します。  これは非同期の中止に限られるため、これらが同じになることはありません。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <asynchronousThreadAbort />  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 `asynchronousThreadAbort` MDA は、独立して実行されるスレッドで <xref:System.Threading.Thread.Abort%2A> を呼び出すだけでアクティブになります。  スレッドの開始関数がより複雑な一連の操作で構成され、中止によって中断されるポイントを特定できない場合は、影響を考慮してください。  
  
```  
using System.Threading;  
void FireMda()  
{  
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Abort();   
    t.Join();  
}  
```  
  
## 参照  
 <xref:System.Threading.Thread>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)