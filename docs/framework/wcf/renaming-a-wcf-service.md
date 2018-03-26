---
title: WCF サービス名の変更
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2ab3d780f85131fc7adf24c5f420bd5fe643d9e
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2018
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="26119-102">WCF サービス名の変更</span><span class="sxs-lookup"><span data-stu-id="26119-102">Renaming a WCF Service</span></span>
<span data-ttu-id="26119-103">ここでは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスの名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="26119-103">This topic describes how you can rename a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="26119-104">WCF サービス名の変更</span><span class="sxs-lookup"><span data-stu-id="26119-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="26119-105">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] テンプレートでサービスの名前を変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="26119-105">Perform the following steps to rename a service in a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] template,</span></span>  
  
-   <span data-ttu-id="26119-106">サービスを実装するクラスの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="26119-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="26119-107">次の例に示すように、このサービスの構成ファイルで、サービスの名前を新しい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="26119-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="26119-108">構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="26119-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="26119-109">サービスが Web ホストである場合、\*.svc ファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="26119-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="26119-110">この svc ファイルを開き、次の例に示すように、サービスの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="26119-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="26119-111">自己ホスト アプリケーションには svc ファイルがないので、この手順は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="26119-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="26119-112">WCF サービス コントラクト名の変更</span><span class="sxs-lookup"><span data-stu-id="26119-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="26119-113">サービス コントラクトの名前を変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="26119-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="26119-114">サービス コントラクトの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="26119-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="26119-115">次の例に示すように、このサービスの構成ファイルで、サービス コントラクトの名前を新しい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="26119-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="26119-116">構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="26119-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
