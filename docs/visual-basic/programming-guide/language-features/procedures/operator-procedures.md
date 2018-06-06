---
title: 演算子プロシージャ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: 5b4641ce8509e3111a11ed803d36194d5a301bce
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805712"
---
# <a name="operator-procedures-visual-basic"></a>演算子プロシージャ (Visual Basic)
演算子プロシージャは、一連の標準の演算子の動作を定義する Visual Basic ステートメント (など`*`、 `<>`、または`And`) クラスまたは定義した構造にします。 これとも呼ばれます*演算子のオーバー ロード*です。  
  
## <a name="when-to-define-operator-procedures"></a>演算子プロシージャを定義する場合  
 クラスまたは構造体を定義した場合は、そのクラスまたは構造体の型の変数を宣言できます。 このような変数は、式の一部として操作に参加する必要があります。 これを行うには、演算子のオペランドがあります。  
  
 Visual Basic では、その基本データ型でのみ演算子を定義します。 クラスまたは構造体の型は、両方のオペランドまたは演算子と 1 つの動作を定義できます。  
  
 詳細については、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)です。  
  
## <a name="types-of-operator-procedure"></a>演算子プロシージャの種類  
 演算子プロシージャには、次の種類のいずれかを指定できます。  
  
-   クラスまたは構造体の型の引数が単項演算子の定義。  
  
-   ここで、クラスまたは構造体の型の引数の少なくとも 1 つは二項演算子の定義。  
  
-   クラスまたは構造体の型の引数が変換演算子の定義。  
  
-   クラスまたは構造体の型を返す変換演算子の定義。  
  
 変換演算子は、単項では常に、常に使用する`CType`として定義する演算子です。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 演算子プロシージャを宣言する構文は次のとおりです。  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol* `(` *operand1*`[,`*operand2* `]) As`*データ型*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 使用する、`Widening`または`Narrowing`型変換演算子でのみキーワード。 演算子のシンボルは、常に[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)型変換演算子にします。  
  
 二項演算子を定義する 2 つのオペランドを宣言して、型変換演算子を含む、単項演算子を定義する 1 つのオペランドを宣言します。 すべてのオペランドを宣言する必要があります`ByVal`です。  
  
 各オペランドは同じように宣言のパラメーターを宣言する[Sub プロシージャ](./sub-procedures.md)です。  
  
### <a name="data-type"></a>データの種類  
 クラスまたは定義した構造体で演算子を定義しているために、そのクラスまたは構造体のデータ型のオペランドの少なくとも 1 つがあります。 型変換演算子のオペランドまたは戻り値の型がクラスまたは構造体のデータ型でなければなりません。  
  
 詳細については、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)です。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 演算子プロシージャは、式の中で演算子のシンボルを使用して暗黙的を呼び出します。 オペランドに演算子の定義済みの場合と同じ方法を指定します。  
  
 演算子プロシージャへの暗黙的な呼び出しの構文は次のとおりです。  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol*  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次のような構造は、構成の上位と下位の要素としては、128 ビットの符号付き整数値を格納します。 定義する、`+`を 2 つ追加する演算子`veryLong`値であり、その結果を生成`veryLong`値。  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 次の例では、一般的な呼び出しを`+`で定義されたオペレーター`veryLong`です。  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 使用例を含む詳細については、「[Visual Basic 2005 での演算子のオーバーロード](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Function プロシージャ](./function-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [方法 : 演算子を定義する](./how-to-define-an-operator.md)  
 [方法 : 変換演算子を定義する](./how-to-define-a-conversion-operator.md)  
 [方法 : 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md)  
 [方法: 演算子を定義するクラスを使用する](./how-to-use-a-class-that-defines-operators.md)
