---
title: "/win32manifest (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4a9693bd7eb03dee5a2a9f2d43360b963e9fd876
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="win32manifest-visual-basic"></a><span data-ttu-id="4289d-102">/win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4289d-102">/win32manifest (Visual Basic)</span></span>
<span data-ttu-id="4289d-103">プロジェクトのポータブル実行可能 (PE) ファイルに埋め込まれる、ユーザー定義の Win32 アプリケーション マニフェスト ファイルを識別します。</span><span class="sxs-lookup"><span data-stu-id="4289d-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4289d-104">構文</span><span class="sxs-lookup"><span data-stu-id="4289d-104">Syntax</span></span>  
  
```  
/win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="4289d-105">引数</span><span class="sxs-lookup"><span data-stu-id="4289d-105">Arguments</span></span>  
  
|<span data-ttu-id="4289d-106">用語</span><span class="sxs-lookup"><span data-stu-id="4289d-106">Term</span></span>|<span data-ttu-id="4289d-107">定義</span><span class="sxs-lookup"><span data-stu-id="4289d-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="4289d-108">カスタム マニフェスト ファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="4289d-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4289d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="4289d-109">Remarks</span></span>  
 <span data-ttu-id="4289d-110">既定では、Visual Basic コンパイラには asInvoker の要求実行レベルを示すアプリケーション マニフェストが埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="4289d-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="4289d-111">実行可能ファイルがビルドされる、通常 Visual Studio を使用する場合は、bin \debug または bin \release フォルダーの同じフォルダーに、マニフェストを作成します。</span><span class="sxs-lookup"><span data-stu-id="4289d-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="4289d-112">HighestAvailable または requireAdministrator、要求実行レベルを指定する例については、カスタム マニフェストを指定する場合は、ファイルの名前を指定するこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4289d-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4289d-113">このオプションと[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)オプションは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="4289d-113">This option and the [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="4289d-114">同じコマンド行で両方のオプションを使用しようとする場合は、ビルド エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4289d-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="4289d-115">アプリケーション マニフェストを持たないアプリケーションは、要求実行レベルが Windows Vista のユーザー アカウント制御機能によって、ファイルまたはレジストリの仮想化の対象となりますを指定します。</span><span class="sxs-lookup"><span data-stu-id="4289d-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="4289d-116">仮想化の詳細については、次を参照してください。 [Windows Vista の ClickOnce 配置](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista)します。</span><span class="sxs-lookup"><span data-stu-id="4289d-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="4289d-117">次の条件のいずれかが true の場合、アプリケーションは仮想化が適用されます。</span><span class="sxs-lookup"><span data-stu-id="4289d-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="4289d-118">使用する、`/nowin32manifest`オプション指定しない後のビルド手順で、または Windows リソース (.res) ファイルの一部としてマニフェストを使用して、`/win32resource`オプション。</span><span class="sxs-lookup"><span data-stu-id="4289d-118">You use the `/nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `/win32resource` option.</span></span>  
  
2.  <span data-ttu-id="4289d-119">要求実行レベルが指定されていないカスタム マニフェストを提供します。</span><span class="sxs-lookup"><span data-stu-id="4289d-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="4289d-120">既定のマニフェスト ファイルを作成し、実行可能ファイルと一緒にデバッグとリリースのディレクトリに格納します。</span><span class="sxs-lookup"><span data-stu-id="4289d-120"> creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="4289d-121">表示したりをクリックして既定のアプリケーション マニフェスト ファイルを編集**UAC 設定の表示**上、**アプリケーション**プロジェクト デザイナー タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4289d-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="4289d-122">詳細については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="4289d-122">For more information, see [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="4289d-123">使用できる、アプリケーション マニフェストまたはカスタムのビルド後の手順として、Win32 リソース ファイルの一部としてを使用して、`/nowin32manifest`オプション。</span><span class="sxs-lookup"><span data-stu-id="4289d-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `/nowin32manifest` option.</span></span> <span data-ttu-id="4289d-124">Windows Vista でファイルまたはレジストリの仮想化を回避できるアプリケーションの場合は、その同じオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4289d-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="4289d-125">これにより、PE ファイルの既定のマニフェストを作成およびコンパイラができなくなります。</span><span class="sxs-lookup"><span data-stu-id="4289d-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4289d-126">例</span><span class="sxs-lookup"><span data-stu-id="4289d-126">Example</span></span>  
 <span data-ttu-id="4289d-127">次の例では、Visual Basic コンパイラ PE に挿入される既定のマニフェストを示しています。</span><span class="sxs-lookup"><span data-stu-id="4289d-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4289d-128">コンパイラは、XML マニフェストに標準のアプリケーション名 MyApplication.app を挿入します。</span><span class="sxs-lookup"><span data-stu-id="4289d-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="4289d-129">これは、Windows Server 2003 Service Pack 3 で実行するアプリケーションを有効にする回避策です。</span><span class="sxs-lookup"><span data-stu-id="4289d-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="4289d-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="4289d-130">See Also</span></span>  
 <span data-ttu-id="4289d-131">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="4289d-131">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="4289d-132"> [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)</span><span class="sxs-lookup"><span data-stu-id="4289d-132"> [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)</span></span>
