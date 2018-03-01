---
title: "型&lt;typename&gt; CLS 準拠ではありません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36a49ccf7d2185c26ef8d23eebea216cc193d951
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="45eb7-102">型&lt;typename&gt; CLS 準拠ではありません</span><span class="sxs-lookup"><span data-stu-id="45eb7-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="45eb7-103">変数、プロパティ、または関数の戻り値は、CLS 準拠ではないデータ型で宣言します。</span><span class="sxs-lookup"><span data-stu-id="45eb7-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="45eb7-104">準拠するアプリケーションの[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)CLS 準拠型のみを使用して必要があります (CLS) にします。</span><span class="sxs-lookup"><span data-stu-id="45eb7-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="45eb7-105">次の [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] データ型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="45eb7-105">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="45eb7-106">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="45eb7-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="45eb7-107">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="45eb7-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="45eb7-108">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="45eb7-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="45eb7-109">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="45eb7-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="45eb7-110">**エラー ID:** BC40041</span><span class="sxs-lookup"><span data-stu-id="45eb7-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="45eb7-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="45eb7-111">To correct this error</span></span>  
  
-   <span data-ttu-id="45eb7-112">場合は、アプリケーションは、CLS に準拠する必要がある、この要素のデータ型を最も近い CLS 準拠型に変更します。</span><span class="sxs-lookup"><span data-stu-id="45eb7-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="45eb7-113">たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="45eb7-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="45eb7-114">拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="45eb7-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="45eb7-115">アプリケーションが CLS に準拠させる必要がない場合は、何も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="45eb7-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="45eb7-116">注意してください、コンプライアンス非対応のただしです。</span><span class="sxs-lookup"><span data-stu-id="45eb7-116">You should be aware of its noncompliance, however.</span></span>