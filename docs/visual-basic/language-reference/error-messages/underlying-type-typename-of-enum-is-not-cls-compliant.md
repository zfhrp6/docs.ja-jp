---
title: "基になる型&lt;typename&gt;列挙型の CLS に準拠していません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords: BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6a301c06cb86a4681709fbf67d3f731e2e6a9eb
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="988b4-102">基になる型&lt;typename&gt;列挙型の CLS に準拠していません</span><span class="sxs-lookup"><span data-stu-id="988b4-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="988b4-103">この列挙体は、指定されたデータ型の一部、[言語非依存および言語非依存コンポーネント](../../../../docs/standard/language-independence-and-language-independent-components.md)(CLS)。</span><span class="sxs-lookup"><span data-stu-id="988b4-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="988b4-104">これは、エラーではありません、コンポーネント内であるため、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]と[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]このデータ型をサポートします。</span><span class="sxs-lookup"><span data-stu-id="988b4-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] support this data type.</span></span> <span data-ttu-id="988b4-105">ただし、厳密に CLS 準拠コードで記述された別のコンポーネントがこのデータ型をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="988b4-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="988b4-106">このようなコンポーネントはできないコンポーネントを正常にやり取りすることがあります。</span><span class="sxs-lookup"><span data-stu-id="988b4-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="988b4-107">次の [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] データ型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="988b4-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="988b4-108">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="988b4-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="988b4-109">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="988b4-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="988b4-110">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="988b4-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="988b4-111">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="988b4-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="988b4-112">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="988b4-112">By default, this message is a warning.</span></span> <span data-ttu-id="988b4-113">警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="988b4-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="988b4-114">**エラー ID:** BC40032</span><span class="sxs-lookup"><span data-stu-id="988b4-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="988b4-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="988b4-115">To correct this error</span></span>  
  
-   <span data-ttu-id="988b4-116">場合は、コンポーネントが他のインターフェイス[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]コンポーネント、またはその他のコンポーネントとやり取りしない、何も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="988b4-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="988b4-117">作成されていないコンポーネントとやり取りするかどうか、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]リフレクションを判断できる場合があります、またはドキュメントを参照するかどうか、このデータ型がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="988b4-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="988b4-118">その場合、何も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="988b4-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="988b4-119">このデータ型をサポートしていないコンポーネントとやり取りする場合は、最も近い CLS 準拠型で置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="988b4-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="988b4-120">たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="988b4-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="988b4-121">拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="988b4-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="988b4-122">オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="988b4-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="988b4-123">たとえば、他の多くの環境では `uint` は 16 ビットです。</span><span class="sxs-lookup"><span data-stu-id="988b4-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="988b4-124">このようなコンポーネントに 16 ビットの引数を渡す場合として宣言`UShort`の代わりに`UInteger`、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コード。</span><span class="sxs-lookup"><span data-stu-id="988b4-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="988b4-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="988b4-125">See Also</span></span>  
 [<span data-ttu-id="988b4-126">リフレクション</span><span class="sxs-lookup"><span data-stu-id="988b4-126">Reflection</span></span>](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
 [<span data-ttu-id="988b4-127">リフレクション</span><span class="sxs-lookup"><span data-stu-id="988b4-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="988b4-128">\<経由で PAVE > CLS 準拠コードの記述</span><span class="sxs-lookup"><span data-stu-id="988b4-128">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
