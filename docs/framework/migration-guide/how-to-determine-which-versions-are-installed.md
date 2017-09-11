---
title: "方法: インストールされている .NET Framework バージョンを確認する"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
caps.latest.revision: 62
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cddee407d1245568054871d71f2840f463859535
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="28ce4-102">方法 : インストールされている .NET Framework バージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="28ce4-102">How to: Determine Which .NET Framework Versions Are Installed</span></span>
<span data-ttu-id="28ce4-103">ユーザーはコンピューターに複数のバージョンの .NET Framework をインストールして実行できます。</span><span class="sxs-lookup"><span data-stu-id="28ce4-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="28ce4-104">アプリを開発または配置する場合、どのバージョンの .NET Framework がユーザーのコンピューターにインストールされているかを確認しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="28ce4-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="28ce4-105">.NET Framework は、個別にバージョン管理される 2 つの主要コンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="28ce4-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="28ce4-106">アプリに機能を提供する型やリソースのコレクションである一連のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="28ce4-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="28ce4-107">.NET Framework とアセンブリは同じバージョン番号を共有します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="28ce4-108">アプリのコードを管理および実行する共通言語ランタイム (CLR)。</span><span class="sxs-lookup"><span data-stu-id="28ce4-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="28ce4-109">CLR は独自のバージョン番号で識別されます (「[バージョンおよび依存関係](~/docs/framework/migration-guide/versions-and-dependencies.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="28ce4-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="28ce4-110">コンピューターにインストールされている .NET Framework バージョンの正確な一覧を取得するには、レジストリを表示するか、コードでレジストリを照会することができます。</span><span class="sxs-lookup"><span data-stu-id="28ce4-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="28ce4-111">レジストリの表示 (バージョン 1 ～ 4)</span><span class="sxs-lookup"><span data-stu-id="28ce4-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="28ce4-112">レジストリの表示 (バージョン 4.5 以降)</span><span class="sxs-lookup"><span data-stu-id="28ce4-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="28ce4-113">コードによるレジストリの照会 (バージョン 1 ～ 4)</span><span class="sxs-lookup"><span data-stu-id="28ce4-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="28ce4-114">コードによるレジストリの照会 (バージョン 4.5 以降)</span><span class="sxs-lookup"><span data-stu-id="28ce4-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
  
 <span data-ttu-id="28ce4-115">CLR のバージョンを検索するには、ツールまたはコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="28ce4-115">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="28ce4-116">Clrver ツールの使用</span><span class="sxs-lookup"><span data-stu-id="28ce4-116">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="28ce4-117">コードによる System.Environment クラスの照会</span><span class="sxs-lookup"><span data-stu-id="28ce4-117">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="28ce4-118">.NET Framework の各バージョン用にインストールされている更新プログラムを検出する方法については、「[方法: インストールされている .NET Framework の更新プログラムを確認する](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28ce4-118">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="28ce4-119">.NET Framework のインストールの詳細については、「[開発者向けの .NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28ce4-119">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="28ce4-120">レジストリを表示して .NET Framework のバージョンを検索するには (.NET Framework 1 ～ 4)</span><span class="sxs-lookup"><span data-stu-id="28ce4-120">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="28ce4-121">[**スタート**] ボタンをクリックし、[**ファイル名を指定して実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28ce4-121">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="28ce4-122">[**開く**] ボックスに「**regedit.exe**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-122">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="28ce4-123">regedit.exe を実行するには、管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="28ce4-123">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="28ce4-124">レジストリ エディターで、次のサブキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="28ce4-124">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="28ce4-125">インストールされているバージョンは NDP のサブキーの下に一覧表示されています。</span><span class="sxs-lookup"><span data-stu-id="28ce4-125">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="28ce4-126">バージョン番号は、**Version** エントリに格納されています。</span><span class="sxs-lookup"><span data-stu-id="28ce4-126">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="28ce4-127">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、**Version** エントリは、Client サブキーまたは Full サブキー (NDP の下)、または両方のサブキーの下にあります。</span><span class="sxs-lookup"><span data-stu-id="28ce4-127">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="28ce4-128">レジストリの ".NET Framework セットアップ" フォルダーの先頭はピリオドではありません。</span><span class="sxs-lookup"><span data-stu-id="28ce4-128">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="28ce4-129">レジストリを表示して .NET Framework のバージョンを検索するには (.NET Framework 4.5 以降)</span><span class="sxs-lookup"><span data-stu-id="28ce4-129">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="28ce4-130">[**スタート**] ボタンをクリックし、[**ファイル名を指定して実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28ce4-130">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="28ce4-131">[**開く**] ボックスに「**regedit.exe**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-131">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="28ce4-132">regedit.exe を実行するには、管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="28ce4-132">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="28ce4-133">レジストリ エディターで、次のサブキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="28ce4-133">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="28ce4-134">`Full` サブキーへのパスに `.NET Framework` ではなく `Net Framework` サブキーが含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="28ce4-134">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="28ce4-135">`Full` サブキーが存在しない場合は、.NET Framework 4.5 以降がインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="28ce4-135">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="28ce4-136">`Release` という名前の DWORD 値を確認します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-136">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="28ce4-137">`Release` DWORD がある場合は、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降がコンピューターにインストールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-137">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="28ce4-138">![.NET Framework 4.5 のレジストリ エントリ。](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="28ce4-138">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="28ce4-139">`Release` の値は、インストールされている .NET Framework のバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-139">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    |<span data-ttu-id="28ce4-140">Release DWORD の値</span><span class="sxs-lookup"><span data-stu-id="28ce4-140">Value of the Release DWORD</span></span>|<span data-ttu-id="28ce4-141">バージョン</span><span class="sxs-lookup"><span data-stu-id="28ce4-141">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="28ce4-142">378389</span><span class="sxs-lookup"><span data-stu-id="28ce4-142">378389</span></span>|<span data-ttu-id="28ce4-143">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="28ce4-143">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="28ce4-144">378675</span><span class="sxs-lookup"><span data-stu-id="28ce4-144">378675</span></span>|<span data-ttu-id="28ce4-145">Windows 8.1 または Windows Server 2012 R2 でインストールされた .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="28ce4-145">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="28ce4-146">378758</span><span class="sxs-lookup"><span data-stu-id="28ce4-146">378758</span></span>|<span data-ttu-id="28ce4-147">Windows 8、Windows 7 SP1、または Windows Vista SP2 上でインストールされた .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="28ce4-147">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="28ce4-148">379893</span><span class="sxs-lookup"><span data-stu-id="28ce4-148">379893</span></span>|<span data-ttu-id="28ce4-149">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="28ce4-149">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="28ce4-150">Windows 10 システム上: 393295</span><span class="sxs-lookup"><span data-stu-id="28ce4-150">On Windows 10 systems: 393295</span></span><br /><br /> <span data-ttu-id="28ce4-151">その他すべての OS バージョン上: 393297</span><span class="sxs-lookup"><span data-stu-id="28ce4-151">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="28ce4-152">Windows 10 の 11 月更新版のシステムの場合: 394254</span><span class="sxs-lookup"><span data-stu-id="28ce4-152">On Windows 10 November Update systems: 394254</span></span><br /><br /> <span data-ttu-id="28ce4-153">他のすべての OS バージョンの場合: 394271</span><span class="sxs-lookup"><span data-stu-id="28ce4-153">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="28ce4-154">Windows 10 Anniversary Update の場合: 394802</span><span class="sxs-lookup"><span data-stu-id="28ce4-154">On Windows 10 Anniversary Update: 394802</span></span><br /><br /> <span data-ttu-id="28ce4-155">他のすべての OS バージョンの場合: 394806</span><span class="sxs-lookup"><span data-stu-id="28ce4-155">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="28ce4-156">Windows 10 Creators Update の場合: 460798</span><span class="sxs-lookup"><span data-stu-id="28ce4-156">On Windows 10 Creators Update: 460798</span></span><br/><br/> <span data-ttu-id="28ce4-157">その他すべての OS バージョン上: 460805</span><span class="sxs-lookup"><span data-stu-id="28ce4-157">On all other OS versions: 460805</span></span> | <span data-ttu-id="28ce4-158">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="28ce4-158">.NET Framework 4.7</span></span> |

<a name="net_c"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="28ce4-159">コードでレジストリを照会して .NET Framework のバージョンを検索するには (.NET Framework 1 ～ 4)</span><span class="sxs-lookup"><span data-stu-id="28ce4-159">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="28ce4-160"><xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> クラスを使用して、Windows レジストリの HKEY_LOCAL_MACHINE の下にある Software\Microsoft\NET Framework Setup\NDP\ サブキーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="28ce4-160">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="28ce4-161">このクエリの例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-161">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="28ce4-162">このコードは [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降を検出する方法を示すコードではありません。</span><span class="sxs-lookup"><span data-stu-id="28ce4-162">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="28ce4-163">前のセクションで説明したように、これらのバージョンを検出するには、`Release` DWORD を確認してください。</span><span class="sxs-lookup"><span data-stu-id="28ce4-163">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="28ce4-164">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降のバージョンを検出するコードについては、この記事の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="28ce4-164">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     <span data-ttu-id="28ce4-165">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]</span><span class="sxs-lookup"><span data-stu-id="28ce4-165">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]</span></span>

     <span data-ttu-id="28ce4-166">この例では次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="28ce4-166">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="28ce4-167">コードでレジストリを照会して .NET Framework のバージョンを検索するには (.NET Framework 4.5 以降)</span><span class="sxs-lookup"><span data-stu-id="28ce4-167">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="28ce4-168">`Release` DWORD がある場合は、.NET Framework 4.5 以降がコンピューターにインストールされています。</span><span class="sxs-lookup"><span data-stu-id="28ce4-168">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="28ce4-169">キーワードの値はインストールされているバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-169">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="28ce4-170">このキーワードを確認するには、<xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> クラスの <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> メソッドと <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> メソッドを使って、Windows レジストリの HKEY_LOCAL_MACHINE の下にある Software\Microsoft\NET Framework Setup\NDP\v4\Full サブキーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="28ce4-170">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="28ce4-171">`Release` キーワードの値を確認して、インストールされているバージョンを決定します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-171">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="28ce4-172">上位互換性を確認するには、テーブルに示されている値以上の値があるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-172">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="28ce4-173">.NET Framework のバージョンと関連付けられた `Release` キーワードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-173">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    |<span data-ttu-id="28ce4-174">バージョン</span><span class="sxs-lookup"><span data-stu-id="28ce4-174">Version</span></span>|<span data-ttu-id="28ce4-175">Release DWORD の値</span><span class="sxs-lookup"><span data-stu-id="28ce4-175">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="28ce4-176">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="28ce4-176">.NET Framework 4.5</span></span>|<span data-ttu-id="28ce4-177">378389</span><span class="sxs-lookup"><span data-stu-id="28ce4-177">378389</span></span>|
    |<span data-ttu-id="28ce4-178">Windows 8.1 でインストールされた .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="28ce4-178">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="28ce4-179">378675</span><span class="sxs-lookup"><span data-stu-id="28ce4-179">378675</span></span>|
    |<span data-ttu-id="28ce4-180">Windows 8、Windows 7 SP1、または Windows Vista SP2 上でインストールされた .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="28ce4-180">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="28ce4-181">378758</span><span class="sxs-lookup"><span data-stu-id="28ce4-181">378758</span></span>|
    |<span data-ttu-id="28ce4-182">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="28ce4-182">.NET Framework 4.5.2</span></span>|<span data-ttu-id="28ce4-183">379893</span><span class="sxs-lookup"><span data-stu-id="28ce4-183">379893</span></span>|
    |<span data-ttu-id="28ce4-184">Windows 10 にインストールされた [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ce4-184">[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] installed with Windows 10</span></span>|<span data-ttu-id="28ce4-185">393295</span><span class="sxs-lookup"><span data-stu-id="28ce4-185">393295</span></span>|
    |<span data-ttu-id="28ce4-186">その他のすべての Windows OS バージョンにインストールされた [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ce4-186">[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] installed on all other Windows OS versions</span></span>|<span data-ttu-id="28ce4-187">393297</span><span class="sxs-lookup"><span data-stu-id="28ce4-187">393297</span></span>|
    |<span data-ttu-id="28ce4-188">Windows 10 にインストールされる [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ce4-188">[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] installed on Windows 10</span></span>|<span data-ttu-id="28ce4-189">394254</span><span class="sxs-lookup"><span data-stu-id="28ce4-189">394254</span></span>|
    |<span data-ttu-id="28ce4-190">その他のすべての Windows OS バージョンにインストールされた [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ce4-190">[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] installed on all other Windows OS versions</span></span>|<span data-ttu-id="28ce4-191">394271</span><span class="sxs-lookup"><span data-stu-id="28ce4-191">394271</span></span>|
    |<span data-ttu-id="28ce4-192">Windows 10 Anniversary Update にインストールされる [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ce4-192">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] installed on Windows 10 Anniversary Update</span></span>|<span data-ttu-id="28ce4-193">394802</span><span class="sxs-lookup"><span data-stu-id="28ce4-193">394802</span></span>|
    |<span data-ttu-id="28ce4-194">その他のすべての Windows OS バージョンにインストールされた [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ce4-194">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] installed on all other Windows OS versions</span></span>|<span data-ttu-id="28ce4-195">394806</span><span class="sxs-lookup"><span data-stu-id="28ce4-195">394806</span></span>|
    |<span data-ttu-id="28ce4-196">Windows 10 Creators Update にインストールされた .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="28ce4-196">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="28ce4-197">460798</span><span class="sxs-lookup"><span data-stu-id="28ce4-197">460798</span></span>|
    |<span data-ttu-id="28ce4-198">その他のすべての Windows OS バージョンにインストールされた .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="28ce4-198">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="28ce4-199">460805</span><span class="sxs-lookup"><span data-stu-id="28ce4-199">460805</span></span>|

     <span data-ttu-id="28ce4-200">レジストリの `Release` 値を確認して [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降のバージョンの .NET Framework がインストールされているかどうかを判断する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-200">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     <span data-ttu-id="28ce4-201">[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]   [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]</span><span class="sxs-lookup"><span data-stu-id="28ce4-201">[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]   [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]</span></span>

     <span data-ttu-id="28ce4-202">この例では、バージョンのチェックで推奨されている方法に従います。</span><span class="sxs-lookup"><span data-stu-id="28ce4-202">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="28ce4-203">`Release` エントリの値が既知のリリース キー値*以上*かどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="28ce4-203">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="28ce4-204">最新バージョンから最も古いバージョンの順にチェックします。</span><span class="sxs-lookup"><span data-stu-id="28ce4-204">It checks in order from most recent version to earliest version.</span></span>

<a name="clr_a"></a> 
#### <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="28ce4-205">Clrver ツールを使用して現在のランタイムのバージョンを確認する方法</span><span class="sxs-lookup"><span data-stu-id="28ce4-205">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="28ce4-206">CLR バージョン ツール (Clrver.exe) を使用して、コンピューターにインストールされている共通言語ランタイムのバージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-206">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="28ce4-207">Visual Studio コマンド プロンプトで、「`clrver`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-207">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="28ce4-208">次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="28ce4-208">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="28ce4-209">このツールの使用については、「[Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28ce4-209">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
#### <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="28ce4-210">コードで Environment クラスを照会して現在のランタイム バージョンを確認するには</span><span class="sxs-lookup"><span data-stu-id="28ce4-210">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="28ce4-211"><xref:System.Environment.Version%2A?displayProperty=fullName> プロパティを照会して <xref:System.Version> オブジェクトを取得し、現在コードを実行しているランタイムのバージョンを識別します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-211">Query the <xref:System.Environment.Version%2A?displayProperty=fullName> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="28ce4-212">メジャー リリースの識別子 (バージョン 4.0 の "4" など) を取得するには <xref:System.Version.Major%2A?displayProperty=fullName> プロパティを、マイナー リリースの識別子 (バージョン 4.0 の "0" など) を取得するには <xref:System.Version.Minor%2A?displayProperty=fullName> プロパティを、バージョン文字列全体 (次のコードに示すような "4.0.30319.18010" など) を取得するには <xref:System.Object.ToString%2A?displayProperty=fullName> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="28ce4-212">You can use the <xref:System.Version.Major%2A?displayProperty=fullName> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=fullName> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=fullName> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="28ce4-213">このプロパティは、現在コードを実行しているランタイムのバージョンを表す単一の値を返しますが、アセンブリのバージョンやコンピューターにインストールされている可能性があるランタイムの他のバージョンは返しません。</span><span class="sxs-lookup"><span data-stu-id="28ce4-213">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="28ce4-214">.NET Framework バージョン 4、4.5、4.5.1、および 4.5.2 の場合は、<xref:System.Environment.Version%2A?displayProperty=fullName> プロパティから返される <xref:System.Version> オブジェクトの文字列表現が `4.0.30319.xxxxx` という形式になっています。</span><span class="sxs-lookup"><span data-stu-id="28ce4-214">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=fullName> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="28ce4-215">.NET Framework 4.6 以降の場合は、`4.0.30319.42000` という形式です。</span><span class="sxs-lookup"><span data-stu-id="28ce4-215">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="28ce4-216">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降の場合、ランタイムのバージョンの検出に <xref:System.Environment.Version%2A?displayProperty=fullName> プロパティを使用することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="28ce4-216">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=fullName> property to detect the version of the runtime.</span></span> <span data-ttu-id="28ce4-217">代わりに、この記事で前述した「[コードでレジストリを照会して .NET Framework のバージョンを検索するには (.NET Framework 4.5 以降)](#net_d)」に従って、レジストリを紹介することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="28ce4-217">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="28ce4-218">次に、<xref:System.Environment.Version%2A?displayProperty=fullName> プロパティを照会してランタイム バージョン情報を取得する例を示します。</span><span class="sxs-lookup"><span data-stu-id="28ce4-218">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=fullName> property for runtime version information:</span></span>

     <span data-ttu-id="28ce4-219">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]</span><span class="sxs-lookup"><span data-stu-id="28ce4-219">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]</span></span>

     <span data-ttu-id="28ce4-220">この例では次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="28ce4-220">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="28ce4-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="28ce4-221">See Also</span></span>
 <span data-ttu-id="28ce4-222">[方法: インストールされている .NET Framework の更新プログラムを確認する](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md) </span><span class="sxs-lookup"><span data-stu-id="28ce4-222">[How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md) </span></span>  
 <span data-ttu-id="28ce4-223">[開発者向けの .NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="28ce4-223">[Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md) </span></span>  
 [<span data-ttu-id="28ce4-224">バージョンおよび依存関係</span><span class="sxs-lookup"><span data-stu-id="28ce4-224">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)

