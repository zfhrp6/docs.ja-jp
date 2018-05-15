---
title: '方法: 登録を必要としないアクティベーション用の .NET Framework ベースの COM コンポーネントを構成する'
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 744ce1f2810eee025f071cafaa71e473b6ed4c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="d0321-102">方法: 登録を必要としないアクティベーション用の .NET Framework ベースの COM コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="d0321-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="d0321-103">.NET Framework ベースのコンポーネントの登録を必要としないアクティベーションは、COM コンポーネントの場合よりも少しだけ複雑です。</span><span class="sxs-lookup"><span data-stu-id="d0321-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="d0321-104">セットアップには 2 つのマニフェストが必要です。</span><span class="sxs-lookup"><span data-stu-id="d0321-104">The setup requires two manifests:</span></span>  
  
-   <span data-ttu-id="d0321-105">COM アプリケーションには、マネージ コンポーネントを識別するための Win32 スタイルのアプリケーション マニフェストが必要です。</span><span class="sxs-lookup"><span data-stu-id="d0321-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
-   <span data-ttu-id="d0321-106">.NET Framework ベースのコンポーネントには、実行時に必要なアクティベーション情報のコンポーネント マニフェストが必要です。</span><span class="sxs-lookup"><span data-stu-id="d0321-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="d0321-107">このトピックでは、アプリケーション マニフェストをアプリケーションに関連付ける方法、コンポーネント マニフェストをコンポーネントに関連付ける方法、およびコンポーネント マニフェストをアセンブリに埋め込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d0321-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="d0321-108">アプリケーション マニフェストを作成するには</span><span class="sxs-lookup"><span data-stu-id="d0321-108">To create an application manifest</span></span>  
  
