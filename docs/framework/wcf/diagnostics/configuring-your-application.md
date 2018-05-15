---
title: アプリケーションの構成
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 1844c20ef961f191fb667e31d548518b193a7134
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-your-application"></a><span data-ttu-id="02c30-102">アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="02c30-102">Configuring Your Application</span></span>
<span data-ttu-id="02c30-103">Windows Communication Foundation (WCF) では、.NET 構成システムを使用し、コンピューターとアプリケーションの両方のスコープでサービスを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="02c30-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="02c30-104">WCF によって定義された構成設定がある、`<system.serviceModel>`セクション グループ。</span><span class="sxs-lookup"><span data-stu-id="02c30-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="02c30-105">WCF サービスを構成する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="02c30-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
-   [<span data-ttu-id="02c30-106">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="02c30-106">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [<span data-ttu-id="02c30-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="02c30-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="02c30-108">アプリケーション定義の構成設定は、`<appSettings>` セクション グループで定義されています。</span><span class="sxs-lookup"><span data-stu-id="02c30-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="02c30-109">.NET 構成ファイル内のアプリケーション設定の詳細については、次を参照してください。 [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159)です。</span><span class="sxs-lookup"><span data-stu-id="02c30-109">For more information about application settings in .NET configuration files, see [\<appSettings>](http://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="02c30-110">構成エディターの使用</span><span class="sxs-lookup"><span data-stu-id="02c30-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="02c30-111">WCF[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)管理者および開発者が作成およびグラフィカル ユーザー インターフェイスを使用して WCF サービスの構成設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="02c30-111">The WCF[Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="02c30-112">このツールでは、XML 構成ファイルを直接編集せず WCF バインディング、動作、サービス、および診断の設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="02c30-112">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="02c30-113">Visual Studio の構成ファイルの編集</span><span class="sxs-lookup"><span data-stu-id="02c30-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="02c30-114">Visual Studio での WCF サービス プロジェクトの構成ファイルを編集するを右クリックしてで**ソリューション エクスプ ローラー**を選択し、 **Edit WCF Config**コンテキスト メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="02c30-114">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="02c30-115">これにより、起動、[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="02c30-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02c30-116">右クリックして Visual Studio での WCF Web サービス プロジェクトの構成ファイルを編集する場合**ソリューション エクスプ ローラー**、ことに注意して、 **Edit WCF Config**コンテキスト メニュー項目がありません。</span><span class="sxs-lookup"><span data-stu-id="02c30-116">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="02c30-117">この問題を回避するには、をクリックして、**ツール**] メニューの [選択**WCF Service Config Editor**です。</span><span class="sxs-lookup"><span data-stu-id="02c30-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="02c30-118">その後、構成ファイルを右クリックして使用することができます、 **Edit WCF Config**コンテキスト メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="02c30-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c30-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="02c30-119">See Also</span></span>  
 [<span data-ttu-id="02c30-120">構成エディター ツール (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="02c30-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="02c30-121">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="02c30-121">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="02c30-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="02c30-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
