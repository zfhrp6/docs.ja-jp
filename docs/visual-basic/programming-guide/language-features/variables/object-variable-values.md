---
title: オブジェクト変数の値 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: a5152ad0e5e5ac876783c2b191ee13e845593df8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652117"
---
# <a name="object-variable-values-visual-basic"></a>オブジェクト変数の値 (Visual Basic)
変数、[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)できる任意の型のデータを参照してください。 格納した値、`Object`変数が保持される他の場所で、メモリ内一方変数自体は、データへのポインターを保持します。  
  
## <a name="object-classifier-functions"></a>オブジェクトの分類子関数  
 Visual Basic には、新機能に関する情報を返す関数が用意されて、`Object`変数は、次の表に示すように参照します。  
  
|関数|オブジェクト変数を参照する場合は True を返します|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|1 つの値ではなく、値の配列|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|A [Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)値、または日付と時刻の値として解釈できる文字列|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|型のオブジェクト<xref:System.DBNull>、または存在しないデータを表します|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|派生する例外オブジェクト <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[何も](../../../../visual-basic/language-reference/nothing.md)、つまり、オブジェクトに現在割り当てられていない変数|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|数値、または数値として解釈できる文字列|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|参照型 (文字列、配列、デリゲート、クラス型など)|  
  
 これらの関数を使用して、操作またはプロシージャに無効な値の送信を回避することができます。  
  
## <a name="typeof-operator"></a>TypeOf 演算子  
 使用することも、 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)をオブジェクト変数が現在特定のデータ型を参照しているかどうかを判断します。 `TypeOf`しています.`Is`式に評価される`True`オペランドの実行時の型から派生した、または指定された型を実装する場合。  
  
 次の例では`TypeOf`値型と参照型を参照するオブジェクト変数です。  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 上記の例では、以下の行、**デバッグ**ウィンドウ。  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 オブジェクト変数`num`型のデータを指す`Integer`、および`frm`クラスのオブジェクトを指す<xref:System.Windows.Forms.Form>です。  
  
## <a name="object-arrays"></a>オブジェクトの配列  
 配列を宣言および使用する`Object`変数。 これは、さまざまなデータ型とオブジェクトのクラスを処理する必要がある場合に便利です。 配列内のすべての要素は同じ宣言されたデータ型が必要です。 このデータ型として宣言する`Object`オブジェクトを格納し、クラス、配列内の他のデータ型と共にインスタンスことができます。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [方法: オブジェクトの現在のインスタンスを参照する](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [方法: オブジェクト変数で参照している型を確認する](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [方法: 2 つのオブジェクトが関連しているかどうかを決める](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [方法: 2 つのオブジェクトが同一であるかどうか判別する](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
