---
title: Visual Basic での変数宣言
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 6890ddfd8b463cd731ab3d8f39565b50a31a1192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="variable-declaration-in-visual-basic"></a>Visual Basic での変数宣言
名前と特性を指定する変数を宣言するとします。 変数の宣言ステートメントは、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)です。 その場所と内容は、変数の特性を決定します。  
  
 変数の名前付け規則と考慮事項について、次を参照してください。[宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
## <a name="declaration-levels"></a>宣言のレベル  
  
### <a name="local-and-member-variables"></a>ローカルとメンバー変数  
 A*ローカル変数*はプロシージャ内で宣言されている 1 つです。 A*メンバー変数*; Visual Basic の型のメンバーは、モジュール レベル、そのクラス、構造体、またはモジュールの内部プロシージャ内ではありませんが、クラス、構造体、またはモジュール内で宣言されています。  
  
### <a name="shared-and-instance-variables"></a>共有し、インスタンス変数  
 クラスまたは構造体のメンバー変数のカテゴリが共有されているかどうかに依存します。 宣言されている場合、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)キーワードでは、*共有変数*、1 つのコピーがクラスまたは構造体のすべてのインスタンス間で共有内に存在するとします。  
  
 以外の場合は、*インスタンス変数*、クラスまたは構造体のインスタンスごとの個別のコピーが作成されたとします。 インスタンス変数のコピーは、クラスまたは構造体が作成されたインスタンスでのみ使用可能です。 クラスまたは構造体のインスタンスをすべてのインスタンス変数のコピーの関係。  
  
## <a name="declaring-data-type"></a>データ型を宣言します。  
 [として](../../../../visual-basic/language-reference/statements/as-clause.md)宣言ステートメントの句では、データ型またはオブジェクトを宣言する変数の型を定義することができます。 変数の種類は次のいずれかを指定できます。  
  
-   基本データ型など`Boolean`、 `Long`、または `Decimal`  
  
-   配列や構造体などの複合データ型  
  
-   オブジェクトの種類、または別のアプリケーションまたはアプリケーションで定義されているクラス  
  
-   A[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラスなど<xref:System.Windows.Forms.Label>または <xref:System.Windows.Forms.TextBox>  
  
-   インターフェイス型など、<xref:System.IComparable>または <xref:System.IDisposable>  
  
 データ型を繰り返すことがなく 1 つのステートメントで複数の変数を宣言することができます。 次のステートメントでは、変数で`i`、 `j`、および`k`型として宣言されて`Integer`、`l`と`m`として`Long`、および`x`と`y`として`Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 データ型の詳細については、次を参照してください。[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)です。 オブジェクトの詳細については、次を参照してください。[クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)と[コンポーネントを使用したプログラミング](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)です。  
  
## <a name="local-type-inference"></a>ローカル型の推論  
 *型推論*なしで宣言されたローカル変数のデータ型を決定するために使用、`As`句。 コンパイラは、初期化式の型から変数の型を推論します。 これにより、型を明示的に指定せずに変数を宣言できます。 次の例では、両方とも`num1`と`num2`整数値として厳密に型指定します。  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 ローカル型推論を使用する場合は、`Option Infer`に設定する必要があります`On`です。 詳細については、「[ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」と「[Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」を参照してください。  
  
## <a name="characteristics-of-declared-variables"></a>宣言された変数の特性  
 *有効期間*変数の期間が中に、使用可能です。 一般に、プロシージャまたはクラス) などを宣言した要素が存在し続けます限り、変数が存在します。 変数がそのコンテナー要素の有効期間よりも長く必要がない場合は、宣言で特別な処理を行う必要はありません。 含めることができる場合は、変数は、引き続きそのコンテナー要素よりも長く存在する必要がある場合、`Static`または`Shared`キーワードでその`Dim`ステートメントです。 詳細については、次を参照してください。 [Visual Basic における有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)です。  
  
 *スコープ*変数の名前を修飾せずに参照できるすべてのコードのセットです。 変数のスコープは、宣言されている場所によって決まります。 特定の地域にあるコードでは、その名前を修飾することがなく、その地域で定義されている変数を使用できます。 詳細については、次を参照してください。 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)です。  
  
 変数の*アクセス レベル*へのアクセス許可のあるコードの範囲がします。 これは、アクセス修飾子によって決定されます (など[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)) で使用する、`Dim`ステートメントです。 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法 : 新しい変数を作成する](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)  
 [方法 : 変数に値を格納する、および変数から値を取得する](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
