---
title: "方法: クエリ (LINQ) (Visual Basic) の文字列内の文字を |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dabd63e52707f3078c6cdc41db8c4f0e7dfbf70e
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="c108a-102">方法: クエリ (LINQ) (Visual Basic) の文字列内の文字</span><span class="sxs-lookup"><span data-stu-id="c108a-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="c108a-103"><xref:System.String>クラスに実装するジェネリック<xref:System.Collections.Generic.IEnumerable%601>インターフェイス、任意の文字列は、一連の文字としてクエリを実行できます</xref:System.Collections.Generic.IEnumerable%601></xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="c108a-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="c108a-104">ただし、LINQ の一般的な用途ではありません。</span><span class="sxs-lookup"><span data-stu-id="c108a-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="c108a-105">照合操作の複雑なパターンでは、<xref:System.Text.RegularExpressions.Regex>クラス</xref:System.Text.RegularExpressions.Regex>を使用してください。</span><span class="sxs-lookup"><span data-stu-id="c108a-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c108a-106">例</span><span class="sxs-lookup"><span data-stu-id="c108a-106">Example</span></span>  
 <span data-ttu-id="c108a-107">次の例では、含まれている数字の数を判断するための文字列をクエリします。</span><span class="sxs-lookup"><span data-stu-id="c108a-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="c108a-108">クエリが「再利用される」を初めて実行された後に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c108a-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="c108a-109">これは、機能は、クエリ自体で実際の結果が格納されていないので可能です。</span><span class="sxs-lookup"><span data-stu-id="c108a-109">This is possible because the query itself does not store any actual results.</span></span>  
  
<span data-ttu-id="c108a-110"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="c108a-110"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
## <a name="compiling-the-code"></a><span data-ttu-id="c108a-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c108a-111">Compiling the Code</span></span>  
 <span data-ttu-id="c108a-112">.NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c108a-112">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c108a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c108a-113">See Also</span></span>  
 <span data-ttu-id="c108a-114">[LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="c108a-114">[LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="c108a-115"> [方法: LINQ クエリは、正規表現 (Visual Basic) とを組み合わせる](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="c108a-115"> [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)</span></span>
