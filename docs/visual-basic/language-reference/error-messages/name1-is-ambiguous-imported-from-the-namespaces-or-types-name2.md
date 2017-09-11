---
title: "&quot;&lt;name1&gt;&quot;があいまいな名前空間または型からインポートされた&quot;&lt;name2&gt;&quot; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30561
- bc30561
dev_langs:
- VB
helpviewer_keywords:
- BC30561
ms.assetid: 761091f7-1018-4299-b481-3966a4a2c126
caps.latest.revision: 8
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
ms.openlocfilehash: 435689c201452cff2cb9b9532cd70281f3061ec9
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="39ltname1gt39-is-ambiguous-imported-from-the-namespaces-or-types-39ltname2gt39"></a><span data-ttu-id="7655b-102">'&lt;name1&gt;'があいまいな名前空間または型からインポートされた'&lt;name2&gt;'</span><span class="sxs-lookup"><span data-stu-id="7655b-102">&#39;&lt;name1&gt;&#39; is ambiguous, imported from the namespaces or types &#39;&lt;name2&gt;&#39;</span></span>
<span data-ttu-id="7655b-103">あいまいな名前を指定したため、別の名前と競合しています。</span><span class="sxs-lookup"><span data-stu-id="7655b-103">You have provided a name that is ambiguous and therefore conflicts with another name.</span></span> <span data-ttu-id="7655b-104">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]はコンパイラに競合の解決規則がありません。 自分で名前を区別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7655b-104">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler does not have any conflict resolution rules; you must disambiguate names yourself.</span></span>  
  
 <span data-ttu-id="7655b-105">**エラー ID:** BC30561</span><span class="sxs-lookup"><span data-stu-id="7655b-105">**Error ID:** BC30561</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7655b-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7655b-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="7655b-107">名前の名前空間インポートを削除することであいまいさを解消します。</span><span class="sxs-lookup"><span data-stu-id="7655b-107">Disambiguate the name by removing namespace imports.</span></span>  
  
2.  <span data-ttu-id="7655b-108">名前を完全修飾します。</span><span class="sxs-lookup"><span data-stu-id="7655b-108">Fully qualify the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7655b-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="7655b-109">See Also</span></span>  
 <span data-ttu-id="7655b-110">[Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="7655b-110">[Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="7655b-111"> [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="7655b-111"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="7655b-112"> [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)</span><span class="sxs-lookup"><span data-stu-id="7655b-112"> [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)</span></span>
