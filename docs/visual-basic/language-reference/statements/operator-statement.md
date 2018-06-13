---
title: Operator Statement
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: cb7fe7929e4b6e61ca3b39be5615e09182f2fe0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605499"
---
# <a name="operator-statement"></a>Operator Statement
演算子記号、オペランド、およびクラスまたは構造体に演算子プロシージャを定義するコードを宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a>指定項目  
 `attrlist`  
 任意。 参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。  
  
 `Public`  
 必須。 この演算子プロシージャがあることを示します[パブリック](../../../visual-basic/language-reference/modifiers/public.md)アクセスします。  
  
 `Overloads`  
 任意。 参照してください[Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)です。  
  
 `Shared`  
 必須。 この演算子プロシージャがあることを示します、 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)プロシージャです。  
  
 `Shadows`  
 任意。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。  
  
 `Widening`  
 指定しない限り、変換演算子に必要な`Narrowing`します。 この演算子プロシージャを定義することを示す、 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)変換します。 このヘルプ ページの「拡大と縮小変換」を参照してください。  
  
 `Narrowing`  
 指定しない限り、変換演算子に必要な`Widening`します。 この演算子プロシージャを定義することを示す、 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)変換します。 このヘルプ ページの「拡大と縮小変換」を参照してください。  
  
 `operatorsymbol`  
 必須。 シンボルまたは、この演算子プロシージャを定義する演算子の識別子。  
  
 `operand1`  
 必須。 名前と (変換演算子を含む) 単項演算子のオペランドは、1 つまたは 2 項演算子の左オペランドの型。  
  
 `operand2`  
 二項演算子に必要です。 名前と、バイナリ演算子の右側のオペランドの型。  
  
 `operand1` および`operand2`次の構文と部分があります。  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|パーツ|説明|  
|----------|-----------------|  
|`ByVal`|省略可能、ただし引き渡し方法があります[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)です。|  
|`operandname`|必須。 このオペランドを表す変数の名前。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。|  
|`operandtype`|省略可能な場合を除き、`Option Strict`は`On`します。 このオペランドのデータ型。|  
  
 `type`  
 省略可能な場合を除き、`Option Strict`は`On`します。 演算子プロシージャは、値のデータ型を返します。  
  
 `statements`  
 任意。 演算子プロシージャが実行されるステートメントのブロックです。  
  
 `returnvalue`  
 必須。 演算子プロシージャが呼び出し元のコードに返す値。  
  
 `End` `Operator`  
 必須。 この演算子プロシージャの定義を終了します。  
  
## <a name="remarks"></a>コメント  
 使用することができます`Operator`クラスまたは構造体でのみです。 つまり、*宣言コンテキスト*演算子にソース ファイル、名前空間、モジュール、インターフェイス、プロシージャ、またはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 すべての演算子がある必要があります`Public Shared`です。 指定することはできません`ByRef`、 `Optional`、または`ParamArray`のいずれかのオペランド。  
  
 戻り値を保持するのに演算子記号または識別子を使用することはできません。 使用する必要があります、`Return`ステートメント、およびその値を指定する必要があります。 任意の数の`Return`ステートメントは、プロシージャのどこに表示できます。  
  
 この方法で演算子を定義するが呼び出された*演算子のオーバー ロード*を使用するかどうかにかかわらず、`Overloads`キーワード。 定義可能な演算子を次の表に示します。  
  
|型|演算子|  
|----------|---------------|  
|単項|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|2 項|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|変換 (単項)|`CType`|  
  
 なお、 `=` 2 項の一覧で演算子は、比較演算子、代入演算子ではありません。  
  
 定義するときに`CType`、どちらかを指定する必要があります`Widening`または`Narrowing`です。  
  
## <a name="matched-pairs"></a>一致するペア  
 特定の演算子は、一致するペアとして定義する必要があります。 このようなペアのいずれかの演算子を定義する場合は、他の同様を定義する必要があります。 一致するペア次に示します。  
  
-   `=` および `<>`  
  
-   `>` および `<`  
  
-   `>=` および `<=`  
  
-   `IsTrue` および `IsFalse`  
  
## <a name="data-type-restrictions"></a>データ型の制限  
 すべての演算子を定義するを定義するクラスまたは構造体を含む必要があります。 つまり、クラスまたは構造体は、次のデータ型として表示する必要があります。  
  
-   単項演算子のオペランド。  
  
-   少なくとも 1 つの二項演算子のオペランド。  
  
-   オペランドまたは変換演算子の戻り値の型。  
  
 特定の演算子がある追加のデータ型の制限を次のようにします。  
  
-   定義した場合、`IsTrue`と`IsFalse`演算子を返す必要がある両方の`Boolean`型です。  
  
-   定義した場合、`<<`と`>>`演算子、それら両方を指定してください、`Integer`の入力、`operandtype`の`operand2`します。  
  
 戻り値の型は、いずれかのオペランドの型に対応する必要はありません。 たとえば、比較演算子など`=`または`<>`返すことができます`Boolean`場合でも、どちらのオペランドは`Boolean`します。  
  
## <a name="logical-and-bitwise-operators"></a>論理/ビット処理演算子  
 `And`、 `Or`、 `Not`、および`Xor`演算子は、Visual Basic で論理またはビットごとのいずれかの操作を実行することができます。 ただし、クラスまたは構造体でこれらの演算子のいずれかを定義する場合は、そのビットごとの演算のみを定義できます。  
  
 定義することはできません、`AndAlso`と直接演算子、`Operator`ステートメントです。 ただし、使用することができます`AndAlso`場合は、次の条件を満たしていること。  
  
-   定義した`And`に使用する同じオペランドの型に`AndAlso`です。  
  
-   定義`And`を定義したクラスまたは構造体と同じ型を返します。  
  
-   定義した、`IsFalse`演算子を定義したクラスまたは構造体に`And`です。  
  
 同様に、使用することができます`OrElse`定義している場合`Or`と同じオペランド クラスや構造体の戻り値の型が定義されている`IsTrue`クラスまたは構造体にします。  
  
## <a name="widening-and-narrowing-conversions"></a>Widening and Narrowing Conversions  
 A*拡大変換*、実行時に常に成功したときに、*縮小変換*実行時に失敗することができます。 詳細については、「 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
 変換するプロシージャを宣言する場合`Widening`プロシージャのコードは、エラーを生成しないで必要があります。 これは、次のことを意味します。  
  
-   型の有効な値を返す必要が常に`type`です。  
  
-   これには、すべての例外とその他のエラー条件を処理する必要があります。  
  
-   これは、呼び出しプロシージャから返されたエラーを処理する必要があります。  
  
 変換プロシージャが成功しない可能性があります、ある可能性があるか、ハンドルされない例外が発生する可能性がありますが場合がありますを宣言する必要があります`Narrowing`です。  
  
## <a name="example"></a>例  
 次のコード例では、`Operator`ステートメントに演算子プロシージャを含む構造体の輪郭の定義を`And`、 `Or`、 `IsFalse`、および`IsTrue`演算子。 `And` および`Or`それぞれ型の 2 つのオペランドを受け取る`abc`型を返すと`abc`です。 `IsFalse` および`IsTrue`それぞれ型の 1 つのオペランドを受け取る`abc`返す`Boolean`です。 これらの定義を使用する呼び出し元のコードを許可する`And`、 `AndAlso`、 `Or`、および`OrElse`型のオペランドを持つ`abc`します。  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [IsFalse 演算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [IsTrue 演算子](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [方法 : 演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [方法 : 変換演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [方法 : 演算子プロシージャを呼び出す](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)  
 [方法: 演算子を定義するクラスを使用する](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
