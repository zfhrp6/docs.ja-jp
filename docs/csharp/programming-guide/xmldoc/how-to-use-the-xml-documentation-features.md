---
title: '方法 : XML ドキュメント機能を使用する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: d7f1f51040033cf25f7f1aefb04d249e6e028ca3
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472777"
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="d2bb4-102">方法 : XML ドキュメント機能を使用する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="d2bb4-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="d2bb4-103">次の例では、ドキュメント化された型の基本的な概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2bb4-104">例</span><span class="sxs-lookup"><span data-stu-id="d2bb4-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  

<span data-ttu-id="d2bb4-105">この例では、次の内容の .xml ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-105">The example generates an .xml file with the following contents:</span></span>

```xml  
<?xml version="1.0"?>  
<doc>  
 <assembly>  
 <name>xmlsample</name>  
 </assembly>  
 <members>  
 <member name="T:SomeClass">  
 <summary>  
 Class level summary documentation goes here.</summary>  
 <remarks>  
 Longer comments can be associated with a type or member  
 through the remarks tag</remarks>  
 </member>  
 <member name="F:SomeClass.m_Name">  
 <summary>  
 Store for the name property</summary>  
 </member>  
 <member name="M:SomeClass.#ctor">  
 <summary>The class constructor.</summary>  
 </member>  
 <member name="M:SomeClass.SomeMethod(System.String)">  
 <summary>  
 Description for SomeMethod.</summary>  
 <param name="s"> Parameter description for s goes here</param>  
 <seealso cref="T:System.String">  
 You can use the cref attribute on any tag to reference a type or member  
 and the compiler will check that the reference exists. </seealso>  
 </member>  
 <member name="M:SomeClass.SomeOtherMethod">  
 <summary>  
 Some other method. </summary>  
 <returns>  
 Return results are described through the returns tag.</returns>  
 <seealso cref="M:SomeClass.SomeMethod(System.String)">  
 Notice the use of the cref attribute to reference a specific method </seealso>  
 </member>  
 <member name="M:SomeClass.Main(System.String[])">  
 <summary>  
 The entry point for the application.  
 </summary>  
 <param name="args"> A list of command line arguments</param>  
 </member>  
 <member name="P:SomeClass.Name">  
 <summary>  
 Name property </summary>  
 <value>A value tag is used to describe the property value</value>  
 </member>  
 </members>  
</doc>   
```

## <a name="compiling-the-code"></a><span data-ttu-id="d2bb4-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d2bb4-106">Compiling the Code</span></span>  
 <span data-ttu-id="d2bb4-107">この例をコンパイルするには、次のコマンド行を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-107">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="d2bb4-108">これによって作成される XML ファイル XMLsample.xml は、ブラウザーで、または TYPE コマンドを使って、表示できます。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-108">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d2bb4-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="d2bb4-109">Robust Programming</span></span>  
 <span data-ttu-id="d2bb4-110">XML ドキュメントは、/// で始まります。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-110">XML documentation starts with ///.</span></span> <span data-ttu-id="d2bb4-111">新しいプロジェクトを作成すると、開始の /// 行がいくつか自動的に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="d2bb4-112">これらのコメントの処理にはいくつか制限があります。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="d2bb4-113">ドキュメントは整形式の XML である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="d2bb4-114">XML が整形式ではない場合は、警告が生成され、エラーが発生したことを示すコメントがドキュメント ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="d2bb4-115">開発者は、独自のタグ セットを自由に作成できます。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="d2bb4-116">推奨されるタグのセットがあります (「[ドキュメント コメントとして推奨されるタグ](recommended-tags-for-documentation-comments.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="d2bb4-117">推奨されるタグの一部には特別な意味があります。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="d2bb4-118">\<param> タグは、パラメーターの記述に使われます。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="d2bb4-119">このタグがあると、コンパイラは、パラメーターが存在すること、およびすべてのパラメーターがドキュメントで記述されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="d2bb4-120">検証で問題がある場合、コンパイラは警告を生成します。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-120">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="d2bb4-121">`cref` 属性は任意のタグにアタッチでき、コード要素への参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="d2bb4-122">コンパイラは、このコード要素が存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-122">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="d2bb4-123">検証で問題がある場合、コンパイラは警告を生成します。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="d2bb4-124">コンパイラは、`cref` 属性で記述されている型を探すとき、`using` ステートメントに従います。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="d2bb4-125">\<summary> タグは、型またはメンバーに関する追加情報を表示するために、Visual Studio の IntelliSense によって使われます。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="d2bb4-126">XML ファイルでは、型とメンバーに関する完全な情報は提供されません (たとえば、型の情報は含まれません)。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="d2bb4-127">型またはメンバーの完全な情報を取得するには、ドキュメント ファイルと併せて、実際の型またはメンバーでリフレクションを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2bb4-128">参照</span><span class="sxs-lookup"><span data-stu-id="d2bb4-128">See Also</span></span>  
 [<span data-ttu-id="d2bb4-129">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="d2bb4-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d2bb4-130">/doc (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="d2bb4-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="d2bb4-131">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="d2bb4-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
