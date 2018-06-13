---
title: '方法: オブジェクト変数で参照している型を確認する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 0dfd4ed87b65f536802ae71cbc3de41e1c4f83af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651315"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>方法: オブジェクト変数で参照している型を確認する (Visual Basic)
オブジェクト変数には、他の場所に格納されているデータへのポインターが含まれています。 実行時にそのデータの種類を変更できます。 時点で使用することができます、<xref:System.Type.GetTypeCode%2A>を現在の実行時の型を特定のメソッドまたは[TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)かどうかを現在の検索を実行時の型が、指定した型と互換性がします。  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>現在のオブジェクト変数を入力を正確なを確認するのを参照します。  
  
1.  オブジェクト変数を呼び出して、<xref:System.Object.GetType%2A>を取得する方法、<xref:System.Type?displayProperty=nameWithType>オブジェクト。  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  <xref:System.Type?displayProperty=nameWithType>クラス、共有メソッドを呼び出す<xref:System.Type.GetTypeCode%2A>を取得する、<xref:System.TypeCode>オブジェクトの種類の列挙値。  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     テストすることができます、<xref:System.TypeCode>などは、目的のどちらかの列挙体メンバーに対して列挙値`Double`です。  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>変数の型がを指定した型と互換性がオブジェクトかどうかを判断するには  
  
-   使用して、`TypeOf`演算子と組み合わせて、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)でオブジェクトをテストする、`TypeOf`しています.`Is`式。  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`しています.`Is`式を返します`True`オブジェクトのランタイム型が指定した型に互換性があります。  
  
     互換性のための基準は、指定した型がクラス、構造体、またはインターフェイスによって異なります。 一般に、型は互換性のあるオブジェクトと同じ型の継承、または指定された型を実装する場合。 詳細については、次を参照してください。 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 指定した型であることを変数または式に注意してください。 クラス、構造体、インターフェイスなど、定義された型の名前があります。 などの組み込みの型が含まれます`Integer`と`String`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
