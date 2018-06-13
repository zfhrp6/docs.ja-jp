---
title: 属性&#39; &lt;attributename&gt; &#39;複数回適用できません
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: df97a4e391406661db98eb1c958c0e12e45b6c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584860"
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="2387e-102">属性&#39; &lt;attributename&gt; &#39;複数回適用できません</span><span class="sxs-lookup"><span data-stu-id="2387e-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="2387e-103">属性は、1 回のみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="2387e-103">The attribute can only be applied once.</span></span> <span data-ttu-id="2387e-104">`AttributeUsage`属性は属性を複数回適用できるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="2387e-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="2387e-105">**エラー ID:** BC30663</span><span class="sxs-lookup"><span data-stu-id="2387e-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2387e-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="2387e-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="2387e-107">属性は 1 回のみ適用することを確認します。</span><span class="sxs-lookup"><span data-stu-id="2387e-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="2387e-108">開発したカスタム属性を使用している場合は、変更することを検討してください、`AttributeUsage`を次の例と同様、複数の属性の使用を許可する属性。</span><span class="sxs-lookup"><span data-stu-id="2387e-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2387e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="2387e-109">See Also</span></span>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="2387e-110">カスタム属性の作成</span><span class="sxs-lookup"><span data-stu-id="2387e-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="2387e-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="2387e-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
