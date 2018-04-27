---
title: 基になる型&lt;typename&gt;列挙型の CLS に準拠していません
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44727a60f99e0d00cde7d569e2017928551b1812
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="b545e-102">基になる型&lt;typename&gt;列挙型の CLS に準拠していません</span><span class="sxs-lookup"><span data-stu-id="b545e-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="b545e-103">この列挙体は、指定されたデータ型の一部、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS)。</span><span class="sxs-lookup"><span data-stu-id="b545e-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="b545e-104">これは、エラーではありません、コンポーネント内であるため、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]と Visual Basic は、このデータ型をサポートします。</span><span class="sxs-lookup"><span data-stu-id="b545e-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and Visual Basic support this data type.</span></span> <span data-ttu-id="b545e-105">ただし、厳密に CLS 準拠コードで記述された別のコンポーネントがこのデータ型をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b545e-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="b545e-106">このようなコンポーネントはできないコンポーネントを正常にやり取りすることがあります。</span><span class="sxs-lookup"><span data-stu-id="b545e-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="b545e-107">次の Visual Basic データ型は CLS 準拠ではありません。</span><span class="sxs-lookup"><span data-stu-id="b545e-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="b545e-108">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="b545e-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="b545e-109">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="b545e-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="b545e-110">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="b545e-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="b545e-111">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="b545e-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="b545e-112">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="b545e-112">By default, this message is a warning.</span></span> <span data-ttu-id="b545e-113">警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="b545e-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b545e-114">**エラー ID:** BC40032</span><span class="sxs-lookup"><span data-stu-id="b545e-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b545e-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b545e-115">To correct this error</span></span>  
  
-   <span data-ttu-id="b545e-116">場合は、コンポーネントが他のインターフェイス[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]コンポーネント、またはその他のコンポーネントとやり取りしない、何も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b545e-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="b545e-117">作成されていないコンポーネントとやり取りするかどうか、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]リフレクションを判断できる場合があります、またはドキュメントを参照するかどうか、このデータ型がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b545e-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="b545e-118">その場合、何も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b545e-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="b545e-119">このデータ型をサポートしていないコンポーネントとやり取りする場合は、最も近い CLS 準拠型で置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="b545e-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="b545e-120">たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b545e-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="b545e-121">拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b545e-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="b545e-122">オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b545e-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="b545e-123">たとえば、他の多くの環境では `uint` は 16 ビットです。</span><span class="sxs-lookup"><span data-stu-id="b545e-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="b545e-124">このようなコンポーネントに 16 ビットの引数を渡す場合として宣言`UShort`の代わりに`UInteger`マネージ コードを Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="b545e-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b545e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="b545e-125">See Also</span></span>  
 [<span data-ttu-id="b545e-126">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b545e-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="b545e-127">リフレクション</span><span class="sxs-lookup"><span data-stu-id="b545e-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 
