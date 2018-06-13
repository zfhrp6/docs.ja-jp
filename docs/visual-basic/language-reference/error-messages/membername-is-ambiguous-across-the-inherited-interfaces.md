---
title: '&#39;&lt;membername&gt; &#39; 、継承インターフェイス間であいまいな&#39; &lt;interfacename1&gt; &#39;と&#39; &lt;interfacename2&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 23d1a11bcee2a4faae40f2683d109d5820ee5f9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585302"
---
# <a name="39ltmembernamegt39-is-ambiguous-across-the-inherited-interfaces-39ltinterfacename1gt39-and-39ltinterfacename2gt39"></a>&#39;&lt;membername&gt; &#39; 、継承インターフェイス間であいまいな&#39; &lt;interfacename1&gt; &#39;と&#39; &lt;interfacename2&gt;&#39;
インターフェイスは、同じ名前の 2 つ以上のメンバーを複数のインターフェイスから継承します。  
  
 **エラー ID:** BC30685  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   値のキャストを使用する基本インターフェイス例えば：  
  
    ```  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
