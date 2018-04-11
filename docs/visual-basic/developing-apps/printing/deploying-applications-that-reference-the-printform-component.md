---
title: PrintForm コンポーネント (Visual Basic) を参照するアプリケーションの配置
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 15b6e21e769c90e23e66e4f87b37f74462423985
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="cf5d9-102">PrintForm コンポーネント (Visual Basic) を参照するアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="cf5d9-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="cf5d9-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを参照するアプリケーションを配置する場合は、コンポーネントをターゲット コンピューターにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="cf5d9-104">PowerPack コントロールは、Visual Studio には含まれなくなりましたが、 [ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="cf5d9-105">必要条件として PrintForm をインストールする</span><span class="sxs-lookup"><span data-stu-id="cf5d9-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="cf5d9-106">アプリケーションを正しく配置するためには、アプリケーションによって参照されるすべてのコンポーネントを配置する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="cf5d9-107">必須コンポーネントのインストール プロセスは、 *ブートストラップ*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="cf5d9-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントのインストール時に、Microsoft Visual Basic Power Packs ブートストラップ パッケージが [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ブートストラップ ディレクトリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bootstrapper directory.</span></span> <span data-ttu-id="cf5d9-109">その後、 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] または Windows インストーラー配置のための必要条件を追加する手順に従うと、このパッケージが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="cf5d9-110">既定では、ブートストラップ コンポーネントは、インストール パッケージと同じ場所から配置されます。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="cf5d9-111">または、必要に応じてユーザーがダウンロードできるような URL またはファイルの共有位置からコンポーネントを配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf5d9-112">ブートストラップ コンポーネントをインストールするには、コンピューターに対する管理者または同様のユーザー アクセス許可が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="cf5d9-113">つまり、 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] アプリケーションの場合、アプリケーションで指定されたセキュリティ レベルに関係なく、アプリケーションをインストールするために管理アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-113">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="cf5d9-114">アプリケーションのインストール後は、管理アクセス許可がなくてもアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="cf5d9-115">インストール中に、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントがターゲット コンピューター上に存在しなければ、ユーザーはこれをインストールするよう求められます。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="cf5d9-116">ブートストラップの代わりに、Microsoft Systems Management Server などの電子ソフトウェア配布システムを使って <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを事前に配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf5d9-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf5d9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf5d9-117">See also</span></span>  
 [<span data-ttu-id="cf5d9-118">方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする</span><span class="sxs-lookup"><span data-stu-id="cf5d9-118">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="cf5d9-119">PrintForm コンポーネント</span><span class="sxs-lookup"><span data-stu-id="cf5d9-119">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