1.  <span data-ttu-id="d0321-109">XML エディターを使用して、1 つ以上のマネージ コンポーネントと相互運用する COM アプリケーションによって所有されるアプリケーション マニフェストを作成または編集します。</span><span class="sxs-lookup"><span data-stu-id="d0321-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2.  <span data-ttu-id="d0321-110">ファイルの先頭に次の標準ヘッダーを挿入します。</span><span class="sxs-lookup"><span data-stu-id="d0321-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="d0321-111">マニフェストの要素とその属性については、次を参照してください。[アプリケーション マニフェスト](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="d0321-111">For information about manifest elements and their attributes, see [Application Manifests](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx).</span></span>  
  
3.  <span data-ttu-id="d0321-112">マニフェストの所有者を指定します。</span><span class="sxs-lookup"><span data-stu-id="d0321-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="d0321-113">次の例では、`myComApp` バージョン 1 がマニフェスト ファイルを所有しています。</span><span class="sxs-lookup"><span data-stu-id="d0321-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  <span data-ttu-id="d0321-114">依存アセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0321-114">Identify dependent assemblies.</span></span> <span data-ttu-id="d0321-115">`myComApp` が `myManagedComp` に依存する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d0321-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5.  <span data-ttu-id="d0321-116">マニフェスト ファイルに名前を付けて保存します。</span><span class="sxs-lookup"><span data-stu-id="d0321-116">Save and name the manifest file.</span></span> <span data-ttu-id="d0321-117">アプリケーション マニフェストの名前は、アセンブリ実行可能ファイルの名前に拡張子 .manifest が付いたものです。</span><span class="sxs-lookup"><span data-stu-id="d0321-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="d0321-118">たとえば、myComApp.exe のアプリケーション マニフェスト ファイル名は myComApp.exe.manifest です。</span><span class="sxs-lookup"><span data-stu-id="d0321-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="d0321-119">アプリケーション マニフェストは、COM アプリケーションと同じディレクトリにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="d0321-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="d0321-120">また、アプリケーションの .exe ファイルにリソースとして追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="d0321-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="d0321-121">詳細については、詳細については、次を参照してください。[サイド バイ サイド アセンブリに関する](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="d0321-121">For additional information, For more information, see [About Side-by-Side Assemblies](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="d0321-122">コンポーネント マニフェストを作成するには</span><span class="sxs-lookup"><span data-stu-id="d0321-122">To create a component manifest</span></span>  
  
1.  <span data-ttu-id="d0321-123">XML エディターを使用して、マネージ アセンブリを記述するコンポーネント マニフェストを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0321-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2.  <span data-ttu-id="d0321-124">ファイルの先頭に次の標準ヘッダーを挿入します。</span><span class="sxs-lookup"><span data-stu-id="d0321-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  <span data-ttu-id="d0321-125">ファイルの所有者を指定します。</span><span class="sxs-lookup"><span data-stu-id="d0321-125">Identify the owner of the file.</span></span> <span data-ttu-id="d0321-126">アプリケーション マニフェスト ファイル内の `<assemblyIdentity>` 要素の `<dependentAssembly>` 要素は、コンポーネント マニフェスト内の要素と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0321-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="d0321-127">次の例では、`myManagedComp` バージョン 1.2.3.4 がマニフェスト ファイルを所有しています。</span><span class="sxs-lookup"><span data-stu-id="d0321-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4.  <span data-ttu-id="d0321-128">アセンブリ内の各クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0321-128">Identify each class in the assembly.</span></span> <span data-ttu-id="d0321-129">マネージ アセンブリ内の各クラスを一意に識別するには `<clrClass>` 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="d0321-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="d0321-130">この要素は、`<assembly>` 要素のサブ要素であり、次の表に示す属性を持っています。</span><span class="sxs-lookup"><span data-stu-id="d0321-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="d0321-131">属性</span><span class="sxs-lookup"><span data-stu-id="d0321-131">Attribute</span></span>|<span data-ttu-id="d0321-132">説明</span><span class="sxs-lookup"><span data-stu-id="d0321-132">Description</span></span>|<span data-ttu-id="d0321-133">必須</span><span class="sxs-lookup"><span data-stu-id="d0321-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="d0321-134">アクティブにするクラスを指定する識別子。</span><span class="sxs-lookup"><span data-stu-id="d0321-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="d0321-135">[はい]</span><span class="sxs-lookup"><span data-stu-id="d0321-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="d0321-136">ユーザーにコンポーネントを説明する文字列。</span><span class="sxs-lookup"><span data-stu-id="d0321-136">A string that informs the user about the component.</span></span> <span data-ttu-id="d0321-137">既定では文字列は空です。</span><span class="sxs-lookup"><span data-stu-id="d0321-137">An empty string is the default.</span></span>|<span data-ttu-id="d0321-138">×</span><span class="sxs-lookup"><span data-stu-id="d0321-138">No</span></span>|  
    |`name`|<span data-ttu-id="d0321-139">マネージ クラスを表す文字列。</span><span class="sxs-lookup"><span data-stu-id="d0321-139">A string that represents the managed class.</span></span>|<span data-ttu-id="d0321-140">[はい]</span><span class="sxs-lookup"><span data-stu-id="d0321-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="d0321-141">遅延バインディングによるアクティベーションで使用される識別子。</span><span class="sxs-lookup"><span data-stu-id="d0321-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="d0321-142">×</span><span class="sxs-lookup"><span data-stu-id="d0321-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="d0321-143">COM スレッド モデル。</span><span class="sxs-lookup"><span data-stu-id="d0321-143">The COM threading model.</span></span> <span data-ttu-id="d0321-144">"Both" が既定値です。</span><span class="sxs-lookup"><span data-stu-id="d0321-144">"Both" is the default value.</span></span>|<span data-ttu-id="d0321-145">×</span><span class="sxs-lookup"><span data-stu-id="d0321-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="d0321-146">使用する共通言語ランタイム (CLR: Common Language Runtime) のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0321-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="d0321-147">この属性を指定せず、CLR がまだ読み込まれていない場合は、インストールされている最新の CLR (CLR Version 4 よりも前のバージョン) でコンポーネントが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d0321-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="d0321-148">v1.0.3705、v1.1.4322、または v2.0.50727 を指定すると、インストールされている最新の CLR バージョン (CLR Version 4 よりも前のバージョン。通常は v2.0.50727) に自動的にロールフォワードされます。</span><span class="sxs-lookup"><span data-stu-id="d0321-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="d0321-149">別のバージョンの CLR が既に読み込まれていて、指定されたバージョンをインプロセスで並行して (side-by-side で) 読み込むことができる場合は、指定されたバージョンが読み込まれます。それ以外の場合は、読み込まれた CLR が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d0321-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="d0321-150">これにより、読み込みエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d0321-150">This might cause a load failure.</span></span>|<span data-ttu-id="d0321-151">×</span><span class="sxs-lookup"><span data-stu-id="d0321-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="d0321-152">クラスに関する型情報を格納するタイプ ライブラリの識別子。</span><span class="sxs-lookup"><span data-stu-id="d0321-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="d0321-153">×</span><span class="sxs-lookup"><span data-stu-id="d0321-153">No</span></span>|  
  
     <span data-ttu-id="d0321-154">属性タグはすべて大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="d0321-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="d0321-155">OLE/COM オブジェクト ビューアー (Oleview.exe) で、エクスポートされたアセンブリのタイプ ライブラリを表示することによって、CLSID、ProgID、スレッド モデル、およびランタイムのバージョンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="d0321-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="d0321-156">`testClass1` および `testClass2` という 2 つのクラスを識別するコンポーネント マニフェストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d0321-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"   
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5.  <span data-ttu-id="d0321-157">マニフェスト ファイルに名前を付けて保存します。</span><span class="sxs-lookup"><span data-stu-id="d0321-157">Save and name the manifest file.</span></span> <span data-ttu-id="d0321-158">コンポーネント マニフェストの名前は、アセンブリ ライブラリの名前に拡張子 .manifest が付いたものです。</span><span class="sxs-lookup"><span data-stu-id="d0321-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="d0321-159">たとえば、myManagedComp.dll の場合は、myManagedComp.manifest になります。</span><span class="sxs-lookup"><span data-stu-id="d0321-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="d0321-160">コンポーネント マニフェストはリソースとしてアセンブリに埋め込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0321-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="d0321-161">コンポーネント マニフェストをマネージ アセンブリに埋め込むには</span><span class="sxs-lookup"><span data-stu-id="d0321-161">To embed a component manifest in a managed assembly</span></span>  
  
1.  <span data-ttu-id="d0321-162">次のステートメントを含むリソース スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0321-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="d0321-163">このステートメントで、`myManagedComp.manifest` は埋め込むコンポーネント マニフェストの名前です。</span><span class="sxs-lookup"><span data-stu-id="d0321-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="d0321-164">この例では、スクリプト ファイル名は `myresource.rc` です。</span><span class="sxs-lookup"><span data-stu-id="d0321-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2.  <span data-ttu-id="d0321-165">Microsoft Windows リソース コンパイラ (Rc.exe) を使用してスクリプトをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="d0321-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="d0321-166">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="d0321-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="d0321-167">Rc.exe は `myresource.res` リソース ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="d0321-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3.  <span data-ttu-id="d0321-168">もう一度アセンブリのソース ファイルをコンパイルし、**/win32res** オプションを使用してリソース ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0321-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     <span data-ttu-id="d0321-169">ここでも、`myresource.res` は埋め込むリソースを含むリソース ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="d0321-169">Again, `myresource.res` is the name of the resource file containing embedded resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0321-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0321-170">See Also</span></span>  
 [<span data-ttu-id="d0321-171">登録を必要としない COM 相互運用機能</span><span class="sxs-lookup"><span data-stu-id="d0321-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
 <span data-ttu-id="d0321-172">[登録を必要としない COM 相互運用機能の要件](https://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da(v=vs.100)))</span><span class="sxs-lookup"><span data-stu-id="d0321-172">[Requirements for Registration-Free COM Interop](https://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da(v=vs.100)))</span></span>  
 <span data-ttu-id="d0321-173">[登録を必要としないアクティベーション用の COM コンポーネントを構成する](https://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe(v=vs.100)))</span><span class="sxs-lookup"><span data-stu-id="d0321-173">[Configuring COM Components for Registration-Free Activation](https://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe(v=vs.100)))</span></span>  
 [<span data-ttu-id="d0321-174">.NET ベースのコンポーネントの登録を必要としないアクティベーション: チュートリアル</span><span class="sxs-lookup"><span data-stu-id="d0321-174">Registration-Free Activation of .NET-Based Components: A Walkthrough</span></span>](https://msdn.microsoft.com/library/ms973915.aspx)
