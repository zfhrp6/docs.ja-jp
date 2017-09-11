---
title: "&lt;include&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- include
- <include>
dev_langs:
- CSharp
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: df0438dd742db802bb0f935d840006236d5d9bf9
ms.openlocfilehash: 0cabcc25c4e35027c600e4af2bccfad7f9db1514
ms.contentlocale: ja-jp
ms.lasthandoff: 08/29/2017

---
# <a name="ltincludegt-c-programming-guide"></a><span data-ttu-id="c81c1-102">&lt;include&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c81c1-102">&lt;include&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c81c1-103">構文</span><span class="sxs-lookup"><span data-stu-id="c81c1-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c81c1-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c81c1-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="c81c1-105">文書を含む XML ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="c81c1-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="c81c1-106">ファイル名をパスで修飾することができます。</span><span class="sxs-lookup"><span data-stu-id="c81c1-106">The file name can be qualified with a path.</span></span> <span data-ttu-id="c81c1-107">`filename` を単一引用符 (' ') で囲みます。</span><span class="sxs-lookup"><span data-stu-id="c81c1-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="c81c1-108">タグ `name` につながる `filename` 内のタグのパス。</span><span class="sxs-lookup"><span data-stu-id="c81c1-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="c81c1-109">パスを単一引用符 (' ') で囲みます。</span><span class="sxs-lookup"><span data-stu-id="c81c1-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="c81c1-110">コメントの前に配置するタグの名前指定子。`name` には `id` が指定されます。</span><span class="sxs-lookup"><span data-stu-id="c81c1-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="c81c1-111">コメントの前に配置するタグの ID。</span><span class="sxs-lookup"><span data-stu-id="c81c1-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="c81c1-112">ID は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="c81c1-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c81c1-113">コメント</span><span class="sxs-lookup"><span data-stu-id="c81c1-113">Remarks</span></span>  
 <span data-ttu-id="c81c1-114">\<include> タグを使用して、ソース コード内の型とメンバーを記述する別のファイル内のコメントを参照することができます。</span><span class="sxs-lookup"><span data-stu-id="c81c1-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="c81c1-115">これは文書化のコメントをソース コード ファイル内に直接配置する方法の代替です。</span><span class="sxs-lookup"><span data-stu-id="c81c1-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="c81c1-116">別のファイルにドキュメントを配置することで、ソース コードから分離して、ソースの制御をドキュメントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="c81c1-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="c81c1-117">1 人のユーザーがソース コード ファイルをチェックアウトし、他のユーザーがドキュメント ファイルをチェックアウトすることができます。</span><span class="sxs-lookup"><span data-stu-id="c81c1-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="c81c1-118">\<include> タグは XML XPath 構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c81c1-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="c81c1-119">\<include> の使用をカスタマイズする方法については、XPath に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c81c1-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c81c1-120">例</span><span class="sxs-lookup"><span data-stu-id="c81c1-120">Example</span></span>  
 <span data-ttu-id="c81c1-121">これは、複数ファイルの例です。</span><span class="sxs-lookup"><span data-stu-id="c81c1-121">This is a multifile example.</span></span> <span data-ttu-id="c81c1-122">\<include> を使用する最初のファイルを以下に記載します。</span><span class="sxs-lookup"><span data-stu-id="c81c1-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 <span data-ttu-id="c81c1-123">[!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c81c1-123">[!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]</span></span>  
  
 <span data-ttu-id="c81c1-124">2 番目のファイル xml_include_tag.doc には、次のドキュメントのコメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c81c1-124">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
```xml  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a><span data-ttu-id="c81c1-125">プログラムの出力</span><span class="sxs-lookup"><span data-stu-id="c81c1-125">Program Output</span></span>  
 <span data-ttu-id="c81c1-126">コマンド ライン `/doc:DocFileName.xml.` で Test および Test2 クラスをコンパイルするときに、次の出力が生成されます。Visual Studio では、プロジェクト デザイナーの [ビルド] ウィンドウで、XML ドキュメント コメントのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="c81c1-126">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="c81c1-127">C# コンパイラが \<include> タグを認識すると、現在のソース ファイルではなく xml_include_tag.doc でドキュメントのコメントを検索します。</span><span class="sxs-lookup"><span data-stu-id="c81c1-127">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="c81c1-128">コンパイラは次に、DocFileName.xml を生成します。これは、最終的なドキュメントを生成するために、[Sandcastle](https://github.com/EWSoftware/SHFB) などのドキュメント ツールによって利用されます。</span><span class="sxs-lookup"><span data-stu-id="c81c1-128">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a><span data-ttu-id="c81c1-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c81c1-129">See Also</span></span>  
 <span data-ttu-id="c81c1-130">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c81c1-130">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="c81c1-131">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="c81c1-131">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

