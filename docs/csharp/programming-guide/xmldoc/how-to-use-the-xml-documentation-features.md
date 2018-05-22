---
title: '方法 : XML ドキュメント機能を使用する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 6c7e30d23868959145e8941057f1c633fe6e374e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="58956-102">方法 : XML ドキュメント機能を使用する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="58956-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="58956-103">次の例では、ドキュメント化された型の基本的な概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="58956-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58956-104">例</span><span class="sxs-lookup"><span data-stu-id="58956-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 <span data-ttu-id="58956-105">**// この .xml ファイルは、上記のコード サンプルで生成されました。**</span><span class="sxs-lookup"><span data-stu-id="58956-105">**// This .xml file was generated with the previous code sample.**</span></span>  
<span data-ttu-id="58956-106">**\<?xml version="1.0"?>**</span><span class="sxs-lookup"><span data-stu-id="58956-106">**\<?xml version="1.0"?>**</span></span>  
<span data-ttu-id="58956-107">**\<doc>**</span><span class="sxs-lookup"><span data-stu-id="58956-107">**\<doc>**</span></span>  
 <span data-ttu-id="58956-108">**\<assembly>**</span><span class="sxs-lookup"><span data-stu-id="58956-108">**\<assembly>**</span></span>  
 <span data-ttu-id="58956-109">**\<name>xmlsample\</name>**</span><span class="sxs-lookup"><span data-stu-id="58956-109">**\<name>xmlsample\</name>**</span></span>  
 <span data-ttu-id="58956-110">**\</assembly>**</span><span class="sxs-lookup"><span data-stu-id="58956-110">**\</assembly>**</span></span>  
 <span data-ttu-id="58956-111">**\<members>**</span><span class="sxs-lookup"><span data-stu-id="58956-111">**\<members>**</span></span>  
 <span data-ttu-id="58956-112">**\<member name="T:SomeClass">**</span><span class="sxs-lookup"><span data-stu-id="58956-112">**\<member name="T:SomeClass">**</span></span>  
 <span data-ttu-id="58956-113">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-113">**\<summary>**</span></span>  
 <span data-ttu-id="58956-114">**Class level summary documentation goes here.\</summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-114">**Class level summary documentation goes here.\</summary>**</span></span>  
 <span data-ttu-id="58956-115">**\<remarks>**</span><span class="sxs-lookup"><span data-stu-id="58956-115">**\<remarks>**</span></span>  
 <span data-ttu-id="58956-116">**Longer comments can be associated with a type or member**</span><span class="sxs-lookup"><span data-stu-id="58956-116">**Longer comments can be associated with a type or member**</span></span>  
 <span data-ttu-id="58956-117">**through the remarks tag\</remarks>**</span><span class="sxs-lookup"><span data-stu-id="58956-117">**through the remarks tag\</remarks>**</span></span>  
 <span data-ttu-id="58956-118">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="58956-118">**\</member>**</span></span>  
 <span data-ttu-id="58956-119">**\<member name="F:SomeClass.m_Name">**</span><span class="sxs-lookup"><span data-stu-id="58956-119">**\<member name="F:SomeClass.m_Name">**</span></span>  
 <span data-ttu-id="58956-120">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-120">**\<summary>**</span></span>  
 <span data-ttu-id="58956-121">**Store for the name property\</summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-121">**Store for the name property\</summary>**</span></span>  
 <span data-ttu-id="58956-122">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="58956-122">**\</member>**</span></span>  
 <span data-ttu-id="58956-123">**\<member name="M:SomeClass.#ctor">**</span><span class="sxs-lookup"><span data-stu-id="58956-123">**\<member name="M:SomeClass.#ctor">**</span></span>  
 <span data-ttu-id="58956-124">**\<summary>The class constructor.\</summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-124">**\<summary>The class constructor.\</summary>**</span></span>  
 <span data-ttu-id="58956-125">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="58956-125">**\</member>**</span></span>  
 <span data-ttu-id="58956-126">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="58956-126">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="58956-127">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-127">**\<summary>**</span></span>  
 <span data-ttu-id="58956-128">**Description for SomeMethod.\</summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-128">**Description for SomeMethod.\</summary>**</span></span>  
 <span data-ttu-id="58956-129">**\<param name="s"> Parameter description for s goes here\</param>**</span><span class="sxs-lookup"><span data-stu-id="58956-129">**\<param name="s"> Parameter description for s goes here\</param>**</span></span>  
 <span data-ttu-id="58956-130">**\<seealso cref="T:System.String">**</span><span class="sxs-lookup"><span data-stu-id="58956-130">**\<seealso cref="T:System.String">**</span></span>  
 <span data-ttu-id="58956-131">**You can use the cref attribute on any tag to reference a type or member**</span><span class="sxs-lookup"><span data-stu-id="58956-131">**You can use the cref attribute on any tag to reference a type or member**</span></span>  
 <span data-ttu-id="58956-132">**and the compiler will check that the reference exists. \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="58956-132">**and the compiler will check that the reference exists. \</seealso>**</span></span>  
 <span data-ttu-id="58956-133">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="58956-133">**\</member>**</span></span>  
 <span data-ttu-id="58956-134">**\<member name="M:SomeClass.SomeOtherMethod">**</span><span class="sxs-lookup"><span data-stu-id="58956-134">**\<member name="M:SomeClass.SomeOtherMethod">**</span></span>  
 <span data-ttu-id="58956-135">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-135">**\<summary>**</span></span>  
 <span data-ttu-id="58956-136">**Some other method. \</summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-136">**Some other method. \</summary>**</span></span>  
 <span data-ttu-id="58956-137">**\<returns>**</span><span class="sxs-lookup"><span data-stu-id="58956-137">**\<returns>**</span></span>  
 <span data-ttu-id="58956-138">**Return results are described through the returns tag.\</returns>**</span><span class="sxs-lookup"><span data-stu-id="58956-138">**Return results are described through the returns tag.\</returns>**</span></span>  
 <span data-ttu-id="58956-139">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="58956-139">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="58956-140">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="58956-140">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span></span>  
 <span data-ttu-id="58956-141">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="58956-141">**\</member>**</span></span>  
 <span data-ttu-id="58956-142">**\<member name="M:SomeClass.Main(System.String[])">**</span><span class="sxs-lookup"><span data-stu-id="58956-142">**\<member name="M:SomeClass.Main(System.String[])">**</span></span>  
 <span data-ttu-id="58956-143">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-143">**\<summary>**</span></span>  
 <span data-ttu-id="58956-144">**The entry point for the application.**</span><span class="sxs-lookup"><span data-stu-id="58956-144">**The entry point for the application.**</span></span>  
 <span data-ttu-id="58956-145">**\</summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-145">**\</summary>**</span></span>  
 <span data-ttu-id="58956-146">**\<param name="args"> A list of command line arguments\</param>**</span><span class="sxs-lookup"><span data-stu-id="58956-146">**\<param name="args"> A list of command line arguments\</param>**</span></span>  
 <span data-ttu-id="58956-147">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="58956-147">**\</member>**</span></span>  
 <span data-ttu-id="58956-148">**\<member name="P:SomeClass.Name">**</span><span class="sxs-lookup"><span data-stu-id="58956-148">**\<member name="P:SomeClass.Name">**</span></span>  
 <span data-ttu-id="58956-149">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-149">**\<summary>**</span></span>  
 <span data-ttu-id="58956-150">**Name property \</summary>**</span><span class="sxs-lookup"><span data-stu-id="58956-150">**Name property \</summary>**</span></span>  
 <span data-ttu-id="58956-151">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="58956-151">**\<value>**</span></span>  
 <span data-ttu-id="58956-152">**A value tag is used to describe the property value\</value>**</span><span class="sxs-lookup"><span data-stu-id="58956-152">**A value tag is used to describe the property value\</value>**</span></span>  
 <span data-ttu-id="58956-153">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="58956-153">**\</member>**</span></span>  
 <span data-ttu-id="58956-154">**\</members>**</span><span class="sxs-lookup"><span data-stu-id="58956-154">**\</members>**</span></span>  
