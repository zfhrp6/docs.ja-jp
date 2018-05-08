---
title: 保存と復元のタイム ゾーン
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7c9aefa08d837ce93e718ff32a463d95dabcdc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="saving-and-restoring-time-zones"></a>保存と復元のタイム ゾーン

<xref:System.TimeZoneInfo>クラスが定義済みのタイム ゾーン データを取得する、レジストリに依存します。 ただし、レジストリは、動的な構造です。 さらに、レジストリが含まれているタイム ゾーン情報は、現在の年の時刻の調整および変換を処理するには、主に、オペレーティング システムによって使用されます。 これは、正確なタイム ゾーン データに依存するアプリケーションの 2 つの主要な影響があります。

* アプリケーションで必要とされるタイム ゾーンは、レジストリで、定義されていない可能性があります。 または名前が変更されているか、レジストリから削除します。

* レジストリで定義されているタイム ゾーンには、履歴のタイム ゾーンの変換に必要な特定の調整規則の情報が不足している可能性があります。

<xref:System.TimeZoneInfo>クラス (保存) をシリアル化および逆シリアル化のタイム ゾーンのデータを (復元) のサポートにより、これらの制限に対処します。

## <a name="time-zone-serialization-and-deserialization"></a>タイム ゾーンのシリアル化および逆シリアル化

保存とタイム ゾーンのデータをシリアル化およびタイム ゾーンを復元するには、2 つのメソッド呼び出しが含まれます。

* シリアル化することができます、<xref:System.TimeZoneInfo>を呼び出してそのオブジェクトのオブジェクト<xref:System.TimeZoneInfo.ToSerializedString%2A>メソッドです。 メソッドは、パラメーターを受け取らないし、タイム ゾーン情報を含む文字列を返します。

* 逆シリアル化することができます、<xref:System.TimeZoneInfo>オブジェクトには、その文字列を渡すことによってシリアル化された文字列から、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType>メソッドです。

## <a name="serialization-and-deserialization-scenarios"></a>シリアル化および逆シリアル化のシナリオ

保存 (またはシリアル化) する機能、<xref:System.TimeZoneInfo>オブジェクトを文字列と復元 (または逆シリアル化)、後で使用できるユーティリティとの柔軟性の両方が増加、<xref:System.TimeZoneInfo>クラスです。 ここでは、一部のシリアル化および逆シリアル化は最も有用な状況について説明します。

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>シリアル化して、アプリケーションでのタイム ゾーン データを逆シリアル化

必要な場合、文字列からシリアル化されたタイム ゾーンを復元することができます。 レジストリから取得されたタイム ゾーンが特定の日付範囲内での日付を正しく変換できない場合は、アプリケーションでこれを行うことがあります。 Windows XP のレジストリのタイム ゾーン データでは、通常、Windows Vista のレジストリで定義されているタイム ゾーンは約 2 つの調整規則の情報を提供します、単一の調整規則をサポートしています。 これは、過去の時刻の変換が不正確であることを意味します。 シリアル化とタイム ゾーンのデータの逆シリアル化は、この制限を処理できます。

次の例では、カスタム<xref:System.TimeZoneInfo>米国を表すための調整規則がないクラスが定義されています。東部標準時のゾーンは 1883 1917、米国の州の夏時間の導入前にします。 カスタムのタイム ゾーンがグローバル スコープを持つ変数にシリアル化されます。 タイム ゾーンの変換メソッド`ConvertUtcTime`は変換する世界協定世界時 (UTC) の時間に渡されます。 日付と時刻は、1917年またはそれ以前に発生する場合、カスタム東部標準時ゾーンはシリアル化された文字列から復元され、レジストリから取得されたタイム ゾーンが置き換えられます。

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>タイム ゾーンの例外を処理

レジストリは動的な構造であるため、その内容は次偶発的または意図的な変更される可能性があります。 つまり、レジストリで定義されている必要があり、正常に実行するアプリケーションに必要なタイム ゾーンが存在しない可能性があります。 タイム ゾーンのシリアル化および逆シリアル化をサポートせず、その結果を処理するが、ほとんどの選択肢がある<xref:System.TimeZoneNotFoundException>アプリケーションを終了しています。 ただし、タイム ゾーンのシリアル化および逆シリアル化を使用することができますを処理する、予期しない<xref:System.TimeZoneNotFoundException>復元することによって、シリアル化された文字列と、アプリケーションから必要なタイム ゾーンは引き続き実行します。

次の例では、作成し、カスタム中部標準時ゾーンのシリアル化します。 中部標準時ゾーンのレジストリから取得が試行されます。 取得操作では、いずれかがスローされた場合、<xref:System.TimeZoneNotFoundException>または<xref:System.InvalidTimeZoneException>、例外ハンドラーは、タイム ゾーンを逆シリアル化します。

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>シリアル化された文字列を格納して、必要なときにそれを復元します。

前の例では、文字列変数にタイム ゾーン情報を格納し、必要なときにこれを復元します。 ただし、シリアル化されたタイム ゾーン情報自体に格納できる、外部のファイル、リソース ファイルなど、いくつかのストレージ メディアを格納する文字列は、アプリケーション、またはレジストリに埋め込まれます。 (カスタム タイム ゾーンに関する情報をレジストリで、システムのタイム ゾーンのキーとは別に保存するかを注意してください)。

この方法でシリアル化されたタイム ゾーン文字列を格納すると、タイム ゾーンの作成ルーチンも、アプリケーション自体とは別になります。 たとえば、タイム ゾーンの作成ルーチンは実行し、アプリケーションが使用できる履歴タイム ゾーン情報を含むデータ ファイルを作成できます。 データ ファイルを指定できます、アプリケーションと共にインストールして開くことがし、1 つまたは複数のタイム ゾーンの逆シリアル化できます、アプリケーションで必要なときにします。

タイム ゾーンのシリアル化されたデータを保存する埋め込みリソースを使用する例は、次を参照してください。[する方法: 埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)と[する方法: 埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)です。

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
