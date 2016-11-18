---
title: "ローカル システムで定義されているタイム ゾーンの検索"
description: "ローカル システムで定義されているタイム ゾーンの検索"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3a6ee323-f3cf-486d-aa0c-103931f1eba9
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: e7f07a1f86ca31a24e25d98de2f8918ff098db24

---

# <a name="finding-the-time-zones-defined-on-a-local-system"></a>ローカル システムで定義されているタイム ゾーンの検索

[System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスは、パブリック コンストラクターを公開しません。 そのため、`new` キーワードを使用して新しい [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを作成することはできません。 [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをインスタンス化するには、代わりに、定義済みのタイム ゾーンの情報をオペレーティング システムから取得します。 このトピックでは、オペレーティング システムによって格納されているデータからタイム ゾーンをインスタンス化する方法について説明します。 また、[TimeZoneInfo](xref:System.TimeZoneInfo) クラスの `static` (Visual Basic では `Shared`) プロパティを使用すると、世界協定時刻 (UTC: Coordinated Universal Time) およびローカル タイム ゾーンにアクセスできます。

## <a name="accessing-individual-time-zones"></a>個別のタイム ゾーンへのアクセス

[TimeZoneInfo](xref:System.TimeZoneInfo) クラスには、UTC 時刻とローカル タイム ゾーンを表す 2 つの定義済みタイム ゾーン オブジェクトがあります。 これらは、それぞれ [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) プロパティと [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティから取得できます。 UTC またはローカル タイム ゾーンにアクセスする方法については、「[方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](access-utc-and-local.md)」を参照してください。 

また、オペレーティング システムで定義されているタイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをインスタンス化することもできます。 特定のタイム ゾーン オブジェクトをインスタンス化する方法については、「[方法: TimeZoneInfo オブジェクトをインスタンス化する](instantiate-time-zone-info.md)」を参照してください。

## <a name="time-zone-identifiers"></a>タイム ゾーン ID

タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。 ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。 ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName) プロパティに対応します。 ただし、例外もあります。 有効な ID を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、それに対応するタイム ゾーン ID を記録することです。 タイム ゾーンを列挙する方法については、「[方法: コンピューター上に存在するタイム ゾーンを列挙する](enumerate-time-zones.md)」を参照してください。

## <a name="see-also"></a>関連項目

[日付、時刻およびタイム ゾーン](index.md)

[方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](access-utc-and-local.md)

[方法: TimeZoneInfo オブジェクトをインスタンス化する](instantiate-time-zone-info.md)

[方法: コンピューター上に存在するタイム ゾーンを列挙する](enumerate-time-zones.md)

[タイム ゾーン間での時刻の変換](converting-between-time-zones.md)


<!--HONumber=Nov16_HO3-->


