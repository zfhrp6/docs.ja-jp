---
title: アプリケーションの構成
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 170583239ed357904e723aebdaef9809938b5123
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-your-application"></a><span data-ttu-id="e2beb-102">アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="e2beb-102">Configuring Your Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="e2beb-103"> では、.NET 構成システムを使用して、コンピューターとアプリケーションのスコープでサービスを構成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e2beb-103"> uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="e2beb-104">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって定義された構成設定は、`<system.serviceModel>` セクション グループにあります。</span><span class="sxs-lookup"><span data-stu-id="e2beb-104">Configuration settings defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="e2beb-105">構成する方法について、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービスを次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2beb-105">For more information about how to configure a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e2beb-106">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="e2beb-106">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [<span data-ttu-id="e2beb-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e2beb-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="e2beb-108">アプリケーション定義の構成設定は、`<appSettings>` セクション グループで定義されています。</span><span class="sxs-lookup"><span data-stu-id="e2beb-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="e2beb-109">.NET 構成ファイル内のアプリケーション設定の詳細については、次を参照してください。 [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159)です。</span><span class="sxs-lookup"><span data-stu-id="e2beb-109">For more information about application settings in .NET configuration files, see [\<appSettings>](http://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="e2beb-110">構成エディターの使用</span><span class="sxs-lookup"><span data-stu-id="e2beb-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="e2beb-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)作成および構成設定を変更するには、管理者および開発者[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]services のグラフィカル ユーザー インターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e2beb-111">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using a graphical user interface.</span></span> <span data-ttu-id="e2beb-112">このツールを使用すると、XML 構成ファイルを直接編集せずに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のバインディング、動作、サービス、および診断の設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="e2beb-112">With this tool, you can manage settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="e2beb-113">Visual Studio の構成ファイルの編集</span><span class="sxs-lookup"><span data-stu-id="e2beb-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="e2beb-114">構成ファイルを編集する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービス プロジェクトを Visual Studio で、右クリックして **ソリューション エクスプ ローラー**を選択し、 **Edit WCF Config**コンテキスト メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="e2beb-114">To edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="e2beb-115">これにより、起動、[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="e2beb-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2beb-116">構成ファイルを編集する場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]で右クリックして Visual Studio で Web サービス プロジェクト**ソリューション エクスプ ローラー**、ことに注意して、 **Edit WCF Config**コンテキスト メニュー項目がありません。</span><span class="sxs-lookup"><span data-stu-id="e2beb-116">If you edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="e2beb-117">この問題を回避するには、をクリックして、**ツール**] メニューの [選択**WCF Service Config Editor**です。</span><span class="sxs-lookup"><span data-stu-id="e2beb-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="e2beb-118">その後、構成ファイルを右クリックして使用することができます、 **Edit WCF Config**コンテキスト メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="e2beb-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2beb-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2beb-119">See Also</span></span>  
 [<span data-ttu-id="e2beb-120">構成エディター ツール (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="e2beb-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="e2beb-121">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="e2beb-121">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="e2beb-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e2beb-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
