---
title: "メンバーの型 &quot;&lt;membername&gt;&quot; CLS 準拠ではありません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40025
- vbc40025
dev_langs:
- VB
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: 14
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
ms.openlocfilehash: ab4d0936603ae133bd7def4341f29d5fcdf7188b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a><span data-ttu-id="a660e-102">メンバーの型 '&lt;membername&gt;' CLS 準拠ではありません</span><span class="sxs-lookup"><span data-stu-id="a660e-102">Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="a660e-103">このメンバーに指定されたデータ型の一部では、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS に) します。</span><span class="sxs-lookup"><span data-stu-id="a660e-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span> <span data-ttu-id="a660e-104">これはないため、エラー、コンポーネント内で、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]と[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]このデータ型をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a660e-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] and [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] support this data type.</span></span> <span data-ttu-id="a660e-105">ただし、厳密に CLS 準拠のコードで記述された別のコンポーネントでは、このデータ型がサポートしない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a660e-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="a660e-106">このようなコンポーネントは、コンポーネントと正常にやり取りできません可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a660e-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="a660e-107">次の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] データ型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="a660e-107">The following [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="a660e-108">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="a660e-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="a660e-109">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="a660e-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="a660e-110">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="a660e-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="a660e-111">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="a660e-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="a660e-112">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="a660e-112">By default, this message is a warning.</span></span> <span data-ttu-id="a660e-113">警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="a660e-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a660e-114">**エラー ID:** BC40025</span><span class="sxs-lookup"><span data-stu-id="a660e-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a660e-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a660e-115">To correct this error</span></span>  
  
-   <span data-ttu-id="a660e-116">他のコンポーネントの場合[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]コンポーネント、またはその他のコンポーネントとやり取りしない、何も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a660e-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="a660e-117">作成されていないコンポーネントとやり取りするかどうか、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リフレクションを決定することができます、またはドキュメントを参照するかどうか、このデータ型がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a660e-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="a660e-118">その場合は、何も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a660e-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="a660e-119">このデータ型をサポートしていないコンポーネントとやり取りする場合は、CLS 準拠で最も近い型を置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="a660e-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="a660e-120">たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a660e-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="a660e-121">拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a660e-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="a660e-122">オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a660e-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="a660e-123">たとえば、他の多くの環境では `uint` は 16 ビットです。</span><span class="sxs-lookup"><span data-stu-id="a660e-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="a660e-124">このようなコンポーネントに 16 ビットの引数を渡す場合として宣言`UShort`の代わりに`UInteger`、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コードです。</span><span class="sxs-lookup"><span data-stu-id="a660e-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a660e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a660e-125">See Also</span></span>  
 <span data-ttu-id="a660e-126">[リフレクション](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775) </span><span class="sxs-lookup"><span data-stu-id="a660e-126">[Reflection](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775) </span></span>  
<span data-ttu-id="a660e-127"> [\<経由で PAVE > CLS 準拠のコードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="a660e-127"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>
