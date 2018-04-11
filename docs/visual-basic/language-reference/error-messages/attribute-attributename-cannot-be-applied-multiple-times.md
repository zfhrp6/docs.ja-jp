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
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="71440-102">属性 &#39;&lt;attributename&gt;&#39; 複数回適用できません</span><span class="sxs-lookup"><span data-stu-id="71440-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="71440-103">属性は、1 回のみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="71440-103">The attribute can only be applied once.</span></span> <span data-ttu-id="71440-104">`AttributeUsage`属性は属性を複数回適用できるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="71440-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="71440-105">**エラー ID:** BC30663</span><span class="sxs-lookup"><span data-stu-id="71440-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="71440-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="71440-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="71440-107">属性は 1 回のみ適用することを確認します。</span><span class="sxs-lookup"><span data-stu-id="71440-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="71440-108">開発したカスタム属性を使用している場合は、変更することを検討してください、`AttributeUsage`を次の例と同様、複数の属性の使用を許可する属性。</span><span class="sxs-lookup"><span data-stu-id="71440-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71440-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="71440-109">See Also</span></span>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="71440-110">カスタム属性の作成</span><span class="sxs-lookup"><span data-stu-id="71440-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="71440-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="71440-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
