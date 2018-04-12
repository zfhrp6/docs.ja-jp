---
title: '既定のプロパティ &#39;&lt;propertyname1&gt;&#39; 既定のプロパティ &#39; と競合しています&lt;propertyname2&gt;&#39; &#39;&lt;classname&gt;&#39; ため、宣言する必要があります (& a) #39 です。Shadows &#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="02926-102">既定のプロパティ &#39;&lt;propertyname1&gt;&#39; 既定のプロパティ &#39; と競合しています&lt;propertyname2&gt;&#39; &#39;&lt;classname&gt;&#39; ため、宣言する必要があります (& a) #39 です。Shadows &#39;</span><span class="sxs-lookup"><span data-stu-id="02926-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="02926-103">プロパティは、基本クラスで定義されたプロパティと同じ名前で宣言されます。</span><span class="sxs-lookup"><span data-stu-id="02926-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="02926-104">このような状況は、このクラスのプロパティは、基底クラスのプロパティをシャドウする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02926-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="02926-105">このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="02926-105">This message is a warning.</span></span> <span data-ttu-id="02926-106">`Shadows` は、既定で指定されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="02926-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="02926-107">警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="02926-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="02926-108">**エラー ID:** BC40007</span><span class="sxs-lookup"><span data-stu-id="02926-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="02926-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="02926-109">To correct this error</span></span>  
  
-   <span data-ttu-id="02926-110">追加、`Shadows`プロパティの名前が宣言されているキーワードを宣言、または変更します。</span><span class="sxs-lookup"><span data-stu-id="02926-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02926-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="02926-111">See Also</span></span>  
 [<span data-ttu-id="02926-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="02926-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="02926-113">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="02926-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
