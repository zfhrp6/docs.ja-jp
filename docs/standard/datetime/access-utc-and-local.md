---
title: "方法 : 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする | Microsoft Docs"
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
  - "ローカル タイム ゾーンへのアクセス"
  - "定義済みのタイム ゾーン"
  - "タイム ゾーン [.NET Framework], local"
  - "タイム ゾーン [.NET Framework], 取得"
  - "タイム ゾーン [.NET Framework], UTC"
  - "UTC 時刻, 定義済み"
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする
<xref:System.TimeZoneInfo> クラスに用意されている 2 つのプロパティ、<xref:System.TimeZoneInfo.Utc%2A> および <xref:System.TimeZoneInfo.Local%2A> を使用すると、コードから定義済みのタイム ゾーン オブジェクトにアクセスできます。  このトピックでは、これらのプロパティから返される <xref:System.TimeZoneInfo> オブジェクトにアクセスする方法について説明します。  
  
### 世界協定時刻 \(UTC: Coordinated Universal Time\) の TimeZoneInfo オブジェクトにアクセスするには  
  
1.  `static` \(Visual Basic では `Shared`\) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> プロパティを使用して、世界協定時刻にアクセスします。  
  
2.  プロパティから返された <xref:System.TimeZoneInfo> オブジェクトをオブジェクト変数に割り当てることはせず、そのまま <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> プロパティを使用して世界協定時刻にアクセスします。  
  
### ローカル タイム ゾーンにアクセスするには  
  
1.  `static` \(Visual Basic では `Shared`\) <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> プロパティを使用して、ローカル システム タイム ゾーンにアクセスします。  
  
2.  プロパティから返された <xref:System.TimeZoneInfo> オブジェクトをオブジェクト変数に割り当てることはせず、そのまま <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> プロパティを使用してローカル タイム ゾーンにアクセスします。  
  
## 使用例  
 次のコードは、米国およびカナダ東部標準時タイム ゾーンの時刻に変換し、コンソールにタイム ゾーンの名前を表示するために <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> と <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> のプロパティを使用します。  
  
 [!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
 [!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]  
  
 ローカル タイム ゾーンにアクセスする場合は、<xref:System.TimeZoneInfo> オブジェクト変数にローカル タイム ゾーンを割り当てることはせず、必ず <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> プロパティを使用してください。  同様に、世界協定時刻にアクセスする場合は、UTC ゾーンを <xref:System.TimeZoneInfo> オブジェクト変数に割り当てることはせず、必ず <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> プロパティを使用してください。これにより、<xref:System.TimeZoneInfo> オブジェクト変数が <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=fullName> メソッド呼び出しによって無効になるのを防ぐことができます。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Core.dll への参照をプロジェクトに追加する。  
  
-   <xref:System> 名前空間を `using` ステートメントでインポートする \(C\# のコードで必要\)。  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)   
 [方法 : TimeZoneInfo オブジェクトをインスタンス化する](../../../docs/standard/datetime/instantiate-time-zone-info.md)