---
title: '&lt;値&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: f33a4ec32b45d8996bd39f0cc49097b5fd9252e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602460"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="ca0b2-102">&lt;値&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca0b2-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="ca0b2-103">プロパティの説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="ca0b2-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca0b2-104">構文</span><span class="sxs-lookup"><span data-stu-id="ca0b2-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca0b2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ca0b2-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="ca0b2-106">プロパティの説明。</span><span class="sxs-lookup"><span data-stu-id="ca0b2-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca0b2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ca0b2-107">Remarks</span></span>  
 <span data-ttu-id="ca0b2-108">使用して、`<value>`タグ プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ca0b2-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="ca0b2-109">Visual Studio 開発環境で、コード ウィザードを使用してプロパティを追加する場合に追加、 [\<概要 >](../../../visual-basic/language-reference/xmldoc/summary.md)新しいプロパティのタグ。</span><span class="sxs-lookup"><span data-stu-id="ca0b2-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="ca0b2-110">手動で追加する必要がありますし、`<value>`プロパティを表す値を記述するタグです。</span><span class="sxs-lookup"><span data-stu-id="ca0b2-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="ca0b2-111">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="ca0b2-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca0b2-112">例</span><span class="sxs-lookup"><span data-stu-id="ca0b2-112">Example</span></span>  
 <span data-ttu-id="ca0b2-113">この例では、`<value>`をどのような値を記述するタグ、`Counter`プロパティを保持します。</span><span class="sxs-lookup"><span data-stu-id="ca0b2-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ca0b2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca0b2-114">See Also</span></span>  
 [<span data-ttu-id="ca0b2-115">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="ca0b2-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
