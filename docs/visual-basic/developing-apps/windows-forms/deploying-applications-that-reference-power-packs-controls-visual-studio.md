---
title: "Power Packs コントロール (Visual Studio) を参照するアプリケーションを展開する |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
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
ms.openlocfilehash: ad1aba4f2e725abbe560f0c71fbb543e15741200
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="2fb1d-102">Power Packs コントロール (Visual Studio) を参照するアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="2fb1d-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="2fb1d-103">Power Packs コントロールを参照するアプリケーションを展開するかどうか (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>、 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>、 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>、または<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>)、対象のコンピューターで、コントロールをインストールする必要があります</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.RectangleShape></xref:Microsoft.VisualBasic.PowerPacks.OvalShape></xref:Microsoft.VisualBasic.PowerPacks.LineShape>。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="2fb1d-104">前提条件として、Power Packs コントロールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="2fb1d-105">アプリケーションを正しく配置するためには、アプリケーションによって参照されるすべてのコンポーネントを配置する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="2fb1d-106">必須コンポーネントのインストール プロセスは、 *ブートストラップ*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="2fb1d-107">[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]が開発用コンピューターにブートス トラップ パッケージを追加 Power Pack でインストールされている、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]ブートス トラップ ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-107">When [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] is installed on your development computer, a Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] bootstrapper directory.</span></span> <span data-ttu-id="2fb1d-108">このパッケージは次のいずれかの前提条件を追加する手順を実行すると使用可能になります[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]または Windows インストーラーの展開。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="2fb1d-109">既定では、ブートストラップ コンポーネントは、インストール パッケージと同じ場所から配置されます。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="2fb1d-110">または、必要に応じてユーザーがダウンロードできるような URL またはファイルの共有位置からコンポーネントを配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fb1d-111">ブートストラップ コンポーネントをインストールするには、コンピューターに対する管理者または同様のユーザー アクセス許可が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="2fb1d-112">[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]アプリケーション、つまり、ユーザーに、アプリケーションで指定されたセキュリティ レベルに関係なく、アプリケーションをインストールする管理アクセス許可は必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-112">For [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="2fb1d-113">アプリケーションのインストール後は、管理アクセス許可がなくてもアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="2fb1d-114">インストール中に、これらが対象のコンピューターに存在しない場合は、Power Packs コントロールをインストールするユーザーがように求められます。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="2fb1d-115">ブートス トラップする代わりに、事前に Microsoft Systems Management Server などの電子ソフトウェア配布システムを使用して Power Packs コントロールを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="2fb1d-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fb1d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2fb1d-116">See also</span></span>  
 <span data-ttu-id="2fb1d-117">[方法: ClickOnce アプリケーションと共に必須コンポーネントをインストール](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span><span class="sxs-lookup"><span data-stu-id="2fb1d-117">[How to: Install Prerequisites with a ClickOnce Application](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span></span>  
<span data-ttu-id="2fb1d-118"> [Visual Basic Power Packs コントロール](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)</span><span class="sxs-lookup"><span data-stu-id="2fb1d-118"> [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)</span></span>
