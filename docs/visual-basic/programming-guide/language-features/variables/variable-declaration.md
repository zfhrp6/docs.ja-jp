---
title: "Visual Basic での変数宣言 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables, declarations
- Dim statement, variable declaration
- declaring variables
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime, variables
- variables [Visual Basic], lifetime
- access levels, variables
- scope, declaration statements
- variables [Visual Basic], access level
- local variables, declarations
- scope, variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8cabb2d319288653c80099c816e46e822429d6ec
ms.lasthandoff: 03/13/2017

---
# <a name="variable-declaration-in-visual-basic"></a>Visual Basic での変数宣言
名前と特性を指定する変数を宣言するとします。 変数の宣言ステートメントは、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)します。 その場所や内容は、変数の特性を決定します。  
  
 変数の名前付け規則と考慮事項では、次を参照してください。[宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
## <a name="declaration-levels"></a>宣言のレベル  
  
### <a name="local-and-member-variables"></a>ローカル変数とメンバー変数  
 A*ローカル変数*プロシージャ内で宣言されている&1; つです。 A*メンバー変数*のメンバーである、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]型クラス、構造体、またはモジュールに内部プロシージャ内ではありませんが、クラス、構造体、またはモジュール内のモジュール レベルで宣言されています。  
  
### <a name="shared-and-instance-variables"></a>共有し、インスタンス変数  
 クラスまたは構造体のメンバー変数のカテゴリが共有されるかどうかに依存します。 宣言されている場合、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)は、キーワード、*共有変数*、1 つのコピーがクラスまたは構造体のすべてのインスタンス間で共有内に存在するとします。  
  
 以外の場合は、*インスタンス変数*、およびクラスまたは構造体の各インスタンスの独立したコピーを作成します。 インスタンス変数のコピーは、クラスまたは構造体が作成されたインスタンスでのみ使用可能です。 これは、クラスまたは構造体の他の任意のインスタンスにインスタンス変数のコピーに依存しません。  
  
## <a name="declaring-data-type"></a>データ型の宣言  
 [として](../../../../visual-basic/language-reference/statements/as-clause.md)宣言ステートメントに句を使用すると、データ型またはオブジェクトを宣言する変数の型を定義します。 変数の種類を次のいずれかを指定できます。  
  
-   基本データ型など、 `Boolean`、 `Long`、または`Decimal`  
  
-   配列や構造体などの複合データ型  
  
-   オブジェクトの種類、または、アプリケーションまたは別のアプリケーションのいずれかを定義したクラス  
  
-   A[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]クラスなど、<xref:System.Windows.Forms.Label>または<xref:System.Windows.Forms.TextBox></xref:System.Windows.Forms.TextBox></xref:System.Windows.Forms.Label>  
  
-   インターフェイス型など、<xref:System.IComparable>または<xref:System.IDisposable></xref:System.IDisposable></xref:System.IComparable>  
  
 データ型を繰り返さなくても、1 つのステートメントで複数の変数を宣言できます。 次のステートメントでは、変数で`i`、 `j`、および`k`型として宣言されて`Integer`、`l`と`m`として`Long`、および`x`と`y`として`Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 データ型の詳細については、次を参照してください。[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)します。 オブジェクトの詳細については、次を参照してください。[オブジェクトおよびクラス](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)と[コンポーネントを使用したプログラミング](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)します。  
  
## <a name="local-type-inference"></a>ローカル型の推論  
 *型の推論*なしで宣言されたローカル変数のデータ型を決定するために使用、`As`句。 コンパイラは、初期化式の型から変数の型を推論します。 これにより、型を明示的に指定せずに変数を宣言することができます。 次の例では両方とも`num1`と`num2`整数として厳密に型指定します。  
  
 [!code-vb[VbVbalrTypeInference&#1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 ローカル型推論を使用する場合は、`Option Infer`に設定する必要があります`On`します。 詳細については、次を参照してください。[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)と[Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)します。  
  
## <a name="characteristics-of-declared-variables"></a>宣言された変数の特性  
 *有効期間*変数は、一定時間その中に、使用可能です。 一般に、変数は、(手順やクラスで) 宣言された要素が存在し続けます限り存在します。 変数がそのコンテナー要素の有効期間よりも長く必要がない場合は、宣言で特別な対応を行う必要はありません。 含めることができますが、変数は、引き続きそのコンテナー要素よりも長く存在する必要がある場合、`Static`または`Shared`キーワードでその`Dim`ステートメントです。 詳細については、次を参照してください。 [Visual Basic における有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)します。  
  
 *スコープ*の変数の名前を修飾せずに参照できるすべてのコードのセットです。 変数のスコープは、宣言されている場所によって決まります。 指定したリージョンに置かれているコードは、その名前を修飾しなくても、そのリージョンで定義されている変数を使用できます。 詳細については、次を参照してください。 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)します。  
  
 変数の*アクセス レベル*へのアクセス許可のあるコードの範囲は、です。 これは、アクセス修飾子によって決まります (よう[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)) で使用する、`Dim`ステートメントです。 詳細については、次を参照してください。 [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: 新しい変数を作成](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)   
 [方法: 変数に出入りするデータを移動](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [保護されています。](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [静的](../../../../visual-basic/language-reference/modifiers/static.md)   
 [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
