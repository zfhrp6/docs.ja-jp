---
title: "invalidCERCall MDA | Microsoft Docs"
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
  - "invalid CER calls"
  - "InvalidCERCall MDA"
  - "MDAs (managed debugging assistants), CER calls"
  - "constrained execution regions"
  - "CER calls"
  - "managed debugging assistants (MDAs), CER calls"
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# invalidCERCall MDA
`invalidCERCall` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、信頼性のコントラクトを持たないメソッド、または極度に脆弱なコントラクトを持つメソッドへの呼び出しが、制約された実行領域 \(CER: Constrained Execution Region\) グラフ内で行われたときにアクティブになります。  脆弱なコントラクトとは、最悪の場合の状態破損が、呼び出しに渡されるインスタンスよりもスコープが大きいこと、つまり、<xref:System.AppDomain> やプロセスの状態が破損すること、または CER 内で呼び出されたときに呼び出し結果が常に確定的に計算できるとは限らないことを宣言するコントラクトです。  
  
## 症状  
 CER でのコードの実行時に予想外の結果が生じます。  症状は限定されていません。  症状としては、信頼性の低いメソッドへの呼び出し時に予想外の <xref:System.OutOfMemoryException> や <xref:System.Threading.ThreadAbortException> などの例外が発生する可能性があります。これは、ランタイムが、事前にその呼び出しを準備していなかったり、実行時に <xref:System.Threading.ThreadAbortException> 例外から保護していなかったりするためです。  より大きな脅威は、実行時にメソッドから生じる例外により、<xref:System.AppDomain> やプロセスが不安定な状態になる可能性があることです。これは、CER の目的とは正反対です。  CER の作成目的は、このような状態破損を回避することだからです。  破損状態の症状は、一貫した状態の定義がアプリケーションによって異なるため、それぞれのアプリケーションに固有です。  
  
## 原因  
 CER 内のコードが、<xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> を持たない、または CER で実行できない脆弱な <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> を持つ関数を呼び出しています。  
  
 信頼性のコントラクトの構文という点からすると、脆弱なコントラクトとは、<xref:System.Runtime.ConstrainedExecution.Consistency> 列挙値を指定しないコントラクトや、<xref:System.Runtime.ConstrainedExecution.Consistency>、<xref:System.Runtime.ConstrainedExecution.Consistency>、または <xref:System.Runtime.ConstrainedExecution.Cer> の <xref:System.Runtime.ConstrainedExecution.Consistency> 値を指定するコントラクトです。  これらの条件はいずれも、呼び出されるコードにより、CER 内で一貫した状態を維持しようとする他のコードの試みが阻害される可能性があることを意味します。CER では、コードによってエラーを確定的な方法で処理できるため、アプリケーションにとって重要な内部のインバリアントを保持し、メモリ不足例外などの一時的なエラーが発生した場合にアプリケーションが動作を継続できます。  
  
 この MDA がアクティブになった場合は、CER で呼び出されているメソッドが呼び出し元が予期しない形で失敗したり、<xref:System.AppDomain> やプロセスの状態を破損または回復不可能なままにして失敗したりする可能性があります。  呼び出されたコードが正しく実行され、コントラクトの欠落だけが問題となることもあります。  ただし、信頼性の高いコードの記述に関連する問題は軽微であり、コントラクトの欠落は、コードを正しく実行できないことを示す良好な指標です。  コントラクトは、プログラマが信頼できる形でコードを作成していることを示し、またコードの今後のバージョンで信頼性の保証が変わらないと約束していることを示す指標です。つまり、コントラクトとは意志の宣言であり、単なる実装詳細ではありません。  
  
 脆弱なコントラクトを持つメソッドやコントラクトが存在しないメソッドは、予測不可能なさまざまな形で失敗する可能性があるため、ランタイムは、ロードの小さい JIT コンパイル、ジェネリック ディクショナリの読み込み、スレッドの中止などによってもたらされる、予測不可能な固有のエラーをメソッドから削除しようとしません。  つまり、この MDA がアクティブになったときは、ランタイムには、呼び出されたメソッドが、定義されている CER に含まれておらず、このサブツリーの準備を継続すると、潜在的なエラーがマスクされるため、呼び出し先がこのノードで終了したことを示します。  
  
## 解決策  
 有効な信頼性のコントラクトを関数に追加するか、その関数呼び出しの使用を避けます。  
  
## ランタイムへの影響  
 脆弱なコントラクトを CER から呼び出すと、CER エラーが発生し、CER の操作が終了する可能性があります。  これにより、<xref:System.AppDomain> プロセス状態が破損することがあります。  
  
## 出力  
 この MDA のサンプル出力を次に示します。  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>   
 <xref:System.Runtime.ConstrainedExecution>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)