---
title: "オブジェクト変数の値 (Visual Basic) |Microsoft ドキュメント"
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
- object variables, values
- values, of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
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
ms.openlocfilehash: ff219571de9c76802d3f8d3046cf6b6f9d5be9d5
ms.lasthandoff: 03/13/2017

---
# <a name="object-variable-values-visual-basic"></a>オブジェクト変数の値 (Visual Basic)
変数、 [Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)できる任意の型のデータを参照してください。 格納した値、`Object`変数が保持される他の場所で、メモリ内一方、変数自体が、データへのポインターを保持します。  
  
## <a name="object-classifier-functions"></a>オブジェクトの分類子関数  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]内容に関する情報を返す関数が用意されて、`Object`変数は、次の表に示すように参照します。  
  
|関数|オブジェクト変数を指す場合、True を返します|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A></xref:Microsoft.VisualBasic.Information.IsArray%2A>|1 つの値ではなく、値の配列|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A></xref:Microsoft.VisualBasic.Information.IsDate%2A>|A [Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)値、または日付と時刻の値として解釈できる文字列|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A></xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|型<xref:System.DBNull>、または存在しないデータを表す</xref:System.DBNull>オブジェクト|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A></xref:Microsoft.VisualBasic.Information.IsError%2A>|派生する例外オブジェクト<xref:System.Exception></xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A></xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[何も](../../../../visual-basic/language-reference/nothing.md)、つまり、オブジェクトに現在割り当てられていない変数|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A></xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|数値、または数値として解釈できる文字列|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A></xref:Microsoft.VisualBasic.Information.IsReference%2A>|参照型 (文字列、配列、デリゲート、クラス型など)|  
  
 これらの関数を使用すると、無効な値を操作またはプロシージャの送信を回避します。  
  
## <a name="typeof-operator"></a>TypeOf 演算子  
 使用することも、 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)オブジェクト変数が現在特定のデータ型を表しているかどうかを決定します。 The `TypeOf`...`Is`式に評価される`True`オペランドの実行時の型から派生した、または指定された型を実装する場合。  
  
 次の例では使用`TypeOf`オブジェクト変数の値と参照型を参照します。  
  
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
  
 上記の例では、次の行を**デバッグ**ウィンドウ。  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 オブジェクト変数`num`型のデータを指す`Integer`、および`frm` <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form>クラスのオブジェクトを参照  
  
## <a name="object-arrays"></a>オブジェクトの配列  
 配列を宣言および使用する`Object`変数です。 これは、さまざまなデータ型とオブジェクトのクラスを処理する必要がある場合に便利です。 配列内のすべての要素には、宣言されたデータ型は同じ必要があります。 このデータ型として宣言する`Object`オブジェクトを格納し、クラスのインスタンスは、配列内の他のデータ型と並行することができます。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [方法: オブジェクトの現在のインスタンスを参照してください](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [方法: オブジェクト変数が指す型を確認](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [方法:&2; つのオブジェクトが関連するかどうかを判別します。](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [方法:&2; つのオブジェクトが同一かどうかを判断します。](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)   
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
