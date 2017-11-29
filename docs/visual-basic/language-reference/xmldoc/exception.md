---
title: "&lt;例外&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d718a7c2213a61f7f60ed80a04f9bd03f6c770a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="4cdd7-102">&lt;例外&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cdd7-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="4cdd7-103">どの例外がスローされる可能性を指定します。</span><span class="sxs-lookup"><span data-stu-id="4cdd7-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cdd7-104">構文</span><span class="sxs-lookup"><span data-stu-id="4cdd7-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cdd7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4cdd7-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="4cdd7-106">現在のコンパイル環境から使用できる例外の参照。</span><span class="sxs-lookup"><span data-stu-id="4cdd7-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="4cdd7-107">コンパイラは、指定された例外が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4cdd7-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="4cdd7-108">`member` は、二重引用符 (" ") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cdd7-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="4cdd7-109">説明です。</span><span class="sxs-lookup"><span data-stu-id="4cdd7-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cdd7-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4cdd7-110">Remarks</span></span>  
 <span data-ttu-id="4cdd7-111">使用して、`<exception>`タグをどの例外をスローするを指定します。</span><span class="sxs-lookup"><span data-stu-id="4cdd7-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="4cdd7-112">このタグは、メソッドの定義に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4cdd7-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="4cdd7-113">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="4cdd7-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cdd7-114">例</span><span class="sxs-lookup"><span data-stu-id="4cdd7-114">Example</span></span>  
 <span data-ttu-id="4cdd7-115">この例では、`<exception>`例外を記述するタグを`IntDivide`関数がスローすることができます。</span><span class="sxs-lookup"><span data-stu-id="4cdd7-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4cdd7-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cdd7-116">See Also</span></span>  
 [<span data-ttu-id="4cdd7-117">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="4cdd7-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
