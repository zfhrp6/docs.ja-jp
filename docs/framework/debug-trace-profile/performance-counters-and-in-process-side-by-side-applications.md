---
title: "Performance Counters and In-Process Side-By-Side Applications | Microsoft Docs"
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
  - "performance counters"
  - "performance counters,and in-process side-by-side applications"
  - "performance,.NET Framework applications"
  - "performance monitoring,counters"
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
caps.latest.revision: 26
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 26
---
# Performance Counters and In-Process Side-By-Side Applications
パフォーマンス モニター \(Perfmon.exe\) を使用すると、ランタイム単位でパフォーマンス カウンターを区別できます。  このトピックでは、この機能を有効にするために必要なレジストリの変更について説明します。  
  
## 既定の動作  
 既定では、パフォーマンス モニターにはアプリケーション単位でパフォーマンス カウンターが表示されます。  ただし、これが問題となる状況が 2 つあります。  
  
-   同じ名前を持つ 2 つのアプリケーションを監視する場合。  たとえば、どちらのアプリケーションも myapp.exe という名前である場合、**\[インスタンス\]** 列には、一方が **myapp** として、もう一方が **myapp\#1** として表示されます。  この場合、パフォーマンス カウンターとアプリケーションの対応関係がわかりにくくなります。  **myapp\#1** について収集されたデータが、最初の myapp.exe のものであるか、2 番目の myapp.exe のものであるかが明確ではありません。  
  
-   1 つのアプリケーションで、共通言語ランタイムの複数のインスタンスが使用される場合。  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、インプロセスでの side\-by\-side ホスティングのシナリオに対応しています。つまり、1 つのプロセスまたはアプリケーションで、共通言語ランタイムの複数のインスタンスを読み込むことができます。  myapp.exe という名前の 1 つのアプリケーションで 2 つのランタイム インスタンスを読み込む場合、既定では、**\[インスタンス\]** 列にそれぞれ **myapp** と **myapp\#1** として表示されます。  この場合、**myapp** と **myapp\#1** は、同じ名前を持つ 2 つのアプリケーションを指しているのか、2 つのランタイムを使用する 1 つのアプリケーションを指しているのか明確ではありません。  同じ名前を持つ複数のアプリケーションで複数のランタイムを読み込む場合は、さらにあいまいになります。  
  
 レジストリ キーを設定すると、このあいまいさを解消することができます。  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] を使用して開発されたアプリケーションの場合、このレジストリの変更を行うと、**\[インスタンス\]** 列のアプリケーション名にプロセス ID とランタイム インスタンス ID が付加されます。  *application* または *application*\#1 の代わりに、アプリケーションが **\[インスタンス\]** 列の *application*の\_\_`p`*processID*の`r`*runtimeID* として表示されます。  アプリケーションが以前のバージョンの共通言語ランタイムを使用して開発している場合は、そのインスタンスが*application\_*`p`*processID* として [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] がインストールされている必要があります。  
  
## インプロセス side\-by\-side アプリケーションのパフォーマンス カウンター  
 1 つのアプリケーションでホストされる複数の共通言語ランタイム バージョンのパフォーマンス カウンターを設定するには、次の表に示すように、1 つのレジストリ キー設定を変更する必要があります。  
  
|||  
|-|-|  
|キー名|HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Services\\.NETFramework\\Performance|  
|値の名前|ProcessNameFormat|  
|値の種類|REG\_DWORD|  
|値|1 \(0x00000001\)|  
  
 `ProcessNameFormat` の値が 0 の場合は、既定の動作が有効であることを示します。つまり、Perfmon.exe には、アプリケーション単位でパフォーマンス カウンターが表示されます。  この値を 1 に設定すると、Perfmon.exe では、複数のバージョンのアプリケーションのあいまいさを解消し、ランタイム単位でパフォーマンス カウンターを用意します。  `ProcessNameFormat` レジストリ キー設定のその他の値は、今後使用するために予約されており、サポートされていません。  
  
 `ProcessNameFormat` レジストリ キー設定を更新したら、インスタンスの名前付け機能を正常に動作させるために、Perfmon.exe またはパフォーマンス カウンターのその他のコンシューマーを再起動する必要があります。  
  
 `ProcessNameFormat` 値をプログラムで変更する方法を次の例に示します。  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 このレジストリの変更を行うと、Perfmon.exe では *application* がアプリケーションの名前です。*application*での `p`*processID*\_\_の`r`*runtimeID*として [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]を、*processID* であるアプリケーションのプロセス ID を対象とし、*runtimeID* が共通言語ランタイムの ID であるアプリケーションの名前が表示されます。  たとえば、myapp.exe という名前の 1 つのアプリケーションで共通言語ランタイムの 2 つのインスタンスを読み込む場合、Perfmon.exe では、一方のインスタンスが myapp\_p1416\_r10 として、もう一方が myapp\_p3160\_r10 として識別されます。  ランタイム ID は、プロセス内のランタイムのあいまいさを解消するだけで、ランタイムに関するその他の情報は提供しません \(たとえば、ランタイム ID はランタイムのバージョンや SKU とは関係がありません\)。  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] がインストールされている場合、このレジストリの変更は、以前のバージョンの .NET Framework を使用して開発されたアプリケーションにも適用されます。  これらは  *application\_*`p`*processID*として、Perfmon.exe で *application* がアプリケーションの名前で、*processID* はプロセス ID の場合に表示されます。  たとえば、myapp.exe という名前の 2 つのアプリケーションのパフォーマンス カウンターを監視する場合は、一方のアプリケーションが myapp\_p23900 として、もう一方が myapp\_p24908 として表示されます。  
  
> [!NOTE]
>  プロセス ID によって、以前のバージョンのランタイムを使用する同じ名前の 2 つのアプリケーションを区別するときのあいまいさが解消されます。  以前のバージョンの共通言語ランタイムは side\-by\-side 実行に対応していないため、ランタイム ID は以前のバージョンには必要ありません。  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] が存在しないかアンインストールされている場合は、このレジストリ キーを設定しても効果はありません。  これは、同じ名前の 2 種類のアプリケーションが *application* と *application\#1* として、Perfmon.exe で表示することを意味します。たとえば、**\[myapp\]** と **\[myapp\#1\]** として\)。