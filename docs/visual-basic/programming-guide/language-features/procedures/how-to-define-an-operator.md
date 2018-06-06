---
title: '方法: 演算子を定義する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 1f5a020a710cecdfd8722a9fca0a8b329697eced
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805400"
---
# <a name="how-to-define-an-operator-visual-basic"></a>方法: 演算子を定義する (Visual Basic)
標準の演算子の動作を定義するクラスまたは構造体を定義している場合 (など`*`、 `<>`、または`And`) 1 つまたは両方のオペランドがクラスまたは構造体の型であるときです。  
  
 クラスまたは構造体で演算子プロシージャとして標準の演算子を定義します。 演算子のすべてのプロシージャである必要があります`Public``Shared`です。  
  
 クラスまたは構造体で演算子を定義とも呼びます*オーバー ロード*演算子。  
  
## <a name="example"></a>例  
 次の例では定義、`+`構造体の演算子と呼ばれる`height`です。 構造体は、フィートおよびインチ単位の高さを使用します。 1 つ*インチ*2.54 センチメートル、および 1 つは、 *foot* 12 インチです。 コンス トラクターを実行するのには、正規化された値 (インチ < 12.0)*剰余*12 の演算です。 `+`演算子では、コンス トラクターを使用して、正規化された値を生成します。  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 構造体をテストする`height`を次のコード。  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 使用例を含む詳細については、「[Visual Basic 2005 での演算子のオーバーロード](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [演算子プロシージャ](./operator-procedures.md)  
 [方法 : 変換演算子を定義する](./how-to-define-a-conversion-operator.md)  
 [方法 : 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md)  
 [方法: 演算子を定義するクラスを使用する](./how-to-use-a-class-that-defines-operators.md)  
 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [方法 : 構造体を宣言する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)
