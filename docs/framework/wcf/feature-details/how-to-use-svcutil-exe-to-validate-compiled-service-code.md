---
title: "方法 : Svcutil.exe を使用してコンパイル済みサービス コードを検証する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b60356bd66a49c9599a8e0a9138d3b92dbe0b23c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="d4577-102">方法 : Svcutil.exe を使用してコンパイル済みサービス コードを検証する</span><span class="sxs-lookup"><span data-stu-id="d4577-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>
<span data-ttu-id="d4577-103">使用することができます、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)にサービスをホストせず、サービスの実装と構成のエラーを検出します。</span><span class="sxs-lookup"><span data-stu-id="d4577-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="d4577-104">サービスを検証するには</span><span class="sxs-lookup"><span data-stu-id="d4577-104">To validate a service</span></span>  
  
1.  <span data-ttu-id="d4577-105">サービスを実行可能ファイルおよび 1 つ以上の依存アセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="d4577-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2.  <span data-ttu-id="d4577-106">SDK コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="d4577-106">Open an SDK command prompt</span></span>  
  
3.  <span data-ttu-id="d4577-107">コマンド プロンプトで、次の形式を使用して Svcutil.exe ツールを起動します。</span><span class="sxs-lookup"><span data-stu-id="d4577-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="d4577-108">さまざまなパラメーターの詳細については、のサービス Validationsection を参照してください、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="d4577-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="d4577-109">`/serviceName` オプションを使用して、検証するサービスの構成名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4577-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="d4577-110">`assemblyPath` 引数には、検証対象のサービスの実行可能ファイルへのパス、およびサービス型を格納している 1 つ以上のアセンブリへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4577-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="d4577-111">実行可能アセンブリに、サービス構成を提供する関連構成ファイルが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4577-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="d4577-112">標準のコマンドライン ワイルドカードを使用して、複数のアセンブリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d4577-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4577-113">例</span><span class="sxs-lookup"><span data-stu-id="d4577-113">Example</span></span>  
 <span data-ttu-id="d4577-114">次のコマンドでは、myServiceHost.exe 実行可能ファイルに実装されたサービス myServiceName を検証します。</span><span class="sxs-lookup"><span data-stu-id="d4577-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="d4577-115">サービスの構成ファイル (myServiceHost.exe.config) は自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d4577-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4577-116">参照</span><span class="sxs-lookup"><span data-stu-id="d4577-116">See Also</span></span>  
 [<span data-ttu-id="d4577-117">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d4577-117">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
