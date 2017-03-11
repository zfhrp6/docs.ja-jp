---
title: "Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30369"
  - "bc30369"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Shared"
  - "BC30369"
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

共有プロシージャの内部から、クラスの非共有メンバーを参照しようとしています。  次のコードは、この状態を示す例です。  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 この例では、`x = 10` の代入ステートメントにより、このエラー メッセージが表示されます。  これは、共有プロシージャがインスタンス変数にアクセスしようとしているからです。  
  
 変数 `x` は、[Shared](../../../visual-basic/language-reference/modifiers/shared.md) として宣言されていないためインスタンス メンバーです。  `sample` クラスの各インスタンスに、独自の変数 `x` が個別に含まれています。  1 つのインスタンスで `x` に値を設定したり、この値を変更したりしても、他の各インスタンスにある `x` の値は変わりません。  
  
 一方、`setX` プロシージャは、`sample` クラスの全インスタンスで `Shared` されています。  これは、クラスの特定のインスタンスに関連付けられているわけではなく、操作がインスタンスごとに独立して行われることを意味します。  特定のインスタンスとの関係がないため、`setX` はインスタンス変数にアクセスできません。  `Shared` 変数のみを操作できます。  `setX` で共有変数に値を設定するか、この値を変更した場合、このクラスのすべてのインスタンスで変更後の値が利用できます。  
  
 **Error ID:** BC30369  
  
### このエラーを解決するには  
  
1.  このメンバーを、クラスのすべてのインスタンスで共有するのか、インスタンスごとに保持するのかを決定します。  
  
2.  メンバーの実体を 1 つだけ作成して、すべてのインスタンスで共有する場合は、メンバー宣言に `Shared` キーワードを追加します。  プロシージャ宣言に `Shared` キーワードを含めます。  
  
3.  インスタンスごとにメンバーの実体を独自に作成する場合は、メンバー宣言に `Shared` を指定しないでください。  プロシージャ宣言から `Shared` キーワードを削除します。  
  
## 参照  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)