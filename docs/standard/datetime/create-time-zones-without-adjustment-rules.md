---
title: '方法: 調整規則のないタイム ゾーンを作成'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 214e3bca811f87f4b8367b459564449d16e7c289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572903"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>方法: 調整規則のないタイム ゾーンを作成

アプリケーションで必要とされる正確なタイム ゾーン情報は、いくつかの原因の特定のシステムに存在していない可能性があります。

* タイム ゾーンはローカル システムのレジストリで定義されていません。

* タイム ゾーンに関するデータが変更されたか、レジストリから削除されました。

* タイム ゾーンが存在しますが、過去の特定の期間のタイム ゾーンの調整に関する正確な情報はありません。

このような場合を呼び出すことができます、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドをアプリケーションに必要なタイム ゾーンを定義します。 このメソッドのオーバー ロードを使用して、調整規則の有無は、タイム ゾーンを作成することができます。 タイム ゾーンが夏時間をサポートする場合は、いずれかの固定または浮動小数点の調整ルールの調整を定義できます。 (これらの用語の定義、「タイム ゾーンの用語」のセクションを参照してください。[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md))。

> [!IMPORTANT]
> 呼び出して作成されたカスタムのタイム ゾーン、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドは、レジストリに追加されません。 代わりに、によって返されるオブジェクトの参照を介してのみアクセスすることができます、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドの呼び出しです。

このトピックでは、調整規則のないタイム ゾーンを作成する方法を示します。 夏時間の調整規則をサポートするタイム ゾーンを作成するを参照してください。[する方法: 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)です。

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>調整規則のないタイム ゾーンを作成するには

1. タイム ゾーンの表示名を定義します。

   表示名に依存して標準形式にタイム ゾーンのオフセット世界協定時刻 (UTC) からかっこで囲まれて、その後に、1 つまたは複数のタイム ゾーン、または 1 つの都市以上、cou のタイム ゾーンを識別する文字列ntries またはタイム ゾーン内の領域。

2. タイム ゾーンの標準時の名前を定義します。 通常、この文字列は、タイム ゾーンの識別子としても使用します。

3. タイム ゾーンの標準の名前とは異なる id を使用する場合は、タイム ゾーン id を定義します。

4. インスタンスを作成、 <xref:System.TimeSpan> UTC からのタイム ゾーンのオフセットを定義するオブジェクト。 タイム ゾーンの時刻 (utc) より後に、正の値のオフセットを持っています。 タイム ゾーンの時刻は UTC よりも前に、負のオフセットを持っています。

5. 呼び出す、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>新しいタイム ゾーンをインスタンス化するメソッド。

## <a name="example"></a>例

次の例では、調整規則がない、南極のモーソンをカスタム タイム ゾーンを定義します。

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

割り当てられた文字列、<xref:System.TimeZoneInfo.DisplayName%2A>プロパティ (utc) からのタイム ゾーンのオフセットがタイム ゾーンのわかりやすい説明によってその後に、標準形式に依存します。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* される System.Core.dll への参照をプロジェクトに追加します。

* 次の名前空間は、インポートします。

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
[する方法: 調整規則のあるタイム ゾーンを作成します。](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
