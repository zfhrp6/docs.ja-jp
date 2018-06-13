---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39;実装する必要があります&#39; &lt;methodname&gt; &#39;インターフェイスの&#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: daeeab853f6a7f582542fa15ffc09ce749731d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594384"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39;実装する必要があります&#39; &lt;methodname&gt; &#39;インターフェイスの&#39; &lt;interfacename&gt;&#39;
クラスまたは構造体、インターフェイスを実装する要求が、インターフェイスによって定義されたプロシージャは実装されません。 インターフェイスのすべてのメンバーを実装する必要があります。  
  
 **エラー ID:** BC30149  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  同じ名前と、インターフェイスで定義されているシグネチャを持つプロシージャを宣言します。 含めることを確認するには、少なくとも、`End Function`または`End Sub`ステートメントです。  
  
2.  追加、`Implements`句の末尾に、`Function`または`Sub`ステートメントです。 例えば:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
