---
title: Option Strict Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: de9703c43d32fba4a5f9d661546e0beb66c24602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="option-strict-statement"></a>Option Strict Statement
暗黙的なデータ型の変換のみ拡大変換を制限、遅延バインディングは許可されていません、および結果となる暗黙の型指定は許可されていません、`Object`型です。  
  
## <a name="syntax"></a>構文  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`On`|任意。 により、`Option Strict`をチェックします。|  
|`Off`|任意。 無効に`Option Strict`をチェックします。|  
  
## <a name="remarks"></a>コメント  
 ときに`Option Strict On`または`Option Strict`ファイルで、コンパイル時エラーが発生する、次の条件が表示されます。  
  
-   暗黙的な縮小変換  
  
-   遅延バインディング  
  
-   結果が `Object` 型となる暗黙の型指定  
  
> [!NOTE]
>  設定することが警告の構成で、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)コンパイル時エラーが発生する 3 つの条件に対応する 3 つの設定があります。 これらの設定を使用する方法については、次を参照してください。 [IDE で警告の構成を設定する](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)このトピックで後述します。  
  
 `Option Strict Off`ステートメントは、これらのエラーまたは警告を有効にする、関連付けられた IDE 設定を指定する場合でもエラーと警告は、次の 3 つのすべての条件のチェックをオフにします。 `Option Strict On`関連付けられている IDE 設定を指定すると、これらのエラーまたは警告をオフにする場合でも、ステートメントがエラーと警告は、次の 3 つのすべての条件のチェックをオンにします。  
  
 使用する場合、`Option Strict`ステートメントがファイル内の他のコード ステートメントより前に記述する必要があります。  
  
 設定すると`Option Strict`に`On`、Visual Basic では、すべてのプログラミング要素のデータ型を指定することを確認します。 データ型を明示的に指定またはローカル型推論を使用して指定できます。 すべてのプログラミング要素のデータ型を指定することをお勧め、次の理由。  
  
-   変数およびパラメーターについての IntelliSense サポートを使用できます。 これにより、コードを入力すると、そのプロパティおよびその他のメンバーを参照してください。  
  
-   これにより、コンパイラが型チェックを実行できます。 型チェック、型変換エラーのため実行時に失敗するステートメントを検索できます。 また、これらのメソッドをサポートしていないオブジェクトに対するメソッドの呼び出しを識別します。  
  
-   高速化のコードを実行します。 理由は、1 つがある場合、プログラミング要素のデータ型を指定しないと、Visual Basic コンパイラが割り当てる、`Object`型です。 コンパイルされたコードは間を変換する必要があります`Object`およびその他のデータ型は、パフォーマンスが低下します。  
  
## <a name="implicit-narrowing-conversion-errors"></a>暗黙的な縮小変換エラー  
 縮小変換する暗黙的なデータ型変換がある場合は、暗黙的な縮小変換エラーが発生します。  
  
 Visual Basic は、多くのデータ型を他のデータ型に変換できます。 1 つのデータ型の値でありより精度の低いまたは容量の小さいデータ型に変換するときに、データ損失が発生することができます。 このような縮小変換が失敗した場合、実行時エラーが発生します。 `Option Strict` これらの縮小変換のコンパイル時の通知のことを確認して、それらを回避するようにします。 詳細については、次を参照してください。[暗黙的および明示的な変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)と[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)です。  
  
 エラーが発生する変換では、式に発生する暗黙的な変換を含めます。 詳細については、次のトピックを参照してください。  
  
-   [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char データ型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 使用して文字列を連結すると、 [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)、すべての文字列への変換は、拡大変換と見なされます。 場合でも、暗黙的な縮小変換エラーは、これらの変換を生成しないように`Option Strict`にします。  
  
 対応するパラメーターと異なるデータ型が引数を持つメソッドを呼び出すときに縮小変換、コンパイル時エラーが発生場合`Option Strict`にします。 拡大変換または明示的な変換を使用して、コンパイル時のエラーを回避できます。  
  
 内の要素からの変換のコンパイル時に暗黙的な縮小変換エラーが抑制されます、`For Each…Next`ループ コントロール変数のコレクション。 これが発生した場合でも`Option Strict`にします。 詳細についてを参照してください「の縮小変換」[ごとにしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)します。  
  
## <a name="late-binding-errors"></a>遅延バインド エラー  
 `Object` 型として宣言された変数のプロパティまたはメソッドにオブジェクトを代入する場合は、そのオブジェクトは遅延バインディングされます。 詳細については、次を参照してください。 [Early and 遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)です。  
  
## <a name="implicit-object-type-errors"></a>暗黙的なオブジェクトの種類のエラー  
 適切な型が宣言された変数を推論できない場合は暗黙的なオブジェクトの型エラーが発生するため、`Object` の型が推論されます。 これは主に、`As` 句を使用せず、`Option Infer` をオフにして、`Dim` ステートメントを使用して変数を宣言した場合に発生します。 詳細については、次を参照してください。 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)と[Visual Basic 言語仕様](../../../visual-basic/reference/language-specification/index.md)です。  
  
 メソッドのパラメーターに、`As`句は省略可能場合`Option Strict`は無効になっています。 ただし、すべて 1 つのパラメーターで使用する場合、`As`句、これらはすべて使用する必要の。 場合`Option Strict`が有効になって、`As`句がパラメーター定義のそれぞれに必要です。  
  
 使用せずに変数を宣言する場合、`As`句には、設定と`Nothing`、変数の型を持つ`Object`します。 コンパイル時エラーが発生しないここではときに`Option Strict`上と`Option Infer`にします。 この例は、`Dim something = Nothing`です。  
  
