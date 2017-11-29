---
title: "&lt;返します&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6130a6fabe450900fe19ef4d361654508f907ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="7048d-102">&lt;返します&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7048d-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="7048d-103">プロパティまたは関数の戻り値を指定します。</span><span class="sxs-lookup"><span data-stu-id="7048d-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7048d-104">構文</span><span class="sxs-lookup"><span data-stu-id="7048d-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7048d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7048d-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="7048d-106">戻り値の説明。</span><span class="sxs-lookup"><span data-stu-id="7048d-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7048d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="7048d-107">Remarks</span></span>  
 <span data-ttu-id="7048d-108">使用して、`<returns>`タグを戻り値を記述するメソッドの宣言をコメントにします。</span><span class="sxs-lookup"><span data-stu-id="7048d-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="7048d-109">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="7048d-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7048d-110">例</span><span class="sxs-lookup"><span data-stu-id="7048d-110">Example</span></span>  
 <span data-ttu-id="7048d-111">この例では、`<returns>`何かを説明するタグ、`DoesRecordExist`関数が返される。</span><span class="sxs-lookup"><span data-stu-id="7048d-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7048d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7048d-112">See Also</span></span>  
 [<span data-ttu-id="7048d-113">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="7048d-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
