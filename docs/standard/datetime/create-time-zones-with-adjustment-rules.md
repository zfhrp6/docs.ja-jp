---
title: '方法: 調整規則のあるタイム ゾーンを作成します。'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c63b93e0dc587571605edb305979b8f97bf54cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>方法: 調整規則のあるタイム ゾーンを作成します。

アプリケーションで必要とされる正確なタイム ゾーン情報は、いくつかの原因の特定のシステムに存在していない可能性があります。

* タイム ゾーンはローカル システムのレジストリで定義されていません。

* タイム ゾーンに関するデータが変更されたか、レジストリから削除されました。

* タイム ゾーンには、過去の特定の期間のタイム ゾーンの調整に関する正確な情報はありません。

このような場合を呼び出すことができます、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドをアプリケーションに必要なタイム ゾーンを定義します。 このメソッドのオーバー ロードを使用して、調整規則の有無は、タイム ゾーンを作成することができます。 タイム ゾーンが夏時間をサポートする場合は、いずれかの固定または浮動小数点の調整ルールの調整を定義できます。 (これらの用語の定義、「タイム ゾーンの用語」のセクションを参照してください。[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md))。

> [!IMPORTANT]
> 呼び出して作成されたカスタムのタイム ゾーン、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドは、レジストリに追加されません。 代わりに、によって返されるオブジェクトの参照を介してのみアクセスすることができます、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドの呼び出しです。

このトピックでは、調整規則のあるタイム ゾーンを作成する方法を示します。 夏時間の調整規則をサポートしていないタイム ゾーンを作成するを参照してください。[する方法: 調整規則なしのタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)です。

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>浮動調整規則のあるタイム ゾーンを作成するには

1. 調整 (つまりからの切り替えの各移行につきと標準時に一定の特定の期間) ごとに、次の操作を行います。

    1. タイム ゾーンの調整の切り替えの開始時刻を定義します。

       呼び出す必要があります、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>メソッドに渡すと、 <xref:System.DateTime> 、遷移、遷移の月を定義する整数値、遷移が発生する曜日を定義する整数値の時刻を定義する値と<xref:System.DayOfWeek>遷移が発生する曜日を定義する値。 このメソッドの呼び出しをインスタンス化、<xref:System.TimeZoneInfo.TransitionTime>オブジェクト。

    2. タイム ゾーンの調整の切り替えの終了時刻を定義します。 別の呼び出しが必要です、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>メソッドです。 このメソッドの呼び出し、2 番目のインスタンスを作成<xref:System.TimeZoneInfo.TransitionTime>オブジェクト。

    3. 呼び出す、<xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A>メソッドの有効な開始と、調整の終了日を渡すことと、<xref:System.TimeSpan>で、切り替え効果、および 2 つの時間を定義するオブジェクト<xref:System.TimeZoneInfo.TransitionTime>タイミングを定義するオブジェクト夏時間との間の遷移時間が発生します。 このメソッドの呼び出しをインスタンス化、<xref:System.TimeZoneInfo.AdjustmentRule>オブジェクト。

    4. 割り当てる、<xref:System.TimeZoneInfo.AdjustmentRule>オブジェクトの配列を<xref:System.TimeZoneInfo.AdjustmentRule>オブジェクト。

2. タイム ゾーンの表示名を定義します。 表示名に依存して標準形式にタイム ゾーンのオフセット世界協定時刻 (UTC) からかっこで囲まれて、その後に、1 つまたは複数のタイム ゾーン、または 1 つの都市以上、cou のタイム ゾーンを識別する文字列ntries またはタイム ゾーン内の領域。

3. タイム ゾーンの標準時の名前を定義します。 通常、この文字列は、タイム ゾーンの識別子としても使用します。

4. タイム ゾーンの夏時間の名前を定義します。

5. タイム ゾーンの標準の名前とは異なる id を使用する場合は、タイム ゾーン id を定義します。

6. インスタンスを作成、 <xref:System.TimeSpan> UTC からのタイム ゾーンのオフセットを定義するオブジェクト。 タイム ゾーンの時刻 (utc) より後に、正の値のオフセットを持っています。 タイム ゾーンの時刻は UTC よりも前に、負のオフセットを持っています。

7. 呼び出す、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>新しいタイム ゾーンをインスタンス化するメソッド。

## <a name="example"></a>例

次の例では、さまざまな 1918年から現在までの時間間隔の調整規則を含む、United states 中部標準時ゾーンを定義します。

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

この例で作成したタイム ゾーンには、複数の調整規則があります。 有効な開始と調整規則の終了日と重複しない別の調整規則の日付を確認する注意する必要があります。 オーバー ラップがある場合、<xref:System.InvalidTimeZoneException>がスローされます。

調整規則を浮動小数点型、値 5 に渡されます、`week`のパラメーター、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>メソッドを特定の月の最後の週に、遷移が発生することを示します。

配列を作成で<xref:System.TimeZoneInfo.AdjustmentRule>で使用するオブジェクト、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>メソッドを呼び出すコードは、初期化、調整の数とタイム ゾーンの作成に必要なサイズの配列。 代わりに、このコード例では、<xref:System.Collections.Generic.List%601.Add%2A>汎用各調整規則を追加するメソッドを<xref:System.Collections.Generic.List%601>のコレクション<xref:System.TimeZoneInfo.AdjustmentRule>オブジェクト。 コードを呼び出すし、<xref:System.Collections.Generic.List%601.CopyTo%2A>にこのコレクションのメンバーを配列にコピーする方法です。

また、例では、<xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A>固定日付の調整を定義します。 これは、呼び出しに似ています、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>メソッドを除いてことは、時間、月、および遷移パラメーターの 1 日のみが必要です。

例は、次のようなコードを使用してテストできます。

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* される System.Core.dll への参照をプロジェクトに追加します。

* 次の名前空間は、インポートします。

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
[する方法: 調整規則のないタイム ゾーンを作成](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
