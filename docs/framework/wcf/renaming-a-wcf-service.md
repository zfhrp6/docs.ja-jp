---
title: WCF サービス名の変更
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498988"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="e39ea-102">WCF サービス名の変更</span><span class="sxs-lookup"><span data-stu-id="e39ea-102">Renaming a WCF Service</span></span>
<span data-ttu-id="e39ea-103">このトピックでは、Windows Communication Foundation (WCF) サービスの名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e39ea-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="e39ea-104">WCF サービス名の変更</span><span class="sxs-lookup"><span data-stu-id="e39ea-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="e39ea-105">Windows Communication Foundation (WCF) のテンプレートでは、サービスの名前を変更する次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e39ea-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
-   <span data-ttu-id="e39ea-106">サービスを実装するクラスの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="e39ea-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="e39ea-107">次の例に示すように、このサービスの構成ファイルで、サービスの名前を新しい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="e39ea-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="e39ea-108">構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="e39ea-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="e39ea-109">サービスが Web ホストである場合、\*.svc ファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e39ea-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="e39ea-110">この svc ファイルを開き、次の例に示すように、サービスの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="e39ea-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="e39ea-111">自己ホスト アプリケーションには svc ファイルがないので、この手順は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e39ea-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="e39ea-112">WCF サービス コントラクト名の変更</span><span class="sxs-lookup"><span data-stu-id="e39ea-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="e39ea-113">サービス コントラクトの名前を変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e39ea-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="e39ea-114">サービス コントラクトの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="e39ea-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="e39ea-115">次の例に示すように、このサービスの構成ファイルで、サービス コントラクトの名前を新しい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="e39ea-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="e39ea-116">構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="e39ea-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
