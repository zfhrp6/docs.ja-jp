---
title: '方法: 拡張メソッドを呼び出す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 32691183bcd1632a82b1e9a2668790abbf8f80fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648568"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>方法: 拡張メソッドを呼び出す (Visual Basic)
拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。 拡張メソッドが宣言されており、スコープに取り込む後、は、拡張する型のインスタンス メソッドと同様に呼び出すことができます。 拡張メソッドを作成する方法の詳細については、次を参照してください。[する方法: 拡張メソッドを記述](./how-to-write-an-extension-method.md)です。  
  
 次の手順は、拡張メソッドを参照してください`PrintAndPunctuate`、2 番目のパラメーターを渡して、文字列を呼び出すインスタンス、どのような値を続けて表示される`punc`です。  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 メソッドが呼び出されるとスコープ内にある必要があります。  
  
### <a name="to-call-an-extension-method"></a>拡張メソッドを呼び出す  
  
1.  拡張メソッドの最初のパラメーターのデータ型を持つ変数を宣言します。 `PrintAndPunctuate`、する必要があります、<xref:System.String>変数。  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  変数が、拡張メソッドを呼び出し、その値が最初のパラメーターにバインドされている`aString`です。 次のステートメントの呼び出しが表示されます`Ready?`です。  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     この拡張メソッドの呼び出しは単に検索する通知などのいずれかを呼び出し、<xref:System.String>インスタンス メソッドを 1 つのパラメーターを必要とします。  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  別の文字列変数を宣言し、任意の文字列での動作を確認するには、もう一度メソッドを呼び出します。  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     この時間は、結果:`or not!!!`です。  
  
## <a name="example"></a>例  
 次のコード作成の完全な例、単純な拡張メソッドを使用します。  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports ConsoleApplication1.StringExtensions  
  
Module Module1  
  
    Sub Main()  
  
        Dim example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
        Dim example2 = "Goodbye"  
        example2.PrintAndPunctuate("?")  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
End Module  
  
' Output:  
' Hello.  
' Hello!!!!  
' Goodbye?  
```  
  
## <a name="see-also"></a>関連項目  
 [方法 : 拡張メソッドを作成する](./how-to-write-an-extension-method.md)  
 [拡張メソッド](./extension-methods.md)  
 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