<span data-ttu-id="58956-155">**\</doc>**</span><span class="sxs-lookup"><span data-stu-id="58956-155">**\</doc>**</span></span>   
## <a name="compiling-the-code"></a><span data-ttu-id="58956-156">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="58956-156">Compiling the Code</span></span>  
 <span data-ttu-id="58956-157">この例をコンパイルするには、次のコマンド行を入力します。</span><span class="sxs-lookup"><span data-stu-id="58956-157">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="58956-158">これによって作成される XML ファイル XMLsample.xml は、ブラウザーで、または TYPE コマンドを使って、表示できます。</span><span class="sxs-lookup"><span data-stu-id="58956-158">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="58956-159">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="58956-159">Robust Programming</span></span>  
 <span data-ttu-id="58956-160">XML ドキュメントは、/// で始まります。</span><span class="sxs-lookup"><span data-stu-id="58956-160">XML documentation starts with ///.</span></span> <span data-ttu-id="58956-161">新しいプロジェクトを作成すると、開始の /// 行がいくつか自動的に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="58956-161">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="58956-162">これらのコメントの処理にはいくつか制限があります。</span><span class="sxs-lookup"><span data-stu-id="58956-162">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="58956-163">ドキュメントは整形式の XML である必要があります。</span><span class="sxs-lookup"><span data-stu-id="58956-163">The documentation must be well-formed XML.</span></span> <span data-ttu-id="58956-164">XML が整形式ではない場合は、警告が生成され、エラーが発生したことを示すコメントがドキュメント ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="58956-164">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="58956-165">開発者は、独自のタグ セットを自由に作成できます。</span><span class="sxs-lookup"><span data-stu-id="58956-165">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="58956-166">推奨されるタグ セットがあります (「関連項目」セクションを参照)。</span><span class="sxs-lookup"><span data-stu-id="58956-166">There is a recommended set of tags (see the Further Reading section).</span></span> <span data-ttu-id="58956-167">推奨されるタグの一部には特別な意味があります。</span><span class="sxs-lookup"><span data-stu-id="58956-167">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="58956-168">\<param> タグは、パラメーターの記述に使われます。</span><span class="sxs-lookup"><span data-stu-id="58956-168">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="58956-169">このタグがあると、コンパイラは、パラメーターが存在すること、およびすべてのパラメーターがドキュメントで記述されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="58956-169">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="58956-170">検証で問題がある場合、コンパイラは警告を生成します。</span><span class="sxs-lookup"><span data-stu-id="58956-170">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="58956-171">`cref` 属性は任意のタグにアタッチでき、コード要素への参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="58956-171">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="58956-172">コンパイラは、このコード要素が存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="58956-172">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="58956-173">検証で問題がある場合、コンパイラは警告を生成します。</span><span class="sxs-lookup"><span data-stu-id="58956-173">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="58956-174">コンパイラは、`cref` 属性で記述されている型を探すとき、`using` ステートメントに従います。</span><span class="sxs-lookup"><span data-stu-id="58956-174">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="58956-175">\<summary> タグは、型またはメンバーに関する追加情報を表示するために、Visual Studio の IntelliSense によって使われます。</span><span class="sxs-lookup"><span data-stu-id="58956-175">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="58956-176">XML ファイルでは、型とメンバーに関する完全な情報は提供されません (たとえば、型の情報は含まれません)。</span><span class="sxs-lookup"><span data-stu-id="58956-176">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="58956-177">型またはメンバーの完全な情報を取得するには、ドキュメント ファイルと併せて、実際の型またはメンバーでリフレクションを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="58956-177">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58956-178">参照</span><span class="sxs-lookup"><span data-stu-id="58956-178">See Also</span></span>  
 [<span data-ttu-id="58956-179">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="58956-179">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="58956-180">/doc (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="58956-180">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="58956-181">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="58956-181">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
