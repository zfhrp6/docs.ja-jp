---
title: "PrintForm コンポーネント (Visual Basic) を参照するアプリケーションを展開する |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7b625e0c58653f1ee9a2d263d7d2d29ad3b2e3c1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="d406c-102">PrintForm コンポーネント (Visual Basic) を参照するアプリケーションを展開します。</span><span class="sxs-lookup"><span data-stu-id="d406c-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="d406c-103">参照するアプリケーションを展開する場合、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントは、コンポーネントは、セットアップ先のコンピューターにインストールする必要があります</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。</span><span class="sxs-lookup"><span data-stu-id="d406c-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="d406c-104">PowerPack コントロールは、Visual Studio には含まれなくなりましたが、 [ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="d406c-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="d406c-105">前提条件として、PrintForm をインストールします。</span><span class="sxs-lookup"><span data-stu-id="d406c-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="d406c-106">アプリケーションを正しく配置するためには、アプリケーションによって参照されるすべてのコンポーネントを配置する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="d406c-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="d406c-107">必須コンポーネントのインストール プロセスは、 *ブートストラップ*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d406c-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="d406c-108">ときに、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントが開発用コンピューターにインストールされている Microsoft Visual Basic Power Packs ブートス トラップ パッケージを追加する、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]ブートス トラップ ディレクトリ</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。</span><span class="sxs-lookup"><span data-stu-id="d406c-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] bootstrapper directory.</span></span> <span data-ttu-id="d406c-109">このパッケージは次のいずれかの前提条件を追加する手順を実行すると使用可能になります[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]または Windows インストーラーの展開。</span><span class="sxs-lookup"><span data-stu-id="d406c-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="d406c-110">既定では、ブートストラップ コンポーネントは、インストール パッケージと同じ場所から配置されます。</span><span class="sxs-lookup"><span data-stu-id="d406c-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="d406c-111">または、必要に応じてユーザーがダウンロードできるような URL またはファイルの共有位置からコンポーネントを配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="d406c-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d406c-112">ブートストラップ コンポーネントをインストールするには、コンピューターに対する管理者または同様のユーザー アクセス許可が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d406c-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="d406c-113">[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]アプリケーション、つまり、ユーザーに、アプリケーションで指定されたセキュリティ レベルに関係なく、アプリケーションをインストールする管理アクセス許可は必要があります。</span><span class="sxs-lookup"><span data-stu-id="d406c-113">For [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="d406c-114">アプリケーションのインストール後は、管理アクセス許可がなくてもアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="d406c-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="d406c-115">インストール中に、ユーザーがインストールするように求められます、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントがセットアップ先のコンピューターに存在しない場合</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。</span><span class="sxs-lookup"><span data-stu-id="d406c-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="d406c-116">ブートス トラップする代わりは事前に展開する、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>Microsoft Systems Management Server のような電子ソフトウェア配布システムを使用してコンポーネント</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。</span><span class="sxs-lookup"><span data-stu-id="d406c-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d406c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d406c-117">See also</span></span>  
 <span data-ttu-id="d406c-118">[方法: ClickOnce アプリケーションと共に必須コンポーネントをインストール](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span><span class="sxs-lookup"><span data-stu-id="d406c-118">[How to: Install Prerequisites with a ClickOnce Application](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span></span>  
<span data-ttu-id="d406c-119"> [PrintForm コンポーネント](../../../visual-basic/developing-apps/printing/printform-component.md)</span><span class="sxs-lookup"><span data-stu-id="d406c-119"> [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)</span></span>
