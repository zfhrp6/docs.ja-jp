---
title: "Lambda Expressions in PLINQ and TPL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Func delegate, creating with lambda expression"
  - "Action delegate, creating with lambda expression"
  - "lambda expressions, with Action and Func"
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Lambda Expressions in PLINQ and TPL
タスク並列ライブラリ \(TPL: Task Parallel Library\) には、デリゲートの <xref:System.Func%601?displayProperty=fullName> 系または <xref:System.Action?displayProperty=fullName> 系を入力パラメーターとして取得する多くのメソッドが用意されています。  これらのデリゲートを使用して、カスタムのプログラム ロジックを並列ループ、タスク、またはクエリに渡します。  PLINQ と同様に、TPL のコード例では、ラムダ式を使用してこれらのデリゲートのインスタンスをインライン コード ブロックとして作成しています。  ここでは、Func および Action について簡単に紹介し、タスク並列ライブラリと PLINQ のラムダ式を使用する方法について説明します。  
  
 **メモ** 一般的なデリゲートの詳細については、「[デリゲート](../Topic/Delegates%20\(C%23%20Programming%20Guide\).md)」および「[Delegates](../Topic/Delegates%20\(Visual%20Basic\).md)」を参照してください。  C\# および [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] におけるラムダ式の詳細については、「[ラムダ式](../Topic/Lambda%20Expressions%20\(C%23%20Programming%20Guide\).md)」および「[Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)」を参照してください。  
  
## Func デリゲート  
 `Func` デリゲートは、値を返すメソッドをカプセル化します。  Func シグネチャでは、常に最後または右端の型パラメーターで戻り値の型が指定されます。  コンパイラ エラーの一般的な原因の 1 つは、<xref:System.Func%602?displayProperty=fullName> に 2 つの入力パラメーターを渡そうとすることです。実際には、この型が受け取る入力パラメーターは 1 つだけです。  Framework クラス ライブラリでは、<xref:System.Func%601?displayProperty=fullName>、<xref:System.Func%602?displayProperty=fullName>、<xref:System.Func%603?displayProperty=fullName> などから <xref:System.Func%6017?displayProperty=fullName> まで、17 の `Func` のバージョンが定義されています。  
  
## Action デリゲート  
 <xref:System.Action?displayProperty=fullName> デリゲートは、値を返さないメソッド \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の Sub\) または [void](../Topic/void%20\(C%23%20Reference\).md) を返すメソッドをカプセル化します。  Action の型シグネチャでは、型パラメーターは入力パラメーターのみを表します。  Func と同様、Framework クラス ライブラリでは 17 バージョンの Action が定義されています。この中には型パラメーターを持たないものから、16 の型パラメーターを持つものまであります。  
  
## 例  
 <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=fullName> メソッドの次の例は、ラムダ式を使用して Func デリゲートと Action デリゲートの両方を表現する方法を示しています。  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## 参照  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)