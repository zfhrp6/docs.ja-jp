---
title: "ローカル システムで定義されているタイム ゾーンの検索"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e61f05741c1edd86d9baad4f6ebc9f4e91318250
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>ローカル システムで定義されているタイム ゾーンの検索

<xref:System.TimeZoneInfo> クラスは、パブリック コンストラクターを公開しません。 そのため、`new` キーワードを使用して新しい <xref:System.TimeZoneInfo> オブジェクトを作成することはできません。 <xref:System.TimeZoneInfo> オブジェクトをインスタンス化するには、代わりに、定義済みのタイム ゾーンの情報をレジストリから取得するか、カスタム タイム ゾーンを作成します。 このトピックでは、レジストリに格納されているデータからタイム ゾーンをインスタンス化する方法について説明します。 また、<xref:System.TimeZoneInfo> クラスの `static` (Visual Basic では `shared`) プロパティを使用すると、世界協定時刻 (UTC: Coordinated Universal Time) およびローカル タイム ゾーンにアクセスできます。

> [!NOTE]
> レジストリで定義されていないタイム ゾーンの場合は、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドのオーバーロードを呼び出すことによりカスタム タイム ゾーンを作成できます。 については、カスタム タイム ゾーンを作成する、[する方法: 調整規則のないタイム ゾーンを作成](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)と[する方法: 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)トピックです。 さらに、<xref:System.TimeZoneInfo.FromSerializedString%2A> メソッドを使用して、シリアル化された文字列から復元することにより、<xref:System.TimeZoneInfo> オブジェクトをインスタンス化することもできます。 シリアル化と逆シリアル化、<xref:System.TimeZoneInfo>オブジェクトは、後ほど、[する方法: 埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)と[する方法: 埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)トピックです。

## <a name="accessing-individual-time-zones"></a>個別のタイム ゾーンへのアクセス

<xref:System.TimeZoneInfo> クラスには、UTC 時刻とローカル タイム ゾーンを表す 2 つの定義済みタイム ゾーン オブジェクトがあります。 これらは、それぞれ <xref:System.TimeZoneInfo.Utc%2A> プロパティと <xref:System.TimeZoneInfo.Local%2A> プロパティから取得できます。 UTC またはローカル タイム ゾーンへのアクセス方法の詳細については、次を参照してください。[する方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトをアクセス](../../../docs/standard/datetime/access-utc-and-local.md)です。

また、レジストリで定義されているタイム ゾーンを表す <xref:System.TimeZoneInfo> オブジェクトをインスタンス化することもできます。 特定のタイム ゾーン オブジェクトをインスタンス化する方法の詳細については、次を参照してください。[する方法: TimeZoneInfo オブジェクトをインスタンス化](../../../docs/standard/datetime/instantiate-time-zone-info.md)です。

## <a name="time-zone-identifiers"></a>タイム ゾーン id

タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。 ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。 ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> プロパティに対応します。 ただし、例外もあります。 有効な ID を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、それに対応するタイム ゾーン ID を記録することです。

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[する方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトをアクセス](../../../docs/standard/datetime/access-utc-and-local.md)
[する方法: TimeZoneInfo オブジェクトをインスタンス化](../../../docs/standard/datetime/instantiate-time-zone-info.md)
[タイム ゾーン間で時刻の変換](../../../docs/standard/datetime/converting-between-time-zones.md)
