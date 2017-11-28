---
title: "チュートリアル: Visual Studio でマネージ アセンブリからの型を埋め込む (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cbd95c71525a92714ab5758855964e323345b2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="fe744-102">チュートリアル: Visual Studio でマネージ アセンブリからの型を埋め込む (C#)</span><span class="sxs-lookup"><span data-stu-id="fe744-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="fe744-103">厳密な名前を持つマネージ アセンブリから型情報を埋め込むと、アプリケーション内で型を疎結合して、バージョンに依存しないプログラムを実現できます。</span><span class="sxs-lookup"><span data-stu-id="fe744-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="fe744-104">つまり、各バージョン用の再コンパイルを必要とすることなく、マネージ ライブラリの複数のバージョンから型を使用するプログラムを記述できます。</span><span class="sxs-lookup"><span data-stu-id="fe744-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="fe744-105">型の埋め込みは、COM 相互運用と共によく使用されます (Microsoft Office からのオートメーション オブジェクトを使用するアプリケーションなど)。</span><span class="sxs-lookup"><span data-stu-id="fe744-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="fe744-106">型情報を埋め込むと、同じビルドのプログラムを、別のコンピューター上にある別バージョンの Microsoft Office と連携させることができます。</span><span class="sxs-lookup"><span data-stu-id="fe744-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="fe744-107">ただし、型の埋め込みは完全なマネージ ソリューションと共に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="fe744-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="fe744-108">型情報は、次の特性を持つアセンブリから埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="fe744-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="fe744-109">アセンブリが、少なくとも 1 つのパブリック インターフェイスを公開している。</span><span class="sxs-lookup"><span data-stu-id="fe744-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="fe744-110">埋め込みインターフェイスに `ComImport` 属性と `Guid` 属性 (および一意の GUID) が付けられている。</span><span class="sxs-lookup"><span data-stu-id="fe744-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="fe744-111">アセンブリに、`ImportedFromTypeLib` 属性または `PrimaryInteropAssembly` 属性、およびアセンブリ レベルの `Guid` 属性が付けられている。</span><span class="sxs-lookup"><span data-stu-id="fe744-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="fe744-112">(既定では、アセンブリ レベルの `Guid` 属性は Visual C# プロジェクト テンプレートに含まれています。)</span><span class="sxs-lookup"><span data-stu-id="fe744-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="fe744-113">埋め込み可能なパブリック インターフェイスを指定したら、それらのインターフェイスを実装するランタイム クラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="fe744-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="fe744-114">その後、クライアント プログラムは、パブリック インターフェイスを含んだアセンブリを参照し、参照の `Embed Interop Types` プロパティを `True` に設定することで、デザイン時にそれらのインターフェイスの型情報を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="fe744-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="fe744-115">これは、コマンド ライン コンパイラを使用し、`/link` コンパイラ オプションを使用してアセンブリを参照することに相当します。</span><span class="sxs-lookup"><span data-stu-id="fe744-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="fe744-116">クライアント プログラムはその後、それらのインターフェイスとして型指定されたランタイム オブジェクトのインスタンスを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="fe744-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="fe744-117">厳密な名前を持つランタイム アセンブリの新バージョンを作成した場合、クライアント プログラムを、更新後のランタイム アセンブリで再コンパイルする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fe744-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="fe744-118">クライアント プログラムでは、パブリック インターフェイスの埋め込み型情報を使用して、利用可能なバージョンをどちらでも引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="fe744-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="fe744-119">型埋め込みの主な機能は、COM 相互運用アセンブリからの型情報の埋め込みをサポートすることなので、完全なマネージ ソリューションで型情報を埋め込む場合には、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="fe744-120">COM 相互運用に固有の属性のみが埋め込まれます。その他の属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="fe744-121">型がジェネリック パラメーターを使用していて、ジェネリック パラメーターの型が埋め込み型である場合、その型はアセンブリの境界を越えて使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="fe744-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="fe744-122">アセンブリの境界を越える場合の例としては、別のアセンブリからメソッドを呼び出す場合や、別のアセンブリで定義されている型から型を派生させる場合が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="fe744-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="fe744-123">定数は埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="fe744-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="fe744-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> クラスでは、埋め込み型をキーとして利用できません。</span><span class="sxs-lookup"><span data-stu-id="fe744-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="fe744-125">埋め込み型をキーとしてサポートするために、独自のディクショナリ型を実装することは可能です。</span><span class="sxs-lookup"><span data-stu-id="fe744-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="fe744-126">このチュートリアルでは、次のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="fe744-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="fe744-127">埋め込み可能な型情報を含んだパブリック インターフェイスを持つ、厳密な名前付きのアセンブリを作成する。</span><span class="sxs-lookup"><span data-stu-id="fe744-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="fe744-128">そのパブリック インターフェイスを実装する、厳密な名前付きのランタイム アセンブリを作成する。</span><span class="sxs-lookup"><span data-stu-id="fe744-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="fe744-129">パブリック インターフェイスから型情報を埋め込み、ランタイム アセンブリからクラスのインスタンスを作成する、クライアント プログラムを作成する。</span><span class="sxs-lookup"><span data-stu-id="fe744-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="fe744-130">ランタイム アセンブリを変更し、リビルドする。</span><span class="sxs-lookup"><span data-stu-id="fe744-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="fe744-131">クライアント プログラムを実行して、新バージョンのランタイム アセンブリが、クライアント プログラムを再コンパイルしなくても使用されていることを確認する。</span><span class="sxs-lookup"><span data-stu-id="fe744-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="fe744-132">インターフェイスの作成</span><span class="sxs-lookup"><span data-stu-id="fe744-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="fe744-133">型等価性インターフェイス プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="fe744-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="fe744-134">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をクリックし、**[プロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe744-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="fe744-135">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fe744-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="fe744-136">**[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe744-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="fe744-137">**[名前]** ボックスに `TypeEquivalenceInterface` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="fe744-138">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="fe744-139">**ソリューション エクスプローラー**で、 Class1.cs ファイルを右クリックし、**[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="fe744-140">ファイルの名前を `ISampleInterface.cs` に変更し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fe744-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="fe744-141">ファイルの名前を変更すると、クラスの名前も `ISampleInterface` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="fe744-142">このクラスは、クラスのパブリック インターフェイスを表します。</span><span class="sxs-lookup"><span data-stu-id="fe744-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="fe744-143">TypeEquivalenceInterface プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="fe744-144">**[ビルド]** タブをクリックします。開発用コンピューター上の有効な場所への出力パスを設定します (`C:\TypeEquivalenceSample` など)。</span><span class="sxs-lookup"><span data-stu-id="fe744-144">Click the the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="fe744-145">この場所は、このチュートリアルの後の手順でも使用されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="fe744-146">プロジェクト プロパティの編集を続けたまま、**[署名]** タブをクリックします。**[アセンブリの署名]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="fe744-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="fe744-147">**[厳密な名前のキー ファイルを選択してください]** ボックスの一覧で **[<新規作成...>]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="fe744-148">**[キー ファイル名]** ボックスに、「`key.snk`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="fe744-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="fe744-149">**[キーファイルをパスワードで保護する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="fe744-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="fe744-150">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="fe744-151">ISampleInterface.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="fe744-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="fe744-152">ISampleInterface クラス ファイルに、ISampleInterface インターフェイスを作成するための次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fe744-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
  
    namespace TypeEquivalenceInterface  
    {  
        [ComImport]  
        [Guid("8DA56996-A151-4136-B474-32784559F6DF")]  
        public interface ISampleInterface  
        {  
            void GetUserInput();  
            string UserInput { get; }  
        }  
    }  
    ```  
  
7.  <span data-ttu-id="fe744-153">**[ツール]** メニューの **[GUID の作成]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="fe744-154">**[GUID の作成]**ダイアログ ボックスで、**[レジストリ形式]** をクリックし、**[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="fe744-155">**[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="fe744-156">`Guid` 属性で、サンプルの GUID を削除し、**[GUID の作成]** ダイアログ ボックスからコピーした GUID を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="fe744-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="fe744-157">コピーした GUID から中かっこ ({}) を削除します。</span><span class="sxs-lookup"><span data-stu-id="fe744-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="fe744-158">**ソリューション エクスプローラー**で、**[プロパティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="fe744-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="fe744-159">AssemblyInfo.cs ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="fe744-160">ファイルに次の属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="fe744-160">Add the following attribute to the file.</span></span>  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     <span data-ttu-id="fe744-161">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="fe744-161">Save the file.</span></span>  
  
10. <span data-ttu-id="fe744-162">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="fe744-162">Save the project.</span></span>  
  
11. <span data-ttu-id="fe744-163">TypeEquivalenceInterface プロジェクトを右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="fe744-164">クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="fe744-165">ランタイム クラスの作成</span><span class="sxs-lookup"><span data-stu-id="fe744-165">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="fe744-166">型等価性ランタイム プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="fe744-166">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="fe744-167">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="fe744-168">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fe744-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="fe744-169">**[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe744-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="fe744-170">**[名前]** ボックスに `TypeEquivalenceRuntime` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="fe744-171">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-171">The new project is created.</span></span>  
  
3.  <span data-ttu-id="fe744-172">**ソリューション エクスプローラー**で、 Class1.cs ファイルを右クリックし、**[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="fe744-173">ファイルの名前を `SampleClass.cs` に変更し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fe744-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="fe744-174">ファイルの名前を変更すると、クラスの名前も `SampleClass` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="fe744-175">このクラスが `ISampleInterface` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="fe744-175">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="fe744-176">TypeEquivalenceRuntime プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="fe744-177">**[ビルド]** タブをクリックします。出力パスを、TypeEquivalenceInterface プロジェクトで使用したのと同じ場所に設定します (たとえば、`C:\TypeEquivalenceSample`)。</span><span class="sxs-lookup"><span data-stu-id="fe744-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="fe744-178">プロジェクト プロパティの編集を続けたまま、**[署名]** タブをクリックします。**[アセンブリの署名]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="fe744-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="fe744-179">**[厳密な名前のキー ファイルを選択してください]** ボックスの一覧で **[<新規作成...>]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-179">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="fe744-180">**[キー ファイル名]** ボックスに、「`key.snk`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="fe744-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="fe744-181">**[キーファイルをパスワードで保護する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="fe744-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="fe744-182">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-182">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="fe744-183">TypeEquivalenceRuntime プロジェクトを右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="fe744-184">**[参照]** タブをクリックし、出力パスのフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="fe744-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="fe744-185">TypeEquivalenceInterface.dll ファイルを選択し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="fe744-186">**ソリューション エクスプローラー**で、**[参照]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="fe744-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="fe744-187">TypeEquivalenceInterface 参照を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe744-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="fe744-188">TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、**[特定バージョン]** プロパティを **[False]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="fe744-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
8.  <span data-ttu-id="fe744-189">SampleClass クラス ファイルに、SampleClass クラスを作成するための次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fe744-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using TypeEquivalenceInterface;  
  
    namespace TypeEquivalenceRuntime  
    {  
        public class SampleClass : ISampleInterface  
        {  
            private string p_UserInput;  
            public string UserInput { get { return p_UserInput; } }  
  
            public void GetUserInput()  
            {  
                Console.WriteLine("Please enter a value:");  
                p_UserInput = Console.ReadLine();  
            }  
        }  
    )  
    ```  
  
9. <span data-ttu-id="fe744-190">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="fe744-190">Save the project.</span></span>  
  
10. <span data-ttu-id="fe744-191">TypeEquivalenceRuntime プロジェクトを右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="fe744-192">クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="fe744-193">クライアント プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="fe744-193">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="fe744-194">型等価性クライアント プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="fe744-194">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="fe744-195">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="fe744-196">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fe744-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="fe744-197">**[テンプレート]** ペインの **[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe744-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="fe744-198">**[名前]** ボックスに `TypeEquivalenceClient` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="fe744-199">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-199">The new project is created.</span></span>  
  
3.  <span data-ttu-id="fe744-200">TypeEquivalenceClient プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="fe744-201">**[ビルド]** タブをクリックします。出力パスを、TypeEquivalenceInterface プロジェクトで使用したのと同じ場所に設定します (たとえば、`C:\TypeEquivalenceSample`)。</span><span class="sxs-lookup"><span data-stu-id="fe744-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="fe744-202">TypeEquivalenceClient プロジェクトを右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="fe744-203">**[参照]** タブをクリックし、出力パスのフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="fe744-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="fe744-204">TypeEquivalenceInterface.dll ファイル (TypeEquivalenceRuntime.dll ではない) を選択し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="fe744-205">**ソリューション エクスプローラー**で、**[参照]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="fe744-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="fe744-206">TypeEquivalenceInterface 参照を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe744-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="fe744-207">TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、**[相互運用型の埋め込み]** プロパティを **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="fe744-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
6.  <span data-ttu-id="fe744-208">Program.cs ファイルに、クライアント プログラムを作成するための次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fe744-208">Add the following code to the Program.cs file to create the client program.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using TypeEquivalenceInterface;  
    using System.Reflection;  
  
    namespace TypeEquivalenceClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");  
                ISampleInterface sampleClass =   
                    (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");  
                sampleClass.GetUserInput();  
                Console.WriteLine(sampleClass.UserInput);  
                Console.WriteLine(sampleAssembly.GetName().Version.ToString());  
                Console.ReadLine();  
            }  
        }  
    }  
    ```  
  
7.  <span data-ttu-id="fe744-209">Ctrl キーを押しながら F5 キーを押して、プログラムをビルドおよび実行します。</span><span class="sxs-lookup"><span data-stu-id="fe744-209">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="fe744-210">インターフェイスの変更</span><span class="sxs-lookup"><span data-stu-id="fe744-210">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="fe744-211">インターフェイスを変更するには</span><span class="sxs-lookup"><span data-stu-id="fe744-211">To modify the interface</span></span>  
  
1.  <span data-ttu-id="fe744-212">Visual Studio で、**[ファイル]** メニューの **[開く]** をポイントし、**[プロジェクト/ソリューション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="fe744-213">**[プロジェクトを開く]** ダイアログ ボックスで、TypeEquivalenceInterface プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="fe744-214">**[アプリケーション]** タブをクリックします。**[アセンブリ情報]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="fe744-215">**[アセンブリ バージョン]** と **[ファイル バージョン]** の値を `2.0.0.0` に変更します。</span><span class="sxs-lookup"><span data-stu-id="fe744-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="fe744-216">SampleInterface.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="fe744-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="fe744-217">ISampleInterface インターフェイスに、次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="fe744-217">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     <span data-ttu-id="fe744-218">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="fe744-218">Save the file.</span></span>  
  
4.  <span data-ttu-id="fe744-219">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="fe744-219">Save the project.</span></span>  
  
5.  <span data-ttu-id="fe744-220">TypeEquivalenceInterface プロジェクトを右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="fe744-221">クラス ライブラリ .dll ファイルの新バージョンがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="fe744-222">ランタイム クラスの変更</span><span class="sxs-lookup"><span data-stu-id="fe744-222">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="fe744-223">ランタイム クラスを変更するには</span><span class="sxs-lookup"><span data-stu-id="fe744-223">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="fe744-224">Visual Studio で、**[ファイル]** メニューの **[開く]** をポイントし、**[プロジェクト/ソリューション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="fe744-225">**[プロジェクトを開く]** ダイアログ ボックスで、TypeEquivalenceRuntime プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="fe744-226">**[アプリケーション]** タブをクリックします。**[アセンブリ情報]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="fe744-227">**[アセンブリ バージョン]** と **[ファイル バージョン]** の値を `2.0.0.0` に変更します。</span><span class="sxs-lookup"><span data-stu-id="fe744-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="fe744-228">SampleClass.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="fe744-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="fe744-229">SampleClass クラスに次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="fe744-229">Add the following lines of code to the SampleClass class.</span></span>  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     <span data-ttu-id="fe744-230">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="fe744-230">Save the file.</span></span>  
  
4.  <span data-ttu-id="fe744-231">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="fe744-231">Save the project.</span></span>  
  
5.  <span data-ttu-id="fe744-232">TypeEquivalenceRuntime プロジェクトを右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe744-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="fe744-233">クラス ライブラリ .dll ファイルの更新バージョンがコンパイルされ、前に指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="fe744-234">ファイル エクスプローラーで、出力パスのフォルダー (たとえば、C:\TypeEquivalenceSample) を開きます。</span><span class="sxs-lookup"><span data-stu-id="fe744-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="fe744-235">TypeEquivalenceClient.exe をダブルクリックして、プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="fe744-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="fe744-236">プログラムでは、再コンパイルを行わなくても、新バージョンの TypeEquivalenceRuntime アセンブリが反映されます。</span><span class="sxs-lookup"><span data-stu-id="fe744-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe744-237">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe744-237">See Also</span></span>  
 [<span data-ttu-id="fe744-238">/link (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="fe744-238">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="fe744-239">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="fe744-239">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fe744-240">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="fe744-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="fe744-241">アセンブリとグローバル アセンブリ キャッシュ (C#)</span><span class="sxs-lookup"><span data-stu-id="fe744-241">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
