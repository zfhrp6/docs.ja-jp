---
title: "方法 : あいまいな時刻を解決する | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "あいまいな時刻 [.NET Framework]"
  - "タイム ゾーン [.NET Framework], あいまいな時刻"
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : あいまいな時刻を解決する
あいまいな時刻とは、複数の世界協定時刻 \(UTC: Coordinated Universal Time\) に対応する時刻です。  このようなことは、あるタイム ゾーンで夏時間から標準時間に移行する際など、クロック時刻を元に戻すときに発生します。  あいまいな時刻は、次のいずれかの方法で対処できます。  
  
-   UTC に対する時刻の対応方法を想定します。  たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻を表す、などと想定できます。  
  
-   あいまいな時刻がユーザーによって入力されたデータの項目である場合は、あいまいさの解決をユーザーに任せることができます。  
  
 このトピックでは、タイム ゾーンの標準時刻を表すと想定することであいまいな時刻を解決する方法を示します。  
  
### あいまいな時刻をタイム ゾーンの標準時刻に対応させるには  
  
1.  <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> メソッドを呼び出して、時刻があいまいかどうかを判定します。  
  
2.  時刻があいまいな場合は、タイム ゾーンの <xref:System.TimeZoneInfo.BaseUtcOffset%2A> プロパティによって返される <xref:System.TimeSpan> オブジェクトから時刻を減算します。  
  
3.  `static` \(Visual Basic .NET では `Shared`\) <xref:System.DateTime.SpecifyKind%2A> メソッドを呼び出して、UTC の日時値の <xref:System.DateTime.Kind%2A> プロパティに <xref:System.DateTimeKind?displayProperty=fullName> を設定します。  
  
## 使用例  
 次の例では、あいまいな時刻がローカル タイム ゾーンの標準時刻を表すと想定することで、あいまいな時刻を UTC に変換する方法を示します。  
  
 [!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
 [!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]  
  
 この例は、渡された <xref:System.DateTime> 値があいまいかどうかを判定する `ResolveAmbiguousTime` という名前のメソッドで構成されます。  値があいまいな場合、メソッドは対応する UTC 時刻を表す <xref:System.DateTime> 値を返します。  メソッドは、ローカル タイム ゾーンの <xref:System.TimeZoneInfo.BaseUtcOffset%2A> プロパティの値をローカル時刻から減算することで、この変換を行います。  
  
 通常、あいまいな時刻は、<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> メソッドを呼び出し、あいまいな時刻に対して可能性のある UTC オフセットが格納されている <xref:System.TimeSpan> オブジェクトの配列を取得することで処理します。  しかし、この例では、あいまいな時刻は常にタイム ゾーンの標準時刻に対応する、と断定的に想定しています。  <xref:System.TimeZoneInfo.BaseUtcOffset%2A> プロパティは、UTC とタイム ゾーンの標準時刻の間のオフセットを返します。  
  
 この例では、ローカル タイム ゾーンに対するすべての参照は、<xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> プロパティを通して行います。ローカル タイム ゾーンをオブジェクト変数に割り当てることはしません。  <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=fullName> メソッドを呼び出すと、ローカル タイム ゾーンが割り当てられているオブジェクトは無効になるので、これが推奨される方法です。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Core.dll への参照をプロジェクトに追加する。  
  
-   <xref:System> 名前空間を `using` ステートメントでインポートする \(C\# のコードで必要\)。  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [方法 : ユーザーがあいまいな時刻を解決できるようにする](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)