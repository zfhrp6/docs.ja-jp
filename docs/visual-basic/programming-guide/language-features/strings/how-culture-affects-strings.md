---
title: "カルチャが Visual Basic における文字列に与える影響 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- locale, effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 63228a40897b29d0324be73ca1a17bcb19af2a16
ms.lasthandoff: 03/13/2017

---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Visual Basic においてカルチャが文字列に与える影響
このヘルプ ページの説明方法[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]カルチャ文字列の変換との比較を実行する情報を使用します。  
  
## <a name="when-to-use-culture-specific-strings"></a>カルチャ固有の文字列を使用する場合  
 通常は、カルチャに固有の文字列に記載されているすべてのデータを使用する必要があります、ユーザーからの読み取りし、カルチャに依存しない文字列を使用するアプリケーションの内部データおよびします。  
  
 たとえば、文字列として日付を入力するユーザーの質問は、アプリケーション、カルチャに基づく文字列の書式設定のユーザーを想定する必要があり、アプリケーションでは、文字列を適切に変換する必要があります。 アプリケーションがユーザー インターフェイスでは、その日付を表している場合は、ユーザーのカルチャの表示にする必要があります。  
  
 ただし、アプリケーションは、日付を中央のサーバーにアップロードする場合、は、可能性のある別の日付形式の間で混乱を避けるため、1 つの特定のカルチャに従って文字列を書式設定する必要があります。  
  
