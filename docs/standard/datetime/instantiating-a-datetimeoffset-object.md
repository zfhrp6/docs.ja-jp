---
title: DateTimeOffset オブジェクトのインスタンス化
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a48ea87bb5eb1e302ae6a1169c22ea30bd4bc7ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="instantiating-a-datetimeoffset-object"></a>DateTimeOffset オブジェクトのインスタンス化

<xref:System.DateTimeOffset>構造体は、さまざまな新しいを作成する方法を提供しています<xref:System.DateTimeOffset>値。 新規のインスタンス化に使用可能なメソッドに直接対応してそれらの多く<xref:System.DateTime>値、日付と時刻の値には世界協定時刻 (UTC) からのオフセットを指定するための機能強化。 具体的には、インスタンスを作成できる、<xref:System.DateTimeOffset>次の方法で値。

* 日付と時刻のリテラルを使用します。

* 呼び出して、<xref:System.DateTimeOffset>コンス トラクターです。

* 値を暗黙的に変換して<xref:System.DateTimeOffset>値。

* 日付と時刻の文字列形式を解析する。

このトピックでは大きい詳細とコードを新しいのインスタンス化のこれらの方法を示す<xref:System.DateTimeOffset>値。

## <a name="date-and-time-literals"></a>日付と時刻のリテラル

サポートされている、インスタンスを作成する最も一般的な方法のいずれかの言語、<xref:System.DateTime>値が日付と時刻をハード コーディングされたリテラル値としてを提供することです。 たとえば、次の Visual Basic コードを作成、<xref:System.DateTime>オブジェクトの値がある 2008 年 1 月 1 日午前 10時 00分です。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> サポートする言語を使用する場合は、日付と時刻のリテラルを使用して値を初期化することも<xref:System.DateTime>リテラルです。 たとえば、次の Visual Basic コードを作成、<xref:System.DateTimeOffset>オブジェクト。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

コンソール出力に示す、<xref:System.DateTimeOffset>この方法で作成された値には、ローカル タイム ゾーンのオフセットが割り当てられます。 つまり、<xref:System.DateTimeOffset>別のコンピューターに、コードが実行される場合に、リテラル文字を使用して割り当てられた値が 1 つの特定の時点を識別できません。

## <a name="datetimeoffset-constructors"></a>DateTimeOffset コンス トラクター

<xref:System.DateTimeOffset>型は、6 つのコンス トラクターを定義します。 直接対応しているうちの 4 つ<xref:System.DateTime>コンス トラクターには、追加のパラメーター型の<xref:System.TimeSpan>日付を定義して、UTC からの時刻のオフセットします。 これらを定義できます、<xref:System.DateTimeOffset>個別の日付と時刻要素の値に基づいて値。 次のコードがインスタンス化するこれら 4 つのコンス トラクターを使用するなど、 <xref:System.DateTimeOffset> 7/1/2008 のと同じ値を持つオブジェクト 12時 05分 AM +01: 00 です。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

なお、ときの値、<xref:System.DateTimeOffset>を使用してインスタンス化されるオブジェクト、<xref:System.Globalization.PersianCalendar>オブジェクトとして、コンス トラクターへの引数のいずれかがコンソールに表示されたら、ペルシャ暦ではなく、グレゴリオ暦の日付として表されます。 ペルシャ暦を使用して日付を出力の例を参照してください。、<xref:System.Globalization.PersianCalendar>トピックです。

