---
title: "How Culture Affects Strings in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "locale, effect on strings"
  - "strings [Visual Basic], locale dependence"
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How Culture Affects Strings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このヘルプ ページでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で文字列の変換と比較を実行するときに、カルチャ情報がどのように使用されるかについて説明します。  
  
## カルチャ固有文字列を使用する状況  
 通常は、ユーザーとやり取りするデータにはカルチャ固有文字列を使用し、アプリケーションの内部データにはカルチャ不変文字列を使用します。  
  
 たとえば、日付を文字列として入力するようユーザーに要求する場合、アプリケーションは、ユーザーが自分のカルチャに従った形式で文字列を入力するだろうということを予測し、その文字列を適切に変換する必要があります。  さらに、その日付をユーザー インターフェイス上に表示するときには、ユーザーのカルチャに従った形式で表示する必要があります。  
  
 しかし、その日付を中央のサーバーにアップロードする場合には、日付形式の相違による混乱を防ぐために、その文字列を特定のカルチャに従った形式にする必要があります。  
  
## カルチャに依存する関数  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のすべての文字列変換関数 \(`Str` 関数と `Val` 関数を除く\) は、アプリケーションのカルチャ情報に基づいて、アプリケーション ユーザーのカルチャに適した変換および比較を行います。  
  
 さまざまなカルチャ設定がされたコンピューター上で実行されるアプリケーションを開発するときに、そのアプリケーション内で文字列変換関数を正しく使用するための鍵は、どの関数が特定のカルチャ設定を使用して、どの関数が現在のカルチャ設定を使用するかを理解することです。  アプリケーションのカルチャ設定は、既定ではオペレーティング システムのカルチャ設定を継承するという点に注意してください。  詳細については、「<xref:Microsoft.VisualBasic.Strings.Asc%2A>」、「<xref:Microsoft.VisualBasic.Strings.AscW%2A>」、「<xref:Microsoft.VisualBasic.Strings.Chr%2A>」、「<xref:Microsoft.VisualBasic.Strings.ChrW%2A>」、「<xref:Microsoft.VisualBasic.Strings.Format%2A>」、「<xref:Microsoft.VisualBasic.Conversion.Hex%2A>」、「<xref:Microsoft.VisualBasic.Conversion.Oct%2A>」、および「[Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)」を参照してください。  
  
 `Str` 関数 \(数値を文字列に変換\) と `Val` 関数 \(文字列を数値に変換\) は、文字列と数値の間で変換を行うときにアプリケーションのカルチャ情報を使用しません。  代わりに、ピリオド \(.\) だけを有効な桁区切り記号として認識します。  これらの関数と同様の処理を行うカルチャ対応関数には次のものがあります。  
  
-   **現在のカルチャを使用する変換。** `CStr` 関数と `Format` 関数は数値を文字列に変換し、`CDbl` 関数と `CInt` 関数は文字列を数値に変換します。  
  
-   **特定のカルチャを使用する変換。**それぞれの数値オブジェクトには、数値を文字列に変換する `ToString(IFormatProvider)` メソッドと、文字列を数値に変換する `Parse(String, IFormatProvider)` メソッドがあります。  たとえば `Double` 型には <xref:System.Double.ToString%28System.IFormatProvider%29> メソッドと <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> メソッドがあります。  
  
 詳細については、「<xref:Microsoft.VisualBasic.Conversion.Str%2A>」および「<xref:Microsoft.VisualBasic.Conversion.Val%2A>」を参照してください。  
  
