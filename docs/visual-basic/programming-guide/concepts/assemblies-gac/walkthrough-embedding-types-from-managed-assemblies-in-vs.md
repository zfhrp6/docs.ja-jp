---
title: "チュートリアル: Visual Studio (Visual Basic) のアセンブリをマネージ型からの埋め込み |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: adc58e081cd9b874a841d84b11d92cbffb6ba6b8
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="77e2f-102">チュートリアル: Visual Studio (Visual Basic) でのマネージ アセンブリから型の埋め込み</span><span class="sxs-lookup"><span data-stu-id="77e2f-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="77e2f-103">厳密な名前のマネージ アセンブリから型情報を埋め込む場合は、バージョンに依存しないを実現するために、アプリケーションの種類を疎結合できます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="77e2f-104">つまり、バージョンごとに再コンパイルすることがなくマネージ ライブラリの複数のバージョンからの型を使用するプログラムを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="77e2f-105">型の埋め込みは COM 相互運用の Microsoft Office からのオートメーション オブジェクトを使用するアプリケーションなどでよく使用します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="77e2f-106">型情報を埋め込むと、Microsoft Office の異なるコンピューター上の異なるバージョンを使用するプログラムの同じビルドができます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="77e2f-107">ただし、完全に管理されたソリューションを埋め込み型を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="77e2f-108">次の特性を持つアセンブリから型情報を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="77e2f-109">アセンブリは、少なくとも&1; つのパブリック インターフェイスを公開します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="77e2f-110">埋め込みのインターフェイスが付いた、`ComImport`属性と`Guid`属性 (および一意の GUID)。</span><span class="sxs-lookup"><span data-stu-id="77e2f-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="77e2f-111">アセンブリが付いた、`ImportedFromTypeLib`属性または`PrimaryInteropAssembly`属性、およびアセンブリ レベル`Guid`属性です。</span><span class="sxs-lookup"><span data-stu-id="77e2f-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="77e2f-112">(既定では、Visual Basic プロジェクト テンプレートには、アセンブリ レベルが含まれて`Guid`属性です)。</span><span class="sxs-lookup"><span data-stu-id="77e2f-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="77e2f-113">埋め込むことができるパブリック インターフェイスを指定したら、それらのインターフェイスを実装するランタイム クラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="77e2f-114">クライアント プログラムをパブリック インターフェイスと設定を含むアセンブリを参照することでデザイン時にこれらのインターフェイスの型情報を埋め込むことができますし、`Embed Interop Types`プロパティへの参照の`True`です。</span><span class="sxs-lookup"><span data-stu-id="77e2f-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="77e2f-115">これは、コマンド ライン コンパイラを使用してを使用して、アセンブリの参照に相当する、`/link`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="77e2f-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="77e2f-116">クライアント プログラムは、これらのインターフェイスとして型指定されたランタイム オブジェクトのインスタンスを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="77e2f-117">厳密な名前のランタイム アセンブリの新しいバージョンを作成する場合、クライアント プログラムは、更新されたランタイム アセンブリを再コンパイルするのにはありません。</span><span class="sxs-lookup"><span data-stu-id="77e2f-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="77e2f-118">代わりに、クライアント プログラムは、どちらのバージョンのランタイム アセンブリは、パブリック インターフェイスの場合、埋め込み型情報を使用して、使用可能なを使用し続けます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="77e2f-119">型の埋め込みの主な機能は、COM 相互運用機能アセンブリから型情報の埋め込みをサポートするためにはであるために完全に管理されたソリューションの種類の情報を埋め込む場合に次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="77e2f-120">COM 相互運用機能に固有の属性のみが埋め込まれます。その他の属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="77e2f-121">型がジェネリック パラメーターを使用してジェネリック パラメーターの型は、埋め込みの型には、その型がアセンブリの境界を越えて使用できません。</span><span class="sxs-lookup"><span data-stu-id="77e2f-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="77e2f-122">アセンブリの境界を越えるの例としては、別のアセンブリからメソッドの呼び出しをまたは型の派生型から別のアセンブリで定義されています。</span><span class="sxs-lookup"><span data-stu-id="77e2f-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="77e2f-123">定数は埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="77e2f-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="77e2f-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>クラスは、キーとして埋め込み型をサポートしていません</xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="77e2f-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> class does not support an embedded type as a key.</span></span> <span data-ttu-id="77e2f-125">キーとして埋め込み型をサポートするために、独自のディクショナリ型を実装することができます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="77e2f-126">このチュートリアルでは、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="77e2f-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="77e2f-127">埋め込むことができる型情報を格納するパブリック インターフェイスを持つ厳密な名前のアセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="77e2f-128">パブリック インターフェイスを実装する厳密な名前のランタイム アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="77e2f-129">パブリック インターフェイスから型情報を埋め込むし、ランタイム アセンブリからクラスのインスタンスを作成するクライアント プログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="77e2f-130">変更し、ランタイム アセンブリを再構築します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="77e2f-131">クライアント プログラムを再コンパイルしなくても新しいバージョンのランタイム アセンブリが使用されていることをクライアントのプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="77e2f-132">インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="77e2f-133">型の等価性インターフェイス プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="77e2f-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="77e2f-134">Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="77e2f-135">**新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類** ウィンドウで、ことを確認して**Windows**が選択されています。</span><span class="sxs-lookup"><span data-stu-id="77e2f-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="77e2f-136">選択**クラス ライブラリ**で、**テンプレート**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="77e2f-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="77e2f-137">**名**ボックスに、入力`TypeEquivalenceInterface`、 をクリックし、 **OK**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="77e2f-138">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="77e2f-139">**ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="77e2f-140">ファイルを`ISampleInterface.vb`ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="77e2f-141">ファイルの名前変更の名前も変更は、クラスに`ISampleInterface`します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="77e2f-142">このクラスは、クラスのパブリック インターフェイスを表します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="77e2f-143">TypeEquivalenceInterface プロジェクトを右クリックし、クリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="77e2f-144">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-144">Click the **Compile** tab.</span></span> <span data-ttu-id="77e2f-145">など、開発用コンピューター上の有効な場所に出力パスを設定`C:\TypeEquivalenceSample`します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-145">Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="77e2f-146">この場所は、このチュートリアルの後の手順でも使用されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-146">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="77e2f-147">クリックしても、プロジェクトのプロパティを編集している間、**署名** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-147">While still editing the project properties, click the **Signing** tab.</span></span> <span data-ttu-id="77e2f-148">選択、**アセンブリに署名**オプション。</span><span class="sxs-lookup"><span data-stu-id="77e2f-148">Select the **Sign the assembly** option.</span></span> <span data-ttu-id="77e2f-149">**厳密な名前キー ファイルを選択して**一覧で、クリックして** <New...> **</New...> 。</span><span class="sxs-lookup"><span data-stu-id="77e2f-149">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="77e2f-150">**キー ファイル名**ボックスに、入力`key.snk`します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-150">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="77e2f-151">クリア、**パスワードでキー ファイルを保護する**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-151">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="77e2f-152">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-152">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="77e2f-153">ISampleInterface.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-153">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="77e2f-154">ISampleInterface インターフェイスを作成する ISampleInterface クラス ファイルに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-154">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
<span data-ttu-id="77e2f-155"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="77e2f-155"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
7.  <span data-ttu-id="77e2f-156">**ツール** メニューのをクリックして**Guid の作成**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-156">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="77e2f-157">**GUID の作成**ダイアログ ボックスで、をクリックして**レジストリ形式** をクリックし、**コピー**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-157">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="77e2f-158">[ **終了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-158">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="77e2f-159">`Guid`属性、サンプルの GUID を削除しからコピーした GUID を貼り付けます、 **GUID の作成** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="77e2f-159">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="77e2f-160">コピーした GUID には、中かっこ ({}) を削除します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-160">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="77e2f-161">**プロジェクト**] メニューのをクリックして**[すべてのファイル**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-161">On the **Project** menu, click **Show All Files**.</span></span>  
  
10. <span data-ttu-id="77e2f-162">**ソリューション エクスプ ローラー**、展開、 **My Project**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="77e2f-162">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="77e2f-163">AssemblyInfo.vb をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-163">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="77e2f-164">ファイルに次の属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-164">Add the following attribute to the file.</span></span>  
  
<span data-ttu-id="77e2f-165"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="77e2f-165"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="77e2f-166">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-166">Save the file.</span></span>  
  
11. <span data-ttu-id="77e2f-167">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-167">Save the project.</span></span>  
  
12. <span data-ttu-id="77e2f-168">TypeEquivalenceInterface プロジェクトを右クリックし、クリックして**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-168">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="77e2f-169">クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルドの出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-169">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="77e2f-170">ランタイム クラスの作成</span><span class="sxs-lookup"><span data-stu-id="77e2f-170">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="77e2f-171">型の等価性のランタイム プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="77e2f-171">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="77e2f-172">Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-172">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="77e2f-173">**新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類** ウィンドウで、ことを確認して**Windows**が選択されています。</span><span class="sxs-lookup"><span data-stu-id="77e2f-173">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="77e2f-174">選択**クラス ライブラリ**で、**テンプレート**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="77e2f-174">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="77e2f-175">**名**ボックスに、入力`TypeEquivalenceRuntime`、 をクリックし、 **OK**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-175">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="77e2f-176">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-176">The new project is created.</span></span>  
  
3.  <span data-ttu-id="77e2f-177">**ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-177">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="77e2f-178">ファイルを`SampleClass.vb`ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-178">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="77e2f-179">クラスの名前を変更も、ファイルの名前を変更する`SampleClass`です。</span><span class="sxs-lookup"><span data-stu-id="77e2f-179">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="77e2f-180">このクラスは実装、`ISampleInterface`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="77e2f-180">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="77e2f-181">TypeEquivalenceRuntime プロジェクトを右クリックし、クリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-181">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="77e2f-182">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-182">Click the **Compile** tab.</span></span> <span data-ttu-id="77e2f-183">たとえば、TypeEquivalenceInterface プロジェクトで使用した同じ場所に出力パスを設定`C:\TypeEquivalenceSample`します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-183">Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="77e2f-184">クリックしても、プロジェクトのプロパティを編集している間、**署名** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-184">While still editing the project properties, click the **Signing** tab.</span></span> <span data-ttu-id="77e2f-185">選択、**アセンブリに署名**オプション。</span><span class="sxs-lookup"><span data-stu-id="77e2f-185">Select the **Sign the assembly** option.</span></span> <span data-ttu-id="77e2f-186">**厳密な名前キー ファイルを選択して**一覧で、クリックして** <New...> **</New...> 。</span><span class="sxs-lookup"><span data-stu-id="77e2f-186">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="77e2f-187">**キー ファイル名**ボックスに、入力`key.snk`します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-187">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="77e2f-188">クリア、**パスワードでキー ファイルを保護する**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-188">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="77e2f-189">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-189">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="77e2f-190">TypeEquivalenceRuntime プロジェクトを右クリックし、クリックして**参照の追加**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-190">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="77e2f-191">クリックして、**参照**タブし、出力パスのフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-191">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="77e2f-192">TypeEquivalenceInterface.dll ファイルを選択し、クリックして**OK**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-192">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="77e2f-193">**プロジェクト**] メニューのをクリックして**[すべてのファイル**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-193">On the **Project** menu, click **Show All Files**.</span></span>  
  
8.  <span data-ttu-id="77e2f-194">**ソリューション エクスプ ローラー**、展開、**参照**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="77e2f-194">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="77e2f-195">TypeEquivalenceInterface 参照を選択します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-195">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="77e2f-196">TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、設定、**特定のバージョン**プロパティを**False**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-196">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
9. <span data-ttu-id="77e2f-197">SampleClass クラスを作成する SampleClass クラス ファイルに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-197">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
<span data-ttu-id="77e2f-198"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="77e2f-198"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
10. <span data-ttu-id="77e2f-199">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-199">Save the project.</span></span>  
  
11. <span data-ttu-id="77e2f-200">TypeEquivalenceRuntime プロジェクトを右クリックし、クリックして**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-200">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="77e2f-201">クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルドの出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-201">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="77e2f-202">クライアント プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="77e2f-202">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="77e2f-203">型の等価性のクライアント プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="77e2f-203">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="77e2f-204">Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-204">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="77e2f-205">**新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類** ウィンドウで、ことを確認して**Windows**が選択されています。</span><span class="sxs-lookup"><span data-stu-id="77e2f-205">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="77e2f-206">選択**コンソール アプリケーション**で、**テンプレート**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="77e2f-206">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="77e2f-207">**名**ボックスに、入力`TypeEquivalenceClient`、 をクリックし、 **OK**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-207">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="77e2f-208">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-208">The new project is created.</span></span>  
  
3.  <span data-ttu-id="77e2f-209">TypeEquivalenceClient プロジェクトを右クリックし、クリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-209">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="77e2f-210">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-210">Click the **Compile** tab.</span></span> <span data-ttu-id="77e2f-211">たとえば、TypeEquivalenceInterface プロジェクトで使用した同じ場所に出力パスを設定`C:\TypeEquivalenceSample`します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-211">Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="77e2f-212">TypeEquivalenceClient プロジェクトを右クリックし、クリックして**参照の追加**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-212">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="77e2f-213">クリックして、**参照**タブし、出力パスのフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-213">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="77e2f-214">TypeEquivalenceInterface.dll ファイル (TypeEquivalenceRuntime.dll ではない) を選択し、クリックして**OK**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-214">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="77e2f-215">**プロジェクト**] メニューのをクリックして**[すべてのファイル**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-215">On the **Project** menu, click **Show All Files**.</span></span>  
  
6.  <span data-ttu-id="77e2f-216">**ソリューション エクスプ ローラー**、展開、**参照**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="77e2f-216">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="77e2f-217">TypeEquivalenceInterface 参照を選択します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-217">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="77e2f-218">TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、設定、 **Embed Interop Types**プロパティを**True**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-218">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
7.  <span data-ttu-id="77e2f-219">Module1.vb ファイルをクライアント プログラムを作成するには、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-219">Add the following code to the Module1.vb file to create the client program.</span></span>  
  
<span data-ttu-id="77e2f-220"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="77e2f-220"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
8.  <span data-ttu-id="77e2f-221">ビルドして、プログラムを実行するには、CTRL + F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-221">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="77e2f-222">インターフェイスを変更します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-222">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="77e2f-223">インターフェイスを変更するには</span><span class="sxs-lookup"><span data-stu-id="77e2f-223">To modify the interface</span></span>  
  
1.  <span data-ttu-id="77e2f-224">Visual Studio での**ファイル** メニューをポイント**開く**、順にクリック**プロジェクト/ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="77e2f-225">**プロジェクトを開く**ダイアログ ボックスで、TypeEquivalenceInterface プロジェクトを右クリックし、をクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-225">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="77e2f-226">**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-226">Click the **Application** tab.</span></span> <span data-ttu-id="77e2f-227">クリックして、**アセンブリ情報** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-227">Click the **Assembly Information** button.</span></span> <span data-ttu-id="77e2f-228">変更、**アセンブリ バージョン**と**ファイル バージョン**値`2.0.0.0`です。</span><span class="sxs-lookup"><span data-stu-id="77e2f-228">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="77e2f-229">ISampleInterface.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-229">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="77e2f-230">ISampleInterface インターフェイスには、次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-230">Add the following line of code to the ISampleInterface interface.</span></span>  
  
<span data-ttu-id="77e2f-231"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="77e2f-231"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="77e2f-232">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-232">Save the file.</span></span>  
  
4.  <span data-ttu-id="77e2f-233">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-233">Save the project.</span></span>  
  
5.  <span data-ttu-id="77e2f-234">TypeEquivalenceInterface プロジェクトを右クリックし、クリックして**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-234">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="77e2f-235">クラス ライブラリの .dll ファイルの新しいバージョンがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-235">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="77e2f-236">ランタイム クラスの変更</span><span class="sxs-lookup"><span data-stu-id="77e2f-236">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="77e2f-237">ランタイム クラスを変更するには</span><span class="sxs-lookup"><span data-stu-id="77e2f-237">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="77e2f-238">Visual Studio での**ファイル** メニューをポイント**開く**、順にクリック**プロジェクト/ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-238">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="77e2f-239">**プロジェクトを開く** ダイアログ ボックスで、TypeEquivalenceRuntime プロジェクトを右クリックし、クリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-239">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="77e2f-240">**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-240">Click the **Application** tab.</span></span> <span data-ttu-id="77e2f-241">クリックして、**アセンブリ情報** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-241">Click the **Assembly Information** button.</span></span> <span data-ttu-id="77e2f-242">変更、**アセンブリ バージョン**と**ファイル バージョン**値`2.0.0.0`です。</span><span class="sxs-lookup"><span data-stu-id="77e2f-242">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="77e2f-243">SampleClass.vbfile を開きます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-243">Open the SampleClass.vbfile.</span></span> <span data-ttu-id="77e2f-244">SampleClass クラスに次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-244">Add the following lines of code to the SampleClass class.</span></span>  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  <span data-ttu-id="77e2f-245">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-245">Save the project.</span></span>  
  
5.  <span data-ttu-id="77e2f-246">TypeEquivalenceRuntime プロジェクトを右クリックし、クリックして**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="77e2f-246">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="77e2f-247">クラス ライブラリの .dll ファイルの更新バージョンがコンパイルされ、以前に指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-247">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="77e2f-248">ファイル エクスプ ローラーでは、出力パスのフォルダー (たとえば、C:\TypeEquivalenceSample) を開きます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-248">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="77e2f-249">プログラムを実行する TypeEquivalenceClient.exe をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="77e2f-249">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="77e2f-250">プログラムは、再コンパイルされたことがなく TypeEquivalenceRuntime アセンブリの新しいバージョンに反映されます。</span><span class="sxs-lookup"><span data-stu-id="77e2f-250">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e2f-251">関連項目</span><span class="sxs-lookup"><span data-stu-id="77e2f-251">See Also</span></span>  
 <span data-ttu-id="77e2f-252">[/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md) </span><span class="sxs-lookup"><span data-stu-id="77e2f-252">[/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md) </span></span>  
<span data-ttu-id="77e2f-253"> [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="77e2f-253"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="77e2f-254"> [アセンブリを使用したプログラミング](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6) </span><span class="sxs-lookup"><span data-stu-id="77e2f-254"> [Programming with Assemblies](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6) </span></span>  
<span data-ttu-id="77e2f-255"> [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="77e2f-255"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>

