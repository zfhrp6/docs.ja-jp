---
title: 識別子が長すぎます。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 10ae608903301d7e5662de3356030d682e11fd00
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="identifier-is-too-long"></a><span data-ttu-id="b37c4-102">識別子が長すぎます。</span><span class="sxs-lookup"><span data-stu-id="b37c4-102">Identifier is too long</span></span>
<span data-ttu-id="b37c4-103">名前、またはすべてのプログラミング要素の識別子は、1023 文字に制限されます。</span><span class="sxs-lookup"><span data-stu-id="b37c4-103">The name, or identifier, of every programming element is limited to 1023 characters.</span></span> <span data-ttu-id="b37c4-104">さらに、完全修飾名が 1023 文字を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="b37c4-104">In addition, a fully qualified name cannot exceed 1023 characters.</span></span> <span data-ttu-id="b37c4-105">つまり、全体の識別子の文字列 (`<namespace>.<...>.<namespace>.<class>.<element>`) 1023 を上回る文字で、メンバー アクセス演算子を含むことはできません (`.`) 文字です。</span><span class="sxs-lookup"><span data-stu-id="b37c4-105">This means that the entire identifier string (`<namespace>.<...>.<namespace>.<class>.<element>`) cannot be more than 1023 characters long, including the member-access operator (`.`) characters.</span></span>  
  
 <span data-ttu-id="b37c4-106">**エラー ID:** BC30033</span><span class="sxs-lookup"><span data-stu-id="b37c4-106">**Error ID:** BC30033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b37c4-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b37c4-107">To correct this error</span></span>  
  
-   <span data-ttu-id="b37c4-108">識別子の長さを短くします。</span><span class="sxs-lookup"><span data-stu-id="b37c4-108">Reduce the length of the identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b37c4-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="b37c4-109">See Also</span></span>  
 [<span data-ttu-id="b37c4-110">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="b37c4-110">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
