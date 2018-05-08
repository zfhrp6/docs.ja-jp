---
title: '方法: あいまいな時刻を解決することができます'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4083871dd97a36529351aacbdcd39980bdde74a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>方法: あいまいな時刻を解決することができます

あいまいな時刻とは、複数の世界協定時刻 (UTC) にマップされる時刻です。 これは、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。 あいまいな時刻を処理する場合は、次のいずれかの操作を行います。

* あいまいな時刻が、ユーザーによって入力されたデータの項目の場合は、あいまいさの解決をユーザーに任せることができます。

* 時刻が UTC にどのようにマップされるかを想定します。 たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。

このトピックでは、あいまいな時刻を解決するには、ユーザーを許可する方法を示します。

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>ユーザーにあいまいな時刻を解決させるには

1. ユーザーによって入力された日付と時刻を取得します。

2. 呼び出す、<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>時刻があいまいかどうかを調べます。

3. 時刻があいまいな場合は、呼び出し、<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>の配列を取得する方法を<xref:System.TimeSpan>オブジェクト。 配列内の各要素には、あいまいな時刻にマップできる UTC オフセットが含まれています。

4. ユーザーに目的のオフセットを選択させます。

5. ローカル時刻からユーザーによって選択されたオフセットを減算して、UTC の日時を取得します。

6. 呼び出す、 `static` (`Shared` Visual Basic .NET で)<xref:System.DateTime.SpecifyKind%2A>値を設定する (utc) 日付と時刻のメソッド<xref:System.DateTime.Kind%2A>プロパティを<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>です。

## <a name="example"></a>例

次の例では、ユーザーに日付と時刻を入力するように求め、それがあいまいである場合は、ユーザーにあいまいな時刻をマップする UTC 時刻を選択させています。

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

コード例の中核を成すの配列を使用して<xref:System.TimeSpan>あいまいな時刻 (utc) からの可能なオフセットを示すオブジェクト。 ただし、これらのオフセットは、ユーザーにとって意味がない可能性があります。 オフセットの意味を明確にするには、コードで、オフセットがローカル タイム ゾーンの標準時刻を表すか、または夏時間を表すかに注意します。 コードを決定する時間は標準的などの時間が夏時間の値とオフセットを比較することによって、<xref:System.TimeZoneInfo.BaseUtcOffset%2A>プロパティです。 このプロパティは、UTC とタイム ゾーンの標準時間の差を示します。

この例では、ローカル タイム ゾーンへのすべての参照はを通じて行われます、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>プロパティ以外のローカル時刻ゾーンをオブジェクト変数に割り当てることはありません。 これは、ためにの推奨される方法への呼び出し、<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>メソッドには、ローカル タイム ゾーンに割り当てられているすべてのオブジェクトが無効にします。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* される System.Core.dll への参照をプロジェクトに追加します。

* <xref:System>と共に名前空間をインポートする、`using`ステートメント (c# コードで必要です)。

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[する方法: あいまいな時刻を解決するには](../../../docs/standard/datetime/resolve-ambiguous-times.md)