### <a name="default-data-types-and-values"></a>既定のデータ型と値  
 次の表に、型を指定して、データ内の初期化子のさまざまな組み合わせの結果、 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)です。  
  
|データ型が指定されているか|初期化子が指定されているか|例|結果|  
|---|---|---|---|  
|Ｘ|Ｘ|`Dim qty`|`Option Strict` がオフ (既定値) の場合、変数は `Nothing` に設定されます。<br /><br /> `Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|Ｘ|○|`Dim qty = 5`|`Option Infer` がオン (既定値) の場合、変数は初期化子のデータ型になります。 参照してください[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。<br /><br /> `Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。<br /><br /> `Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|○|Ｘ|`Dim qty As Integer`|変数は、データ型の既定値に初期化されます。 詳細については、次を参照してください。 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)です。|  
|[はい]|○|`Dim qty  As Integer = 5`|初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Option Strict ステートメントが存在する場合されません。  
 ソース コードが含まれていない場合、`Option Strict`ステートメントでは、 **Option strict**の設定、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用します。 **[コンパイル] ページ**にエラーが生成される条件をさらに制御を提供する設定があります。  
  
 使用することができます、コマンド ライン コンパイラを使用している場合、 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラ オプションの設定を指定する`Option Strict`です。  
  
### <a name="to-set-option-strict-in-the-ide"></a>IDE で Option Strict を設定するには  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **コンパイル** タブの値を設定、 **Option Strict**ボックス。  
  
###  <a name="conditions"></a> IDE で警告の構成を設定するには  
 使用すると、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)の代わりに、`Option Strict`ステートメントでは、エラーが生成される条件をさらに制御があります。 **警告の構成**のセクション、 **[コンパイル] ページ**コンパイル時エラーが発生する 3 つの条件に対応する設定を持つときに`Option Strict`にします。 これらの設定を次に示します。  
  
-   **暗黙的な変換**  
  
-   **遅延バインディング、呼び出しが実行時に失敗する可能性があります**  
  
-   **暗黙的な型、オブジェクトと見なされます**  
  
 **[Option Strict]** を **[オン]** に設定すると、これら 3 つの警告の構成設定のすべてが **[エラー]** に設定されます。 **[Option Strict]** を **[オフ]** に設定すると、3 つの設定すべてが **[なし]** に設定されます。  
  
 各警告の構成設定を個別に **[なし]**、**[警告]**、または **[エラー]** に変更することができます。 3 つの警告の構成設定がすべて **[エラー]** に設定されている場合、`Option strict` ボックスに `On` が表示されます。 3 つすべてが **[なし]** に設定されている場合、このボックスには `Off` が表示されます。 これらの設定のその他の組み合わせに対しては、**(カスタム)** が表示されます。  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>新しいプロジェクトの Option Strict の既定の設定を設定するには  
 プロジェクトを作成するときに、 **Option Strict**の設定、**コンパイル** タブに設定されている、 **Option Strict**での設定、**オプション**ダイアログ ボックス。  
  
 設定する`Option Strict`このダイアログ ボックスで、上、**ツール** メニューのをクリックして**オプション**です。 **[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、**[VISUAL BASIC の既定値]** をクリックします。 初期の既定の設定**VB 既定**は`Off`します。  
  
### <a name="to-set-option-strict-on-the-command-line"></a>コマンドラインで Option Strict を設定するには  
 含める、 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラ オプション、 **vbc**コマンド。  
  
## <a name="example"></a>例  
 次の例では、変換は縮小変換を暗黙の型変換によって発生したコンパイル時エラーを示します。 対応するこのようなエラー、**暗黙的な変換**の条件、 **[コンパイル] ページ**です。  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、コンパイル時エラーが原因で遅延バインディングを示します。 対応するこのようなエラー、**遅れてバインディング; 呼び出しが失敗する実行時に**の条件、 **[コンパイル] ページ**です。  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>例  
 次の例では、暗黙的な型で宣言されている変数によって発生したエラー`Object`です。 このようなエラーに対応しています、**暗黙の型以外のオブジェクトと見なされます**の条件、 **[コンパイル] ページ**です。  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [方法: オブジェクトのメンバーにアクセスする](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Office ソリューションの遅延バインディング](https://msdn.microsoft.com/library/3xxe951d)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
