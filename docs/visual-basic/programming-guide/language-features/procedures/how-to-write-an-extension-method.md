---
title: "How to: Write an Extension Method (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "extending data types"
  - "writing extension methods"
  - "extension methods [Visual Basic]"
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Write an Extension Method (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。  拡張メソッドは、そのクラスのインスタンスの場合と同じ要領で呼び出すことができます。  
  
### 拡張メソッドを定義するには  
  
1.  Visual Studio で新規または既存の Visual Basic アプリケーションを開きます。  
  
2.  拡張メソッドを定義するファイルの先頭に、次のインポート ステートメントを記述します。  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  新規または既存のアプリケーションのモジュールで、拡張属性を指定してメソッド定義を開始します。  
  
    ```  
    <Extension()>  
    ```  
  
4.  通常の方法でメソッドを宣言します。ただし、最初のパラメーターの型は、拡張するデータ型に設定する必要があります。  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## 使用例  
 モジュール `StringExtensions` で拡張メソッドを宣言する例を次に示します。  2 番目のモジュール `Module1` では、`StringExtensions` をインポートして、メソッドを呼び出します。  拡張メソッドを呼び出すときには、拡張メソッドがスコープの中に入っていなければなりません。  拡張メソッド `PrintAndPunctuate` は、文字列インスタンスと、パラメーターとして渡す区切り記号の文字列を表示するメソッドによって、<xref:System.String> クラスを拡張しています。  
  
```vb#  
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
  
```vb#  
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
  
 このメソッドでは 2 つのパラメーターを定義していますが、呼び出し時には 1 つしか指定していません。  メソッド定義の最初のパラメーター `aString` は、そのメソッドを呼び出す `String` のインスタンスである `example` にバインドされています。  この例の出力は次のようになります。  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## 参照  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)