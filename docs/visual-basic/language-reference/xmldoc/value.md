---
title: "&lt;値&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a72c6330596e59d26fbae9d13f6b9c8b1987e519
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="5447b-102">&lt;値&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5447b-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="5447b-103">プロパティの説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="5447b-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5447b-104">構文</span><span class="sxs-lookup"><span data-stu-id="5447b-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5447b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5447b-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="5447b-106">プロパティの説明。</span><span class="sxs-lookup"><span data-stu-id="5447b-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5447b-107">コメント</span><span class="sxs-lookup"><span data-stu-id="5447b-107">Remarks</span></span>  
 <span data-ttu-id="5447b-108">使用して、`<value>`タグ プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5447b-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="5447b-109">Visual Studio 開発環境で、コード ウィザードを使用してプロパティを追加する場合に追加、 [\<概要 >](../../../visual-basic/language-reference/xmldoc/summary.md)新しいプロパティのタグ。</span><span class="sxs-lookup"><span data-stu-id="5447b-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="5447b-110">手動で追加する必要がありますし、`<value>`プロパティを表す値を記述するタグです。</span><span class="sxs-lookup"><span data-stu-id="5447b-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="5447b-111">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="5447b-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5447b-112">例</span><span class="sxs-lookup"><span data-stu-id="5447b-112">Example</span></span>  
 <span data-ttu-id="5447b-113">この例では、`<value>`をどのような値を記述するタグ、`Counter`プロパティを保持します。</span><span class="sxs-lookup"><span data-stu-id="5447b-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5447b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5447b-114">See Also</span></span>  
 [<span data-ttu-id="5447b-115">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="5447b-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
