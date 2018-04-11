---
title: 属性 &#39;&lt;attributename&gt;&#39; 複数回適用できません
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 216cf54fd164ca95b6378517a679b5b54183559f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>属性 &#39;&lt;attributename&gt;&#39; 複数回適用できません
属性は、1 回のみ適用できます。 `AttributeUsage`属性は属性を複数回適用できるかどうかを決定します。  
  
 **エラー ID:** BC30663  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  属性は 1 回のみ適用することを確認します。  
  
2.  開発したカスタム属性を使用している場合は、変更することを検討してください、`AttributeUsage`を次の例と同様、複数の属性の使用を許可する属性。  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.AttributeUsageAttribute>  
 [カスタム属性の作成](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
