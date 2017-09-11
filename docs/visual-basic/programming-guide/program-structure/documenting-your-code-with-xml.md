---
title: "XML (Visual Basic) を使用してコードを文書化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML, documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0ce3f216f9e851feb0b3506b6ed1279b7d9479e7
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="6fd87-102">XML の使用によるコードのドキュメントの作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fd87-102">Documenting Your Code with XML (Visual Basic)</span></span>
<span data-ttu-id="6fd87-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML を使用してコードを文書化することができます</span><span class="sxs-lookup"><span data-stu-id="6fd87-103">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], you can document your code using XML</span></span>  
  
## <a name="xml-documentation-comments"></a><span data-ttu-id="6fd87-104">XML ドキュメントのコメント</span><span class="sxs-lookup"><span data-stu-id="6fd87-104">XML Documentation Comments</span></span>  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="6fd87-105">プロジェクトの XML ドキュメントを自動的に作成する簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="6fd87-105"> provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="6fd87-106">型とメンバーの XML スケルトンを自動的に生成し、パラメーターごとに、その他の注釈の概要、説明的なドキュメントを提供できます。</span><span class="sxs-lookup"><span data-stu-id="6fd87-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="6fd87-107">適切なセットアップは、.xml 拡張子と、プロジェクトと同じ名前の XML ファイルに XML ドキュメントが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="6fd87-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="6fd87-108">詳細については、次を参照してください。 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)します。</span><span class="sxs-lookup"><span data-stu-id="6fd87-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
 <span data-ttu-id="6fd87-109">XML ファイルを使用または XML として操作できます。</span><span class="sxs-lookup"><span data-stu-id="6fd87-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="6fd87-110">このファイルは、プロジェクトの出力 .exe または .dll ファイルと同じディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="6fd87-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>  
  
 <span data-ttu-id="6fd87-111">XML ドキュメントの先頭`'''`します。</span><span class="sxs-lookup"><span data-stu-id="6fd87-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="6fd87-112">これらのコメントの処理には、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="6fd87-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="6fd87-113">ドキュメントが整形式である XML です。</span><span class="sxs-lookup"><span data-stu-id="6fd87-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="6fd87-114">XML の形式が正しくない場合、は、警告が生成され、ドキュメント ファイルにエラーが発生したことを示すコメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6fd87-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>  
  
-   <span data-ttu-id="6fd87-115">開発者は、自由に独自のタグのセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6fd87-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="6fd87-116">推奨されるタグ (このトピックの「関連項目」を参照してください) 設定があります。</span><span class="sxs-lookup"><span data-stu-id="6fd87-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="6fd87-117">推奨されるタグの一部は、特別な意味を持っています。</span><span class="sxs-lookup"><span data-stu-id="6fd87-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="6fd87-118">\<Param > タグを使用して、パラメーターを説明します。</span><span class="sxs-lookup"><span data-stu-id="6fd87-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="6fd87-119">使用する場合、コンパイラは、パラメーターが存在して、すべてのパラメーターが、ドキュメントに記載されているを確認します。</span><span class="sxs-lookup"><span data-stu-id="6fd87-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="6fd87-120">検証に失敗した場合、コンパイラは警告を発します。</span><span class="sxs-lookup"><span data-stu-id="6fd87-120">If the verification fails, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="6fd87-121">`cref`属性は、コード要素への参照を提供する任意のタグに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="6fd87-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="6fd87-122">コンパイラは、このコード要素が存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="6fd87-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="6fd87-123">検証に失敗した場合、コンパイラは警告を発します。</span><span class="sxs-lookup"><span data-stu-id="6fd87-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="6fd87-124">コンパイラではいずれかのことも考慮`Imports`ステートメントで示される型を探すときに、`cref`属性です。</span><span class="sxs-lookup"><span data-stu-id="6fd87-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="6fd87-125">\<概要 > タグを使用してでは、IntelliSense によって[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]型またはメンバーに関する追加情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="6fd87-125">The \<summary> tag is used by IntelliSense in [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] to display additional information about a type or member.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6fd87-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fd87-126">Related Sections</span></span>  
 <span data-ttu-id="6fd87-127">ドキュメントのコメントを XML ファイルの作成方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fd87-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6fd87-128">/doc</span><span class="sxs-lookup"><span data-stu-id="6fd87-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [<span data-ttu-id="6fd87-129">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="6fd87-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="6fd87-130">XML ファイルの処理</span><span class="sxs-lookup"><span data-stu-id="6fd87-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="6fd87-131">方法: XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="6fd87-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [<span data-ttu-id="6fd87-132">Visual Studio の XML ツール</span><span class="sxs-lookup"><span data-stu-id="6fd87-132">XML Tools in Visual Studio</span></span>](https://docs.microsoft.com/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a><span data-ttu-id="6fd87-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fd87-133">See Also</span></span>  
 <span data-ttu-id="6fd87-134">[Visual Basic でのアプリケーションの開発](../../../visual-basic/developing-apps/index.md) </span><span class="sxs-lookup"><span data-stu-id="6fd87-134">[Developing Applications with Visual Basic](../../../visual-basic/developing-apps/index.md) </span></span>  
<span data-ttu-id="6fd87-135"> [Visual Basic のプログラミング ガイド](../../../visual-basic/programming-guide/index.md)</span><span class="sxs-lookup"><span data-stu-id="6fd87-135"> [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)</span></span>
