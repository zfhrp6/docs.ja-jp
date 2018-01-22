---
title: "方法 : Visual Basic の StringBuilder を使用して文字列を作成する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9def5da754d9075a8b498ac80e624caae5c97b96
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="bd0c3-102">方法 : Visual Basic の StringBuilder を使用して文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="bd0c3-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="bd0c3-103">この例を使用して多数の小さな文字列から長い文字列を構築する、<xref:System.Text.StringBuilder>クラスです。</span><span class="sxs-lookup"><span data-stu-id="bd0c3-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="bd0c3-104"><xref:System.Text.StringBuilder>クラスより効率的、`&=`演算子を多数の文字列を連結する場合。</span><span class="sxs-lookup"><span data-stu-id="bd0c3-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd0c3-105">例</span><span class="sxs-lookup"><span data-stu-id="bd0c3-105">Example</span></span>  
 <span data-ttu-id="bd0c3-106">次の例のインスタンスを作成する、<xref:System.Text.StringBuilder>クラスが、そのインスタンスに 1,000 文字列を追加して、文字列形式を返します。</span><span class="sxs-lookup"><span data-stu-id="bd0c3-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bd0c3-107">参照</span><span class="sxs-lookup"><span data-stu-id="bd0c3-107">See Also</span></span>  
 [<span data-ttu-id="bd0c3-108">StringBuilder クラスの使用</span><span class="sxs-lookup"><span data-stu-id="bd0c3-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)  
 [<span data-ttu-id="bd0c3-109">& = 演算子</span><span class="sxs-lookup"><span data-stu-id="bd0c3-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="bd0c3-110">文字列</span><span class="sxs-lookup"><span data-stu-id="bd0c3-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="bd0c3-111">新しい文字列の作成</span><span class="sxs-lookup"><span data-stu-id="bd0c3-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="bd0c3-112">文字列の操作</span><span class="sxs-lookup"><span data-stu-id="bd0c3-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)  
 [<span data-ttu-id="bd0c3-113">文字列の例</span><span class="sxs-lookup"><span data-stu-id="bd0c3-113">Strings Sample</span></span>](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)
