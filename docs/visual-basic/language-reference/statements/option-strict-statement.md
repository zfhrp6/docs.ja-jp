---
title: "Option Strict ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Strict
- vb.OptionStrict
dev_langs:
- VB
helpviewer_keywords:
- Strict keyword
- Option Strict statement
- conversions, implicit
- late binding
- implicit conversions
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
caps.latest.revision: 49
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 3bf0d4939f24c38392d7ca4764c41d12366067b5
ms.lasthandoff: 03/13/2017

---
# <a name="option-strict-statement"></a>Option Strict Statement
暗黙的なデータ型の変換のみ拡大変換を制限、遅延バインディングが禁止およびが発生する暗黙の型指定を許可しません、`Object`型です。  
  
## <a name="syntax"></a>構文  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`On`|省略可能です。 により、`Option Strict`をチェックします。|  
|`Off`|省略可能です。 無効に`Option Strict`をチェックします。|  
  
## <a name="remarks"></a>コメント  
 `Option Strict On`または`Option Strict`ファイルにコンパイル エラーが発生する、次の条件が表示されます。  
  
-   暗黙的な縮小変換  
  
-   遅延バインディング  
  
-   発生する暗黙の型指定、`Object`型  
  
> [!NOTE]
>  に対して設定した警告の構成で、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)コンパイル時エラーが発生する&3; つの条件に対応する&3; つの設定があります。 これらの設定を使用する方法については、次を参照してください。 [IDE で警告の構成を設定する](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)このトピックで後述します。  
  
 `Option Strict Off`ステートメントは、関連付けられている IDE 設定を指定すると、これらのエラーまたは警告を有効にする場合でもエラーと警告は、次の&3; つのすべての条件のチェックをオフにします。 `Option Strict On`関連する IDE 設定を指定すると、これらのエラーまたは警告をオフにする場合でも、ステートメントがエラーと警告は、次の&3; つのすべての条件のチェックをオンにします。  
  
 使用する場合、`Option Strict`ステートメントは、ファイル内の他のコード ステートメントの前に出現する必要があります。  
  
 設定すると`Option Strict`に`On`、Visual Basic では、すべてのプログラミングの要素のデータ型が指定されているを確認します。 データ型を明示的に指定またはローカル型推論を使用して指定します。 プログラミングのすべての要素のデータ型を指定することをお勧め、次の理由。  
  
-   これにより、IntelliSense で変数とパラメーターをサポートできます。 これにより、コードを入力すると、そのプロパティおよびその他のメンバーを参照してください。  
  
-   コンパイラが型チェックを実行するようになります。 型チェックでは、型変換エラーのため、実行時に失敗するステートメントを検索できます。 また、これらのメソッドをサポートしていないオブジェクトに対するメソッドの呼び出しを識別します。  
  
-   コードの実行の速度が向上します。 この理由の&1; つは、プログラミングの要素のデータ型を指定しない場合、Visual Basic コンパイラが割り当てる、`Object`型です。 コンパイルされたコードは、間を変換する必要があります`Object`およびその他のデータ型は、パフォーマンスが低下します。  
  
## <a name="implicit-narrowing-conversion-errors"></a>暗黙的な縮小変換エラー  
 縮小変換であるデータ型の変換がある場合に、暗黙的な縮小変換エラーが発生します。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]多くのデータ型を他のデータ型に変換できます。 精度が低いまたは小規模な容量を持つデータ型に&1; つのデータ型の値が変換されるときに、データ損失が発生することができます。 このような縮小変換が失敗した場合、実行時エラーが発生します。 `Option Strict`それらを回避するようには、これらの縮小変換のコンパイル時に通知を確実にします。 詳細については、次を参照してください。[暗黙的および明示的な変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)と[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)します。  
  
 エラーが発生する変換には、式で発生する暗黙的な変換が含まれます。 詳細については、次のトピックを参照してください。  
  
-   [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char データ型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 使用して文字列を連結すると、 [>/documents/report1.rdl」の演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)文字列へのすべての変換は拡大変換と見なされます。 これらの変換は暗黙的な縮小変換のエラーであってを生成しないように`Option Strict`にします。  
  
 場合に縮小変換がコンパイル時エラーになります、対応するパラメーターと異なるデータ型を持つ引数を持つメソッドを呼び出すと、`Option Strict`にします。 拡大変換または明示的な変換を使用して、コンパイル時エラーを回避できます。  
  
 コンパイル単位内の要素からの変換で暗黙的な縮小変換エラーが抑制されている、`For Each…Next`ループ制御変数のコレクション。 これが発生した場合でも`Option Strict`にします。 詳細については、「縮小変換」」セクションを参照してください[ごとにしています.。次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)です。  
  
## <a name="late-binding-errors"></a>遅延バインド エラー  
 プロパティまたはメソッドの型に宣言されている変数に代入される場合、オブジェクトは遅延バインディング`Object`します。 詳細については、次を参照してください。[早期と遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)します。  
  
## <a name="implicit-object-type-errors"></a>暗黙の型のオブジェクトの種類のエラー  
 適切な型ができない場合に暗黙の型のオブジェクトの種類のエラーが発生するための型で宣言された変数の推論`Object`は一切関係ありません。 これを使用する場合、主に発生する、`Dim`ステートメントを使用せずに変数を宣言する、`As`句、および`Option Infer`は無効になっています。 詳細については、次を参照してください。 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)と[Visual Basic 言語仕様](../../../visual-basic/reference/language-specification.md)します。  
  
 メソッド パラメーターの`As`句は省略可能な場合`Option Strict`は無効になっています。 ただし、1 つのパラメーターを使用している場合、`As`句、これらはすべて使用する必要です。 場合`Option Strict`が有効で、`As`句が各パラメーター定義が必要です。  
  
 使用せずに変数を宣言する場合、`As`句に設定し、 `Nothing`、変数の型を持つ`Object`です。 コンパイル時エラーが発生しないここでとき`Option Strict`上と`Option Infer`にします。 この例は、`Dim something = Nothing`です。  
  
