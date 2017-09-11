---
title: "既定のプロパティ &quot;&lt;propertyname1&gt;&quot;既定のプロパティは&quot;&lt;propertyname2&gt;&quot;で&quot;&lt;classname&gt;&quot;、&quot;Shadows&quot; と宣言する必要があります |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
dev_langs:
- VB
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6eac9e0fdc468e27afac82a8a7c9b2251a8f7317
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="caf97-102">既定のプロパティ '&lt;propertyname1&gt;'既定のプロパティは'&lt;propertyname2&gt;'で'&lt;classname&gt;'、'Shadows' と宣言する必要があります</span><span class="sxs-lookup"><span data-stu-id="caf97-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="caf97-103">プロパティは、基本クラスで定義されたプロパティと同じ名前の宣言します。</span><span class="sxs-lookup"><span data-stu-id="caf97-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="caf97-104">このような状況でこのクラスのプロパティは、基本クラスのプロパティをシャドウする必要があります。</span><span class="sxs-lookup"><span data-stu-id="caf97-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="caf97-105">このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="caf97-105">This message is a warning.</span></span> <span data-ttu-id="caf97-106">`Shadows`既定で見なされます。</span><span class="sxs-lookup"><span data-stu-id="caf97-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="caf97-107">警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="caf97-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="caf97-108">**エラー ID:** BC40007</span><span class="sxs-lookup"><span data-stu-id="caf97-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="caf97-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="caf97-109">To correct this error</span></span>  
  
-   <span data-ttu-id="caf97-110">追加、`Shadows`プロパティの名前が宣言されるキーワードを宣言、または変更します。</span><span class="sxs-lookup"><span data-stu-id="caf97-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf97-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="caf97-111">See Also</span></span>  
 <span data-ttu-id="caf97-112">[シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="caf97-112">[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="caf97-113"> [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span><span class="sxs-lookup"><span data-stu-id="caf97-113"> [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span></span>
