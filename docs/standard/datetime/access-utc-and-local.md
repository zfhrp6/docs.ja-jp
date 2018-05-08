---
title: '方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトにアクセス'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7ddf7ba69d8bed84f62d329fd26794e2641d954
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトにアクセス

<xref:System.TimeZoneInfo>クラスには、2 つのプロパティが用意されています<xref:System.TimeZoneInfo.Utc%2A>と<xref:System.TimeZoneInfo.Local%2A>、定義済みのタイム ゾーン オブジェクトをコードのアクセス権を付与します。 このトピックでは、これらのプロパティから返される <xref:System.TimeZoneInfo> オブジェクトにアクセスする方法について説明します。

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>世界協定時刻 (UTC) の TimeZoneInfo オブジェクトにアクセスするには

1. 使用して、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>協定世界時にアクセスするプロパティです。

2. 割り当てるのではなく、<xref:System.TimeZoneInfo>オブジェクト変数に、プロパティによって返されるオブジェクトに引き続きアクセスを介して世界協定時刻、<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>プロパティです。

### <a name="to-access-the-local-time-zone"></a>ローカル タイム ゾーンにアクセスするには

1. 使用して、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>ローカル システムのタイム ゾーンにアクセスするプロパティです。

2. 割り当てるのではなく、<xref:System.TimeZoneInfo>オブジェクト変数に、プロパティによって返されるオブジェクトに引き続きアクセスを通じて、ローカル タイム ゾーン、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>プロパティです。

## <a name="example"></a>例

次のコードでは、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>と<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>プロパティから米国およびカナダ東部標準時ゾーンの時刻の変換をできるだけでなく、タイム ゾーンの名前をコンソールに表示します。

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

を介して、ローカル タイム ゾーンを常にアクセスする必要があります、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>にゾーンのローカル時刻を割り当てるのではなく、プロパティ、<xref:System.TimeZoneInfo>オブジェクト変数です。 同様に、アクセスすることは常に世界協定時刻で、<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>にゾーンの UTC を割り当てるのではなく、プロパティ、<xref:System.TimeZoneInfo>オブジェクト変数です。 これにより、<xref:System.TimeZoneInfo>オブジェクト変数への呼び出しによって無効にされてから、<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>メソッドです。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* される System.Core.dll への参照をプロジェクトに追加します。

* <xref:System>と共に名前空間をインポートする、`using`ステートメント (c# コードで必要です)。

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[する方法: TimeZoneInfo オブジェクトをインスタンス化](../../../docs/standard/datetime/instantiate-time-zone-info.md)
