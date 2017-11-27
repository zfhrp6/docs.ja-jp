---
title: '&lt;seealso&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a1acbf2ee8f416e28987cc9d63dd3bf6d8c2dcf3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltseealsogt-visual-basic"></a><span data-ttu-id="23b46-102">&lt;seealso&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23b46-102">&lt;seealso&gt; (Visual Basic)</span></span>
<span data-ttu-id="23b46-103">「参照」セクションに表示されるリンクをを指定します。</span><span class="sxs-lookup"><span data-stu-id="23b46-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b46-104">構文</span><span class="sxs-lookup"><span data-stu-id="23b46-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23b46-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="23b46-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="23b46-106">現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。</span><span class="sxs-lookup"><span data-stu-id="23b46-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="23b46-107">コンパイラは、指定されたコード要素が存在し、合格ことを確認`member`出力 XML 内の要素名にします。</span><span class="sxs-lookup"><span data-stu-id="23b46-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="23b46-108">`member` は、二重引用符 (" ") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="23b46-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23b46-109">コメント</span><span class="sxs-lookup"><span data-stu-id="23b46-109">Remarks</span></span>  
 <span data-ttu-id="23b46-110">使用して、`<seealso>`タグ「参照」セクションに表示するテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="23b46-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="23b46-111">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) タグを使用すると、テキスト内からリンクを指定できます。</span><span class="sxs-lookup"><span data-stu-id="23b46-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="23b46-112">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="23b46-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23b46-113">例</span><span class="sxs-lookup"><span data-stu-id="23b46-113">Example</span></span>  
 <span data-ttu-id="23b46-114">この例では、`<seealso>`にタグを付ける、`DoesRecordExist`解説セクションを参照する、`UpdateRecord`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="23b46-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="23b46-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="23b46-115">See Also</span></span>  
 [<span data-ttu-id="23b46-116">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="23b46-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
