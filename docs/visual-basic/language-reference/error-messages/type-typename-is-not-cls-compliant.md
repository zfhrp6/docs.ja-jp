---
title: "型&lt;typename&gt; CLS 準拠ではありません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
dev_langs:
- VB
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 7
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
ms.openlocfilehash: a8d65568e862c941d5b927582833dff803219bf9
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="0864e-102">型&lt;typename&gt; CLS 準拠ではありません</span><span class="sxs-lookup"><span data-stu-id="0864e-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="0864e-103">変数、プロパティ、または関数の戻り値は、CLS 準拠ではないデータ型で宣言します。</span><span class="sxs-lookup"><span data-stu-id="0864e-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="0864e-104">アプリケーションに対応しているが、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) には、CLS 準拠型のみを使用して必要があります。</span><span class="sxs-lookup"><span data-stu-id="0864e-104">For an application to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="0864e-105">次の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] データ型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="0864e-105">The following [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="0864e-106">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="0864e-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="0864e-107">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="0864e-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="0864e-108">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="0864e-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="0864e-109">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="0864e-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="0864e-110">**エラー ID:** BC40041</span><span class="sxs-lookup"><span data-stu-id="0864e-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0864e-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0864e-111">To correct this error</span></span>  
  
-   <span data-ttu-id="0864e-112">アプリケーションは、CLS に準拠する必要がある、最も近い CLS 準拠型にこの要素のデータ型を変更します。</span><span class="sxs-lookup"><span data-stu-id="0864e-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="0864e-113">たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0864e-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="0864e-114">拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0864e-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="0864e-115">アプリケーションが CLS に準拠する必要がない場合は、何も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0864e-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="0864e-116">必ず、非準拠に注意してくださいただしください。</span><span class="sxs-lookup"><span data-stu-id="0864e-116">You should be aware of its noncompliance, however.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0864e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0864e-117">See Also</span></span>  
 [<span data-ttu-id="0864e-118">\<経由で PAVE > CLS 準拠のコードの記述</span><span class="sxs-lookup"><span data-stu-id="0864e-118">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
