---
title: "Web 設定スキーマ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a4ece61330fe8e41d9afb894791f9f9e36db35f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="web-settings-schema"></a><span data-ttu-id="df860-102">Web 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="df860-102">Web Settings Schema</span></span>
<span data-ttu-id="df860-103">Web 設定は、CPU と、ASP.NET ホスト層によって管理されているプロセス全体の動作に適用される CPU および ASP.NET 設定の実行レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="df860-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="df860-104">これらの設定は、ASP.NET アプリケーションの Web.config ファイルで指定されているアプリケーション ドメインの種類の設定とは異なります。</span><span class="sxs-lookup"><span data-stu-id="df860-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="df860-105">Web 設定は、.NET Framework のバージョンのインストール フォルダーに配置された Aspnet.config ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="df860-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="df860-106">たとえば、[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] の Aspnet.config ファイルは次のフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="df860-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="df860-107">Web 設定は、machine.config ファイル、ルート、Web.config ファイル、アプリケーション レベルの Web.config ファイルなどの他の構成ファイルでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="df860-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="df860-108">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="df860-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="df860-109">\<system.web> 要素 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="df860-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="df860-110">\<applicationPool> 要素 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="df860-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="df860-111">要素</span><span class="sxs-lookup"><span data-stu-id="df860-111">Element</span></span>|<span data-ttu-id="df860-112">説明</span><span class="sxs-lookup"><span data-stu-id="df860-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df860-113">\<system.web ></span><span class="sxs-lookup"><span data-stu-id="df860-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="df860-114">ASP.NET ホスト層が使用する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="df860-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="df860-115">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="df860-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="df860-116">CPU と、ASP.NET ホスト層によって管理されているプロセス全体の動作に適用される CPU および ASP.NET 設定の実行レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="df860-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df860-117">参照</span><span class="sxs-lookup"><span data-stu-id="df860-117">See Also</span></span>  
 [<span data-ttu-id="df860-118">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="df860-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
