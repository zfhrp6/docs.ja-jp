---
title: "Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30686"
  - "bc30686"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30686"
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

インターフェイスが、2 つのインターフェイスを継承しており、継承元の各インターフェイスで既定のプロパティが同じ名前で宣言されています。  修飾子を付けないと、この既定のプロパティに対するアクセスをコンパイラが解決できません。  次に例を示します。  
  
```  
Public Interface Iface1  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface2  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface3  
    Inherits Iface1, Iface2  
End Interface  
Public Class testClass  
    Public Sub accessDefaultProperty()  
        Dim testObj As Iface3  
        Dim testInt As Integer = testObj(1)  
    End Sub  
End Class  
```  
  
 `testObj(1)` と指定した場合、コンパイラは既定のプロパティに解決しようとします。  しかし、継承しているインターフェイスが原因で、既定のプロパティとして 2 つの可能性が生じます。その結果、コンパイラからこのエラーが示されます。  
  
 **Error ID:** BC30686  
  
### このエラーを解決するには  
  
-   同じ名前のメンバーを継承しないようにします。  上の例で `testObj` が、たとえば `Iface2` のメンバーである必要がない場合、次のように宣言します。  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     または  
  
-   継承しているインターフェイスをクラス内で実装します。  こうすると、継承したプロパティを別々の名前で実装できます。  ただし、実装したクラスで既定のプロパティにすることができるのは、そのうちの 1 つだけです。  次に例を示します。  
  
    ```  
    Public Class useIface3  
        Implements Iface3  
        Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop  
            ' Insert code to define Get and Set procedures for prop1.  
        End Property  
        Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop  
            ' Insert code to define Get and Set procedures for prop2.  
        End Property  
    End Class  
    ```  
  
## 参照  
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)