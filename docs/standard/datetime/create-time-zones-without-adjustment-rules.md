---
title: "方法 : 調整規則のないタイム ゾーンを作成する | Microsoft Docs"
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
  - "調整規則 [.NET Framework]"
  - "タイム ゾーン [.NET Framework], 調整規則"
  - "タイム ゾーン [.NET Framework], 作成"
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 調整規則のないタイム ゾーンを作成する
アプリケーションで必要な正確なタイム ゾーン情報が、次のような理由で特定のシステムに存在しない場合があります。  
  
-   ローカル システムのレジストリでタイム ゾーンが定義されていない。  
  
-   タイム ゾーンに関するデータがレジストリで変更または削除されている。  
  
-   タイム ゾーンは存在するが、過去の特定の期間のタイム ゾーン調整に関する正確な情報がない。  
  
 このような場合は、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出して、アプリケーションで必要なタイム ゾーンを定義できます。  このメソッドのオーバーロードを使用すると、調整規則のあるタイム ゾーンまたは調整規則のないタイム ゾーンを作成できます。  タイム ゾーンが夏時間をサポートする場合は、固定調整規則または浮動調整規則の調整を定義できます。これらの用語の定義については、「[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)」の「タイム ゾーンの用語」の節を参照してください。  
  
> [!IMPORTANT]
>  <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出すことで作成されるカスタム タイム ゾーンは、レジストリには追加されません。  カスタム タイム ゾーンには、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドの呼び出しによって返されるオブジェクト参照を通してのみアクセスできます。  
  
 このトピックでは、調整規則のないタイム ゾーンを作成する方法について説明します。  夏時間調整規則をサポートするタイム ゾーンを作成する方法については、「[方法 : 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)」を参照してください。  
  
### 調整規則のないタイム ゾーンを作成するには  
  
1.  タイム ゾーンの表示名を指定します。  
  
     表示名は、世界協定時刻 \(UTC: Coordinated Universal Time\) からのタイム ゾーンのオフセットをかっこで囲み、その後にタイム ゾーン、タイム ゾーン内の 1 つ以上の都市、またはタイム ゾーン内の 1 つ以上の国や地域を表す文字列が続く標準形式に従います。  
  
2.  タイム ゾーンの標準時間の名前を指定します。  通常は、この文字列がタイム ゾーンの ID としても使用されます。  
  
3.  タイム ゾーンの標準名とは異なる ID を使用する場合は、タイム ゾーン ID を指定します。  
  
4.  UTC からのタイム ゾーンのオフセットを定義する <xref:System.TimeSpan> オブジェクトをインスタンス化します。  UTC より後の時刻のタイム ゾーンでは正のオフセットになります。  UTC より前の時刻のタイム ゾーンでは負のオフセットになります。  
  
5.  <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=fullName> メソッドを呼び出して、新しいタイム ゾーンをインスタンス化します。  
  
## 使用例  
 次の例では、南極のモーソンの、調整規則のないカスタム タイム ゾーンを定義します。  
  
 [!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
 [!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]  
  
 <xref:System.TimeZoneInfo.DisplayName%2A> プロパティに割り当てる文字列は、UTC からのタイム ゾーンのオフセットの後に、タイム ゾーンのわかりやすい説明を続ける標準形式に従います。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Core.dll への参照をプロジェクトに追加する。  
  
-   次の名前空間をインポートする。  
  
     [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
     [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)   
 [方法 : 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)