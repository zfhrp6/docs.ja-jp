---
title: "&lt;含める&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22eebaa8da8ef082e132cfdf8cb68498bfe16d73
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltincludegt-visual-basic"></a><span data-ttu-id="cb044-102">&lt;含める&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb044-102">&lt;include&gt; (Visual Basic)</span></span>
<span data-ttu-id="cb044-103">型と、ソース コード内のメンバーを表す別のファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="cb044-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb044-104">構文</span><span class="sxs-lookup"><span data-stu-id="cb044-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb044-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cb044-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="cb044-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="cb044-106">Required.</span></span> <span data-ttu-id="cb044-107">ドキュメントを含むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="cb044-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="cb044-108">ファイル名をパスで修飾することができます。</span><span class="sxs-lookup"><span data-stu-id="cb044-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="cb044-109">囲む`filename`を二重引用符 ("") です。</span><span class="sxs-lookup"><span data-stu-id="cb044-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="cb044-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="cb044-110">Required.</span></span> <span data-ttu-id="cb044-111">タグ `name` につながる `filename` 内のタグのパス。</span><span class="sxs-lookup"><span data-stu-id="cb044-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="cb044-112">パスを二重引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="cb044-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="cb044-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="cb044-113">Required.</span></span> <span data-ttu-id="cb044-114">コメントの前に、タグの名前指定子。</span><span class="sxs-lookup"><span data-stu-id="cb044-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="cb044-115">`Name``id`です。</span><span class="sxs-lookup"><span data-stu-id="cb044-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="cb044-116">必須です。</span><span class="sxs-lookup"><span data-stu-id="cb044-116">Required.</span></span> <span data-ttu-id="cb044-117">コメントの前に配置するタグの ID。</span><span class="sxs-lookup"><span data-stu-id="cb044-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="cb044-118">ID を単一引用符で囲みます (' ')。</span><span class="sxs-lookup"><span data-stu-id="cb044-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb044-119">コメント</span><span class="sxs-lookup"><span data-stu-id="cb044-119">Remarks</span></span>  
 <span data-ttu-id="cb044-120">使用して、`<include>`タイプを記述する別のファイル内のコメントおよびソース コード内のメンバーを参照するタグです。</span><span class="sxs-lookup"><span data-stu-id="cb044-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="cb044-121">これは文書化のコメントをソース コード ファイル内に直接配置する方法の代替です。</span><span class="sxs-lookup"><span data-stu-id="cb044-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="cb044-122">`<include>`タグは、W3C XML Path Language (XPath) Version 1.0 の推奨設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb044-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="cb044-123">カスタマイズする方法の詳細については、 `<include>` http://www.w3.org/tr/xpath 使用することはできます。</span><span class="sxs-lookup"><span data-stu-id="cb044-123">More information for ways to customize your `<include>` use is available at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb044-124">例</span><span class="sxs-lookup"><span data-stu-id="cb044-124">Example</span></span>  
 <span data-ttu-id="cb044-125">この例では、`<include>`メンバー ドキュメント コメントをという名前のファイルからインポートするタグ`commentFile.xml`です。</span><span class="sxs-lookup"><span data-stu-id="cb044-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="cb044-126">形式、`commentFile.xml`のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cb044-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb044-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb044-127">See Also</span></span>  
 [<span data-ttu-id="cb044-128">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="cb044-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
