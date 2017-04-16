---
title: "方法 : グレゴリオ暦以外の暦の日付を表示する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "書式指定 [.NET Framework]、日付"
  - "日付 [.NET Framework]、書式設定"
  - "暦 [.NET Framework]、表示 (日付を)"
  - "表示 (日付と時刻のデータを)"
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : グレゴリオ暦以外の暦の日付を表示する
<xref:System.DateTime> 型と <xref:System.DateTimeOffset> 型は、既定の暦としてグレゴリオ暦を使用します。  つまり、日付および時刻の値の `ToString` メソッドを呼び出すと、その日付および時刻が別の暦を使って作成された場合でも、グレゴリオ暦でその日付および時刻を表した文字列表現が表示されます。  この動作を次のコード例に示します。ここでは、2 つの異なる方法でペルシャ暦の日付および時刻の値を作成しますが、<xref:System.DateTime.ToString%2A> メソッドを呼び出すときにはグレゴリオ暦で日付および時刻の値を表示します。  この例の 2 つの技法はよく使用されますが、特定の暦で日付を表示する方法としては適切ではありません。  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 特定の暦で日付を表示するために 2 つの異なる技法を使用できます。  最初の方法では、暦は特定のカルチャの既定の暦である必要があります。  2 番目の方法は、任意の暦で使用できます。  
  
### カルチャの既定の暦で日付を表示するには  
  
1.  使用する暦 \(カレンダー\) を表す、<xref:System.Globalization.Calendar> クラスから派生したカレンダー オブジェクトをインスタンス化します。  
  
2.  日付の表示に使われる書式設定が属するカルチャを表す <xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化します。  
  
3.  <xref:System.Array.Exists%2A?displayProperty=fullName> メソッドを呼び出すことにより、カレンダー オブジェクトが <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=fullName> プロパティによって返される配列のメンバーかどうかを判別します。  これは、そのカレンダー \(暦\) を <xref:System.Globalization.CultureInfo> オブジェクトの既定の暦に指定できることを示します。  配列のメンバーでない場合には、「任意の暦で日付を表示するには」の説明に従ってください。  
  
4.  カレンダー オブジェクトを、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName> プロパティによって返される <xref:System.Globalization.DateTimeFormatInfo> オブジェクトの <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> プロパティに割り当てます。  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo> クラスには、<xref:System.Globalization.CultureInfo.Calendar%2A> プロパティもあります。  ただし、これは読み取り専用の定数であるため、<xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=fullName> プロパティに割り当てられた新しい既定の暦を表すようには変更されません。  
  
5.  <xref:System.DateTime.ToString%2A> メソッドまたは <xref:System.DateTime.ToString%2A> メソッドを呼び出して、前の手順で既定の暦が変更された <xref:System.Globalization.CultureInfo> オブジェクトをそれに渡します。  
  
### 任意の暦で日付を表示するには  
  
1.  使用する暦 \(カレンダー\) を表す、<xref:System.Globalization.Calendar> クラスから派生したカレンダー オブジェクトをインスタンス化します。  
  
2.  日付および時刻の値の文字列表現にどの日付および時刻要素を表示させるかを決定します。  
  
3.  表示させるそれぞれの日付および時刻要素ごとに、カレンダー オブジェクトの `Get`… メソッドを呼び出します。  次のメソッドを使用できます。  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A> は、適切な暦の年を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A> は、適切な暦の月を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A> は、適切な暦の月の日付を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A> は、適切な暦の日付の時間を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A> は、適切な暦の時刻の分を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A> は、適切な暦の時刻の秒を表示します。  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A> は、適切な暦の時刻のミリ秒を表示します。  
  
## 使用例  
 この例では、2 つの異なる暦を使って日付を表示します。  ar\-JO カルチャの既定の暦としてヒジュラ暦を定義した後、日付を表示します。さらに、fa\-IR カルチャのオプションの暦としてサポートされないペルシャ暦を使って日付を表示します。  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 それぞれの <xref:System.Globalization.CultureInfo> オブジェクトは、<xref:System.Globalization.CultureInfo.OptionalCalendars%2A> プロパティによって示される暦を 1 つ以上サポートすることができます。  このうち 1 つがカルチャの既定の暦として指定され、読み取り専用の <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=fullName> プロパティによって返されます。  オプションの暦の 1 つを既定として指定するには、その暦を表す <xref:System.Globalization.Calendar> オブジェクトを、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName> プロパティによって返される <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=fullName> プロパティに割り当てます。  ただし、\(<xref:System.Globalization.PersianCalendar> クラスによって表されるペルシャ暦のような\) いくつかの暦は、どのカルチャのオプションの暦としても機能しません。  
  
 この例では、特定の暦を使って日付の文字列表現を生成する際の多くの詳細な処理を行うために、再利用可能なカレンダー ユーティリティ クラス `CalendarUtility` を定義します。  `CalendarUtility` クラスには、次のメンバーがあります。  
  
-   パラメーター化されたコンストラクター。その単一のパラメーターは、日付を表す際に使用される <xref:System.Globalization.Calendar> オブジェクトです。  クラスのプライベート フィールドにこれが割り当てられます。  
  
-   プライベート メソッド `CalendarExists`。これは、`CalendarUtility` オブジェクトによって表される暦が、パラメーターとしてメソッドに渡される <xref:System.Globalization.CultureInfo> オブジェクトでサポートされるかどうかを示すブール値を返します。  このメソッドは、<xref:System.Array.Exists%2A?displayProperty=fullName> メソッドへの呼び出しをラップし、<xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=fullName> 配列をこのメソッドに渡します。  
  
-   プライベート メソッド `HasSameName`。これは、<xref:System.Array.Exists%2A?displayProperty=fullName> メソッドにパラメーターとして渡される <xref:System.Predicate%601> デリゲートに割り当てられます。  メソッドが `true` を返すまで、配列の各メンバーがメソッドに渡されます。  このメソッドは、オプションの暦の名前が、`CalendarUtility` オブジェクトによって表される暦と同じかどうかを判断します。  
  
-   オーバーロードされたパブリック メソッド `DisplayDate`。これに渡されるパラメーターは、`CalendarUtility` オブジェクトによって表される暦で表示する <xref:System.DateTime> または <xref:System.DateTimeOffset> 値と、使用する書式指定規則が属するカルチャの 2 つです。  日付の文字列表現を返す際の動作は、使用する書式指定規則が属するカルチャにおいて、対象となる暦がサポートされるかどうかに依存します。  
  
 この例の <xref:System.DateTime> または <xref:System.DateTimeOffset> 値を作成するのにどんな暦が使われたかにかかわらず、この値は通常、グレゴリオ暦の日付で表現されます。  これは、暦の情報が <xref:System.DateTime> 型と <xref:System.DateTimeOffset> 型に保持されないためです。  内部的には、これは 0001 年 1 月 1 日の真夜中から数えたタイマー刻みの回数として表されます。  この回数の解釈は、暦によって異なります。  ほとんどのカルチャでは、既定の暦はグレゴリオ暦です。  
  
## コードのコンパイル  
 この例では System.Core.dll を参照する必要があります。  
  
 コマンド ラインで csc.exe または vb.exe を使用してコードをコンパイルします。  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でコードをコンパイルするには、コンソール アプリケーション プロジェクト テンプレートの中にコードを配置します。  
  
## 参照  
 [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)