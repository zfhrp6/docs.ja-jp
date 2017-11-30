---
title: "-win32manifest (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 40b1fa1f9aa465a56eccaf5fff5cf7bb59144e85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="win32manifest-c-compiler-options"></a><span data-ttu-id="a25fe-102">/win32manifest (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="a25fe-102">/win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="a25fe-103">**/win32manifest** オプションは、プロジェクトのポータブル実行可能 (PE) ファイルに埋め込まれる、ユーザー定義の Win32 アプリケーション マニフェスト ファイルを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a25fe-103">Use the **/win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a25fe-104">構文</span><span class="sxs-lookup"><span data-stu-id="a25fe-104">Syntax</span></span>  
  
```console  
/win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="a25fe-105">引数</span><span class="sxs-lookup"><span data-stu-id="a25fe-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="a25fe-106">カスタム マニフェスト ファイルの名前と場所。</span><span class="sxs-lookup"><span data-stu-id="a25fe-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a25fe-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a25fe-107">Remarks</span></span>  
 <span data-ttu-id="a25fe-108">既定では、 [!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] コンパイラは "asInvoker" の要求実行レベルを指定するアプリケーション マニフェストを埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="a25fe-108">By default, the [!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="a25fe-109">マニフェストは、実行可能ファイルがビルドされたフォルダーと同じフォルダーに作成されます (Visual Studio を使用している場合、通常は bin\Debug または bin\Release フォルダー)。</span><span class="sxs-lookup"><span data-stu-id="a25fe-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="a25fe-110">カスタム マニフェストを指定する場合 (たとえば、"highestAvailable" または "requireAdministrator" の要求実行レベルを指定する場合) は、このオプションを使用してファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a25fe-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a25fe-111">このオプションと [/win32res (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) オプションは、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="a25fe-111">This option and the [/win32res (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="a25fe-112">同じコマンド行で両方のオプションを使おうすると、ビルド エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="a25fe-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="a25fe-113">アプリケーション マニフェストがないアプリケーションでは、要求実行レベルは、Windows のユーザー アカウント制御機能の下にあるファイルまたはレジストリの仮想化されますを指定します。</span><span class="sxs-lookup"><span data-stu-id="a25fe-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="a25fe-114">詳細については、次を参照してください。[ユーザー アカウント制御](/windows/access-protection/user-account-control/user-account-control-overview)です。</span><span class="sxs-lookup"><span data-stu-id="a25fe-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="a25fe-115">次の条件のいずれかに該当する場合、アプリケーションは仮想化の対象となります。</span><span class="sxs-lookup"><span data-stu-id="a25fe-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
-   <span data-ttu-id="a25fe-116">**/nowin32manifest** オプションを使用していて、後のビルド手順でマニフェストを提供していないか、**/win32res** オプションを使用して Windows リソース (.res) ファイルの一部としていない。</span><span class="sxs-lookup"><span data-stu-id="a25fe-116">You use the **/nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **/win32res** option.</span></span>  
  
-   <span data-ttu-id="a25fe-117">要求実行レベルが指定されていないカスタム マニフェストを提供している。</span><span class="sxs-lookup"><span data-stu-id="a25fe-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="a25fe-118"> は、既定の .manifest ファイルを作成し、それを実行可能ファイルと一緒にデバッグ ディレクトリとリリースディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="a25fe-118"> creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="a25fe-119">カスタム マニフェストを追加するには、任意のテキスト エディターでカスタム マニフェストを作成し、そのファイルをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="a25fe-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="a25fe-120">または、**ソリューション エクスプ ローラー**で **[プロジェクト]** アイコンを右クリックし、**[新しい項目の追加]** をクリックして、**[アプリケーション マニフェスト ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a25fe-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="a25fe-121">新規または既存のマニフェスト ファイルを追加すると、そのマニフェストは **[マニフェスト]** ドロップダウン リストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a25fe-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="a25fe-122">詳しくは、「[[アプリケーション] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a25fe-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="a25fe-123">アプリケーション マニフェストは、カスタムのビルド後手順として提供するか、または [/nowin32manifest (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) オプションを使用して、Win32 リソース ファイルの一部として提供できます。</span><span class="sxs-lookup"><span data-stu-id="a25fe-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [/nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="a25fe-124">アプリケーションを Windows Vista でファイルまたはレジストリの仮想化の対象にする場合は、これと同じオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="a25fe-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="a25fe-125">これにより、コンパイラがポータブル実行可能 (PE) ファイル内に既定のマニフェストを作成し、埋め込むことを回避できます。</span><span class="sxs-lookup"><span data-stu-id="a25fe-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a25fe-126">例</span><span class="sxs-lookup"><span data-stu-id="a25fe-126">Example</span></span>  
 <span data-ttu-id="a25fe-127">次の例は、Visual C# コンパイラが PE に挿入する既定のマニフェストを示したものです。</span><span class="sxs-lookup"><span data-stu-id="a25fe-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a25fe-128">コンパイラは、標準のアプリケーション名 "MyApplication.app" を xml に挿入します。</span><span class="sxs-lookup"><span data-stu-id="a25fe-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="a25fe-129">これは、アプリケーションを Windows Server 2003 Service Pack 3 で実行できるようにするための回避策です。</span><span class="sxs-lookup"><span data-stu-id="a25fe-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a25fe-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a25fe-130">See Also</span></span>  
 [<span data-ttu-id="a25fe-131">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="a25fe-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="a25fe-132">/nowin32manifest (c# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="a25fe-132">/nowin32manifest (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
 [<span data-ttu-id="a25fe-133">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="a25fe-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
