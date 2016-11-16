---
title: "日付、時刻、およびタイム ゾーン"
description: "日付、時刻、およびタイム ゾーン"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 76e6cacc-1c0c-4a71-8cb8-018c112385ba
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: a4d0a68ac32c3d722a1479ca2b067892fd88bf52

---

# <a name="dates-times-and-time-zones"></a>日付、時刻、およびタイム ゾーン

.NET は基本的な [System.DateTime](xref:System.DateTime) 構造体だけでなく、タイム ゾーンでの作業をサポートする次のクラスも提供しています。

* [System.TimeZoneInfo](xref:System.TimeZoneInfo)
    
  システムのローカル タイム ゾーンおよび世界協定時刻 (UTC) ゾーンでの作業を行うには、このクラスを使用します。
  
* [System.DateTimeOffset](xref:System.DateTimeOffset)  

  UTC からのオフセット (つまり時差) がわかっている日付および時刻で作業を行う場合は、この構造体を使用します。 [DateTimeOffset](xref:System.DateTimeOffset) 構造体は、日付および時刻の値と、その時刻の UTC からのオフセットを組み合わせたものです。 UTC との関係により、個々の日付と時刻の値によって具体的な日時が明確に特定されます。 これにより、[DateTime](xref:System.DateTime) の値よりも、[DateTimeOffset](xref:System.DateTimeOffset) の値の方がコンピューター間で移植しやすくなります。 
  
ドキュメントのこのセクションでは、タイム ゾーンでの作業を行ったり、あるタイム ゾーンから別のタイム ゾーンに日付と時刻を変換できる、タイム ゾーンに対応したアプリケーションを作成するために必要な情報を提供します。

## <a name="in-this-section"></a>このセクションの内容

[タイムゾーンの概要](time-zone-overview.md) - タイム ゾーンに対応したアプリケーションの作成に関連する用語、概念、問題について説明します。
    
[DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](choosing-between-datetime.md) - 日付および時刻のデータでの作業を行う場合、どのようなときに [System.DateTime](xref:System.DateTime)、[System.DateTimeOffset](xref:System.DateTimeOffset)、[System.TimeZoneInfo](xref:System.TimeZoneInfo) の型を使用するかについて説明します。
    
[ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md) - ローカル システムで検出されたタイム ゾーンを列挙する方法について説明します。

[DateTimeOffset オブジェクトのインスタンス化](instantiating-a-datetimeoffset-object.md) - [System.DateTimeOffset](xref:System.DateTimeOffset) オブジェクトをインスタンス化する方法、および [System.DateTime](xref:System.DateTime) の値を [System.DateTimeOffset](xref:System.DateTimeOffset) の値に変換する方法について説明します。

[日付と時刻を使用した算術演算の実行](performing-arithmetic-operations.md) - [System.DateTime](xref:System.DateTime) および [System.DateTimeOffset](xref:System.DateTimeOffset) の値の加算、減算、比較に関連する問題について説明します。

[DateTime と DateTimeOffset 間の変換](converting-between-datetime-and-offset.md) - [System.DateTime](xref:System.DateTime) の値と [System.DateTimeOffset](xref:System.DateTimeOffset) の値の変換方法について説明します。

[タイム ゾーン間での時刻の変換](converting-between-time-zones.md) - タイム ゾーン間での時刻の変換方法について説明します。

[方法: コンピューター上に存在するタイム ゾーンを列挙する](enumerate-time-zones.md) - コンピューターのレジストリに定義されているタイム ゾーンを列挙して、ユーザーが一覧から事前定義のタイム ゾーンを選択できるようにするための例を提供します。

[方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](access-utc-and-local.md) - 世界協定時刻とローカル タイム ゾーンにアクセスする方法について説明します。

[方法: TimeZoneInfo オブジェクトをインスタンス化する](instantiate-time-zone-info.md) - ローカル システムのレジストリから [System.TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをインスタンス化する方法について説明します。

[方法: 日付と時刻の演算でタイム ゾーンを使用する](use-time-zones-in-arithmetic.md) - タイム ゾーンの調整規則を反映する日付と時刻の演算を実行する方法について説明します。

[方法: あいまいな時刻を解決する](resolve-ambiguous-times.md) - 時刻をタイム ゾーンの標準時刻に対応させることで、あいまいな時刻を解決する方法について説明します。

[方法: ユーザーがあいまいな時刻を解決できるようにする](let-users-resolve-ambiguous-times.md) - ユーザーがあいまいな現地時刻と世界協定時刻の対応を決定できるようにする方法について説明します。

## <a name="reference"></a>参照

[System.TimeZoneInfo](xref:System.TimeZoneInfo)

[System.DateTimeOffset](xref:System.DateTimeOffset)

[System.DateTime](xref:System.DateTime)



<!--HONumber=Nov16_HO3-->