## 特定のカルチャの使用  
 たとえば、日付を文字列形式にして Web サービスに送信するアプリケーションを開発しているとします。  このアプリケーションでは、文字列変換の際に特定のカルチャを使用する必要があります。  この理由を説明するために、日付の <xref:System.DateTime.ToString> メソッドを使用した場合の結果を考えてみましょう。このメソッドを使用して 20005 年 7 月 4 日という日付を変換した場合、United States English \(en\-US\) のカルチャで実行すると "7\/4\/2005 12:00:00 AM" という結果になりますが、German \(de\-DE\) のカルチャで実行すると "04.07.2005 00:00:00" という結果になります。  
  
 特定のカルチャの形式で文字列変換を実行する必要があるときは、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] に組み込まれている `CultureInfo` クラスを使用します。  特定のカルチャに関する `CultureInfo` オブジェクトを新規作成するには、<xref:System.Globalization.CultureInfo.%23ctor%2A> コンストラクターにカルチャの名前を渡します。  サポートされるカルチャの名前については、<xref:System.Globalization.CultureInfo> クラスのページを参照してください。  
  
 別の方法として、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> プロパティから*インバリアント カルチャ*のインスタンスを取得することもできます。  インバリアント カルチャは English カルチャに基づいていますが、いくつかの相違点があります。  たとえば、インバリアント カルチャでは、12 時間制ではなく 24 時間制が指定されます。  
  
 日付を特定カルチャの文字列に変換するには、その日付オブジェクトの <xref:System.DateTime.ToString%28System.IFormatProvider%29> メソッドに <xref:System.Globalization.CultureInfo> オブジェクトを渡します。  たとえば次のコードでは、日付はアプリケーションのカルチャ設定に関係なく常に "07\/04\/2005 00:00:00" と表示されます。  
  
 [!code-vb[VbVbalrConcepts#1](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/visualbasic/how-culture-affects-stri_1.vb)]  
  
> [!NOTE]
>  日付リテラルは常に English カルチャに従って解釈されます。  
  
## 文字列の比較  
 文字列の比較が必要な状況としては、主に次の 2 つがあります。  
  
-   **ユーザーに表示するデータを並べ替える。**現在のカルチャに基づく演算を行い、文字列が適切に並べ替えられるようにします。  
  
-   **アプリケーション内部の 2 つの文字列が完全に一致するかどうかを確認する \(通常はセキュリティ目的で使用\)。**現在のカルチャを無視した演算を行います。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の <xref:Microsoft.VisualBasic.Strings.StrComp%2A> 関数では、両方の種類の比較を実行できます。  比較の種類は、オプションの引数 `Compare` を指定することによって制御できます。通常の入出力では `Text` を使用し、厳密な比較が要求される場合は `Binary` を使用します。  
  
 `StrComp` 関数は、2 つの文字列を並べ替え順序に基づいて比較した結果を表す整数を返します。  結果が正の場合は、1 番目の文字列の方が 2 番目の文字列より大きいことになります。  結果が負の場合は 1 番目の文字列の方が小さく、0 の場合は 2 つの文字列が等しいことになります。  
  
 [!code-vb[VbVbalrStrings#22](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/how-culture-affects-stri_2.vb)]  
  
 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] に用意されている、`StrComp` 関数と同様の機能を持つ <xref:System.String.Compare%2A?displayProperty=fullName> メソッドを使用することもできます。  このメソッドは、基本文字列クラスのオーバーロードされた静的メソッドです。  次のコードは、このメソッドの使用例です。  
  
 [!code-vb[VbVbalrStrings#48](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/how-culture-affects-stri_3.vb)]  
  
 比較の実行方法をより細かく制御するには、<xref:System.String.Compare%2A> メソッドのオーバーロードを使用します。  <xref:System.String.Compare%2A?displayProperty=fullName> メソッドでは、`comparisonType` 引数を使用して比較の種類を指定できます。  
  
||||  
|-|-|-|  
|`comparisonType` 引数の値|比較の種類|使用する状況|  
|`Ordinal`|文字列のコンポーネント バイトに基づいて比較します。|大文字と小文字を区別する識別子、セキュリティ関連の設定、またはバイトが正確に一致する必要があるその他の非言語的識別子を比較するときに使用します。|  
|`OrdinalIgnoreCase`|文字列のコンポーネント バイトに基づいて比較します。<br /><br /> `OrdinalIgnoreCase` では、2 つの文字の大文字と小文字だけが違っているときに、インバリアント カルチャ情報を使用して比較結果を判断します。|大文字と小文字を区別する識別子、セキュリティ関連の設定、および Windows に格納されているデータを比較するときに使用します。|  
|`CurrentCulture` または `CurrentCultureIgnoreCase`|現在のカルチャでの文字列の解釈に基づいて比較します。|ユーザーに表示するデータ、ほとんどのユーザー入力、および言語的解釈を必要とするその他のデータを比較するときに使用します。|  
|`InvariantCulture` または `InvariantCultureIgnoreCase`|インバリアント カルチャでの文字列の解釈に基づいて比較します。<br /><br /> これは `Ordinal` や `OrdinalIgnoreCase` とは異なります。インバリアント カルチャは、自身の許容範囲外の文字を等価のインバリアント文字として扱うからです。|永続データを比較するときや、固定の並べ替え順序を必要とする言語関連のデータを表示するときにのみ使用します。|  
  
### セキュリティの考慮事項  
 比較処理または大文字\/小文字変換処理の結果に基づいてアプリケーションのセキュリティ関連の決定を下す場合は、その処理を <xref:System.String.Compare%2A?displayProperty=fullName> メソッドで実行し、`comparisonType` 引数に `Ordinal` または `OrdinalIgnoreCase` を渡してください。  
  
## 参照  
 <xref:System.Globalization.CultureInfo>   
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)