### <a name="default-data-types-and-values"></a>既定のデータ型と値  
 次の表に、データ型との初期化子を指定するさまざまな組み合わせの結果、 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)します。  
  
|データ型が指定されているか|初期化子が指定されているか|例|結果|  
|---|---|---|---|  
|Ｘ|Ｘ|`Dim qty`|
          `Option Strict` がオフ (既定値) の場合、変数は `Nothing` に設定されます。<br /><br /> `Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|Ｘ|○|`Dim qty = 5`|`Option Infer` がオン (既定値) の場合、変数は初期化子のデータ型になります。 参照してください[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。<br /><br /> `Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。<br /><br /> `Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|○|Ｘ|`Dim qty As Integer`|変数は、データ型の既定値に初期化されます。 詳細については、次を参照してください。 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)します。|  
|はい|○|`Dim qty  As Integer = 5`|初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Option Strict ステートメントが存在しない場合  
 ソース コードが含まれていない場合、`Option Strict`ステートメント、 **Option strict**の設定、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用します。 **[コンパイル] ページ**はエラーが生成される条件をさらに制御を提供する設定があります。  
  
 使用することができます、コマンド ライン コンパイラを使用している場合、 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラ オプションの設定を指定する`Option Strict`です。  
  
### <a name="to-set-option-strict-in-the-ide"></a>IDE で Option Strict を設定するには  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
1.  **ソリューション エクスプ ローラー**プロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **コンパイル** タブの値を設定、 **Option Strict**ボックス。  
  
###  <a name="conditions"></a>IDE で警告の構成を設定するには  
 使用すると、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)の代わりに、`Option Strict`ステートメントがあるエラーが生成される条件をさらに制御します。 **警告の構成**のセクション、 **[コンパイル] ページ**がコンパイル時エラーが発生する&3; つの条件に対応する設定と`Option Strict`にします。 これらの設定を次に示します。  
  
-   **暗黙の変換**  
  
-   **遅延バインディングです。呼び出しが実行時に失敗する可能性があります。**  
  
-   **暗黙の型。オブジェクトと見なされます**  
  
 設定すると**Option Strict**に**に**、これらの警告の構成設定の&3; つすべてに設定されて**エラー**します。 設定すると**Option Strict**に**オフ**、3 つすべての設定が  **None**します。  
  
 各警告する構成設定を個別に変更できます**None**、**警告**、または**エラー**します。 次の&3; つのすべての警告の構成設定が設定されている場合**エラー**、`On`で表示される、`Option strict`ボックス。 3 つすべてが設定されている場合**None**、`Off`このボックスに表示されます。 これらの設定の他の任意の組み合わせの**(カスタム)**が表示されます。  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>新しいプロジェクトの Option Strict の既定の設定を設定するには  
 プロジェクトを作成するときに、 **Option Strict**の設定、**コンパイル**に設定されているタブ、 **Option Strict**で設定、**オプション** ダイアログ ボックス。  
  
 設定する`Option Strict`この ダイアログ ボックスで、**ツール** メニューのをクリックして**オプション**します。 **オプション** ダイアログ ボックスで、展開**プロジェクトおよびソリューション**、 をクリックし、 **VB が既定で**します。 初期の既定の設定**VB 既定**は`Off`です。  
  
### <a name="to-set-option-strict-on-the-command-line"></a>コマンドラインで Option Strict を設定するには  
 含める、 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラ オプションで、 **vbc**コマンドです。  
  
## <a name="example"></a>例  
 次の例では、変換は縮小変換を暗黙の型変換によって発生したコンパイル時エラーを示します。 このようなエラーは、**暗黙的な変換**条件、 **[コンパイル] ページ**します。  
  
 [!code-vb[VbVbalrStatements #&161;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、遅延バインディングによるコンパイル時エラーを示します。 対応してこのようなエラー、**遅延バインディングです。 呼び出しが実行時に失敗でした**条件、 **[コンパイル] ページ**します。  
  
 [!code-vb[VbVbalrStatements #&162;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>例  
 次の例では、暗黙の型で宣言されている変数によって発生したエラー`Object`します。 このようなエラーは、**暗黙的な型; object と見なされます**条件、 **[コンパイル] ページ**します。  
  
 [!code-vb[VbVbalrStatements #&163;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements #&164;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [明示的および暗黙的な変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)   
 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [方法: オブジェクトのメンバーにアクセス](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Office ソリューションの遅延バインディング](https://msdn.microsoft.com/library/3xxe951d)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
