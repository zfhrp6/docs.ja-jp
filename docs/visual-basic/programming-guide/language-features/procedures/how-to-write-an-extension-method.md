---
title: '方法: 拡張メソッドを作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: e220a025c39757b492be033caeb8924523515804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648734"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>方法: 拡張メソッドを作成する (Visual Basic)
拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。 そのクラスのインスタンスの場合と同様、拡張メソッドを呼び出すことができます。  
  
### <a name="to-define-an-extension-method"></a>拡張メソッドを定義するには  
  
1.  Visual Studio で新規または既存の Visual Basic アプリケーションを開きます。  
  
2.  拡張メソッドを定義するファイルの上部には、次の import ステートメントを含めます。  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  新規または既存のアプリケーションでのモジュール内で拡張機能の属性を持つメソッドの定義を開始します。  
  
    ```  
    <Extension()>  
    ```  
  
4.  最初のパラメーターの型が拡張するデータ型にする必要がある点を除いて、通常の方法でメソッドを宣言します。  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>例  
 次の例は、モジュールの拡張メソッドを宣言`StringExtensions`です。 2 番目のモジュール`Module1`、インポート`StringExtensions`メソッドを呼び出します。 拡張メソッドが呼び出されるとスコープ内にある必要があります。 拡張メソッド`PrintAndPunctuate`拡張、<xref:System.String>文字列インスタンスを表示するメソッドを持つクラスが続くでパラメーターとして送信される区切り記号の文字列を指定します。  
  
```vb  
' Declarations will typically be in a separate module.  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
```vb  
' Import the module that holds the extension method you want to use,   
' and call it.  
  
Imports ConsoleApplication2.StringExtensions  
  
Module Module1  
  
    Sub Main()  
        Dim example = "Hello"  
        example.PrintAndPunctuate("?")  
        example.PrintAndPunctuate("!!!!")  
    End Sub  
  
End Module  
```  
  
 メソッドが 2 つのパラメーターで定義されているし、1 つだけ備えたと呼ばれることに注意してください。 最初のパラメーターでは、 `aString`、メソッド定義にバインドされている`example`のインスタンス`String`メソッドを呼び出します。 この例の出力は次のとおりです。  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [拡張メソッド](./extension-methods.md)  
 [Module ステートメント](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
