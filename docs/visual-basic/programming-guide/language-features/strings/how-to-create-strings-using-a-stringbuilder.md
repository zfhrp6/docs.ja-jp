---
title: '方法 : Visual Basic の StringBuilder を使用して文字列を作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 49f3271d41e9e858c6ecafe1dde5330ebff767f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647733"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="dcfe7-102">方法 : Visual Basic の StringBuilder を使用して文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="dcfe7-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="dcfe7-103">この例を使用して多数の小さな文字列から長い文字列を構築する、<xref:System.Text.StringBuilder>クラスです。</span><span class="sxs-lookup"><span data-stu-id="dcfe7-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="dcfe7-104"><xref:System.Text.StringBuilder>クラスより効率的、`&=`演算子を多数の文字列を連結する場合。</span><span class="sxs-lookup"><span data-stu-id="dcfe7-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcfe7-105">例</span><span class="sxs-lookup"><span data-stu-id="dcfe7-105">Example</span></span>  
 <span data-ttu-id="dcfe7-106">次の例のインスタンスを作成する、<xref:System.Text.StringBuilder>クラスが、そのインスタンスに 1,000 文字列を追加して、文字列形式を返します。</span><span class="sxs-lookup"><span data-stu-id="dcfe7-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dcfe7-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcfe7-107">See Also</span></span>  
 [<span data-ttu-id="dcfe7-108">StringBuilder クラスの使用</span><span class="sxs-lookup"><span data-stu-id="dcfe7-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)  
 [<span data-ttu-id="dcfe7-109">& = 演算子</span><span class="sxs-lookup"><span data-stu-id="dcfe7-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="dcfe7-110">文字列</span><span class="sxs-lookup"><span data-stu-id="dcfe7-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="dcfe7-111">新しい文字列の作成</span><span class="sxs-lookup"><span data-stu-id="dcfe7-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="dcfe7-112">文字列の操作</span><span class="sxs-lookup"><span data-stu-id="dcfe7-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)  
 <span data-ttu-id="dcfe7-113">[文字列の例](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dcfe7-113">[Strings Sample](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span></span>
