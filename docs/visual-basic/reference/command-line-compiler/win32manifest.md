---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f81b578c5ee3ffd830cef237fba2272eecd07642
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654087"
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="d611f-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d611f-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="d611f-103">プロジェクトのポータブル実行可能 (PE) ファイルに埋め込まれる、ユーザー定義の Win32 アプリケーション マニフェスト ファイルを識別します。</span><span class="sxs-lookup"><span data-stu-id="d611f-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d611f-104">構文</span><span class="sxs-lookup"><span data-stu-id="d611f-104">Syntax</span></span>  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="d611f-105">引数</span><span class="sxs-lookup"><span data-stu-id="d611f-105">Arguments</span></span>  
  
|<span data-ttu-id="d611f-106">用語</span><span class="sxs-lookup"><span data-stu-id="d611f-106">Term</span></span>|<span data-ttu-id="d611f-107">定義</span><span class="sxs-lookup"><span data-stu-id="d611f-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="d611f-108">カスタム マニフェスト ファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="d611f-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d611f-109">コメント</span><span class="sxs-lookup"><span data-stu-id="d611f-109">Remarks</span></span>  
 <span data-ttu-id="d611f-110">既定では、Visual Basic コンパイラには、asinvoker 要求実行レベルを指定するアプリケーション マニフェストが埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="d611f-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="d611f-111">実行可能ファイルは、ビルド bin \debug か bin \release フォルダー Visual Studio を使用すると、同じフォルダーに、マニフェストを作成します。</span><span class="sxs-lookup"><span data-stu-id="d611f-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="d611f-112">HighestAvailable または requireAdministrator、要求実行レベルを指定する例については、カスタム マニフェストを指定する場合は、ファイルの名前を指定するこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="d611f-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d611f-113">このオプションおよび[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)オプションは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="d611f-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="d611f-114">同じコマンドラインで両方のオプションを使用しようとすると、ビルド エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d611f-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="d611f-115">アプリケーション マニフェストを持たないアプリケーションは、要求実行レベルを指定した場合、Windows Vista のユーザー アカウント制御機能によって、ファイルまたはレジストリの仮想化の対象となります。</span><span class="sxs-lookup"><span data-stu-id="d611f-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="d611f-116">仮想化の詳細については、次を参照してください。 [Windows Vista の ClickOnce 配置](/visualstudio/deployment/clickonce-deployment-on-windows-vista)です。</span><span class="sxs-lookup"><span data-stu-id="d611f-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="d611f-117">アプリケーションは、次の条件のいずれかが true の場合、仮想化されます。</span><span class="sxs-lookup"><span data-stu-id="d611f-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="d611f-118">使用する、`-nowin32manifest`オプションに渡さないように後のビルド手順で、または Windows リソース (.res) ファイルの一部としてマニフェストを使用して、`-win32resource`オプション。</span><span class="sxs-lookup"><span data-stu-id="d611f-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2.  <span data-ttu-id="d611f-119">要求実行レベルが指定されていないカスタム マニフェストを提供している。</span><span class="sxs-lookup"><span data-stu-id="d611f-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="d611f-120">Visual Studio では、既定のマニフェスト ファイルを作成し、実行可能ファイルと一緒にデバッグとリリースのディレクトリに格納します。</span><span class="sxs-lookup"><span data-stu-id="d611f-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="d611f-121">表示またはをクリックして既定のアプリケーション マニフェスト ファイルを編集することができます**UAC 設定の表示**上、**アプリケーション**プロジェクト デザイナーのタブです。</span><span class="sxs-lookup"><span data-stu-id="d611f-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="d611f-122">詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d611f-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="d611f-123">使用できる、アプリケーション マニフェストまたは Win32 リソース ファイルの一部としてカスタム ビルド後のステップとしてを使用して、`-nowin32manifest`オプション。</span><span class="sxs-lookup"><span data-stu-id="d611f-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="d611f-124">アプリケーションを Windows Vista でファイルまたはレジストリの仮想化の対象にする場合は、これと同じオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="d611f-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="d611f-125">これにより、コンパイラからの作成と、PE ファイルの既定のマニフェストを埋め込むことができなくなります。</span><span class="sxs-lookup"><span data-stu-id="d611f-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d611f-126">例</span><span class="sxs-lookup"><span data-stu-id="d611f-126">Example</span></span>  
 <span data-ttu-id="d611f-127">次の例は、Visual Basic コンパイラ PE に挿入される既定のマニフェストを示しています。</span><span class="sxs-lookup"><span data-stu-id="d611f-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d611f-128">コンパイラは、標準的なアプリケーション名 MyApplication.app を XML マニフェストに挿入します。</span><span class="sxs-lookup"><span data-stu-id="d611f-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="d611f-129">これは、アプリケーションを Windows Server 2003 Service Pack 3 で実行できるようにするための回避策です。</span><span class="sxs-lookup"><span data-stu-id="d611f-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d611f-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="d611f-130">See Also</span></span>  
 [<span data-ttu-id="d611f-131">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="d611f-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d611f-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d611f-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
