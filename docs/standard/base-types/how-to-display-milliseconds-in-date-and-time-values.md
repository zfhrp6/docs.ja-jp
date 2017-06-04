---
title: "方法: 日付および時刻の値のミリ秒部分を表示する | Microsoft Docs"
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
  - "日付 [.NET Framework], ミリ秒"
  - "DateTime.ToString メソッド"
  - "表示 (日付と時刻のデータを)"
  - "ミリ秒 [.NET Framework]"
  - "時刻 [.NET Framework], ミリ秒"
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法: 日付および時刻の値のミリ秒部分を表示する
<xref:System.DateTime.ToString?displayProperty=fullName> などの既定の日付および時刻書式指定メソッドは時刻値の時間、分、秒を含めますが、ミリ秒の部分は含めません。  ここでは、書式設定された日付および時刻文字列の中にミリ秒部分を含める方法について説明します。  
  
### DateTime 値のミリ秒部分を表示するには  
  
1.  日付を表す文字列形式を処理している場合には、静的 <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> または <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=fullName> メソッドを使用して、それを <xref:System.DateTime> 値または <xref:System.DateTimeOffset> 値に変換します。  
  
2.  時刻のミリ秒部分の文字列表現を抽出するには、日付および時刻の値の <xref:System.DateTime.ToString%28System.String%29?displayProperty=fullName> メソッドまたは <xref:System.DateTimeOffset.ToString%2A> メソッドを呼び出して、カスタム書式パターン `fff` または `FFF` を単独で、あるいは他のカスタム書式指定子と共に `format` パラメーターとして渡します。  
  
## 使用例  
 この例では、<xref:System.DateTime> および <xref:System.DateTimeOffset> 値のミリ秒の部分をコンソールに表示します。単独で表示する場合と、より長い日付および時刻文字列に含める場合の両方を示します。  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 `fff` 書式パターンを使うと、ミリ秒値に後続のゼロがあればこれは含められます。  `FFF` 書式パターンでは、これが除外されます。  この違いを次の例に示します。  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 日付および時刻のミリ秒部分を含む完全なカスタム書式指定子を定義する場合、アプリケーションの現在のカルチャの時間要素の取り決めに対応しない可能性のあるハードコーディングされた書式を定義するという問題が生じます。  これに代わるより良い方法は、現在のカルチャの <xref:System.Globalization.DateTimeFormatInfo> オブジェクトで定義されているいずれかの日付および時刻表示パターンを取得して、ミリ秒を含むようにそれを修正することです。  この例では、この方法も示されています。  現在のカルチャの完全な日付および時刻パターンを <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=fullName> プロパティから取得した後、その秒パターンの後にカスタム パターン `.ffff` を挿入します。  この例では、1 つのメソッド呼び出しでこの操作を実行するために正規表現が使われていることに注意してください。  
  
 また、カスタム書式指定子を使用して、ミリ秒以外の秒の端数を表示することもできます。  たとえば、カスタム書式指定子 `f` または `F` は 1\/10 秒を表示し、カスタム書式指定子 `ff` または `FF` は 1\/100 秒、カスタム書式指定子 `ffff` または `FFFF` は 1\/10000 秒をそれぞれ表示します。  返される文字列内では、ミリ秒の端数は丸められるのではなく、切り捨てられます。  次の例では、これらの書式指定子が使用されています。  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  1\/10000 秒、1\/100000 秒などの非常に小さな端数単位を表示することが可能です。  ただし、このような値を表示してもあまり意味がない可能性があります。  日付および時刻の値の精度は、システム クロックの分解能に依存します。  Windows NT 3.5 以降および [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] オペレーティング システムでは、クロックの分解能は約 10 ～ 15 ミリ秒です。  
  
## コードのコンパイル  
 コマンド ラインで csc.exe または vb.exe を使用してコードをコンパイルします。  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でコードをコンパイルするには、コンソール アプリケーション プロジェクト テンプレートの中にコードを配置します。  
  
## 参照  
 <xref:System.Globalization.DateTimeFormatInfo>   
 [カスタム日時書式指定文字列](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)