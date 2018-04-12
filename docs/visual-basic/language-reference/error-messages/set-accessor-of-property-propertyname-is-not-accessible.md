---
title: '&#39;です。セット &#39;プロパティ &#39; アクセサー&lt;propertyname&gt;&#39; にアクセスできません'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9256a09b719ad3890e1d7c2cc23ffb0d40eec62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="97979-102">&#39;です。セット &#39;プロパティ &#39; アクセサー&lt;propertyname&gt;&#39; にアクセスできません</span><span class="sxs-lookup"><span data-stu-id="97979-102">&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="97979-103">ステートメントが、プロパティへのアクセスがあるないときに、プロパティの値を格納しようとしています。`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="97979-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="97979-104">場合、 [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)でマークされているより制限の厳しいアクセス レベルよりもその[Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)、次の場合、プロパティ値を設定しようとするが失敗します。</span><span class="sxs-lookup"><span data-stu-id="97979-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="97979-105">`Set`ステートメントがマークされている[プライベート](../../../visual-basic/language-reference/modifiers/private.md)し、呼び出し元のコードがクラスまたはプロパティが定義されている構造体の範囲外です。</span><span class="sxs-lookup"><span data-stu-id="97979-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="97979-106">`Set`ステートメントがマークされている[Protected](../../../visual-basic/language-reference/modifiers/protected.md)呼び出し元のコードは、派生クラスでないか、クラスまたはプロパティが定義されている構造体ではなくとします。</span><span class="sxs-lookup"><span data-stu-id="97979-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="97979-107">`Set`ステートメントがマークされている[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)し、呼び出し元のコードは、プロパティが定義されている同じアセンブリに含まれない。</span><span class="sxs-lookup"><span data-stu-id="97979-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="97979-108">**エラー ID:** BC31102</span><span class="sxs-lookup"><span data-stu-id="97979-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97979-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="97979-109">To correct this error</span></span>  
  
-   <span data-ttu-id="97979-110">プロパティが定義されたソース コードを使っている場合を宣言することを検討してください、`Set`プロパティ自体と同じアクセス レベルを持つプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="97979-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="97979-111">プロパティを定義するソース コードがないか、または制限する必要がある場合、`Set`プロシージャに簡単にアクセスのあるコード領域にプロパティの値を設定するコードを移動しようとしている、プロパティ自体には、複数のレベルにアクセスしますプロパティ。</span><span class="sxs-lookup"><span data-stu-id="97979-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97979-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="97979-112">See Also</span></span>  
 [<span data-ttu-id="97979-113">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="97979-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="97979-114">方法 : 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="97979-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
