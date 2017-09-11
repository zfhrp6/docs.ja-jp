---
title: "方法 : XML ドキュメント機能を使用する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eeee77db523bc0ad97f425d4ba8076ae5740dfe8
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="b4165-102">方法 : XML ドキュメント機能を使用する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b4165-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="b4165-103">次の例では、ドキュメント化された型の基本的な概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="b4165-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4165-104">例</span><span class="sxs-lookup"><span data-stu-id="b4165-104">Example</span></span>  
 <span data-ttu-id="b4165-105">[!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b4165-105">[!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]</span></span>  
  
 <span data-ttu-id="b4165-106">**// この .xml ファイルは、上記のコード サンプルで生成されました。**</span><span class="sxs-lookup"><span data-stu-id="b4165-106">**// This .xml file was generated with the previous code sample.**</span></span>  
<span data-ttu-id="b4165-107">**\<?xml version="1.0"?>**</span><span class="sxs-lookup"><span data-stu-id="b4165-107">**\<?xml version="1.0"?>**</span></span>  
<span data-ttu-id="b4165-108">**\<doc>**</span><span class="sxs-lookup"><span data-stu-id="b4165-108">**\<doc>**</span></span>  
 <span data-ttu-id="b4165-109">**\<assembly>**</span><span class="sxs-lookup"><span data-stu-id="b4165-109">**\<assembly>**</span></span>  
 <span data-ttu-id="b4165-110">**\<name>xmlsample\</name>**</span><span class="sxs-lookup"><span data-stu-id="b4165-110">**\<name>xmlsample\</name>**</span></span>  
 <span data-ttu-id="b4165-111">**\</assembly>**</span><span class="sxs-lookup"><span data-stu-id="b4165-111">**\</assembly>**</span></span>  
 <span data-ttu-id="b4165-112">**\<members>**</span><span class="sxs-lookup"><span data-stu-id="b4165-112">**\<members>**</span></span>  
 <span data-ttu-id="b4165-113">**\<member name="T:SomeClass">**</span><span class="sxs-lookup"><span data-stu-id="b4165-113">**\<member name="T:SomeClass">**</span></span>  
 <span data-ttu-id="b4165-114">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-114">**\<summary>**</span></span>  
 <span data-ttu-id="b4165-115">**Class level summary documentation goes here.\</summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-115">**Class level summary documentation goes here.\</summary>**</span></span>  
 <span data-ttu-id="b4165-116">**\<remarks>**</span><span class="sxs-lookup"><span data-stu-id="b4165-116">**\<remarks>**</span></span>  
 <span data-ttu-id="b4165-117">**Longer comments can be associated with a type or member** </span><span class="sxs-lookup"><span data-stu-id="b4165-117">**Longer comments can be associated with a type or member** </span></span>  
 <span data-ttu-id="b4165-118">**through the remarks tag\</remarks>**</span><span class="sxs-lookup"><span data-stu-id="b4165-118">**through the remarks tag\</remarks>**</span></span>  
 <span data-ttu-id="b4165-119">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b4165-119">**\</member>**</span></span>  
 <span data-ttu-id="b4165-120">**\<member name="F:SomeClass.m_Name">**</span><span class="sxs-lookup"><span data-stu-id="b4165-120">**\<member name="F:SomeClass.m_Name">**</span></span>  
 <span data-ttu-id="b4165-121">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-121">**\<summary>**</span></span>  
 <span data-ttu-id="b4165-122">**Store for the name property\</summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-122">**Store for the name property\</summary>**</span></span>  
 <span data-ttu-id="b4165-123">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b4165-123">**\</member>**</span></span>  
 <span data-ttu-id="b4165-124">**\<member name="M:SomeClass.#ctor">**</span><span class="sxs-lookup"><span data-stu-id="b4165-124">**\<member name="M:SomeClass.#ctor">**</span></span>  
 <span data-ttu-id="b4165-125">**\<summary>The class constructor.\</summary>** </span><span class="sxs-lookup"><span data-stu-id="b4165-125">**\<summary>The class constructor.\</summary>** </span></span>  
 <span data-ttu-id="b4165-126">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b4165-126">**\</member>**</span></span>  
 <span data-ttu-id="b4165-127">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="b4165-127">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="b4165-128">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-128">**\<summary>**</span></span>  
 <span data-ttu-id="b4165-129">**Description for SomeMethod.\</summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-129">**Description for SomeMethod.\</summary>**</span></span>  
 <span data-ttu-id="b4165-130">**\<param name="s"> Parameter description for s goes here\</param>**</span><span class="sxs-lookup"><span data-stu-id="b4165-130">**\<param name="s"> Parameter description for s goes here\</param>**</span></span>  
 <span data-ttu-id="b4165-131">**\<seealso cref="T:System.String">**</span><span class="sxs-lookup"><span data-stu-id="b4165-131">**\<seealso cref="T:System.String">**</span></span>  
 <span data-ttu-id="b4165-132">**You can use the cref attribute on any tag to reference a type or member** </span><span class="sxs-lookup"><span data-stu-id="b4165-132">**You can use the cref attribute on any tag to reference a type or member** </span></span>  
 <span data-ttu-id="b4165-133">**and the compiler will check that the reference exists. \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="b4165-133">**and the compiler will check that the reference exists. \</seealso>**</span></span>  
 <span data-ttu-id="b4165-134">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b4165-134">**\</member>**</span></span>  
 <span data-ttu-id="b4165-135">**\<member name="M:SomeClass.SomeOtherMethod">**</span><span class="sxs-lookup"><span data-stu-id="b4165-135">**\<member name="M:SomeClass.SomeOtherMethod">**</span></span>  
 <span data-ttu-id="b4165-136">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-136">**\<summary>**</span></span>  
 <span data-ttu-id="b4165-137">**Some other method. \</summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-137">**Some other method. \</summary>**</span></span>  
 <span data-ttu-id="b4165-138">**\<returns>**</span><span class="sxs-lookup"><span data-stu-id="b4165-138">**\<returns>**</span></span>  
 <span data-ttu-id="b4165-139">**Return results are described through the returns tag.\</returns>**</span><span class="sxs-lookup"><span data-stu-id="b4165-139">**Return results are described through the returns tag.\</returns>**</span></span>  
 <span data-ttu-id="b4165-140">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="b4165-140">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="b4165-141">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="b4165-141">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span></span>  
 <span data-ttu-id="b4165-142">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b4165-142">**\</member>**</span></span>  
 <span data-ttu-id="b4165-143">**\<member name="M:SomeClass.Main(System.String[])">**</span><span class="sxs-lookup"><span data-stu-id="b4165-143">**\<member name="M:SomeClass.Main(System.String[])">**</span></span>  
 <span data-ttu-id="b4165-144">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-144">**\<summary>**</span></span>  
 <span data-ttu-id="b4165-145">**The entry point for the application.**</span><span class="sxs-lookup"><span data-stu-id="b4165-145">**The entry point for the application.**</span></span>  
 <span data-ttu-id="b4165-146">**\</summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-146">**\</summary>**</span></span>  
 <span data-ttu-id="b4165-147">**\<param name="args"> A list of command line arguments\</param>**</span><span class="sxs-lookup"><span data-stu-id="b4165-147">**\<param name="args"> A list of command line arguments\</param>**</span></span>  
 <span data-ttu-id="b4165-148">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b4165-148">**\</member>**</span></span>  
 <span data-ttu-id="b4165-149">**\<member name="P:SomeClass.Name">**</span><span class="sxs-lookup"><span data-stu-id="b4165-149">**\<member name="P:SomeClass.Name">**</span></span>  
 <span data-ttu-id="b4165-150">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-150">**\<summary>**</span></span>  
 <span data-ttu-id="b4165-151">**Name property \</summary>**</span><span class="sxs-lookup"><span data-stu-id="b4165-151">**Name property \</summary>**</span></span>  
 <span data-ttu-id="b4165-152">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="b4165-152">**\<value>**</span></span>  
 <span data-ttu-id="b4165-153">**A value tag is used to describe the property value\</value>**</span><span class="sxs-lookup"><span data-stu-id="b4165-153">**A value tag is used to describe the property value\</value>**</span></span>  
 <span data-ttu-id="b4165-154">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="b4165-154">**\</member>**</span></span>  
 <span data-ttu-id="b4165-155">**\</members>**</span><span class="sxs-lookup"><span data-stu-id="b4165-155">**\</members>**</span></span>  
<span data-ttu-id="b4165-156">**\</doc>**</span><span class="sxs-lookup"><span data-stu-id="b4165-156">**\</doc>**</span></span>   
## <a name="compiling-the-code"></a><span data-ttu-id="b4165-157">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b4165-157">Compiling the Code</span></span>  
 <span data-ttu-id="b4165-158">この例をコンパイルするには、次のコマンド行を入力します。</span><span class="sxs-lookup"><span data-stu-id="b4165-158">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="b4165-159">これによって作成される XML ファイル XMLsample.xml は、ブラウザーで、または TYPE コマンドを使って、表示できます。</span><span class="sxs-lookup"><span data-stu-id="b4165-159">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b4165-160">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="b4165-160">Robust Programming</span></span>  
 <span data-ttu-id="b4165-161">XML ドキュメントは、/// で始まります。</span><span class="sxs-lookup"><span data-stu-id="b4165-161">XML documentation starts with ///.</span></span> <span data-ttu-id="b4165-162">新しいプロジェクトを作成すると、開始の /// 行がいくつか自動的に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="b4165-162">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="b4165-163">これらのコメントの処理にはいくつか制限があります。</span><span class="sxs-lookup"><span data-stu-id="b4165-163">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="b4165-164">ドキュメントは整形式の XML である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4165-164">The documentation must be well-formed XML.</span></span> <span data-ttu-id="b4165-165">XML が整形式ではない場合は、警告が生成され、エラーが発生したことを示すコメントがドキュメント ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b4165-165">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="b4165-166">開発者は、独自のタグ セットを自由に作成できます。</span><span class="sxs-lookup"><span data-stu-id="b4165-166">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="b4165-167">推奨されるタグ セットがあります (「関連項目」セクションを参照)。</span><span class="sxs-lookup"><span data-stu-id="b4165-167">There is a recommended set of tags (see the Further Reading section).</span></span> <span data-ttu-id="b4165-168">推奨されるタグの一部には特別な意味があります。</span><span class="sxs-lookup"><span data-stu-id="b4165-168">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="b4165-169">\<param> タグは、パラメーターの記述に使われます。</span><span class="sxs-lookup"><span data-stu-id="b4165-169">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="b4165-170">このタグがあると、コンパイラは、パラメーターが存在すること、およびすべてのパラメーターがドキュメントで記述されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b4165-170">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="b4165-171">検証で問題がある場合、コンパイラは警告を生成します。</span><span class="sxs-lookup"><span data-stu-id="b4165-171">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="b4165-172">`cref` 属性は任意のタグにアタッチでき、コード要素への参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="b4165-172">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="b4165-173">コンパイラは、このコード要素が存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="b4165-173">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="b4165-174">検証で問題がある場合、コンパイラは警告を生成します。</span><span class="sxs-lookup"><span data-stu-id="b4165-174">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="b4165-175">コンパイラは、`cref` 属性で記述されている型を探すとき、`using` ステートメントに従います。</span><span class="sxs-lookup"><span data-stu-id="b4165-175">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="b4165-176">\<summary> タグは、型またはメンバーに関する追加情報を表示するために、Visual Studio の IntelliSense によって使われます。</span><span class="sxs-lookup"><span data-stu-id="b4165-176">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b4165-177">XML ファイルでは、型とメンバーに関する完全な情報は提供されません (たとえば、型の情報は含まれません)。</span><span class="sxs-lookup"><span data-stu-id="b4165-177">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="b4165-178">型またはメンバーの完全な情報を取得するには、ドキュメント ファイルと併せて、実際の型またはメンバーでリフレクションを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4165-178">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4165-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4165-179">See Also</span></span>  
 <span data-ttu-id="b4165-180">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b4165-180">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b4165-181">[/doc (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="b4165-181">[/doc (C# Compiler Options)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span></span>  
 [<span data-ttu-id="b4165-182">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="b4165-182">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)

