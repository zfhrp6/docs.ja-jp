---
title: "方法 : Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5db89cf6220f086d2d71b99f3e6440e584d6a5d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="9131d-102">方法 : Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="9131d-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]<span data-ttu-id="9131d-103">インターネット ゾーン アクセス許可セットに制限されている部分的に信頼されたセキュリティ サンド ボックス内で実行します。</span><span class="sxs-lookup"><span data-stu-id="9131d-103"> run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="9131d-104">このアクセス許可セットは、Web で配置されているサービスのみを Web サービス呼び出しを制限、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]元のアプリケーションのサイトです。</span><span class="sxs-lookup"><span data-stu-id="9131d-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="9131d-105">ときに、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]からデバッグ[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]も、Web サービスに参照としては、元の同じサイトがないと見なされます。</span><span class="sxs-lookup"><span data-stu-id="9131d-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="9131d-106">この原因セキュリティ例外を発生させると、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web サービスを呼び出すしようとしています。</span><span class="sxs-lookup"><span data-stu-id="9131d-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="9131d-107">ただし、 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]プロジェクトは、デバッグ中に呼び出し、Web サービスと同じサイトに元のシミュレートするように構成できます。</span><span class="sxs-lookup"><span data-stu-id="9131d-107">However, a [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="9131d-108">これにより、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]を安全にセキュリティ例外を発生させることがなく、Web サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9131d-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>  
  
## <a name="configuring-visual-studio"></a><span data-ttu-id="9131d-109">Visual Studio の構成</span><span class="sxs-lookup"><span data-stu-id="9131d-109">Configuring Visual Studio</span></span>  
 <span data-ttu-id="9131d-110">構成する[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]をデバッグする、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9131d-110">To configure [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>  
  
1.  <span data-ttu-id="9131d-111">**ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9131d-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="9131d-112">**プロジェクト デザイナー**をクリックして、**デバッグ**タブです。</span><span class="sxs-lookup"><span data-stu-id="9131d-112">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="9131d-113">**開始動作**セクションで、**外部プログラムの開始**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9131d-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  <span data-ttu-id="9131d-114">**開始オプション**セクションで、次の点を入力してください、**コマンドライン引数**テキスト ボックス。</span><span class="sxs-lookup"><span data-stu-id="9131d-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="9131d-115">`-debug`  *ファイル名*</span><span class="sxs-lookup"><span data-stu-id="9131d-115">`-debug`  *filename*</span></span>  
  
     <span data-ttu-id="9131d-116">*ファイル名*値を**-デバッグ**パラメーターは、.xbap ファイル名。 例。</span><span class="sxs-lookup"><span data-stu-id="9131d-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  <span data-ttu-id="9131d-117">これは、既定の構成で作成したソリューションは、 [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)]プロジェクト テンプレート。</span><span class="sxs-lookup"><span data-stu-id="9131d-117">This is the default configuration for solutions that are created with the [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>  
  
1.  <span data-ttu-id="9131d-118">**ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9131d-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="9131d-119">**プロジェクト デザイナー**をクリックして、**デバッグ**タブです。</span><span class="sxs-lookup"><span data-stu-id="9131d-119">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="9131d-120">**開始オプション**セクションで、次のコマンド ライン パラメーターを追加、**コマンドライン引数**テキスト ボックス。</span><span class="sxs-lookup"><span data-stu-id="9131d-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="9131d-121">`-debugSecurityZoneURL`  *URL*</span><span class="sxs-lookup"><span data-stu-id="9131d-121">`-debugSecurityZoneURL`  *URL*</span></span>  
  
     <span data-ttu-id="9131d-122">*URL*値を**- debugSecurityZoneURL**パラメーターは、[!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)]として、アプリケーションの元のサイトをシミュレートする場所です。</span><span class="sxs-lookup"><span data-stu-id="9131d-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>  
  
 <span data-ttu-id="9131d-123">たとえば、次のように検討します、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]に次の Web サービスを使用する[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:。</span><span class="sxs-lookup"><span data-stu-id="9131d-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 <span data-ttu-id="9131d-124">元のサイト[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]この Web サービスは。</span><span class="sxs-lookup"><span data-stu-id="9131d-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>  
  
 `http://services.msdn.microsoft.com`  
  
 <span data-ttu-id="9131d-125">その結果、完全な**- debugSecurityZoneURL**コマンド ライン パラメーターと値は。</span><span class="sxs-lookup"><span data-stu-id="9131d-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a><span data-ttu-id="9131d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="9131d-126">See Also</span></span>  
 [<span data-ttu-id="9131d-127">WPF ホスト (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="9131d-127">WPF Host (PresentationHost.exe)</span></span>](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
