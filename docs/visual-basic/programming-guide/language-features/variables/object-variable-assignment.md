---
title: "Object Variable Assignment (Visual Basic) | Microsoft Docs"
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
  - "Nothing keyword, object variable assignment"
  - "object variables, initializing"
  - "variables [Visual Basic], initializing"
  - "objects [Visual Basic], current instance"
  - "object variables, assigning"
  - "variables [Visual Basic], object variables"
  - "current instance, defined"
  - "variables [Visual Basic], assigning"
  - "assignment statements, object variable assignment"
  - "Me keyword, as object variable"
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Object Variable Assignment (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

オブジェクト変数にオブジェクトを代入するには、通常の代入ステートメントを使用します。  次に示す例のように、オブジェクト式または [Nothing](../../../../visual-basic/language-reference/nothing.md) キーワードを代入できます。  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` は、変数に現在代入されているオブジェクトがないことを表します。  
  
## 初期化  
 コードが実行を開始すると、オブジェクト変数は `Nothing` に初期化されます。  宣言に初期化が含まれている場合は、この宣言ステートメントが実行されるたびに、指定した値に再初期化されます。  
  
 [New](../../../../visual-basic/language-reference/operators/new-operator.md) キーワードを使用すると、宣言に初期化を含めることができます。  次に示す宣言ステートメントは、オブジェクト変数 `testUri` と `ver` を宣言し、特定のオブジェクトを代入します。  それぞれ適切なクラスのオーバーロードされたコンストラクターのいずれか 1 つを使用してオブジェクトを初期化します。  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## 関連付けの解除  
 オブジェクト変数を `Nothing` に設定すると、変数と特定のオブジェクトとの関連付けは失われます。  このため、変数を変更するときに誤ってオブジェクトを変更してしまうことがなくなります。  また、次の例のように、オブジェクト変数が有効なオブジェクトを指しているかどうかをテストすることもできます。  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 変数が他のアプリケーションのオブジェクトを参照している場合は、アプリケーションが終了されているのか、単にオブジェクトが無効になっているのかをこのテストで調べることはできません。  
  
 値が `Nothing` のオブジェクト変数は、*null 参照*とも呼ばれます。  
  
## 現在のインスタンス  
 オブジェクトの*現在のインスタンス*とは、その内部で現在コードが実行されているインスタンスです。  すべてのコードはプロシージャ内で実行されるため、現在のインスタンスは、呼び出されたプロシージャでのインスタンスになります。  
  
 `Me` キーワードは、現在のインスタンスを参照するオブジェクト変数として機能します。  プロシージャが [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) でない場合は、`Me` キーワードを使って現在のインスタンスへのポインターを取得できます。  共有プロシージャをクラスの特定のインスタンスに関連付けることはできません。  
  
 `Me` キーワードは、他のモジュールのプロシージャに現在のインスタンスを渡す場合に特に便利です。  たとえば、多数の XML ドキュメントがあり、標準テキストをそれらすべてに追加するとします。  これを実行するプロシージャを定義する例を次に示します。  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 次に、この定義したプロシージャをすべての XML ドキュメント オブジェクトで呼び出し、引数として現在のインスタンスを渡します。  次に例を示します。  
  
```  
addStandardText(Me)  
```  
  
## 参照  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Declare an Object Variable and Assign an Object to It in Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)   
 [How to: Make an Object Variable Not Refer to Any Instance](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)