他の 2 つのコンス トラクターを作成、<xref:System.DateTimeOffset>オブジェクトから、<xref:System.DateTime>値。 最初のデータセットが 1 つのパラメーター、<xref:System.DateTime>に変換する値、<xref:System.DateTimeOffset>値。 結果のオフセット<xref:System.DateTimeOffset>値によって異なります、<xref:System.DateTime.Kind%2A>コンス トラクターの 1 つのパラメーターのプロパティです。 値が場合<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>、オフセットに設定して<xref:System.TimeSpan.Zero?displayProperty=nameWithType>です。 それ以外の場合、オフセットはローカル タイム ゾーンのオフセットと等しい値に設定されます。 次の例は、インスタンスを作成するこのコンス トラクターの使用を示しています。 <xref:System.DateTimeOffset> UTC とローカル タイム ゾーンを表すオブジェクト。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> オーバー ロードを呼び出して、<xref:System.DateTimeOffset>を 1 つを持つコンス トラクター<xref:System.DateTime>パラメーターの暗黙の変換を実行するのには、<xref:System.DateTime>値を<xref:System.DateTimeOffset>値。

作成する 2 番目のコンス トラクター、<xref:System.DateTimeOffset>オブジェクトから、<xref:System.DateTime>値が 2 つのパラメーター:<xref:System.DateTime>変換対象の値と<xref:System.TimeSpan>UTC から日付と時刻を表す値のオフセットします。 このオフセット値に対応する必要があります、<xref:System.DateTime.Kind%2A>コンス トラクターの最初のパラメーターのプロパティまたは<xref:System.ArgumentException>がスローされます。 場合、<xref:System.DateTime.Kind%2A>最初のパラメーターのプロパティが<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>、2 番目のパラメーターの値である必要があります<xref:System.TimeSpan.Zero?displayProperty=nameWithType>です。 場合、<xref:System.DateTime.Kind%2A>最初のパラメーターのプロパティが<xref:System.DateTimeKind.Local?displayProperty=nameWithType>、2 番目のパラメーターの値は、ローカル システムのタイム ゾーンのオフセットである必要があります。 場合、<xref:System.DateTime.Kind%2A>最初のパラメーターのプロパティが<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>オフセットが有効な値を指定できます。 次のコードはこのコンス トラクターを呼び出して変換を<xref:System.DateTime>に<xref:System.DateTimeOffset>値。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>暗黙の型変換

<xref:System.DateTimeOffset>型は、1 つの暗黙的な型変換をサポートしています: から、<xref:System.DateTime>値を<xref:System.DateTimeOffset>値。 (暗黙的な型変換とは、明示的なキャスト (C# の場合) または変換 (Visual Basic の場合) を必要とせず、情報を失わない 1 つの型から別の型への変換です)。 これにより、次のようなコードが可能となります。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

結果のオフセット<xref:System.DateTimeOffset>値によって異なります、<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティの値。 値が場合<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>、オフセットに設定して<xref:System.TimeSpan.Zero?displayProperty=nameWithType>です。 いずれかの値が場合<xref:System.DateTimeKind.Local?displayProperty=nameWithType>または<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>、ローカル タイム ゾーンのオフセットを設定します。

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>日付と時刻の文字列形式を解析します。

<xref:System.DateTimeOffset>の種類をサポートするために日時、日付の文字列形式に変換できる 4 つのメソッド、<xref:System.DateTimeOffset>値。

* <xref:System.DateTimeOffset.Parse%2A>、に日時、日付の文字列形式に変換しようとする、<xref:System.DateTimeOffset>値し、変換が失敗した場合、例外をスローします。

* <xref:System.DateTimeOffset.TryParse%2A>、に日時、日付の文字列形式に変換しようとする、<xref:System.DateTimeOffset>値を返す`false`場合は、変換は失敗します。

* <xref:System.DateTimeOffset.ParseExact%2A>、日付と時刻を指定した形式の文字列形式に変換しようとする、<xref:System.DateTimeOffset>値。 変換が失敗すると、メソッドは例外をスローします。

* <xref:System.DateTimeOffset.TryParseExact%2A>、日付と時刻を指定した形式の文字列形式に変換しようとする、<xref:System.DateTimeOffset>値。 変換が失敗すると、メソッドは `false` を返します。

次の例では、インスタンスを作成するこれらの 4 つの文字列変換メソッドを呼び出し、<xref:System.DateTimeOffset>値。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
