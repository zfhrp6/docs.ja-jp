---
title: XML の使用によるコードのドキュメントの作成 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: fa642adcfea9e80b41b5fc148df2b95b8fa44d88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="43b6c-102">XML の使用によるコードのドキュメントの作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43b6c-102">Documenting Your Code with XML (Visual Basic)</span></span>
<span data-ttu-id="43b6c-103">Visual basic では XML を使用してコードを文書化することができます。</span><span class="sxs-lookup"><span data-stu-id="43b6c-103">In Visual Basic, you can document your code using XML</span></span>  
  
## <a name="xml-documentation-comments"></a><span data-ttu-id="43b6c-104">XML ドキュメントのコメント</span><span class="sxs-lookup"><span data-stu-id="43b6c-104">XML Documentation Comments</span></span>  
 <span data-ttu-id="43b6c-105">Visual Basic では、プロジェクトの XML ドキュメントを自動的に作成する簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="43b6c-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="43b6c-106">型とメンバーに対する XML スケルトンを自動的に生成し、パラメーターごとに、その他の注釈の概要、説明的なドキュメントを提供できます。</span><span class="sxs-lookup"><span data-stu-id="43b6c-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="43b6c-107">適切なセットアップでは、.xml 拡張子と、プロジェクトと同じ名前を持つ XML ファイルに XML ドキュメントが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="43b6c-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="43b6c-108">詳細については、「[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43b6c-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
 <span data-ttu-id="43b6c-109">XML ファイルを消費または XML として操作することができます。</span><span class="sxs-lookup"><span data-stu-id="43b6c-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="43b6c-110">このファイルは、プロジェクトの出力の .exe または .dll ファイルと同じディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="43b6c-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>  
  
 <span data-ttu-id="43b6c-111">XML ドキュメントの先頭`'''`です。</span><span class="sxs-lookup"><span data-stu-id="43b6c-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="43b6c-112">これらのコメントの処理にはいくつか制限があります。</span><span class="sxs-lookup"><span data-stu-id="43b6c-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="43b6c-113">ドキュメントは整形式の XML である必要があります。</span><span class="sxs-lookup"><span data-stu-id="43b6c-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="43b6c-114">場合は、XML の形式が正しくありません、警告が生成され、ドキュメント ファイルにエラーが発生したことを示すコメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="43b6c-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>  
  
-   <span data-ttu-id="43b6c-115">開発者は、独自のタグ セットを自由に作成できます。</span><span class="sxs-lookup"><span data-stu-id="43b6c-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="43b6c-116">推奨されるタグ (このトピックの「関連項目」を参照してください) 設定があります。</span><span class="sxs-lookup"><span data-stu-id="43b6c-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="43b6c-117">推奨されるタグの一部には特別な意味があります。</span><span class="sxs-lookup"><span data-stu-id="43b6c-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="43b6c-118">\<param> タグは、パラメーターの記述に使われます。</span><span class="sxs-lookup"><span data-stu-id="43b6c-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="43b6c-119">このタグがあると、コンパイラは、パラメーターが存在すること、およびすべてのパラメーターがドキュメントで記述されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="43b6c-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="43b6c-120">検証に失敗した場合、コンパイラは警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="43b6c-120">If the verification fails, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="43b6c-121">`cref` 属性は任意のタグにアタッチでき、コード要素への参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="43b6c-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="43b6c-122">コンパイラでは、このコード要素が存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="43b6c-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="43b6c-123">検証に失敗した場合、コンパイラは警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="43b6c-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="43b6c-124">コンパイラではいずれかのことも考慮`Imports`ステートメントで示される型を探すときに、`cref`属性。</span><span class="sxs-lookup"><span data-stu-id="43b6c-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="43b6c-125">\<概要 > タグを型またはメンバーに関する追加情報を表示する Visual Studio での IntelliSense によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="43b6c-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="43b6c-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="43b6c-126">Related Sections</span></span>  
 <span data-ttu-id="43b6c-127">ドキュメント コメントで、XML ファイルを作成する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="43b6c-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>  
  
-   [<span data-ttu-id="43b6c-128">/doc</span><span class="sxs-lookup"><span data-stu-id="43b6c-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [<span data-ttu-id="43b6c-129">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="43b6c-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="43b6c-130">XML ファイルの処理</span><span class="sxs-lookup"><span data-stu-id="43b6c-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="43b6c-131">方法: XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="43b6c-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [<span data-ttu-id="43b6c-132">Visual Studio の XML ツール</span><span class="sxs-lookup"><span data-stu-id="43b6c-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a><span data-ttu-id="43b6c-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="43b6c-133">See Also</span></span>  
 [<span data-ttu-id="43b6c-134">Visual Basic でのアプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="43b6c-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)  
 [<span data-ttu-id="43b6c-135">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="43b6c-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