## <a name="culture-sensitive-functions"></a>カルチャに依存する関数  
 すべての[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列変換関数 (を除き、`Str`と`Val`関数)、アプリケーションのカルチャ情報を使用して、変換および比較がアプリケーションのユーザーのカルチャに適切であるかどうかを確認します。  
  
 キーが正常に文字列変換関数を使用して別のカルチャ設定を持つコンピューターで実行されるアプリケーションでは、どの関数が特定のカルチャ設定を使用し、現在のカルチャ設定を使用するを理解します。 アプリケーションのカルチャ設定は、既定では、継承することオペレーティング システムのカルチャ設定からに注意してください。 詳細については、次を参照してください<xref:Microsoft.VisualBasic.Strings.Asc%2A>、 <xref:Microsoft.VisualBasic.Strings.AscW%2A>、 <xref:Microsoft.VisualBasic.Strings.Chr%2A>、 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>、 <xref:Microsoft.VisualBasic.Strings.Format%2A>、 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>、 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>、および[型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)。</xref:Microsoft.VisualBasic.Conversion.Oct%2A> </xref:Microsoft.VisualBasic.Conversion.Hex%2A> </xref:Microsoft.VisualBasic.Strings.Format%2A> </xref:Microsoft.VisualBasic.Strings.ChrW%2A> </xref:Microsoft.VisualBasic.Strings.Chr%2A> </xref:Microsoft.VisualBasic.Strings.AscW%2A> </xref:Microsoft.VisualBasic.Strings.Asc%2A> 。  
  
 `Str` (数値を文字列に変換する) と`Val`文字列や数値の間で変換するときに (文字列数値からに変換) 関数が、アプリケーションのカルチャ情報を使用しないでください。 代わりに、有効な小数点区切り文字としてピリオド (.) のみを認識できるとします。 これらの関数のカルチャに対応して類似のものは次のとおりです。  
  
-   **現在のカルチャを使用する変換です。** `CStr`と`Format`関数では、数値を文字列に変換され、`CDbl`と`CInt`関数では、文字列を数値に変換します。  
  
-   **特定のカルチャを使用する変換です。** 各数値のオブジェクトには、 `ToString(IFormatProvider)` 、文字列に数値を変換するメソッドと`Parse(String, IFormatProvider)`文字列を数値に変換するメソッドです。 たとえば、`Double`種類では、<xref:System.Double.ToString%28System.IFormatProvider%29>と<xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>メソッド</xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29></xref:System.Double.ToString%28System.IFormatProvider%29>。  
  
 詳細については、「 <xref:Microsoft.VisualBasic.Conversion.Str%2A> <xref:Microsoft.VisualBasic.Conversion.Val%2A>.</xref:Microsoft.VisualBasic.Conversion.Val%2A></xref:Microsoft.VisualBasic.Conversion.Str%2A>の使用」を参照していますください。  
  
## <a name="using-a-specific-culture"></a>特定のカルチャを使用します。  
 (文字列として表した) 日付を Web サービスに送信するアプリケーションを開発することを想像してください。 ここで、アプリケーションでは、文字列の変換の特定のカルチャを使用する必要があります。 理由を示すためには、日付の使用の結果を検討してください<xref:System.DateTime.ToString>メソッド: 場合は、アプリケーションでは、そのメソッドを使用して、2005 年 7 月 4 日の日付の書式設定を返します"2005 年 7 月 4 日 12:00:00 AM"を実行すると、米国英語 (EN-US) カルチャは"04.07.2005 00:00:00"ドイツ (de-de などがあります) のカルチャで実行する場合。</xref:System.DateTime.ToString> 。  
  
 使用する必要がありますで特定のカルチャの書式設定文字列変換を実行する必要がある場合、`CultureInfo`に組み込まれているクラス、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]です。 新規に作成することができます`CultureInfo`カルチャの名前を渡すことによって、特定のカルチャのオブジェクト、<xref:System.Globalization.CultureInfo.%23ctor%2A>コンス トラクター</xref:System.Globalization.CultureInfo.%23ctor%2A> 。 サポートされているカルチャの名前にある、<xref:System.Globalization.CultureInfo>クラスのヘルプ ページ</xref:System.Globalization.CultureInfo>。  
  
 インスタンスを取得する代わりに、*インバリアント カルチャ*から、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>プロパティ</xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>。 インバリアント カルチャが英語のカルチャに基づきますが、違いがあります。 たとえば、インバリアント カルチャでは、12 時間制ではなく、24 時間制を指定します。  
  
 日付をカルチャの文字列に変換するには、渡す、<xref:System.Globalization.CultureInfo>が日付のオブジェクトのオブジェクト<xref:System.DateTime.ToString%28System.IFormatProvider%29>メソッド</xref:System.DateTime.ToString%28System.IFormatProvider%29></xref:System.Globalization.CultureInfo>。 たとえば、次のコードが表示されます"07/04/2005 00時 00分: 00"アプリケーションのカルチャ設定に関係なく、します。  
  
 [!code-vb[VbVbalrConcepts&#1;](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/how-culture-affects-strings_1.vb)]  
  
> [!NOTE]
>  日付リテラルは常に英語のカルチャに従って解釈されます。  
  
## <a name="comparing-strings"></a>文字列の比較  
 文字列の比較が必要な&2; つの重要な状況があります。  
  
-   **ユーザーに表示するデータを並べ替えます。** 現在のカルチャに基づく文字列を適切に並べ替えるための操作を使用します。  
  
-   **アプリケーション内部の&2; つの文字列が (通常はセキュリティ上の理由) 正確に一致するかどうかを決定します。** 現在のカルチャは無視して操作を使用します。  
  
 両方の種類の比較を行うことができます、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Strings.StrComp%2A>関数</xref:Microsoft.VisualBasic.Strings.StrComp%2A>。 省略可能な指定`Compare`比較の種類を制御する引数:`Text`ほとんどの入力と出力に`Binary`完全一致を判断するためです。  
  
 `StrComp`関数を並べ替え順序に基づいて比較される&2; つの文字列間の関係を示す整数を返します。 結果の正の値は、最初の文字列が&2; 番目の文字列より大きいことを示します。 負の結果は、最初の文字列が小さくを示し、0 の文字列間の等価性を示します。  
  
 [!code-vb[VbVbalrStrings #&22;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_2.vb)]  
  
 使用することも、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]のパートナー、 `StrComp` 、関数、<xref:System.String.Compare%2A?displayProperty=fullName>メソッド</xref:System.String.Compare%2A?displayProperty=fullName>。 これは、文字列の基本クラスの静的、オーバー ロードされたメソッドです。 次の例では、このメソッドを使用する方法を示します。  
  
 [!code-vb[VbVbalrStrings #&48;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_3.vb)]  
  
 比較の実行方法をより細かく制御するには、追加のオーバー ロードを使用することができます、<xref:System.String.Compare%2A>メソッド</xref:System.String.Compare%2A>。 <xref:System.String.Compare%2A?displayProperty=fullName>使用するメソッド、`comparisonType`引数を使用する比較の種類を指定します</xref:System.String.Compare%2A?displayProperty=fullName>。  
  
|場合は値`comparisonType`引数|比較の種類|使用に適した状況|  
|---|---|---|  
|`Ordinal`|文字列のコンポーネントのバイト数に基づく比較。|比較するときに、この値を使用します。 識別子の大文字小文字の区別、セキュリティ関連の設定またはバイト数を正確に満たす必要があるその他の非言語的な識別子です。|  
|`OrdinalIgnoreCase`|文字列のコンポーネントのバイト数に基づく比較。<br /><br /> `OrdinalIgnoreCase`インバリアント カルチャ情報を使用して、2 つの文字が異なる場合にのみ大文字と小文字を決定します。|比較するときに、この値を使用します。 小文字を区別しない識別子、セキュリティ関連の設定、および Windows に格納されたデータ。|  
|`CurrentCulture` または `CurrentCultureIgnoreCase`|現在のカルチャでの文字列の解釈に基づく比較。|比較するときに、これらの値を使用します。 ユーザー、ほとんどのユーザー入力、および言語的に解釈を必要とするその他のデータに表示されるデータ。|  
|`InvariantCulture` または `InvariantCultureIgnoreCase`|インバリアント カルチャの文字列の解釈に基づく比較。<br /><br /> これは、異なる、`Ordinal`と`OrdinalIgnoreCase`、インバリアント カルチャは、等価のインバリアント文字として許容される範囲外の文字を処理するためです。|これらの値は、一定の並べ替え順序が必要なデータを保持するか、言語関連データの表示を比較するときにだけに使用します。|  
  
### <a name="security-considerations"></a>セキュリティの考慮事項  
 アプリケーションが、比較演算または大文字の演算の結果に基づいてセキュリティ上の決定を行うかどうかは、操作を使用する必要があります、<xref:System.String.Compare%2A?displayProperty=fullName>メソッド、およびパス`Ordinal`または`OrdinalIgnoreCase`の`comparisonType`引数</xref:System.String.Compare%2A?displayProperty=fullName>。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Globalization.CultureInfo></xref:System.Globalization.CultureInfo>   
 [Visual Basic における文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
