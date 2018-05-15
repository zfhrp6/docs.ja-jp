---
title: 既定のプロパティ&#39; &lt;propertyname1&gt; &#39;既定のプロパティと競合しています&#39; &lt;propertyname2&gt; &#39;で&#39; &lt;classname&gt; &#39;ため、宣言する必要があります&#39;シャドウ&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: b305f7a59a9865ebeb6b6f53607757b719fb4d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="e553a-102">既定のプロパティ&#39; &lt;propertyname1&gt; &#39;既定のプロパティと競合しています&#39; &lt;propertyname2&gt; &#39;で&#39; &lt;classname&gt; &#39;ため、宣言する必要があります&#39;シャドウ&#39;</span><span class="sxs-lookup"><span data-stu-id="e553a-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="e553a-103">プロパティは、基本クラスで定義されたプロパティと同じ名前で宣言されます。</span><span class="sxs-lookup"><span data-stu-id="e553a-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="e553a-104">このような状況は、このクラスのプロパティは、基底クラスのプロパティをシャドウする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e553a-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="e553a-105">このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="e553a-105">This message is a warning.</span></span> <span data-ttu-id="e553a-106">`Shadows` は、既定で指定されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="e553a-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="e553a-107">警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="e553a-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e553a-108">**エラー ID:** BC40007</span><span class="sxs-lookup"><span data-stu-id="e553a-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e553a-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e553a-109">To correct this error</span></span>  
  
-   <span data-ttu-id="e553a-110">追加、`Shadows`プロパティの名前が宣言されているキーワードを宣言、または変更します。</span><span class="sxs-lookup"><span data-stu-id="e553a-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e553a-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="e553a-111">See Also</span></span>  
 [<span data-ttu-id="e553a-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="e553a-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="e553a-113">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="e553a-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
