---
title: "loaderLock MDA | Microsoft Docs"
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
  - "deadlocks [.NET Framework]"
  - "LoaderLock MDA"
  - "MDAs (managed debugging assistants), loader locks"
  - "managed debugging assistants (MDAs), loader locks"
  - "operating system loader locks"
  - "loader locks"
  - "locks, threads"
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# loaderLock MDA
`loaderLock` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、Microsoft Windows オペレーティング システムのローダー ロックを保持するスレッドでマネージ コードを実行しようとする試みを検出します。このような実行は不正であり、デッドロックの発生につながり、DLL がオペレーティング システムのローダーによって初期化される前に使用される可能性があります。  
  
## 症状  
 オペレーティング システムのローダー ロック内でコードを実行したときの最も一般的なエラーは、ローダー ロックを必要とする他の Win32 関数の呼び出しを試行したときにスレッドがデッドロックするというエラーです。このような関数には、`LoadLibrary`、`GetProcAddress`、`FreeLibrary`、`GetModuleHandle` などがあります。これらの関数はアプリケーションが直接呼び出すのではなく、<xref:System.Reflection.Assembly.Load%2A> のような高水準の呼び出しや、プラットフォーム呼び出しメソッドの最初の呼び出しの結果として、共通言語ランタイム \(CLR: Common Language Runtime\) によって呼び出されます。  
  
 デッドロックは、スレッドが別のスレッドが開始または終了するのに待機している場合にも発生することがあります。スレッドが実行を開始または終了したときは、オペレーティング システムのローダー ロックを取得して、影響を受ける DLL にイベントを配信する必要があります。  
  
 さらに、オペレーティング システムのローダーによって DLL が適切に初期化される前に、その DLL への呼び出しが発生することもあります。デッドロック エラーは、デッドロックに関連するすべてのスレッドのスタックをチェックすることにより診断できますが、初期化されていない DLL が使用されていないかどうかの診断は、この MDA を使用しないと非常に困難です。  
  
## 原因  
 .NET Framework Version 1.0 または 1.1 用に構築された、マネージとアンマネージの混合 C\+\+ アセンブリは、**\/NOENTRY** とのリンクなど、特別に注意していない場合には、通常、ローダー ロック内でマネージ コードを実行しようとします。このような問題の詳細については、MSDN ライブラリの「Mixed DLL Loading Problem」を参照してください。  
  
 .NET Framework Version 2.0 用に構築されたマネージとアンマネージの混合 C\+\+ アセンブリの場合は、このような問題が発生する可能性が低く、オペレーティング システムの規則に違反するアンマネージ DLL を使用するアプリケーションと同様にリスクが低減されています。たとえば、アンマネージ DLL の `DllMain` エントリ ポイントで、`CoCreateInstance` を呼び出して COM に公開されているマネージ オブジェクトを取得しようとすると、ローダー ロック内でマネージ コードの実行が試みられます。  .NET Framework Version 2.0 以降のローダー ロックに関する問題の詳細については、「[混在アセンブリの初期化](../Topic/Initialization%20of%20Mixed%20Assemblies.md)」を参照してください。  
  
## 解決策  
 Visual C\+\+ .NET 2002 および Visual C\+\+ .NET 2003 では、`/clr` コンパイラ オプションを指定してコンパイルされた DLL は、読み込み時に非確定的にデッドロックを生じる可能性があります。この問題は、混在モード DLL 読み込み時の問題 \(またはローダー ロックの問題\) と呼ばれていました。  Visual C\+\+ 2005 以降では、混在モード DLL の読み込みプロセスで、確定的でない場合にこのような問題が発生することがほとんどなくなりました。  ただし、ローダー ロックが \(確定的に\) 発生する可能性のあるシナリオはいくつか残っています。  残っているローダー ロックの問題の原因と解決方法の詳細については、「[混在アセンブリの初期化](../Topic/Initialization%20of%20Mixed%20Assemblies.md)」を参照してください。  このトピックに記載されていないローダー ロックの問題については、スレッドのスタックをチェックして、ローダー ロックが発生している原因と問題の解決方法を確認する必要があります。  スタック トレースをチェックして、この MDA をアクティブにしたスレッドを見つけます。このスレッドは、オペレーティング システムのローダー ロックを保持しながら、マネージ コードへの不正な呼び出しを試みています。DLL の `DllMain` または同等のエントリ ポイントがスタックで確認される可能性があります。このようなエントリ ポイントの内部から正当に実行できる操作は、オペレーティング システムの規則によって非常に制限されています。これらの規則では、すべてのマネージ実行が不可能になっています。  
  
## ランタイムへの影響  
 通常、プロセス内部のいくつかのスレッドがデッドロックします。これらのスレッドには、ガベージ コレクションを実行するスレッドが含まれている可能性があるため、このデッドロックによってプロセス全体が重大な影響を受けることがあります。さらに、アセンブリや DLL の読み込みとアンロード、スレッドの開始と終了など、オペレーティング システムのローダー ロックが必要な追加の操作ができなくなります。  
  
 また、場合によっては、初期化される前に呼び出された DLL でアクセス違反などの問題が発生することもまれにあります。  
  
## 出力  
 この MDA は、不正なマネージ実行が試みられていることを報告します。スレッドのスタックをチェックして、ローダー ロックが発生している原因と問題の解決方法を確認する必要があります。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)