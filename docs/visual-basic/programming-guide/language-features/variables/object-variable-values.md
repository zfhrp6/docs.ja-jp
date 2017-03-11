---
title: "Object Variable Values (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object variables, values"
  - "values, of object variables"
  - "data types [Visual Basic], object variable"
  - "variables [Visual Basic], object"
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Object Variable Values (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) の変数は、任意の型のデータを参照できます。  `Object` 変数に格納した値はメモリ内の他の場所に保持され、変数自体はデータへのポインターを保持します。  
  
## オブジェクト分類関数  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、`Object` 変数の参照先に関する情報を返す次の表のような関数が用意されています。  
  
|Function|オブジェクト変数の参照先 \(一致する場合に True を返す\)|  
|--------------|---------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|1 つの値ではなく、値の配列|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|[Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) の値、または日付と時刻の値として解釈できる文字列|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|データが不足しているか存在しないことを表す <xref:System.DBNull> 型のオブジェクト|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<xref:System.Exception> から派生した例外オブジェクト|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|変数に現在代入されているオブジェクトがないことを表す [Nothing](../../../../visual-basic/language-reference/nothing.md)|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|数値、または数値として解釈できる文字列|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|参照型 \(文字列、配列、デリゲート、クラス型など\)|  
  
 これらの関数を使用すると、演算やプロシージャに無効な値が送られるのを防ぐことができます。  
  
## TypeOf 演算子  
 また、[TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) を使って、オブジェクト変数が現在特定のデータ型を参照しているかどうかを調べることもできます。  `TypeOf`...`Is` 式の評価は、オペランドの実行時の型が、指定した型から派生している場合または指定した型を実装している場合に `True` になります。  
  
 次の例では、値型を参照しているオブジェクト変数と参照型を参照しているオブジェクト変数に対して `TypeOf` を使用しています。  
  
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
  
 上記の例では、以下の行が**デバッグ** ウィンドウに書き込まれます。  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 オブジェクト変数 `num` が参照しているのは `Integer` 型のデータであり、`frm` が参照しているのは <xref:System.Windows.Forms.Form> クラスのオブジェクトです。  
  
## オブジェクト配列  
 `Object` 変数の配列を宣言して使用することもできます。  こうすると、さまざまなデータ型やオブジェクト クラスを扱う必要がある場合に便利です。  配列のすべての要素には、同じデータ型が宣言されている必要があります。  このデータ型を `Object` として宣言すると、その他のデータ型と共に、オブジェクトやクラス インスタンスも配列に格納できるようになります。  
  
## 参照  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [How to: Refer to the Current Instance of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)   
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)