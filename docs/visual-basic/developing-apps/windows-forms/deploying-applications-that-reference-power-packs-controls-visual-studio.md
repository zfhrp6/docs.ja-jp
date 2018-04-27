---
title: Power Packs コントロール (Visual Studio) を参照するアプリケーションの配置
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d73c7111c3d89cadcad317c9a67e5f483da7125
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="d21a2-102">Power Packs コントロール (Visual Studio) を参照するアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="d21a2-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="d21a2-103">Power Packs コントロールを参照するアプリケーションを展開するかどうか (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>、 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>、 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>、または<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>)、展開先コンピューターに、コントロールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d21a2-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="d21a2-104">前提条件として Power Packs コントロールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d21a2-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="d21a2-105">アプリケーションを正しく配置するためには、アプリケーションによって参照されるすべてのコンポーネントを配置する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="d21a2-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="d21a2-106">必須コンポーネントのインストール プロセスは、 *ブートストラップ*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d21a2-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="d21a2-107">Visual Studio が開発用コンピューターにインストールされている場合、Power Packs ブートス トラップ パッケージは、Visual Studio ブートス トラップ ディレクトリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d21a2-107">When Visual Studio is installed on your development computer, a Power Packs bootstrapper package is added to the Visual Studio bootstrapper directory.</span></span> <span data-ttu-id="d21a2-108">その後、 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] または Windows インストーラー配置のための必要条件を追加する手順に従うと、このパッケージが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="d21a2-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="d21a2-109">既定では、ブートストラップ コンポーネントは、インストール パッケージと同じ場所から配置されます。</span><span class="sxs-lookup"><span data-stu-id="d21a2-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="d21a2-110">または、必要に応じてユーザーがダウンロードできるような URL またはファイルの共有位置からコンポーネントを配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="d21a2-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d21a2-111">ブートストラップ コンポーネントをインストールするには、コンピューターに対する管理者または同様のユーザー アクセス許可が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d21a2-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="d21a2-112">つまり、 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] アプリケーションの場合、アプリケーションで指定されたセキュリティ レベルに関係なく、アプリケーションをインストールするために管理アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="d21a2-112">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="d21a2-113">アプリケーションのインストール後は、管理アクセス許可がなくてもアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="d21a2-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="d21a2-114">インストール中には、展開先コンピューターに存在しない場合は、Power Packs コントロールをインストールするユーザーが求められます。</span><span class="sxs-lookup"><span data-stu-id="d21a2-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="d21a2-115">ブートス トラップする代わりには、事前に Microsoft Systems Management Server などの電子ソフトウェア配布システムを使用して Power Packs コントロールを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="d21a2-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d21a2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d21a2-116">See also</span></span>  
 [<span data-ttu-id="d21a2-117">方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする</span><span class="sxs-lookup"><span data-stu-id="d21a2-117">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="d21a2-118">Visual Basic Power Packs コントロール</span><span class="sxs-lookup"><span data-stu-id="d21a2-118">Visual Basic Power Packs Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
