---
title: "方法: TimeZoneInfo オブジェクトをインスタンス化"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: defc8c9981b8476660c9c99d20bc50142ee9dfad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>方法: TimeZoneInfo オブジェクトをインスタンス化

<xref:System.TimeZoneInfo> オブジェクトをインスタンス化する最も一般的な方法は、レジストリからオブジェクトに関する情報を取得することです。 このトピックでは、ローカル システムのレジストリから <xref:System.TimeZoneInfo> オブジェクトをインスタンス化する方法について説明します。

### <a name="to-instantiate-a-timezoneinfo-object"></a>TimeZoneInfo オブジェクトをインスタンス化するには

1. <xref:System.TimeZoneInfo> オブジェクトを宣言します。

2. 呼び出す、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType>メソッドです。

3. メソッドによってスローされる例外 (特に、タイム ゾーンがレジストリで定義されていない場合にスローされる <xref:System.TimeZoneNotFoundException> ) を処理します。

## <a name="example"></a>例

次のコードでは、東部標準時のタイム ゾーンを表す <xref:System.TimeZoneInfo> オブジェクトを取得し、現地時刻に対応する東部標準時の時刻を表示します。

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType>メソッドの 1 つのパラメーターは、タイム ゾーンの id を取得するオブジェクトの対応する<xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType>プロパティです。 タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。 ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。 ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される <xref:System.TimeZoneInfo.StandardName%2A> オブジェクトの <xref:System.TimeZoneInfo> プロパティに対応します。 ただし、例外もあります。 有効な識別子を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、対応するタイム ゾーン識別子を記録しておくことです。 この具体例については、「 [How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md)」を参照してください。 [Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) トピックにも、選択したタイム ゾーン識別子の一覧があります。

タイム ゾーンが見つかると、メソッドは <xref:System.TimeZoneInfo> オブジェクトを返します。 タイム ゾーンが見つからない場合、メソッドから <xref:System.TimeZoneNotFoundException>がスローされます。 タイム ゾーンが見つかっても、そのデータが破損しているか不完全な場合には、メソッドから <xref:System.InvalidTimeZoneException>がスローされます。

アプリケーションが依存するタイム ゾーンが必ず存在していなければならない場合は、最初に <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドを呼び出して、レジストリからタイム ゾーンの情報を取得する必要があります。 メソッドの呼び出しが失敗した場合は、例外ハンドラーで、タイム ゾーンの新しいインスタンスを作成するか、シリアル化された <xref:System.TimeZoneInfo> オブジェクトを逆シリアル化してインスタンスを作成し直す必要があります。 参照してください[する方法: 埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)例についてはします。

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[する方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトにアクセス](../../../docs/standard/datetime/access-utc-and-local.md)
