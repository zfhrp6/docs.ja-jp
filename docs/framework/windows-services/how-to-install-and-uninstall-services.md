---
title: '方法: サービスをインストールおよびアンインストールする'
ms.date: 03/30/2017
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
author: ghogen
manager: douge
ms.openlocfilehash: 0d42a37b2e84c310569666771ded38e5feca3608
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513140"
---
# <a name="how-to-install-and-uninstall-services"></a><span data-ttu-id="8def5-102">方法: サービスをインストールおよびアンインストールする</span><span class="sxs-lookup"><span data-stu-id="8def5-102">How to: Install and Uninstall Services</span></span>
<span data-ttu-id="8def5-103">.NET Framework を使用して Windows サービスを開発している場合は、InstallUtil.exe というコマンド ライン ユーティリティを使用してサービス アプリケーションをすばやくインストールできます。</span><span class="sxs-lookup"><span data-stu-id="8def5-103">If you’re developing a Windows Service by using the .NET Framework, you can quickly install your service application by using a command-line utility called InstallUtil.exe.</span></span> <span data-ttu-id="8def5-104">開発者は、ユーザーがインストールおよびアンインストールできる Windows サービスをリリースする場合、InstallShield を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8def5-104">If you’re a developer who wants to release a Windows Service that users can install and uninstall  you should use InstallShield.</span></span> <span data-ttu-id="8def5-105">「[Windows インストーラー配置](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8def5-105">See [Windows Installer Deployment](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8def5-106">サービスをコンピューターからアンインストールする場合は、この記事の手順には従わないでください。</span><span class="sxs-lookup"><span data-stu-id="8def5-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="8def5-107">代わりに、サービスをインストールしたプログラムまたはソフトウェア パッケージを確認し、[コントロール パネル] の **[プログラムの追加と削除]** を選択してそのプログラムをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="8def5-107">Instead, find out which program or software package installed the service, and then choose **Add/Remove Programs** in Control Panel to uninstall that program.</span></span> <span data-ttu-id="8def5-108">多くのサービスが Windows の不可欠な構成要素であることに注意してください。それらを削除すると、システムが不安定になることがあります。</span><span class="sxs-lookup"><span data-stu-id="8def5-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="8def5-109">この記事の手順を使用するためには、まず、Windows サービスにサービス インストーラーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8def5-109">In order to use the steps in this article, you first need to add a service installer to your Windows Service.</span></span> <span data-ttu-id="8def5-110">「[チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8def5-110">See [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="8def5-111">Windows サービス プロジェクトは、F5 キーを押して Visual Studio 開発環境から直接実行することができません。</span><span class="sxs-lookup"><span data-stu-id="8def5-111">Windows Service projects cannot be run directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="8def5-112">これは、プロジェクトを実行する前に、プロジェクトのサービスをインストールする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="8def5-112">This is because the service in the project must be installed before you can run the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="8def5-113">**サーバー エクスプローラー**を起動して、サービスがインストールまたはアンインストールされているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8def5-113">You can launch **Server Explorer** and verify that your service has been installed or uninstalled.</span></span> <span data-ttu-id="8def5-114">詳しくは、「方法: サーバー エクスプローラー/データベース エクスプローラーにアクセスして初期化する」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8def5-114">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
### <a name="to-install-your-service-manually"></a><span data-ttu-id="8def5-115">サービスを手動でインストールするには</span><span class="sxs-lookup"><span data-stu-id="8def5-115">To install your service manually</span></span>  
  
1.  <span data-ttu-id="8def5-116">Windows の **[スタート]** メニューまたは **[スタート]** 画面で、**[Visual Studio]**、**[Visual Studio Tools]**、**[開発者コマンド プロンプト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="8def5-116">On the Windows **Start** menu or **Start** screen, choose **Visual Studio** , **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="8def5-117">Visual Studio コマンド プロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8def5-117">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="8def5-118">プロジェクトのコンパイル済み実行可能ファイルが格納されているディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="8def5-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3.  <span data-ttu-id="8def5-119">プロジェクトの実行可能ファイルをパラメーターとして指定し、コマンド プロンプトから InstallUtil.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="8def5-119">Run InstallUtil.exe from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     <span data-ttu-id="8def5-120">Visual Studio コマンド プロンプトを使用している場合は、InstallUtil.exe がシステム パス上にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="8def5-120">If you’re using the Visual Studio command prompt, InstallUtil.exe should be on the system path.</span></span> <span data-ttu-id="8def5-121">該当しない場合は、パスに追加するか、完全修飾パスを使用して起動します。</span><span class="sxs-lookup"><span data-stu-id="8def5-121">If not, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="8def5-122">このツールは .NET Framework と共にインストールされ、パスは `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>` です。</span><span class="sxs-lookup"><span data-stu-id="8def5-122">This tool is installed with the .NET Framework, and its path is `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span></span> <span data-ttu-id="8def5-123">たとえば、32 ビット版の .NET Framework 4 または 4.5\* では、Windows のインストール ディレクトリが C:\Windows である場合、パスは `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe` になります。</span><span class="sxs-lookup"><span data-stu-id="8def5-123">For example, for the 32-bit version of the .NET Framework 4 or 4.5.\*, if your Windows installation directory is C:\Windows, the path is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span> <span data-ttu-id="8def5-124">64 ビット版の .NET Framework 4 または 4.5.\* では、既定のパスは `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe` になります。</span><span class="sxs-lookup"><span data-stu-id="8def5-124">For the 64-bit version of the .NET Framework 4 or 4.5.\*, the default path is `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span></span>  
  
### <a name="to-uninstall-your-service-manually"></a><span data-ttu-id="8def5-125">サービスを手動でアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="8def5-125">To uninstall your service manually</span></span>  
  
1.  <span data-ttu-id="8def5-126">Windows の **[スタート]** メニューまたは **[スタート]** 画面で、**[Visual Studio]**、**[Visual Studio Tools]**、**[開発者コマンド プロンプト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="8def5-126">On the Windows **Start** menu or **Start** screen, choose **Visual Studio**, **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="8def5-127">Visual Studio コマンド プロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8def5-127">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="8def5-128">プロジェクトの出力先ファイルをパラメーターとして指定し、コマンド プロンプトから InstallUtil.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="8def5-128">Run InstallUtil.exe from the command prompt with your project's output as a parameter:</span></span>  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  <span data-ttu-id="8def5-129">場合によっては、サービスの実行可能ファイルを削除した後も、レジストリ内にサービスが存在したままになることがあります。</span><span class="sxs-lookup"><span data-stu-id="8def5-129">Sometimes, after the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="8def5-130">このような場合は、コマンド [sc delete](http://technet.microsoft.com/library/cc742045.aspx) を使って、レジストリからサービスのエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="8def5-130">In that case, use the command [sc delete](http://technet.microsoft.com/library/cc742045.aspx) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8def5-131">参照</span><span class="sxs-lookup"><span data-stu-id="8def5-131">See Also</span></span>  
 [<span data-ttu-id="8def5-132">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="8def5-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="8def5-133">方法 : Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="8def5-133">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="8def5-134">方法 : サービス アプリケーションにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="8def5-134">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="8def5-135">Installutil.exe (インストーラー ツール)</span><span class="sxs-lookup"><span data-stu-id="8def5-135">Installutil.exe (Installer Tool)</span></span>](../../../docs/framework/tools/installutil-exe-installer-tool.md)
