---
title: 型パラメーターは修飾子として使用できません。
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 563010efc4f3049d330ee2b38b7f59e23292e630
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595144"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="52707-102">型パラメーターは修飾子として使用できません。</span><span class="sxs-lookup"><span data-stu-id="52707-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="52707-103">プログラミング要素は、型パラメーターを含む修飾文字列で修飾されます。</span><span class="sxs-lookup"><span data-stu-id="52707-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="52707-104">型パラメーターでは、ジェネリック型を作成するときに指定されることのある型の要件を表します。</span><span class="sxs-lookup"><span data-stu-id="52707-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="52707-105">これには、特定の定義された型は表しません。</span><span class="sxs-lookup"><span data-stu-id="52707-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="52707-106">修飾文字列には、コンパイル時に定義されている要素のみを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="52707-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="52707-107">次のステートメントでは、このエラーが生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="52707-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="52707-108">**エラー ID:** BC32098</span><span class="sxs-lookup"><span data-stu-id="52707-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52707-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="52707-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="52707-110">修飾文字列から型パラメーターを削除するか、定義済みの型で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="52707-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2.  <span data-ttu-id="52707-111">修飾されているプログラミング要素の検索に構築された型を使用する必要がある場合は、プログラム ロジックを追加を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52707-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52707-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="52707-112">See Also</span></span>  
 [<span data-ttu-id="52707-113">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="52707-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="52707-114">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="52707-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="52707-115">型リスト</span><span class="sxs-lookup"><span data-stu-id="52707-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
