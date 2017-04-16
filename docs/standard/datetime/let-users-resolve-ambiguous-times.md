---
title: "方法 : ユーザーがあいまいな時刻を解決できるようにする | Microsoft Docs"
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
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : ユーザーがあいまいな時刻を解決できるようにする
あいまいな時刻とは、複数の世界協定時刻 \(UTC: Coordinated Universal Time\) に対応する時刻です。  このようなことは、あるタイム ゾーンで夏時間から標準時間に移行する際など、クロック時刻を元に戻すときに発生します。  あいまいな時刻は、次のいずれかの方法で対処できます。  
  
-   あいまいな時刻がユーザーによって入力されたデータの項目である場合は、あいまいさの解決をユーザーに任せることができます。  
  
-   UTC に対する時刻の対応方法を想定します。  たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻を表す、などと想定できます。  
  
 このトピックでは、あいまいな時刻をユーザーに解決させる方法について説明します。  
  
### あいまいな時刻をユーザーに解決させるには  
  
1.  ユーザーが入力した日付と時刻を取得します。  
  
2.  <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> メソッドを呼び出して、時刻があいまいかどうかを判定します。  
  
3.  時刻があいまいな場合は、<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> メソッドを呼び出して、<xref:System.TimeSpan> オブジェクトの配列を取得します。  配列の各要素には、あいまいな時刻に対応する可能性のある UTC オフセットが格納されています。  
  
4.  適切なオフセットを選択するようにユーザーに促します。  
  
5.  ユーザーが選択したオフセットを現地時刻から減算して、UTC の日付と時刻を取得します。  
  
6.  `static` \(Visual Basic .NET では `Shared`\) <xref:System.DateTime.SpecifyKind%2A> メソッドを呼び出して、UTC の日時の値の <xref:System.DateTime.Kind%2A> プロパティに <xref:System.DateTimeKind?displayProperty=fullName> を設定します。  
  
## 使用例  
 次の例では、日付と時刻の入力をユーザーに要求し、入力された値があいまいな場合は、あいまいな時刻に対応する UTC 時刻をユーザーが選択できるようにします。  
  
 [!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
 [!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]  
  
 この例の中核となるコードでは、<xref:System.TimeSpan> オブジェクトの配列を使用して、UTC からのあいまいな時刻のオフセットとして可能性のある値を示しています。  しかし、これらのオフセットはユーザーにとっては意味がないものと考えられます。  オフセットの意味を明確にするため、コードでは、オフセットがローカル タイム ゾーンの標準時刻を表すのか、または夏時間を表すのかも示します。  時刻が標準時刻なのか夏時間なのかを判定するには、オフセットを <xref:System.TimeZoneInfo.BaseUtcOffset%2A> プロパティの値と比較します。  このプロパティは、UTC とタイム ゾーンの標準時刻の間の差を示します。  
  
 この例では、ローカル タイム ゾーンに対するすべての参照は、<xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> プロパティを通して行います。ローカル タイム ゾーンをオブジェクト変数に割り当てることはしません。  <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=fullName> メソッドを呼び出すと、ローカル タイム ゾーンが割り当てられているオブジェクトは無効になるので、これが推奨される方法です。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Core.dll への参照をプロジェクトに追加する。  
  
-   <xref:System> 名前空間を `using` ステートメントでインポートする \(C\# のコードで必要\)。  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [方法 : あいまいな時刻を解決する](../../../docs/standard/datetime/resolve-ambiguous-times.md)