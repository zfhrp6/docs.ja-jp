---
title: "How to: Call an Extension Method (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "calling extension methods"
  - "extension methods [Visual Basic]"
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Call an Extension Method (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。  拡張メソッドを宣言してスコープに組み入れたら、その拡張メソッドによって拡張した型のインスタンス メソッドと同じ要領で拡張メソッドを呼び出すことができます。  拡張メソッドを作成する方法の詳細については、「[How to: Write an Extension Method](../../../../visual-basic/programming-guide/language-features/procedures/how-to-write-an-extension-method.md)」を参照してください。  
  
 ここでは、拡張メソッド `PrintAndPunctuate` に関する手順を取り上げます。このメソッドの呼び出し元になる文字列インスタンスが表示されてから、2 番目のパラメーター `punc` で渡される値が表示されます。  
  
```vb#  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
  
```  
  
 メソッドを呼び出すには、そのメソッドがスコープに入っている必要があります。  
  
### 拡張メソッドを呼び出すには  
  
1.  拡張メソッドの最初のパラメーターのデータ型で変数を宣言します。  `PrintAndPunctuate` の場合は、<xref:System.String> の変数が必要です。  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  その変数が拡張メソッドを呼び出し、その変数の値が最初のパラメーター `aString` にバインドされます。  呼び出しに次のステートメントを使用すると、`Ready?` が表示されます。  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     この拡張メソッドの呼び出しは、1 つのパラメーターが必要な <xref:System.String> インスタンス メソッドの呼び出しとよく似ています。  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  もう 1 つの文字列変数を宣言し、メソッドを再び呼び出して、どの文字列でもそのメソッドが正しく動作するかどうかを確認します。  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     今回の結果は `or not!!!` です。  
  
## 使用例  
 簡単な拡張メソッドを作成して使用する完成版のコード例を以下に示します。  
  
```vb#  
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
  
## 参照  
 [How to: Write an Extension Method](../../../../visual-basic/programming-guide/language-features/procedures/how-to-write-an-extension-method.md)   
 [拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)