---
title: '方法: インストールされている .NET Framework バージョンを確認する'
ms.date: 01/24/2018
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: edf1e5a53f6f578f943cf8775a798b5681d2d9dd
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="dd93b-102">方法: インストールされている .NET Framework バージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="dd93b-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="dd93b-103">ユーザーはコンピューターに複数のバージョンの .NET Framework をインストールして実行できます。</span><span class="sxs-lookup"><span data-stu-id="dd93b-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="dd93b-104">アプリを開発または配置する場合、どのバージョンの .NET Framework がユーザーのコンピューターにインストールされているかを確認しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="dd93b-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="dd93b-105">.NET Framework は、個別にバージョン管理される 2 つの主要コンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="dd93b-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="dd93b-106">アプリに機能を提供する型やリソースのコレクションである一連のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="dd93b-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="dd93b-107">.NET Framework とアセンブリは同じバージョン番号を共有します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="dd93b-108">アプリのコードを管理および実行する共通言語ランタイム (CLR)。</span><span class="sxs-lookup"><span data-stu-id="dd93b-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="dd93b-109">CLR は独自のバージョン番号で識別されます (「[バージョンおよび依存関係](~/docs/framework/migration-guide/versions-and-dependencies.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="dd93b-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="dd93b-110">コンピューターにインストールされている .NET Framework バージョンの正確な一覧を取得するには、レジストリを表示するか、コードでレジストリを照会することができます。</span><span class="sxs-lookup"><span data-stu-id="dd93b-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="dd93b-111">レジストリの表示 (バージョン 1 ～ 4)</span><span class="sxs-lookup"><span data-stu-id="dd93b-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="dd93b-112">レジストリの表示 (バージョン 4.5 以降)</span><span class="sxs-lookup"><span data-stu-id="dd93b-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="dd93b-113">コードによるレジストリの照会 (バージョン 1 ～ 4)</span><span class="sxs-lookup"><span data-stu-id="dd93b-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="dd93b-114">コードによるレジストリの照会 (バージョン 4.5 以降)</span><span class="sxs-lookup"><span data-stu-id="dd93b-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="dd93b-115">PowerShell を使用したレジストリの照会 (バージョン 4.5 以降)</span><span class="sxs-lookup"><span data-stu-id="dd93b-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="dd93b-116">CLR のバージョンを検索するには、ツールまたはコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd93b-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="dd93b-117">Clrver ツールの使用</span><span class="sxs-lookup"><span data-stu-id="dd93b-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="dd93b-118">コードによる System.Environment クラスの照会</span><span class="sxs-lookup"><span data-stu-id="dd93b-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="dd93b-119">.NET Framework の各バージョン用にインストールされている更新プログラムを検出する方法については、「[方法: インストールされている .NET Framework の更新プログラムを確認する](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd93b-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="dd93b-120">.NET Framework のインストールの詳細については、「[開発者向けの .NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd93b-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="dd93b-121">レジストリを表示して .NET Framework のバージョンを検索するには (.NET Framework 1 ～ 4)</span><span class="sxs-lookup"><span data-stu-id="dd93b-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="dd93b-122">**[スタート]** ボタンをクリックし、**[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd93b-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="dd93b-123">**[開く]** ボックスに「**regedit.exe**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="dd93b-124">regedit.exe を実行するには、管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="dd93b-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="dd93b-125">レジストリ エディターで、次のサブキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="dd93b-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="dd93b-126">インストールされているバージョンは NDP のサブキーの下に一覧表示されています。</span><span class="sxs-lookup"><span data-stu-id="dd93b-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="dd93b-127">バージョン番号は、**Version** エントリに格納されています。</span><span class="sxs-lookup"><span data-stu-id="dd93b-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="dd93b-128">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、**Version** エントリは、Client サブキーまたは Full サブキー (NDP の下)、または両方のサブキーの下にあります。</span><span class="sxs-lookup"><span data-stu-id="dd93b-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="dd93b-129">レジストリの ".NET Framework セットアップ" フォルダーの先頭はピリオドではありません。</span><span class="sxs-lookup"><span data-stu-id="dd93b-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="dd93b-130">レジストリを表示して .NET Framework のバージョンを検索するには (.NET Framework 4.5 以降)</span><span class="sxs-lookup"><span data-stu-id="dd93b-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="dd93b-131">**[スタート]** ボタンをクリックし、**[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd93b-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="dd93b-132">**[開く]** ボックスに「**regedit.exe**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="dd93b-133">regedit.exe を実行するには、管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="dd93b-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="dd93b-134">レジストリ エディターで、次のサブキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="dd93b-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="dd93b-135">`Full` サブキーへのパスに `.NET Framework` ではなく `Net Framework` サブキーが含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="dd93b-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="dd93b-136">`Full` サブキーが存在しない場合は、.NET Framework 4.5 以降がインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="dd93b-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="dd93b-137">`Release` という名前の DWORD 値を確認します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="dd93b-138">`Release` DWORD がある場合は、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降がコンピューターにインストールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="dd93b-139">![.NET Framework 4.5 のレジストリ エントリ。](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="dd93b-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="dd93b-140">`Release` の値は、インストールされている .NET Framework のバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="dd93b-141">Release DWORD の値</span><span class="sxs-lookup"><span data-stu-id="dd93b-141">Value of the Release DWORD</span></span>|<span data-ttu-id="dd93b-142">Version</span><span class="sxs-lookup"><span data-stu-id="dd93b-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="dd93b-143">378389</span><span class="sxs-lookup"><span data-stu-id="dd93b-143">378389</span></span>|<span data-ttu-id="dd93b-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="dd93b-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="dd93b-145">378675</span><span class="sxs-lookup"><span data-stu-id="dd93b-145">378675</span></span>|<span data-ttu-id="dd93b-146">Windows 8.1 または Windows Server 2012 R2 でインストールされた .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="dd93b-147">378758</span><span class="sxs-lookup"><span data-stu-id="dd93b-147">378758</span></span>|<span data-ttu-id="dd93b-148">Windows 8、Windows 7 SP1、または Windows Vista SP2 上でインストールされた .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="dd93b-149">379893</span><span class="sxs-lookup"><span data-stu-id="dd93b-149">379893</span></span>|<span data-ttu-id="dd93b-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="dd93b-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="dd93b-151">Windows 10 システム上: 393295</span><span class="sxs-lookup"><span data-stu-id="dd93b-151">On Windows 10 systems: 393295</span></span><br /><br /> <span data-ttu-id="dd93b-152">その他すべての OS バージョン上: 393297</span><span class="sxs-lookup"><span data-stu-id="dd93b-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="dd93b-153">Windows 10 の 11 月更新版のシステムの場合: 394254</span><span class="sxs-lookup"><span data-stu-id="dd93b-153">On Windows 10 November Update systems: 394254</span></span><br /><br /> <span data-ttu-id="dd93b-154">他のすべての OS バージョンの場合: 394271</span><span class="sxs-lookup"><span data-stu-id="dd93b-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="dd93b-155">Windows 10 Anniversary Update の場合: 394802</span><span class="sxs-lookup"><span data-stu-id="dd93b-155">On Windows 10 Anniversary Update: 394802</span></span><br /><br /> <span data-ttu-id="dd93b-156">他のすべての OS バージョンの場合: 394806</span><span class="sxs-lookup"><span data-stu-id="dd93b-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="dd93b-157">Windows 10 Creators Update の場合: 460798</span><span class="sxs-lookup"><span data-stu-id="dd93b-157">On Windows 10 Creators Update: 460798</span></span><br/><br/> <span data-ttu-id="dd93b-158">その他すべての OS バージョン上: 460805</span><span class="sxs-lookup"><span data-stu-id="dd93b-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="dd93b-159">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="dd93b-159">.NET Framework 4.7</span></span> |
    |<span data-ttu-id="dd93b-160">Windows 10 Fall Creators Update の場合: 461308</span><span class="sxs-lookup"><span data-stu-id="dd93b-160">On Windows 10 Fall Creators Update: 461308</span></span><br/><br/> <span data-ttu-id="dd93b-161">その他のすべての OS バージョン: 461310</span><span class="sxs-lookup"><span data-stu-id="dd93b-161">On all other OS versions: 461310</span></span> | <span data-ttu-id="dd93b-162">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-162">.NET Framework 4.7.1</span></span> |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="dd93b-163">コードでレジストリを照会して .NET Framework のバージョンを検索するには (.NET Framework 1 ～ 4)</span><span class="sxs-lookup"><span data-stu-id="dd93b-163">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="dd93b-164"><xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> クラスを使用して、Windows レジストリの HKEY_LOCAL_MACHINE の下にある Software\Microsoft\NET Framework Setup\NDP\ サブキーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="dd93b-164">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="dd93b-165">このクエリの例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-165">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="dd93b-166">このコードは [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降を検出する方法を示すコードではありません。</span><span class="sxs-lookup"><span data-stu-id="dd93b-166">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="dd93b-167">前のセクションで説明したように、これらのバージョンを検出するには、`Release` DWORD を確認してください。</span><span class="sxs-lookup"><span data-stu-id="dd93b-167">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="dd93b-168">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降のバージョンを検出するコードについては、この記事の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd93b-168">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     <span data-ttu-id="dd93b-169">この例では次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="dd93b-169">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="dd93b-170">コードでレジストリを照会して .NET Framework のバージョンを検索するには (.NET Framework 4.5 以降)</span><span class="sxs-lookup"><span data-stu-id="dd93b-170">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="dd93b-171">`Release` DWORD がある場合は、.NET Framework 4.5 以降がコンピューターにインストールされています。</span><span class="sxs-lookup"><span data-stu-id="dd93b-171">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="dd93b-172">キーワードの値はインストールされているバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-172">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="dd93b-173">このキーワードを確認するには、<xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> クラスの <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> メソッドと <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> メソッドを使って、Windows レジストリの HKEY_LOCAL_MACHINE の下にある Software\Microsoft\NET Framework Setup\NDP\v4\Full サブキーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="dd93b-173">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="dd93b-174">`Release` キーワードの値を確認して、インストールされているバージョンを決定します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-174">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="dd93b-175">上位互換性を確認するには、テーブルに示されている値以上の値があるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-175">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="dd93b-176">.NET Framework のバージョンと関連付けられた `Release` キーワードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-176">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="dd93b-177">Version</span><span class="sxs-lookup"><span data-stu-id="dd93b-177">Version</span></span>|<span data-ttu-id="dd93b-178">Release DWORD の値</span><span class="sxs-lookup"><span data-stu-id="dd93b-178">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="dd93b-179">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="dd93b-179">.NET Framework 4.5</span></span>|<span data-ttu-id="dd93b-180">378389</span><span class="sxs-lookup"><span data-stu-id="dd93b-180">378389</span></span>|
    |<span data-ttu-id="dd93b-181">Windows 8.1 でインストールされた .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-181">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="dd93b-182">378675</span><span class="sxs-lookup"><span data-stu-id="dd93b-182">378675</span></span>|
    |<span data-ttu-id="dd93b-183">Windows 8、Windows 7 SP1、または Windows Vista SP2 上でインストールされた .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-183">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="dd93b-184">378758</span><span class="sxs-lookup"><span data-stu-id="dd93b-184">378758</span></span>|
    |<span data-ttu-id="dd93b-185">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="dd93b-185">.NET Framework 4.5.2</span></span>|<span data-ttu-id="dd93b-186">379893</span><span class="sxs-lookup"><span data-stu-id="dd93b-186">379893</span></span>|
    |<span data-ttu-id="dd93b-187">Windows 10 でインストールされた .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="dd93b-187">.NET Framework 4.6 installed with Windows 10</span></span>|<span data-ttu-id="dd93b-188">393295</span><span class="sxs-lookup"><span data-stu-id="dd93b-188">393295</span></span>|
    |<span data-ttu-id="dd93b-189">その他のすべての Windows OS バージョンにインストールされた .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="dd93b-189">.NET Framework 4.6 installed on all other Windows OS versions</span></span>|<span data-ttu-id="dd93b-190">393297</span><span class="sxs-lookup"><span data-stu-id="dd93b-190">393297</span></span>|
    |<span data-ttu-id="dd93b-191">Windows 10 にインストールされた .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-191">.NET Framework 4.6.1 installed on Windows 10</span></span>|<span data-ttu-id="dd93b-192">394254</span><span class="sxs-lookup"><span data-stu-id="dd93b-192">394254</span></span>|
    |<span data-ttu-id="dd93b-193">その他のすべての Windows OS バージョンにインストールされた .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-193">.NET Framework 4.6.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="dd93b-194">394271</span><span class="sxs-lookup"><span data-stu-id="dd93b-194">394271</span></span>|
    |<span data-ttu-id="dd93b-195">Windows 10 Anniversary Update にインストールされた .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="dd93b-195">.NET Framework 4.6.2 installed on Windows 10 Anniversary Update</span></span>|<span data-ttu-id="dd93b-196">394802</span><span class="sxs-lookup"><span data-stu-id="dd93b-196">394802</span></span>|
    |<span data-ttu-id="dd93b-197">その他のすべての Windows OS バージョンにインストールされた .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="dd93b-197">.NET Framework 4.6.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="dd93b-198">394806</span><span class="sxs-lookup"><span data-stu-id="dd93b-198">394806</span></span>|
    |<span data-ttu-id="dd93b-199">Windows 10 Creators Update にインストールされた .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="dd93b-199">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="dd93b-200">460798</span><span class="sxs-lookup"><span data-stu-id="dd93b-200">460798</span></span>|
    |<span data-ttu-id="dd93b-201">その他のすべての Windows OS バージョンにインストールされた .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="dd93b-201">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="dd93b-202">460805</span><span class="sxs-lookup"><span data-stu-id="dd93b-202">460805</span></span>|
    |<span data-ttu-id="dd93b-203">Windows 10 Fall Creators Update にインストールされた .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-203">.NET Framework 4.7.1 installed on Windows 10 Fall Creators Update</span></span>|<span data-ttu-id="dd93b-204">461308</span><span class="sxs-lookup"><span data-stu-id="dd93b-204">461308</span></span>|
    |<span data-ttu-id="dd93b-205">その他のすべての Windows OS バージョンにインストールされた .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-205">.NET Framework 4.7.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="dd93b-206">461310</span><span class="sxs-lookup"><span data-stu-id="dd93b-206">461310</span></span>|

     <span data-ttu-id="dd93b-207">レジストリの `Release` 値を確認して [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降のバージョンの .NET Framework がインストールされているかどうかを判断する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-207">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     <span data-ttu-id="dd93b-208">この例では、バージョンのチェックで推奨されている方法に従います。</span><span class="sxs-lookup"><span data-stu-id="dd93b-208">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="dd93b-209">`Release` エントリの値が既知のリリース キー値*以上*かどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="dd93b-209">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="dd93b-210">最新バージョンから最も古いバージョンの順にチェックします。</span><span class="sxs-lookup"><span data-stu-id="dd93b-210">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="dd93b-211">PowerShell でレジストリを照会して .NET Framework の最低限必要なバージョンを確認するには(.NET Framework 4.5 以降)</span><span class="sxs-lookup"><span data-stu-id="dd93b-211">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="dd93b-212">次の例では、`Release` キーワードの値を確認して、Windows オペレーティング システムのバージョンに関係なく、.NET Framework 4.6.2 以降がインストールされているかどうかを判断します (インストールされている場合は `True` を返し、それ以外の場合は `False`を返します)。</span><span class="sxs-lookup"><span data-stu-id="dd93b-212">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    <span data-ttu-id="dd93b-213">前の例で、`394802` を次の表の別の値に置き換えて、別の最低限必要な .NET Framework バージョンを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="dd93b-213">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="dd93b-214">Version</span><span class="sxs-lookup"><span data-stu-id="dd93b-214">Version</span></span>|<span data-ttu-id="dd93b-215">Release DWORD の最小値</span><span class="sxs-lookup"><span data-stu-id="dd93b-215">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="dd93b-216">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="dd93b-216">.NET Framework 4.5</span></span>|<span data-ttu-id="dd93b-217">378389</span><span class="sxs-lookup"><span data-stu-id="dd93b-217">378389</span></span>|
    |<span data-ttu-id="dd93b-218">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-218">.NET Framework 4.5.1</span></span>|<span data-ttu-id="dd93b-219">378675</span><span class="sxs-lookup"><span data-stu-id="dd93b-219">378675</span></span>|
    |<span data-ttu-id="dd93b-220">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="dd93b-220">.NET Framework 4.5.2</span></span>|<span data-ttu-id="dd93b-221">379893</span><span class="sxs-lookup"><span data-stu-id="dd93b-221">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="dd93b-222">393295</span><span class="sxs-lookup"><span data-stu-id="dd93b-222">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="dd93b-223">394254</span><span class="sxs-lookup"><span data-stu-id="dd93b-223">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="dd93b-224">394802</span><span class="sxs-lookup"><span data-stu-id="dd93b-224">394802</span></span>|
    |<span data-ttu-id="dd93b-225">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="dd93b-225">.NET Framework 4.7</span></span>|<span data-ttu-id="dd93b-226">460798</span><span class="sxs-lookup"><span data-stu-id="dd93b-226">460798</span></span>|
    |<span data-ttu-id="dd93b-227">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="dd93b-227">.NET Framework 4.7.1</span></span>|<span data-ttu-id="dd93b-228">461308</span><span class="sxs-lookup"><span data-stu-id="dd93b-228">461308</span></span>|
    
<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="dd93b-229">Clrver ツールを使用して現在のランタイムのバージョンを確認する方法</span><span class="sxs-lookup"><span data-stu-id="dd93b-229">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="dd93b-230">CLR バージョン ツール (Clrver.exe) を使用して、コンピューターにインストールされている共通言語ランタイムのバージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-230">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="dd93b-231">Visual Studio コマンド プロンプトで、「`clrver`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-231">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="dd93b-232">次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd93b-232">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="dd93b-233">このツールの使用については、「[Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd93b-233">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="dd93b-234">コードで Environment クラスを照会して現在のランタイム バージョンを確認するには</span><span class="sxs-lookup"><span data-stu-id="dd93b-234">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="dd93b-235"><xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティを照会して <xref:System.Version> オブジェクトを取得し、現在コードを実行しているランタイムのバージョンを識別します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-235">Query the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="dd93b-236">メジャー リリースの識別子 (バージョン 4.0 の "4" など) を取得するには <xref:System.Version.Major%2A?displayProperty=nameWithType> プロパティを、マイナー リリースの識別子 (バージョン 4.0 の "0" など) を取得するには <xref:System.Version.Minor%2A?displayProperty=nameWithType> プロパティを、バージョン文字列全体 (次のコードに示すような "4.0.30319.18010" など) を取得するには <xref:System.Object.ToString%2A?displayProperty=nameWithType> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd93b-236">You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="dd93b-237">このプロパティは、現在コードを実行しているランタイムのバージョンを表す単一の値を返しますが、アセンブリのバージョンやコンピューターにインストールされている可能性があるランタイムの他のバージョンは返しません。</span><span class="sxs-lookup"><span data-stu-id="dd93b-237">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="dd93b-238">.NET Framework バージョン 4、4.5、4.5.1、および 4.5.2 の場合は、<xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティから返される <xref:System.Version> オブジェクトの文字列表現が `4.0.30319.xxxxx` という形式になっています。</span><span class="sxs-lookup"><span data-stu-id="dd93b-238">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="dd93b-239">.NET Framework 4.6 以降の場合は、`4.0.30319.42000` という形式です。</span><span class="sxs-lookup"><span data-stu-id="dd93b-239">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="dd93b-240">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降の場合、ランタイムのバージョンの検出に <xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティを使用することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="dd93b-240">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="dd93b-241">代わりに、この記事で前述した「[コードでレジストリを照会して .NET Framework のバージョンを検索するには (.NET Framework 4.5 以降)](#net_d)」に従って、レジストリを紹介することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dd93b-241">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="dd93b-242">次に、<xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティを照会してランタイム バージョン情報を取得する例を示します。</span><span class="sxs-lookup"><span data-stu-id="dd93b-242">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property for runtime version information:</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     <span data-ttu-id="dd93b-243">この例では次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="dd93b-243">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="dd93b-244">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd93b-244">See also</span></span>

[<span data-ttu-id="dd93b-245">方法: インストールされている .NET Framework の更新プログラムを確認する</span><span class="sxs-lookup"><span data-stu-id="dd93b-245">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[<span data-ttu-id="dd93b-246">開発者向けの .NET Framework のインストール</span><span class="sxs-lookup"><span data-stu-id="dd93b-246">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="dd93b-247">バージョンおよび依存関係</span><span class="sxs-lookup"><span data-stu-id="dd93b-247">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)  
