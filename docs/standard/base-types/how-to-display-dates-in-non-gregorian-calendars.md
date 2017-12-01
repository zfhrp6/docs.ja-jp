---
title: "方法 : グレゴリオ暦以外の暦の日付を表示する"
ms.custom: 
ms.date: 03/30/2017
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
- formatting [.NET Framework], dates
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a79860091e549dcf4eaa7090947f9506eceb6119
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>方法 : グレゴリオ暦以外の暦の日付を表示する
<xref:System.DateTime>と<xref:System.DateTimeOffset>型が、既定の暦として構成のグレゴリオ暦カレンダーを使用します。 つまり、日付と時刻値の `ToString` メソッドを呼び出すと、その日付の時刻が別の暦を使用して作成された場合でも、その日付の時刻はグレゴリオ暦の文字列形式で表示されます。 これとペルシャ暦、日付と時刻の値を作成する 2 つの方法を使用しますが、表示されたままそれらの日付と時刻の値はグレゴリオ暦の呼び出したときに次の例に示す、<xref:System.DateTime.ToString%2A>メソッドです。 この例では、一般的に使われているものの、特定の暦で日付を表示するには正しくない 2 つの手法が反映されています。  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 2 つの手法は、特定の暦で日付を表示するために使用できます。 1 番目の手法では、暦は特定のカルチャの既定の暦である必要があります。 2 番目の手法は、任意の暦で使用できます。  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>カルチャの既定の暦の日付を表示するには  
  
1.  派生した予定表オブジェクトをインスタンス化、<xref:System.Globalization.Calendar>を使用するカレンダーを表すクラス。  
  
2.  インスタンスを作成、<xref:System.Globalization.CultureInfo>日付の表示に使用される書式のカルチャを表すオブジェクト。  
  
3.  呼び出す、<xref:System.Array.Exists%2A?displayProperty=nameWithType>カレンダー オブジェクトによって返される配列のメンバーであるかどうかを決定するメソッド、<xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>プロパティです。 これは、予定表がの既定の暦として使用できることを示します、<xref:System.Globalization.CultureInfo>オブジェクト。 配列のメンバーでない場合は、「任意の暦で日付を表示するには」セクションの手順に従います。  
  
4.  予定表オブジェクトを割り当てます、<xref:System.Globalization.DateTimeFormatInfo.Calendar%2A>のプロパティ、<xref:System.Globalization.DateTimeFormatInfo>によって返されるオブジェクト、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>プロパティです。  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo>クラスもあります、<xref:System.Globalization.CultureInfo.Calendar%2A>プロパティです。 ただし、これは読み取り専用であり定数です。割り当てられている新しい既定の暦を反映するためには変更されません、<xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType>プロパティです。  
  
5.  いずれかを呼び出す、<xref:System.DateTime.ToString%2A>または<xref:System.DateTime.ToString%2A>メソッドを渡すと、<xref:System.Globalization.CultureInfo>が既定の暦が前の手順で変更されたオブジェクト。  
  
### <a name="to-display-the-date-in-any-calendar"></a>任意の暦で日付を表示するには  
  
1.  派生した予定表オブジェクトをインスタンス化、<xref:System.Globalization.Calendar>を使用するカレンダーを表すクラス。  
  
2.  日付と時刻の値の文字列形式で表示する日付と時刻の要素を決定します。  
  
3.  日付と時刻を要素ごとに表示する、呼び出し、カレンダー オブジェクトの`Get`しています. メソッドをオーバーライドします。 次のメソッドが使用できます。  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>、適切なカレンダーにおける年を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>、適切なカレンダーにおける月を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>、適切なカレンダーにおける月の日の数を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>、適切な予定表に、1 日の時間を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>、適切なカレンダーで 1 時間、分を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>、適切なカレンダーの分に、秒を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A>、適切なカレンダーで 2 番目の秒部分の 1/1000 を表示します。  
  
## <a name="example"></a>例  
 この例では、2 つの異なる暦を使用して日付を表示します。 ar-JO カルチャの既定の暦としてイスラム暦を定義した後の日付を表示し、その日付を fa-IR カルチャでオプションの暦としてサポートされていないペルシャ暦を使用して表示します。  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 各<xref:System.Globalization.CultureInfo>オブジェクトによって示される 1 つまたは複数のカレンダーをサポートできる、<xref:System.Globalization.CultureInfo.OptionalCalendars%2A>プロパティです。 これらのいずれかのカルチャの既定の暦として指定されており、読み取り専用によって返される<xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType>プロパティです。 オプションの暦のもう 1 つとして指定できるの既定値を割り当てることによって、<xref:System.Globalization.Calendar>にするには、そのカレンダーを表すオブジェクト、<xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType>プロパティから返される、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>プロパティです。 ただし、いくつかカレンダー、によって表されるペルシャ暦など、<xref:System.Globalization.PersianCalendar>クラス、任意のカルチャのオプションの暦としては提供しません。  
  
 例では、特定の暦を使用して日付の文字列形式を生成する詳細の多くを処理するため、再利用可能な暦ユーティリティ クラス `CalendarUtility` を定義しています。 `CalendarUtility` クラスには次のメンバーがあります。  
  
-   パラメーター化されたコンス トラクターは、1 つのパラメーターを持つ、<xref:System.Globalization.Calendar>日付が表すオブジェクト。 これは、クラスのプライベート フィールドに割り当てられます。  
  
-   `CalendarExists`、予定表がによって表されるかどうかを示すブール値を返すプライベート メソッド、`CalendarUtility`によってオブジェクトがサポートされている、<xref:System.Globalization.CultureInfo>をパラメーターとしてメソッドに渡されるオブジェクト。 メソッドへの呼び出しをラップする、<xref:System.Array.Exists%2A?displayProperty=nameWithType>を渡して、メソッド、<xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>配列。  
  
-   `HasSameName`、プライベート メソッドに割り当てられている、<xref:System.Predicate%601>へのパラメーターとして渡されたデリゲート、<xref:System.Array.Exists%2A?displayProperty=nameWithType>メソッドです。 メソッドが `true` を返すまで、配列の各メンバーがメソッドに渡されます。 このメソッドは、オプションの暦の名前が `CalendarUtility` オブジェクトによって表される暦と同じかどうかを判断します。  
  
-   `DisplayDate`、2 つのパラメーターに渡されるオーバー ロードされたパブリック メソッド: いずれか、<xref:System.DateTime>または<xref:System.DateTimeOffset>によって表されるカレンダーで明示するための値、`CalendarUtility`オブジェクト、および使用するルールを持つ書式のカルチャ。 日付の文字列表現を返す際の動作は、ターゲットの暦が、使用される書式指定規則のカルチャでサポートされているかどうかによって異なります。  
  
 作成するために使用するカレンダーに関係なく、<xref:System.DateTime>または<xref:System.DateTimeOffset>値が通常、グレゴリオ暦の日付として表されること、この例の値。 これは、ため、<xref:System.DateTime>と<xref:System.DateTimeOffset>型は、予定表の情報を保持しません。 これらは内部的に 0001 年 1 月 1 日の午前 0 時から経過したタイマー刻みの数として表されます。 その数の解釈は、暦に依存します。 ほとんどのカルチャでは、既定の暦はグレゴリオ暦です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、System.Core.dll への参照が必要です。  
  
 コマンド ラインで csc.exe または vb.exe を使用してコードをコンパイルします。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でコードをコンパイルするには、コンソール アプリケーション プロジェクト テンプレートの中にコードを配置します。  
  
## <a name="see-also"></a>関連項目  
 [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)
