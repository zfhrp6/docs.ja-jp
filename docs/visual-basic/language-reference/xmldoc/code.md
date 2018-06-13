---
title: '&lt;コード&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 9ec9d23f1f62358dc272f9764f88e3bb2ba41f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599753"
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="2ee05-102">&lt;コード&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ee05-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="2ee05-103">テキストが複数行のコードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="2ee05-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee05-104">構文</span><span class="sxs-lookup"><span data-stu-id="2ee05-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ee05-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2ee05-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="2ee05-106">コードとしてマークするテキストです。</span><span class="sxs-lookup"><span data-stu-id="2ee05-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ee05-107">コメント</span><span class="sxs-lookup"><span data-stu-id="2ee05-107">Remarks</span></span>  
 <span data-ttu-id="2ee05-108">使用して、`<code>`タグ コードとして複数の行を指定します。</span><span class="sxs-lookup"><span data-stu-id="2ee05-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="2ee05-109">説明内のテキストをコードとしてマークする場合は、[\<c](../../../visual-basic/language-reference/xmldoc/c.md) タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="2ee05-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="2ee05-110">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="2ee05-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ee05-111">例</span><span class="sxs-lookup"><span data-stu-id="2ee05-111">Example</span></span>  
 <span data-ttu-id="2ee05-112">この例では、\<コード > タグを使用するためのサンプル コードを`ID`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="2ee05-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2ee05-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ee05-113">See Also</span></span>  
 [<span data-ttu-id="2ee05-114">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="2ee05-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
