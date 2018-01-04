---
title: "方法: サービスをインストールおよびアンインストールする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: bf767813f965b2c52a5061f74bbf2fab4572791b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-and-uninstall-services"></a><span data-ttu-id="f0bd1-102">方法: サービスをインストールおよびアンインストールする</span><span class="sxs-lookup"><span data-stu-id="f0bd1-102">How to: Install and Uninstall Services</span></span>
<span data-ttu-id="f0bd1-103">.NET Framework を使用して Windows サービスを開発している場合は、InstallUtil.exe というコマンド ライン ユーティリティを使用してサービス アプリケーションをすばやくインストールできます。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-103">If you’re developing a Windows Service by using the .NET Framework, you can quickly install your service application by using a command-line utility called InstallUtil.exe.</span></span> <span data-ttu-id="f0bd1-104">開発者は、ユーザーがインストールおよびアンインストールできる Windows サービスをリリースする場合、InstallShield を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-104">If you’re a developer who wants to release a Windows Service that users can install and uninstall  you should use InstallShield.</span></span> <span data-ttu-id="f0bd1-105">参照してください[Windows インストーラーの配置](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)です。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-105">See [Windows Installer Deployment](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f0bd1-106">サービスをコンピューターからアンインストールする場合は、この記事の手順には従わないでください。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="f0bd1-107">代わりに、サービスをインストールしたプログラムまたはソフトウェア パッケージを検索し、**プログラムの追加/削除**そのプログラムをアンインストールするコントロール パネルの します。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-107">Instead, find out which program or software package installed the service, and then choose **Add/Remove Programs** in Control Panel to uninstall that program.</span></span> <span data-ttu-id="f0bd1-108">多くのサービスが Windows の不可欠な構成要素であることに注意してください。それらを削除すると、システムが不安定になることがあります。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="f0bd1-109">この記事の手順を使用するためには、まず、Windows サービスにサービス インストーラーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-109">In order to use the steps in this article, you first need to add a service installer to your Windows Service.</span></span> <span data-ttu-id="f0bd1-110">参照してください[チュートリアル: Windows を作成するサービス アプリケーション コンポーネント デザイナーを](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)です。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-110">See [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="f0bd1-111">Windows サービス プロジェクトは、F5 キーを押して Visual Studio 開発環境から直接実行することができません。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-111">Windows Service projects cannot be run directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="f0bd1-112">これは、プロジェクトを実行する前に、プロジェクトのサービスをインストールする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-112">This is because the service in the project must be installed before you can run the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="f0bd1-113">起動する**サーバー エクスプ ローラー**サービスがインストールまたはアンインストールされたことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-113">You can launch **Server Explorer** and verify that your service has been installed or uninstalled.</span></span> <span data-ttu-id="f0bd1-114">詳細については、次を参照してください。 方法: アクセスおよびサーバー エクスプ ローラー データベース エクスプ ローラーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-114">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
### <a name="to-install-your-service-manually"></a><span data-ttu-id="f0bd1-115">サービスを手動でインストールするには</span><span class="sxs-lookup"><span data-stu-id="f0bd1-115">To install your service manually</span></span>  
  
1.  <span data-ttu-id="f0bd1-116">Windows の**開始**メニューまたは**開始**画面で、選択**Visual Studio** 、 **Visual Studio Tools**、**開発者コマンド プロンプト**です。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-116">On the Windows **Start** menu or **Start** screen, choose **Visual Studio** , **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="f0bd1-117">Visual Studio コマンド プロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-117">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="f0bd1-118">プロジェクトのコンパイル済み実行可能ファイルが格納されているディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3.  <span data-ttu-id="f0bd1-119">プロジェクトの実行可能ファイルをパラメーターとして指定し、コマンド プロンプトから InstallUtil.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-119">Run InstallUtil.exe from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     <span data-ttu-id="f0bd1-120">Visual Studio コマンド プロンプトを使用している場合は、InstallUtil.exe がシステム パス上にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-120">If you’re using the Visual Studio command prompt, InstallUtil.exe should be on the system path.</span></span> <span data-ttu-id="f0bd1-121">該当しない場合は、パスに追加するか、完全修飾パスを使用して起動します。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-121">If not, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="f0bd1-122">このツールは .NET Framework と共にインストールされ、パスは `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>` です。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-122">This tool is installed with the .NET Framework, and its path is `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span></span> <span data-ttu-id="f0bd1-123">たとえば、32 ビット版の .NET Framework 4 または 4.5* では、Windows のインストール ディレクトリが C:\Windows である場合、パスは `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe` になります。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-123">For example, for the 32-bit version of the .NET Framework 4 or 4.5.*, if your Windows installation directory is C:\Windows, the path is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span> <span data-ttu-id="f0bd1-124">64 ビット バージョンの .NET Framework 4 または 4.5。\*、既定のパスは`C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`します。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-124">For the 64-bit version of the .NET Framework 4 or 4.5.\*, the default path is `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span></span>  
  
### <a name="to-uninstall-your-service-manually"></a><span data-ttu-id="f0bd1-125">サービスを手動でアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="f0bd1-125">To uninstall your service manually</span></span>  
  
1.  <span data-ttu-id="f0bd1-126">Windows の**開始**メニューまたは**開始**画面で、選択**Visual Studio**、 **Visual Studio Tools**、**開発者コマンド プロンプト**です。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-126">On the Windows **Start** menu or **Start** screen, choose **Visual Studio**, **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="f0bd1-127">Visual Studio コマンド プロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-127">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="f0bd1-128">プロジェクトの出力先ファイルをパラメーターとして指定し、コマンド プロンプトから InstallUtil.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-128">Run InstallUtil.exe from the command prompt with your project's output as a parameter:</span></span>  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  <span data-ttu-id="f0bd1-129">場合によっては、サービスの実行可能ファイルを削除した後も、レジストリ内にサービスが存在したままになることがあります。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-129">Sometimes, after the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="f0bd1-130">その場合は、コマンドを使用して[sc delete](http://technet.microsoft.com/library/cc742045.aspx)をレジストリからサービスのエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="f0bd1-130">In that case, use the command [sc delete](http://technet.microsoft.com/library/cc742045.aspx) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0bd1-131">参照</span><span class="sxs-lookup"><span data-stu-id="f0bd1-131">See Also</span></span>  
 [<span data-ttu-id="f0bd1-132">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="f0bd1-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="f0bd1-133">方法 : Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="f0bd1-133">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="f0bd1-134">方法 : サービス アプリケーションにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="f0bd1-134">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="f0bd1-135">Installutil.exe (インストーラー ツール)</span><span class="sxs-lookup"><span data-stu-id="f0bd1-135">Installutil.exe (Installer Tool)</span></span>](../../../docs/framework/tools/installutil-exe-installer-tool.md)
