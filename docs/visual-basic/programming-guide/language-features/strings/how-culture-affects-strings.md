---
title: Visual Basic においてカルチャが文字列に与える影響
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: 41fd612695fbeacbc7b53cb9e5dbf67939e73482
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654740"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Visual Basic においてカルチャが文字列に与える影響
このヘルプ ページは、Visual Basic はカルチャ情報を使用して、文字列の変換との比較を実行する方法について説明します。  
  
## <a name="when-to-use-culture-specific-strings"></a>カルチャ固有の文字列を使用する場合  
 通常に表示されるすべてのデータのカルチャに固有の文字列を使用する必要があります、ユーザーからの読み取りと、アプリケーションの内部データのカルチャに依存しない文字列を使用しています。  
  
 など、ユーザーが日付を文字列として入力を求めるアプリケーション、そのカルチャに従って文字列の書式を設定するユーザーを想定する必要があり、アプリケーションでは、文字列を適切に変換する必要があります。 その後、アプリケーションでは、ユーザー インターフェイスでは、その日付を表示する場合、は、ユーザーのカルチャで表示にする必要があります。  
  
 ただし、アプリケーションは、中央のサーバーに日付をアップロードする場合、は、可能性のある別の日付形式の間での混乱を避けるため、1 つの特定のカルチャに従って文字列を書式設定する必要があります。  
  
## <a name="culture-sensitive-functions"></a>カルチャに依存した関数  
 すべての Visual Basic の文字列変換関数 (を除き、`Str`と`Val`関数)、アプリケーションのカルチャ情報を使用して、変換および比較が、アプリケーションのカルチャに対して適切であるかどうかを確認ユーザー。  
  
 正常に別のカルチャ設定を持つコンピューターで実行されるアプリケーションに文字列変換関数を使用するキーでは、どの機能が特定のカルチャの設定を使用し、現在のカルチャ設定を使用してを理解します。 アプリケーションのカルチャ設定は、既定から継承されるオペレーティング システムのカルチャ設定に注意してください。 詳細については、次を参照してください。 <xref:Microsoft.VisualBasic.Strings.Asc%2A>、 <xref:Microsoft.VisualBasic.Strings.AscW%2A>、 <xref:Microsoft.VisualBasic.Strings.Chr%2A>、 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>、 <xref:Microsoft.VisualBasic.Strings.Format%2A>、 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>、 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>、および[型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)です。  
  
 `Str` (数値を文字列に変換する) と`Val`文字列と数の間で変換するときに (文字列数値からに変換) 関数が、アプリケーションのカルチャ情報を使用しないでください。 代わりに、有効な小数点区切り文字としてピリオド (.) のみを認識できるとします。 これらの関数のカルチャに対応する類似のものは次のとおりです。  
  
-   **現在のカルチャを使用する変換。** `CStr`と`Format`関数は、文字列に数値を変換し、`CDbl`と`CInt`関数では、文字列を数値に変換します。  
  
-   **特定のカルチャを使用する変換。** 各数値のオブジェクトには、 `ToString(IFormatProvider)` 、文字列に数値を変換するメソッドと`Parse(String, IFormatProvider)`文字列を数値に変換するメソッド。 たとえば、`Double`種類では、<xref:System.Double.ToString%28System.IFormatProvider%29>と<xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>メソッドです。  
  
 詳細については、<xref:Microsoft.VisualBasic.Conversion.Str%2A> および <xref:Microsoft.VisualBasic.Conversion.Val%2A> を参照してください。  
  
