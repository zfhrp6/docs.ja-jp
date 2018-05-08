---
title: オブジェクト変数への代入 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: f20a03c4d9a0e33203629ae066686f4c9f25c105
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="object-variable-assignment-visual-basic"></a>オブジェクト変数への代入 (Visual Basic)
通常の代入ステートメントを使用して、オブジェクト変数にオブジェクトを割り当てます。 オブジェクト式を割り当てることができます、または[Nothing](../../../../visual-basic/language-reference/nothing.md)キーワードとして次の例を示しています。  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` 変数に現在割り当てられているオブジェクトが存在しないことを意味します。  
  
## <a name="initialization"></a>初期化  
 コードが実行されている変数に初期化されるオブジェクトを開始するとき`Nothing`です。 宣言には初期化が含まれているが、宣言ステートメントの実行時に指定した値に再初期化されます。  
  
 使用して、宣言で初期化を含めることができます、[新規](../../../../visual-basic/language-reference/operators/new-operator.md)キーワード。 次の宣言ステートメントは、オブジェクト変数を宣言`testUri`と`ver`しそれらに特定のオブジェクトを割り当てます。 それぞれは、オブジェクトを初期化するために、適切なクラスのオーバー ロードされたコンス トラクターのいずれかを使用します。  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>関連付けの解除  
 オブジェクト変数を設定`Nothing`と特定のオブジェクト変数の関連付けは失われます。 こうと、誤って、変数を変更することによって、オブジェクトを変更します。 次の例のように、オブジェクト変数が有効なオブジェクトをポイントするかどうかをテストすることもできます。  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 変数が参照するオブジェクトが別のアプリケーションの場合は、このテストはそのアプリケーションが終了またはだけオブジェクトを無効にするかどうかを判断できません。  
  
 オブジェクト変数の値を持つ`Nothing`とも呼びます、 *null 参照*です。  
  
## <a name="current-instance"></a>現在のインスタンス  
 *現在のインスタンス*オブジェクトのあるコードが実行されています。 プロシージャ内のすべてのコードが実行されるため、現在のインスタンスは呼び出されたプロシージャです。  
  
 `Me`キーワードは、現在のインスタンスを参照するオブジェクト変数として機能します。 プロシージャがない場合[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)、使用できる、`Me`キーワードを現在のインスタンスへのポインターを取得します。 クラスの特定のインスタンスに関連付けられている共有プロシージャは使用できません。  
  
 使用して`Me`は現在のインスタンスを別のモジュール内のプロシージャに渡すために特に便利です。 たとえば、XML ドキュメントの数があるし、それらのすべてにいくつかの標準的なテキストを追加するとします。 次の例では、これを行うプロシージャを定義します。  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 すべての XML ドキュメント オブジェクトは、プロシージャを呼び出す可能性がありますし、現在のインスタンスを引数として渡します。 次に例を示します。  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [方法: オブジェクト変数を宣言し、Visual Basic でオブジェクトを割り当てます](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [方法: オブジェクト変数がインスタンスを参照しないようにする](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
