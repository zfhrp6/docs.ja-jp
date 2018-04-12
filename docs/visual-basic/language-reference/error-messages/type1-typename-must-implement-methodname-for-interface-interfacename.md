---
title: '&lt;type1&gt;&#39;&lt;typename&gt;&#39; する必要があります実装 &#39;&lt;methodname&gt;&#39; インターフェイス &#39;&lt;interfacename&gt;&#39;です。'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e803ec7d0054f2fa1b9ed2a731fd30c9c3060468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt;&#39; する必要があります実装 &#39;&lt;methodname&gt;&#39; インターフェイス &#39;&lt;interfacename&gt;&#39;です。
クラスまたは構造体、インターフェイスを実装する要求が、インターフェイスによって定義されたプロシージャは実装されません。 インターフェイスのすべてのメンバーを実装する必要があります。  
  
 **エラー ID:** BC30149  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  同じ名前と、インターフェイスで定義されているシグネチャを持つプロシージャを宣言します。 含めることを確認するには、少なくとも、`End Function`または`End Sub`ステートメントです。  
  
2.  追加、`Implements`句の末尾に、`Function`または`Sub`ステートメントです。 例:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
