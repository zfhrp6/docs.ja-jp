---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39;実装する必要があります&#39; &lt;membername&gt; &#39;インターフェイスの&#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 0f93bd137bdc21268cbca139ae739843561350ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596747"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39;実装する必要があります&#39; &lt;membername&gt; &#39;インターフェイスの&#39; &lt;interfacename&gt;&#39;
'\<typename >' を実装する必要があります'\<membername >' のインターフェイス '\<interfacename >' です。 プロパティを実装する必要があります一致する 'ReadOnly' または 'WriteOnly' 指定子。  
  
 クラスまたは構造体、インターフェイスを実装する要求が、プロシージャ、プロパティ、またはインターフェイスで定義されたイベントは実装されません。 インターフェイスのすべてのメンバーを実装する必要があります。  
  
 **エラー ID:** BC30154  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  同じ名前と、インターフェイスで定義されているシグネチャを持つメンバーを宣言します。 含めることを確認するには、少なくとも、 `End Function`、 `End Sub`、または`End Property`ステートメントです。  
  
2.  追加、`Implements`句の末尾に、 `Function`、 `Sub`、 `Property`、または`Event`ステートメントです。 例えば:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  プロパティを実装するときに、以下のことを確認`ReadOnly`または`WriteOnly`は、インターフェイス定義の場合と同じ方法で使用します。  
  
4.  プロパティを実装する場合は、宣言`Get`と`Set`プロシージャに、必要に応じて。  
  
## <a name="see-also"></a>関連項目  
 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
