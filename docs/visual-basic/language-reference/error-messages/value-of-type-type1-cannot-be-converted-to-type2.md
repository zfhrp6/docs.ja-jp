---
title: "型 &#39; type1 &#39; の値変換できません (& a) #39; type2 &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords: BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: efa6fcd4d996fb3277cc4cac2af16a86a2d65977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a><span data-ttu-id="0dc93-102">型 &#39; type1 &#39; の値変換できません (& a) #39; type2 &#39;</span><span class="sxs-lookup"><span data-stu-id="0dc93-102">Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;</span></span>
<span data-ttu-id="0dc93-103">型 'type1' の値は、'type2' へ変換できません。</span><span class="sxs-lookup"><span data-stu-id="0dc93-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="0dc93-104">最初の要素の文字列値を取得する、'Value' プロパティを使用することができます '\<parentElement >' です。</span><span class="sxs-lookup"><span data-stu-id="0dc93-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="0dc93-105">XML リテラルを特定の型を暗黙的にキャストしようとしました。</span><span class="sxs-lookup"><span data-stu-id="0dc93-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="0dc93-106">XML リテラルは、指定した型に暗黙的にキャストできません。</span><span class="sxs-lookup"><span data-stu-id="0dc93-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="0dc93-107">**エラー ID:** BC31194</span><span class="sxs-lookup"><span data-stu-id="0dc93-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0dc93-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0dc93-108">To correct this error</span></span>  
  
-   <span data-ttu-id="0dc93-109">XML リテラルの `Value` プロパティを使用して、その値を `String`として参照します。</span><span class="sxs-lookup"><span data-stu-id="0dc93-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="0dc93-110">`CType` 関数、別の型変換関数、または <xref:System.Convert> クラスを使用して、指定した型として値をキャストします。</span><span class="sxs-lookup"><span data-stu-id="0dc93-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc93-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0dc93-111">See Also</span></span>  
 <xref:System.Convert>  
 [<span data-ttu-id="0dc93-112">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="0dc93-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="0dc93-113">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="0dc93-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="0dc93-114">XML</span><span class="sxs-lookup"><span data-stu-id="0dc93-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
