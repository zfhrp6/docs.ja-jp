---
title: "方法: あいまいな時刻を解決するには"
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
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3706747848dbcd29d4ed2e81d5b7447a127a653
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-resolve-ambiguous-times"></a>方法: あいまいな時刻を解決するには

あいまいな時刻とは、複数の世界協定時刻 (UTC) にマップされる時刻です。 これは、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。 あいまいな時刻を処理する場合は、次のいずれかの操作を行います。

* 時刻が UTC にどのようにマップされるかを想定します。 たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。

* あいまいな時刻が、ユーザーによって入力されたデータ項目である場合は、あいまいさの解決をユーザーに任せることができます。

このトピックでは、タイム ゾーンの標準時を表すと仮定すると、あいまいな時刻を解決する方法を示します。

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>あいまいな時刻をタイム ゾーンの標準時刻にマップするには

1. 呼び出す、<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>時刻があいまいかどうかを調べます。

2. 時刻があいまいな場合は、減算、時刻から、<xref:System.TimeSpan>タイム ゾーンのによって返されるオブジェクト<xref:System.TimeZoneInfo.BaseUtcOffset%2A>プロパティです。

3. 呼び出す、 `static` (`Shared` Visual Basic .NET で)<xref:System.DateTime.SpecifyKind%2A>値を設定する (utc) 日付と時刻のメソッド<xref:System.DateTime.Kind%2A>プロパティを<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>です。

## <a name="example"></a>例

次の例では、ローカル タイム ゾーンの標準時刻を表すと仮定すると、あいまいな時刻を UTC に変換する方法を示します。

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

例では、という名前のメソッドから成る`ResolveAmbiguousTime`を決定するかどうか、<xref:System.DateTime>に渡された値があいまいです。 値があいまいなメソッドを返します、<xref:System.DateTime>を対応する UTC 時刻を表す値です。 このメソッドでは、この変換を処理のローカル タイム ゾーンの値を減算して<xref:System.TimeZoneInfo.BaseUtcOffset%2A>現地時刻からのプロパティです。

あいまいな時刻を呼び出すことによって処理される通常は、<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>の配列を取得する方法を<xref:System.TimeSpan>あいまいな時刻の可能な UTC を格納するオブジェクトをオフセットします。 しかし、この例は、あいまいな時刻は常にタイム ゾーンの標準時刻にマップされるという想定に基づいています。 <xref:System.TimeZoneInfo.BaseUtcOffset%2A>プロパティは、UTC とタイム ゾーンの標準時刻のオフセットを返します。

この例では、ローカル タイム ゾーンへのすべての参照はを通じて行われます、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>プロパティ以外のローカル時刻ゾーンをオブジェクト変数に割り当てることはありません。 これは、ためにの推奨される方法への呼び出し、<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>メソッドには、ローカル タイム ゾーンに割り当てられているすべてのオブジェクトが無効にします。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* される System.Core.dll への参照をプロジェクトに追加します。

* <xref:System>と共に名前空間をインポートする、`using`ステートメント (c# コードで必要です)。

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[する方法: あいまいな時刻を解決することができます](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
