---
title: 'チュートリアル: Visual Studio (Visual Basic) でのマネージ アセンブリから型の埋め込み'
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 1f6176746b783d020c809fb0b5d55d741ce0148b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="8a923-102">チュートリアル: Visual Studio (Visual Basic) でのマネージ アセンブリから型の埋め込み</span><span class="sxs-lookup"><span data-stu-id="8a923-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="8a923-103">厳密な名前を持つマネージ アセンブリから型情報を埋め込むと、アプリケーション内で型を疎結合して、バージョンに依存しないプログラムを実現できます。</span><span class="sxs-lookup"><span data-stu-id="8a923-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="8a923-104">つまり、各バージョン用の再コンパイルを必要とすることなく、マネージ ライブラリの複数のバージョンから型を使用するプログラムを記述できます。</span><span class="sxs-lookup"><span data-stu-id="8a923-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="8a923-105">型の埋め込みは、COM 相互運用と共によく使用されます (Microsoft Office からのオートメーション オブジェクトを使用するアプリケーションなど)。</span><span class="sxs-lookup"><span data-stu-id="8a923-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="8a923-106">型情報を埋め込むと、同じビルドのプログラムを、別のコンピューター上にある別バージョンの Microsoft Office と連携させることができます。</span><span class="sxs-lookup"><span data-stu-id="8a923-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="8a923-107">ただし、型の埋め込みは完全なマネージ ソリューションと共に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="8a923-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="8a923-108">型情報は、次の特性を持つアセンブリから埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="8a923-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="8a923-109">アセンブリが、少なくとも 1 つのパブリック インターフェイスを公開している。</span><span class="sxs-lookup"><span data-stu-id="8a923-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="8a923-110">埋め込みインターフェイスに `ComImport` 属性と `Guid` 属性 (および一意の GUID) が付けられている。</span><span class="sxs-lookup"><span data-stu-id="8a923-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="8a923-111">アセンブリに、`ImportedFromTypeLib` 属性または `PrimaryInteropAssembly` 属性、およびアセンブリ レベルの `Guid` 属性が付けられている。</span><span class="sxs-lookup"><span data-stu-id="8a923-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="8a923-112">(既定では、Visual Basic プロジェクト テンプレートには、アセンブリ レベルが含まれて`Guid`属性です)。</span><span class="sxs-lookup"><span data-stu-id="8a923-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="8a923-113">埋め込み可能なパブリック インターフェイスを指定したら、それらのインターフェイスを実装するランタイム クラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8a923-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="8a923-114">その後、クライアント プログラムは、パブリック インターフェイスを含んだアセンブリを参照し、参照の `Embed Interop Types` プロパティを `True` に設定することで、デザイン時にそれらのインターフェイスの型情報を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="8a923-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="8a923-115">これは、コマンド ライン コンパイラを使用し、`/link` コンパイラ オプションを使用してアセンブリを参照することに相当します。</span><span class="sxs-lookup"><span data-stu-id="8a923-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="8a923-116">クライアント プログラムはその後、それらのインターフェイスとして型指定されたランタイム オブジェクトのインスタンスを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="8a923-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="8a923-117">厳密な名前を持つランタイム アセンブリの新バージョンを作成した場合、クライアント プログラムを、更新後のランタイム アセンブリで再コンパイルする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8a923-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="8a923-118">クライアント プログラムでは、パブリック インターフェイスの埋め込み型情報を使用して、利用可能なバージョンをどちらでも引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a923-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="8a923-119">型埋め込みの主な機能は、COM 相互運用アセンブリからの型情報の埋め込みをサポートすることなので、完全なマネージ ソリューションで型情報を埋め込む場合には、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="8a923-120">COM 相互運用に固有の属性のみが埋め込まれます。その他の属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="8a923-121">型がジェネリック パラメーターを使用していて、ジェネリック パラメーターの型が埋め込み型である場合、その型はアセンブリの境界を越えて使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="8a923-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="8a923-122">アセンブリの境界を越える場合の例としては、別のアセンブリからメソッドを呼び出す場合や、別のアセンブリで定義されている型から型を派生させる場合が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="8a923-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="8a923-123">定数は埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="8a923-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="8a923-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> クラスでは、埋め込み型をキーとして利用できません。</span><span class="sxs-lookup"><span data-stu-id="8a923-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="8a923-125">埋め込み型をキーとしてサポートするために、独自のディクショナリ型を実装することは可能です。</span><span class="sxs-lookup"><span data-stu-id="8a923-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="8a923-126">このチュートリアルでは、次のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="8a923-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="8a923-127">埋め込み可能な型情報を含んだパブリック インターフェイスを持つ、厳密な名前付きのアセンブリを作成する。</span><span class="sxs-lookup"><span data-stu-id="8a923-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="8a923-128">そのパブリック インターフェイスを実装する、厳密な名前付きのランタイム アセンブリを作成する。</span><span class="sxs-lookup"><span data-stu-id="8a923-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="8a923-129">パブリック インターフェイスから型情報を埋め込み、ランタイム アセンブリからクラスのインスタンスを作成する、クライアント プログラムを作成する。</span><span class="sxs-lookup"><span data-stu-id="8a923-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="8a923-130">ランタイム アセンブリを変更し、リビルドする。</span><span class="sxs-lookup"><span data-stu-id="8a923-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="8a923-131">クライアント プログラムを実行して、新バージョンのランタイム アセンブリが、クライアント プログラムを再コンパイルしなくても使用されていることを確認する。</span><span class="sxs-lookup"><span data-stu-id="8a923-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="8a923-132">インターフェイスの作成</span><span class="sxs-lookup"><span data-stu-id="8a923-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="8a923-133">型等価性インターフェイス プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="8a923-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="8a923-134">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="8a923-135">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8a923-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="8a923-136">**[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8a923-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="8a923-137">**[名前]** ボックスに `TypeEquivalenceInterface` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="8a923-138">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="8a923-139">**ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**です。</span><span class="sxs-lookup"><span data-stu-id="8a923-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="8a923-140">ファイルの名前を `ISampleInterface.vb` に変更し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="8a923-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="8a923-141">ファイルの名前を変更すると、クラスの名前も `ISampleInterface` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="8a923-142">このクラスは、クラスのパブリック インターフェイスを表します。</span><span class="sxs-lookup"><span data-stu-id="8a923-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="8a923-143">TypeEquivalenceInterface プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="8a923-144">**[コンパイル]** タブをクリックします。開発用コンピューター上の有効な場所への出力パスを設定します (`C:\TypeEquivalenceSample` など)。</span><span class="sxs-lookup"><span data-stu-id="8a923-144">Click the **Compile** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="8a923-145">この場所は、このチュートリアルの後の手順でも使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="8a923-146">プロジェクト プロパティの編集を続けたまま、**[署名]** タブをクリックします。**[アセンブリの署名]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="8a923-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="8a923-147">**[厳密な名前のキー ファイルを選択してください]** ボックスの一覧で **[<新規作成...>]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="8a923-148">**[キー ファイル名]** ボックスに、「`key.snk`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8a923-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="8a923-149">**[キーファイルをパスワードで保護する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="8a923-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="8a923-150">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="8a923-151">ISampleInterface.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="8a923-151">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="8a923-152">ISampleInterface クラス ファイルに、ISampleInterface インターフェイスを作成するための次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8a923-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
    ```vb  
    Imports System.Runtime.InteropServices  
  
    <ComImport()>  
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>  
    Public Interface ISampleInterface  
        Sub GetUserInput()  
        ReadOnly Property UserInput As String  
    End Interface  
    ```  
  
7.  <span data-ttu-id="8a923-153">**[ツール]** メニューの **[GUID の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="8a923-154">**[GUID の作成]** ダイアログ ボックスで、**[レジストリ形式]** をクリックし、**[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="8a923-155">**[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="8a923-156">`Guid` 属性で、サンプルの GUID を削除し、**[GUID の作成]** ダイアログ ボックスからコピーした GUID を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8a923-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="8a923-157">中かっこを削除 ({}) コピーした GUID からです。</span><span class="sxs-lookup"><span data-stu-id="8a923-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="8a923-158">**[プロジェクト]** メニューの **[すべてのファイルを表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-158">On the **Project** menu, click **Show All Files**.</span></span>  
  
10. <span data-ttu-id="8a923-159">**ソリューション エクスプ ローラー**、展開、 **My Project**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="8a923-159">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="8a923-160">AssemblyInfo.vb をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-160">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="8a923-161">ファイルに次の属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="8a923-161">Add the following attribute to the file.</span></span>  
  
    ```vb  
    <Assembly: ImportedFromTypeLib("")>  
    ```  
  
     <span data-ttu-id="8a923-162">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="8a923-162">Save the file.</span></span>  
  
11. <span data-ttu-id="8a923-163">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="8a923-163">Save the project.</span></span>  
  
12. <span data-ttu-id="8a923-164">TypeEquivalenceInterface プロジェクトを右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-164">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="8a923-165">クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-165">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="8a923-166">ランタイム クラスの作成</span><span class="sxs-lookup"><span data-stu-id="8a923-166">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="8a923-167">型等価性ランタイム プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="8a923-167">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="8a923-168">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-168">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="8a923-169">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8a923-169">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="8a923-170">**[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8a923-170">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="8a923-171">**[名前]** ボックスに `TypeEquivalenceRuntime` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-171">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="8a923-172">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-172">The new project is created.</span></span>  
  
3.  <span data-ttu-id="8a923-173">**ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**です。</span><span class="sxs-lookup"><span data-stu-id="8a923-173">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="8a923-174">ファイルの名前を `SampleClass.vb` に変更し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="8a923-174">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="8a923-175">ファイルの名前を変更すると、クラスの名前も `SampleClass` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-175">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="8a923-176">このクラスが `ISampleInterface` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="8a923-176">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="8a923-177">TypeEquivalenceRuntime プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-177">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="8a923-178">**[コンパイル]** タブをクリックします。出力パスを、TypeEquivalenceInterface プロジェクトで使用したのと同じ場所に設定します (たとえば、`C:\TypeEquivalenceSample`)。</span><span class="sxs-lookup"><span data-stu-id="8a923-178">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="8a923-179">プロジェクト プロパティの編集を続けたまま、**[署名]** タブをクリックします。**[アセンブリの署名]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="8a923-179">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="8a923-180">**[厳密な名前のキー ファイルを選択してください]** ボックスの一覧で **[<新規作成...>]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-180">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="8a923-181">**[キー ファイル名]** ボックスに、「`key.snk`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8a923-181">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="8a923-182">**[キーファイルをパスワードで保護する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="8a923-182">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="8a923-183">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-183">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="8a923-184">TypeEquivalenceRuntime プロジェクトを右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-184">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="8a923-185">**[参照]** タブをクリックし、出力パスのフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="8a923-185">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="8a923-186">TypeEquivalenceInterface.dll ファイルを選択し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-186">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="8a923-187">**[プロジェクト]** メニューの **[すべてのファイルを表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-187">On the **Project** menu, click **Show All Files**.</span></span>  
  
8.  <span data-ttu-id="8a923-188">**ソリューション エクスプローラー**で、**[参照]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="8a923-188">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="8a923-189">TypeEquivalenceInterface 参照を選択します。</span><span class="sxs-lookup"><span data-stu-id="8a923-189">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="8a923-190">TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、**[特定バージョン]** プロパティを **[False]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="8a923-190">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
9. <span data-ttu-id="8a923-191">SampleClass クラス ファイルに、SampleClass クラスを作成するための次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8a923-191">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
    ```vb  
    Imports TypeEquivalenceInterface  
  
    Public Class SampleClass  
        Implements ISampleInterface  
  
        Private p_UserInput As String  
        Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput  
            Get  
                Return p_UserInput  
            End Get  
        End Property  
  
        Public Sub GetUserInput() Implements ISampleInterface.GetUserInput  
            Console.WriteLine("Please enter a value:")  
            p_UserInput = Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
10. <span data-ttu-id="8a923-192">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="8a923-192">Save the project.</span></span>  
  
11. <span data-ttu-id="8a923-193">TypeEquivalenceRuntime プロジェクトを右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-193">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="8a923-194">クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-194">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="8a923-195">クライアント プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="8a923-195">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="8a923-196">型等価性クライアント プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="8a923-196">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="8a923-197">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-197">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="8a923-198">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8a923-198">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="8a923-199">**[テンプレート]** ペインの **[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8a923-199">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="8a923-200">**[名前]** ボックスに `TypeEquivalenceClient` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-200">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="8a923-201">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-201">The new project is created.</span></span>  
  
3.  <span data-ttu-id="8a923-202">TypeEquivalenceClient プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-202">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="8a923-203">**[コンパイル]** タブをクリックします。出力パスを、TypeEquivalenceInterface プロジェクトで使用したのと同じ場所に設定します (たとえば、`C:\TypeEquivalenceSample`)。</span><span class="sxs-lookup"><span data-stu-id="8a923-203">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="8a923-204">TypeEquivalenceClient プロジェクトを右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-204">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="8a923-205">**[参照]** タブをクリックし、出力パスのフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="8a923-205">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="8a923-206">TypeEquivalenceInterface.dll ファイル (TypeEquivalenceRuntime.dll ではない) を選択し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-206">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="8a923-207">**[プロジェクト]** メニューの **[すべてのファイルを表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-207">On the **Project** menu, click **Show All Files**.</span></span>  
  
6.  <span data-ttu-id="8a923-208">**ソリューション エクスプローラー**で、**[参照]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="8a923-208">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="8a923-209">TypeEquivalenceInterface 参照を選択します。</span><span class="sxs-lookup"><span data-stu-id="8a923-209">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="8a923-210">TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、**[相互運用型の埋め込み]** プロパティを **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="8a923-210">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
7.  <span data-ttu-id="8a923-211">クライアント プログラムを作成する、Module1.vb ファイルに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8a923-211">Add the following code to the Module1.vb file to create the client program.</span></span>  
  
    ```vb  
    Imports TypeEquivalenceInterface  
    Imports System.Reflection  
  
    Module Module1  
  
        Sub Main()  
            Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")  
            Dim sampleClass As ISampleInterface = CType( _  
                sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)  
            sampleClass.GetUserInput()  
            Console.WriteLine(sampleClass.UserInput)  
            Console.WriteLine(sampleAssembly.GetName().Version)  
            Console.ReadLine()  
        End Sub  
  
    End Module  
    ```  
  
8.  <span data-ttu-id="8a923-212">Ctrl キーを押しながら F5 キーを押して、プログラムをビルドおよび実行します。</span><span class="sxs-lookup"><span data-stu-id="8a923-212">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="8a923-213">インターフェイスの変更</span><span class="sxs-lookup"><span data-stu-id="8a923-213">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="8a923-214">インターフェイスを変更するには</span><span class="sxs-lookup"><span data-stu-id="8a923-214">To modify the interface</span></span>  
  
1.  <span data-ttu-id="8a923-215">Visual Studio で、**[ファイル]** メニューの **[開く]** をポイントし、**[プロジェクト/ソリューション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-215">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="8a923-216">**[プロジェクトを開く]** ダイアログ ボックスで、TypeEquivalenceInterface プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-216">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="8a923-217">**[アプリケーション]** タブをクリックします。**[アセンブリ情報]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-217">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="8a923-218">**[アセンブリ バージョン]** と **[ファイル バージョン]** の値を `2.0.0.0` に変更します。</span><span class="sxs-lookup"><span data-stu-id="8a923-218">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="8a923-219">ISampleInterface.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="8a923-219">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="8a923-220">ISampleInterface インターフェイスに、次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="8a923-220">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```vb  
    Function GetDate() As Date  
    ```  
  
     <span data-ttu-id="8a923-221">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="8a923-221">Save the file.</span></span>  
  
4.  <span data-ttu-id="8a923-222">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="8a923-222">Save the project.</span></span>  
  
5.  <span data-ttu-id="8a923-223">TypeEquivalenceInterface プロジェクトを右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-223">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="8a923-224">クラス ライブラリ .dll ファイルの新バージョンがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-224">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="8a923-225">ランタイム クラスの変更</span><span class="sxs-lookup"><span data-stu-id="8a923-225">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="8a923-226">ランタイム クラスを変更するには</span><span class="sxs-lookup"><span data-stu-id="8a923-226">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="8a923-227">Visual Studio で、**[ファイル]** メニューの **[開く]** をポイントし、**[プロジェクト/ソリューション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-227">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="8a923-228">**[プロジェクトを開く]** ダイアログ ボックスで、TypeEquivalenceRuntime プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-228">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="8a923-229">**[アプリケーション]** タブをクリックします。**[アセンブリ情報]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-229">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="8a923-230">**[アセンブリ バージョン]** と **[ファイル バージョン]** の値を `2.0.0.0` に変更します。</span><span class="sxs-lookup"><span data-stu-id="8a923-230">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="8a923-231">SampleClass.vbfile を開きます。</span><span class="sxs-lookup"><span data-stu-id="8a923-231">Open the SampleClass.vbfile.</span></span> <span data-ttu-id="8a923-232">SampleClass クラスに次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="8a923-232">Add the following lines of code to the SampleClass class.</span></span>  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  <span data-ttu-id="8a923-233">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="8a923-233">Save the project.</span></span>  
  
5.  <span data-ttu-id="8a923-234">TypeEquivalenceRuntime プロジェクトを右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a923-234">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="8a923-235">クラス ライブラリ .dll ファイルの更新バージョンがコンパイルされ、前に指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-235">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="8a923-236">ファイル エクスプローラーで、出力パスのフォルダー (たとえば、C:\TypeEquivalenceSample) を開きます。</span><span class="sxs-lookup"><span data-stu-id="8a923-236">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="8a923-237">TypeEquivalenceClient.exe をダブルクリックして、プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="8a923-237">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="8a923-238">プログラムでは、再コンパイルを行わなくても、新バージョンの TypeEquivalenceRuntime アセンブリが反映されます。</span><span class="sxs-lookup"><span data-stu-id="8a923-238">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a923-239">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a923-239">See Also</span></span>  
 [<span data-ttu-id="8a923-240">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a923-240">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="8a923-241">プログラミングの概念</span><span class="sxs-lookup"><span data-stu-id="8a923-241">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="8a923-242">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="8a923-242">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="8a923-243">アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a923-243">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
