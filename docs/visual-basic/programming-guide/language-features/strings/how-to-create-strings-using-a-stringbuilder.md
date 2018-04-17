---
title: '方法 : Visual Basic の StringBuilder を使用して文字列を作成する'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0e15c7df07822ee104a88525c209768c05470e3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="11941-102">方法 : Visual Basic の StringBuilder を使用して文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="11941-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="11941-103">この例を使用して多数の小さな文字列から長い文字列を構築する、<xref:System.Text.StringBuilder>クラスです。</span><span class="sxs-lookup"><span data-stu-id="11941-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="11941-104"><xref:System.Text.StringBuilder>クラスより効率的、`&=`演算子を多数の文字列を連結する場合。</span><span class="sxs-lookup"><span data-stu-id="11941-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11941-105">例</span><span class="sxs-lookup"><span data-stu-id="11941-105">Example</span></span>  
 <span data-ttu-id="11941-106">次の例のインスタンスを作成する、<xref:System.Text.StringBuilder>クラスが、そのインスタンスに 1,000 文字列を追加して、文字列形式を返します。</span><span class="sxs-lookup"><span data-stu-id="11941-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="11941-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="11941-107">See Also</span></span>  
 [<span data-ttu-id="11941-108">StringBuilder クラスの使用</span><span class="sxs-lookup"><span data-stu-id="11941-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)  
 [<span data-ttu-id="11941-109">& = 演算子</span><span class="sxs-lookup"><span data-stu-id="11941-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="11941-110">文字列</span><span class="sxs-lookup"><span data-stu-id="11941-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="11941-111">新しい文字列の作成</span><span class="sxs-lookup"><span data-stu-id="11941-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="11941-112">文字列の操作</span><span class="sxs-lookup"><span data-stu-id="11941-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)  
 <span data-ttu-id="11941-113">[文字列の例](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="11941-113">[Strings Sample](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span></span>
