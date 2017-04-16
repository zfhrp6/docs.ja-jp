---
title: "日付、時刻、およびタイム ゾーン | Microsoft Docs"
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
  - "日付と時刻のデータ [.NET Framework]"
  - "時刻 [.NET Framework], タイム ゾーン"
  - "タイム ゾーン オブジェクト [.NET Framework]"
  - "タイム ゾーン [.NET Framework]"
  - "時刻 [.NET Framework], タイム ゾーン"
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# 日付、時刻、およびタイム ゾーン
基本的な <xref:System.DateTime> 構造体に加えて、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] にはタイム ゾーンを扱う次のようなクラスも用意されています。  
  
-   <xref:System.TimeZone>  
  
     システムのローカル タイム ゾーンと世界協定時刻 \(UTC: Coordinated Universal Time\) タイム ゾーンを扱うには、このクラスを使用します。<xref:System.TimeZone> クラスのほとんどの機能は、<xref:System.TimeZoneInfo> クラスに引き継がれています。  
  
-   <xref:System.TimeZoneInfo>  
  
     このクラスを使用すると、システムに事前に定義されている任意のタイム ゾーンを処理し、新しいタイム ゾーンを作成して、1 つのタイム ゾーンから別のタイム ゾーンに日付\/時刻を簡単に変換できます。  新たに開発する場合は、<xref:System.TimeZone> クラスではなく <xref:System.TimeZoneInfo> クラスを使用してください。  
  
-   <xref:System.DateTimeOffset>  
  
     この構造体を使用すると、UTC とのオフセット \(つまり時差\) がわかっている日付\/時刻を処理できます。  <xref:System.DateTimeOffset> 構造体は、日付\/時刻値、およびその時刻と UTC とのオフセットを組み合わせます。  UTC との相対関係が示されるため、個々の日付\/時刻値は 1 つの特定の日時を明確に表すことになります。  このため、<xref:System.DateTimeOffset> 値は <xref:System.DateTime> 値に比べて、コンピューター間での移植性に優れています。  
  
 ここでは、タイム ゾーンを処理するために必要な情報、および 1 つのタイム ゾーンから別のタイム ゾーンに日付\/時刻を変換するタイム ゾーン対応アプリケーションを作成するために必要な情報について説明します。  
  
## このセクションの内容  
 [タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)  
 タイム ゾーン対応アプリケーションの作成に関連した用語、概念、および問題について説明します。  
  
 [DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](../../../docs/standard/datetime/choosing-between-datetime.md)  
 日付\/時刻データを扱う際、どのような場合に <xref:System.DateTime>、<xref:System.DateTimeOffset>、および <xref:System.TimeZoneInfo> の各型を使用できるかについて説明します。  
  
 [ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)  
 ローカル システム上で検出されるタイム ゾーンを列挙する方法について説明します。  
  
 [方法 : コンピューター上に存在するタイム ゾーンを列挙する](../../../docs/standard/datetime/enumerate-time-zones.md)  
 コンピューターのレジストリに定義されているタイム ゾーンを列挙し、1 つの定義済みタイム ゾーンをユーザーがリストから選択できるようにする例を示します。  
  
 [方法 : 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](../../../docs/standard/datetime/access-utc-and-local.md)  
 世界協定時刻とローカル タイム ゾーンにアクセスする方法について説明します。  
  
 [方法 : TimeZoneInfo オブジェクトをインスタンス化する](../../../docs/standard/datetime/instantiate-time-zone-info.md)  
 ローカル システムのレジストリから <xref:System.TimeZoneInfo> オブジェクトをインスタンス化する方法について説明します。  
  
 [DateTimeOffset オブジェクトのインスタンス化](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md)  
 <xref:System.DateTimeOffset> オブジェクトをインスタンス化する方法、および <xref:System.DateTime> 値を <xref:System.DateTimeOffset> 値に変換する方法について説明します。  
  
 [方法 : 調整規則のないタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)  
 夏時間の調整をサポートしないカスタム タイム ゾーンを作成する方法について説明します。  
  
 [方法 : 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)  
 1 つ以上の夏時間調整をサポートするカスタム タイム ゾーンを作成する方法について説明します。  
  
 [タイム ゾーンの保存と復元](../../../docs/standard/datetime/saving-and-restoring-time-zones.md)  
 タイム ゾーン データのシリアル化と逆シリアル化が <xref:System.TimeZoneInfo> でどのようにサポートされるかを説明し、これらの機能を使用できるいくつかのシナリオを示します。  
  
 [方法 : 埋め込みリソースにタイム ゾーンを保存する](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)  
 カスタム タイム ゾーンを作成し、その情報をリソース ファイルに保存する方法について説明します。  
  
 [方法 : 埋め込みリソースからタイム ゾーンを復元する](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)  
 埋め込みリソース ファイルに保存されているカスタム タイム ゾーンをインスタンス化する方法について説明します。  
  
 [日付と時刻を使用した算術演算の実行](../../../docs/standard/datetime/performing-arithmetic-operations.md)  
 <xref:System.DateTime> 値と <xref:System.DateTimeOffset> 値の加算、減算、および比較に関連した問題について説明します。  
  
 [方法 : 日付と時刻の演算でタイム ゾーンを使用する](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)  
 タイム ゾーンの調整規則を考慮して日付と時刻の演算を実行する方法について説明します。  
  
 [DateTime と DateTimeOffset 間の変換](../../../docs/standard/datetime/converting-between-datetime-and-offset.md)  
 <xref:System.DateTime> 値と <xref:System.DateTimeOffset> 値を相互に変換する方法について説明します。  
  
 [タイム ゾーン間での時刻の変換](../../../docs/standard/datetime/converting-between-time-zones.md)  
 1 つのタイム ゾーンから別のタイム ゾーンに時刻を変換する方法について説明します。  
  
 [方法 : あいまいな時刻を解決する](../../../docs/standard/datetime/resolve-ambiguous-times.md)  
 あいまいな時刻をタイム ゾーンの標準時刻に対応付けることによって解決する方法を示します。  
  
 [方法 : ユーザーがあいまいな時刻を解決できるようにする](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)  
 あいまいなローカル時刻と世界協定時刻との対応付けをユーザーが決定できるようにする方法を示します。  
  
## 関連項目  
 <xref:System.TimeZoneInfo?displayProperty=fullName>