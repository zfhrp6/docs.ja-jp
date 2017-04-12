---
title: "演算子プロシージャ (Visual Basic) |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- procedures, operator
- Visual Basic code, operators
- syntax, Operator procedures
- operators [Visual Basic], overloading
- overloaded operators
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
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
ms.openlocfilehash: a9e86c9c466ba236cc33153f2f341af35c622de6
ms.lasthandoff: 03/13/2017

---
# <a name="operator-procedures-visual-basic"></a>演算子プロシージャ (Visual Basic)
演算子プロシージャは、一連の[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]標準の演算子の動作を定義するステートメント (よう`*`、 `<>`、または`And`) クラスまたは定義した構造体の。 いいます*演算子のオーバー ロード*します。  
  
## <a name="when-to-define-operator-procedures"></a>演算子プロシージャを定義する場合  
 クラスまたは構造体を定義した場合は、そのクラスまたは構造体の型の変数を宣言できます。 このような変数は、式の一部として操作に参加する必要があります。 これを行うには、演算子のオペランドがあります。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]その基本的なデータ型に対してのみ演算子を定義します。 クラスまたは構造体の型の両方のオペランドまたは演算子と&1; つの動作を定義できます。  
  
 詳細については、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)します。  
  
## <a name="types-of-operator-procedure"></a>演算子プロシージャの種類  
 演算子プロシージャは、次の種類のいずれかになります。  
  
-   クラスまたは構造体の型の引数が単項演算子の定義。  
  
-   ここで、クラスまたは構造体の型の引数の少なくとも&1; つは二項演算子の定義。  
  
-   引数がクラスまたは構造体の型の変換演算子の定義。  
  
-   クラスまたは構造体の型を返す変換演算子の定義。  
  
 変換演算子は、単項演算子では常に、常に使用する`CType`として定義する演算子です。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 演算子プロシージャを宣言する構文は次のとおりです。  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 使用する、`Widening`または`Narrowing`型変換演算子でのみキーワードです。 演算子記号は常に[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)型変換演算子のです。  
  
 二項演算子を定義する&2; つのオペランドを宣言し、型変換演算子を含む、単項演算子を定義する&1; つのオペランドを宣言します。 すべてのオペランドを宣言する必要があります`ByVal`します。  
  
 各オペランドを宣言すると、同様のパラメーターを宣言する[Sub プロシージャ](./sub-procedures.md)します。  
  
### <a name="data-type"></a>データの種類  
 クラスまたは構造体を定義した演算子を定義しているために、そのクラスまたは構造体のデータ型のオペランドの少なくとも&1; つがあります。 型変換演算子のオペランドまたは戻り値の型がクラスまたは構造体のデータ型でなければなりません。  
  
 詳細については、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)します。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 演算子プロシージャは、式の中で演算子のシンボルを使用して暗黙的を呼び出します。 定義済みの演算子の場合と同じ方法で、オペランドを指定します。  
  
 演算子プロシージャへの暗黙の呼び出しの構文は次のとおりです。  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol    *  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次の構造は、上位および下位の構成要素として、128 ビットの符号付き整数値を格納します。 定義、`+`演算子を&2; つ`veryLong`値であり、その結果を生成`veryLong`値。  
  
 [!code-vb[VbVbcnProcedures 第&23;](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 次の例では、一般的な呼び出しを`+`で定義されたオペレーター`veryLong`します。  
  
 [!code-vb[VbVbcnProcedures #&24;](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 詳細と例については、次を参照してください。 [Visual Basic 2005 の演算子のオーバー ロード](http://go.microsoft.com/fwlink/?LinkId=101703)します。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [Sub プロシージャ](./sub-procedures.md)   
 [Function プロシージャ](./function-procedures.md)   
 [プロパティ プロシージャ](./property-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [方法: 演算子を定義](./how-to-define-an-operator.md)   
 [方法: 変換演算子を定義します。](./how-to-define-a-conversion-operator.md)   
 [方法: 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md)   
 [方法: 演算子を定義するクラスを使用する](./how-to-use-a-class-that-defines-operators.md)
