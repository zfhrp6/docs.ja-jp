---
title: Default プロパティ アクセスは、継承されたインターフェイスのメンバー &#39; の間であいまいです。&lt;defaultpropertyname&gt;&#39;インターフェイス &#39; の;&lt;interfacename1&gt;&#39; と &#39;&lt;defaultpropertyname&gt;&#39;インターフェイス &#39; の;&lt;interfacename2&gt;&#39;です。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23d613668ee2d92484117759dd614ed2cad4bcb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a>Default プロパティ アクセスは、継承されたインターフェイスのメンバー &#39; の間であいまいです。&lt;defaultpropertyname&gt;&#39;インターフェイス &#39; の;&lt;interfacename1&gt;&#39; と &#39;&lt;defaultpropertyname&gt;&#39;インターフェイス &#39; の;&lt;interfacename2&gt;&#39;です。
インターフェイスは、同じ名前の既定のプロパティを宣言の 2 つのインターフェイスから継承します。 コンパイラは、この既定のプロパティを修飾せずに、アクセスを解決できません。 次に例を示します。  
  
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
  
 指定すると`testObj(1)`コンパイラは、既定のプロパティに解決しようとしています。 ただし、プロパティがある 2 つ可能な既定、継承されたインターフェイスのため、コンパイラは、このエラーを通知するようにします。  
  
 **エラー ID:** BC30686  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   同じ名前のメンバーを継承しないようにします。 前の例で場合`testObj`のメンバーのいずれかの必要はありません、たとえば、 `Iface2`、し、次のように宣言します。  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     または  
  
-   クラスに継承するインターフェイスを実装します。 それぞれ異なる名前を持つ継承されたプロパティを実装できます。 ただし、それらの 1 つだけでは、実装するクラスの既定のプロパティがあります。 次に例を示します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