## <a name="using-a-specific-culture"></a>特定のカルチャを使用します。  
 (String 形式) の日付を Web サービスに送信するアプリケーションを開発していることを想像してください。 この場合、アプリケーションでは、文字列の変換の特定のカルチャを使用する必要があります。 理由を示すためには、日付を使用した結果を検討してください<xref:System.DateTime.ToString>メソッド: 場合は、アプリケーションでは、そのメソッドを使用して、2005 年 7 月 4 日、日付の書式設定を返します"2005 年 7 月 4/12:00:00 AM"米国英語 (EN-US) カルチャの実行とは"。04.07.2005 00時 00分: 00"とドイツ (DE-DE) のカルチャに実行します。  
  
 使用する必要があります、特定のカルチャの形式で文字列の変換を実行する必要がある場合、`CultureInfo`に組み込まれているクラス、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]です。 新規に作成することができます`CultureInfo`する、カルチャの名前を渡すことによって、特定のカルチャのオブジェクト、<xref:System.Globalization.CultureInfo.%23ctor%2A>コンス トラクターです。 サポートされているカルチャの名前にある、<xref:System.Globalization.CultureInfo>クラス ヘルプ ページ。  
  
 インスタンスを取得する代わりに、*インバリアント カルチャ*から、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>プロパティです。 インバリアント カルチャがイギリスのカルチャに基づきますが、違いがあります。 たとえば、インバリアント カルチャでは、12 時間形式ではなく、24 時間制を指定します。  
  
 日付をカルチャの文字列に変換する渡す、<xref:System.Globalization.CultureInfo>日付オブジェクトのオブジェクト<xref:System.DateTime.ToString%28System.IFormatProvider%29>メソッドです。 たとえば、次のコードが表示されます"07/04/2005 00時 00分: 00"アプリケーションのカルチャ設定に関係なく、します。  
  
 [!code-vb[VbVbalrConcepts#1](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/how-culture-affects-strings_1.vb)]  
  
> [!NOTE]
>  日付リテラルは、常に英語のカルチャに従って解釈されます。  
  
## <a name="comparing-strings"></a>文字列の比較  
 文字列の比較が必要な 2 つの重要な状況があります。  
  
-   **ユーザーに表示するデータを並べ替えます。** 現在のカルチャに基づいて文字列が適切に並べ替え操作を使用します。  
  
-   **かどうかアプリケーション内部の 2 つの文字列と正確に一致 (通常はセキュリティの目的で) を決定します。** 現在のカルチャは無視して操作を使用します。  
  
 両方の種類の Visual Basic による比較を行うことができます<xref:Microsoft.VisualBasic.Strings.StrComp%2A>関数。 省略可能な指定`Compare`比較の種類を制御する引数:`Text`ほとんどの入力と出力に`Binary`完全一致を判断するためです。  
  
 `StrComp`関数、並べ替えの順序に基づいて、2 つの比較される文字列の間のリレーションシップを示す整数を返します。 結果の正の値は、最初の文字列が 2 番目の文字列より大きいことを示します。 陰性の結果は、最初の文字列が小さくを示し、0 の文字列間の等価性を示します。  
  
 [!code-vb[VbVbalrStrings#22](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_2.vb)]  
  
 使用することも、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]のパートナー、 `StrComp` 、関数、<xref:System.String.Compare%2A?displayProperty=nameWithType>メソッドです。 これは、文字列の基本クラスの静的なオーバー ロードされたメソッドです。 次の例では、このメソッドを使用する方法を示します。  
  
 [!code-vb[VbVbalrStrings#48](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_3.vb)]  
  
 その他のオーバー ロードを使用する比較を実行する方法をより細かく制御するには<xref:System.String.Compare%2A>メソッドです。 <xref:System.String.Compare%2A?displayProperty=nameWithType>メソッドを使用できます、`comparisonType`引数を使用する比較の種類を指定します。  
  
|値を`comparisonType`引数|比較の種類|使用に適した状況|  
|---|---|---|  
|`Ordinal`|文字列のコンポーネントのバイト数に基づく比較です。|比較するときに、この値を使用します。 識別子の大文字小文字を区別、セキュリティ関連の設定、またはバイト数を正確に一致する必要があります、他の非言語的な識別子です。|  
|`OrdinalIgnoreCase`|文字列のコンポーネントのバイト数に基づく比較です。<br /><br /> `OrdinalIgnoreCase` インバリアント カルチャ情報を使用して、2 つの文字が異なる場合にのみ大文字と小文字を決定します。|比較するときに、この値を使用します。 大文字と小文字の識別子、セキュリティ関連の設定、および Windows に格納されたデータ。|  
|`CurrentCulture` または `CurrentCultureIgnoreCase`|現在のカルチャで文字列の解釈に基づく比較です。|比較するときに、これらの値を使用: に、ユーザー、ほとんどのユーザー入力および言語的に解釈を必要とするその他のデータを表示するデータ。|  
|`InvariantCulture` または `InvariantCultureIgnoreCase`|インバリアント カルチャで文字列の解釈に基づく比較です。<br /><br /> これは異なる、`Ordinal`と`OrdinalIgnoreCase`インバリアント カルチャの許容範囲外の文字を等価のインバリアント文字として扱われるため、します。|一定の並べ替え順序を必要とするデータの永続化または言語関連データの表示を比較するときにのみ、これらの値を使用します。|  
  
### <a name="security-considerations"></a>セキュリティの考慮事項  
 アプリケーションが、比較演算子またはケース変更操作の結果に基づいてセキュリティ上の決定を行うかどうかは、操作を使用する必要があります、<xref:System.String.Compare%2A?displayProperty=nameWithType>メソッド、およびパス`Ordinal`または`OrdinalIgnoreCase`の`comparisonType`引数。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Globalization.CultureInfo>  
 [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
