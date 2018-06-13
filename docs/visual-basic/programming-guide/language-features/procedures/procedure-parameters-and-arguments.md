---
title: プロシージャのパラメーターと引数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: b0ab186945b456d7fb4dde3f52724b08a99e2827
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652501"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>プロシージャのパラメーターと引数 (Visual Basic)
ほとんどの場合、プロシージャが呼び出されたときの状況に関する情報を必要とします。 繰り返しまたは共有のタスクを実行する手順は、呼び出しごとに異なる情報を使用します。 この情報は、変数、定数、およびメソッドを呼び出すときに、プロシージャに渡す式で構成されます。  
  
 A*パラメーター*プロシージャには、このメソッドを呼び出すときに指定することが期待される値を表します。 プロシージャの宣言では、そのパラメーターを定義します。  
  
 パラメーターを指定せず、1 つのパラメーター、または 1 つ以上を持つプロシージャを定義することができます。 パラメーターを指定するプロシージャの定義の一部と呼ばれる、*パラメーター リスト*です。  
  
 *引数*プロシージャを呼び出す場合、プロシージャのパラメーターに指定した値を表します。 呼び出し元のコードは、プロシージャを呼び出すときに、引数を指定します。 引数を指定するプロシージャ呼び出しの一部と呼ばれる、*引数リスト*です。  
  
 次の図は、プロシージャを呼び出すコード`safeSquareRoot`2 つの異なる場所からします。 最初の呼び出しは、変数の値を渡します`x`(4.0) パラメーターに`number`、され、戻り値で`root`(2.0)、変数に割り当てられた`y`です。 2 番目の呼び出しにリテラル値 9.0 に渡します`number`、戻り値 (3.0) を変数に代入し、`z`です。  
  
 ![パラメーターに引数を渡すグラフィック ダイアグラム](./media/parametersargue.gif "ParametersArgue")  
パラメーターに引数を渡す  
  
 詳細については、次を参照してください。[の相違点の間でパラメーターと引数](./differences-between-parameters-and-arguments.md)です。  
  
## <a name="parameter-data-type"></a>パラメーターのデータ型  
 使用して、パラメーターのデータ型を定義する、`As`宣言内の句。 たとえば、次の関数は、文字列と整数を受け取ります。  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 型チェック スイッチの場合 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`Off,`、`As`ことを除き、すべてのパラメーターがそれを使用する必要があります任意の 1 つのパラメーターが使用している場合は、句は省略可能です。 型チェックが場合`On`、`As`句はすべてのプロシージャのパラメーターは必須です。  
  
 呼び出し元のコードがなど、対応するパラメーターの異なるデータ型の引数を指定するかどうかは`Byte`を`String`パラメーターを次のいずれかの操作にする必要があります。  
  
-   パラメーターのデータ型に拡大変換するデータ型の引数だけを渡す  
  
-   設定`Option Strict Off`暗黙的な縮小変換です使用できるように、または。  
  
-   変換キーワードを使用して、データ型を明示的に変換します。  
  
### <a name="type-parameters"></a>型パラメーター  
 A*ジェネリック プロシージャ*も 1 つまたは複数定義されて*パラメーター入力*だけでなく、通常のパラメーターです。 ジェネリック プロシージャでは、個々 の呼び出しの要件をデータ型を調整できるように、プロシージャを呼び出すたびに異なるデータ型を渡すには、呼び出し元のコードを許可します。 「 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Function プロシージャ](./function-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [方法 : プロシージャにパラメーターを定義する](./how-to-define-a-parameter-for-a-procedure.md)  
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
