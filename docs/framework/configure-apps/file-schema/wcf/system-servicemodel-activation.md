---
title: '&lt;system.serviceModel.activation&gt;'
ms.date: 03/30/2017
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
ms.openlocfilehash: 7d4ad87e9ad9f0bc4cb3c5157666b098dd0b0243
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemservicemodelactivationgt"></a><span data-ttu-id="47fb7-102">&lt;system.serviceModel.activation&gt;</span><span class="sxs-lookup"><span data-stu-id="47fb7-102">&lt;system.serviceModel.activation&gt;</span></span>
<span data-ttu-id="47fb7-103">この構成セクションは、SMSvcHost.exe ツールの構成設定を表します。</span><span class="sxs-lookup"><span data-stu-id="47fb7-103">This configuration section represents the configuration settings for the SMSvcHost.exe tool.</span></span> <span data-ttu-id="47fb7-104">構成要素は、SMSvcHost.exe.config ファイルで構成できます。</span><span class="sxs-lookup"><span data-stu-id="47fb7-104">The configuration elements can be configured in the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="47fb7-105">特にここには、構成される必要があるコンピューター全体のすべての設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="47fb7-105">Specifically, it includes all machine-wide settings that must be configured.</span></span>  
  
## <a name="sample-configuration-file"></a><span data-ttu-id="47fb7-106">サンプル構成ファイル</span><span class="sxs-lookup"><span data-stu-id="47fb7-106">Sample Configuration File</span></span>  
 <span data-ttu-id="47fb7-107">次は、リスナー プロセス SMSvcHost.exe で使用されるサンプル構成ファイル (SMSvcHost.exe.config) です。</span><span class="sxs-lookup"><span data-stu-id="47fb7-107">The following is a sample configuration file (SMSvcHost.exe.config), which is used by the listener process SMSvcHost.exe.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false" />  
   </runtime>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="10"  
          maxPendingAccepts="2"  
          maxPendingConnections="100"  
          receiveTimeout="00:00:10"  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Network Service account -->  
            <add securityIdentifier="S-1-5-20"/>   
             <!-- Administrators account -->  
            <add securityIdentifier="S-1-5-32-544" />   
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
       <net.pipe maxConnectionsPendingDispatch="100"  
          maxPendingAccepts="2"  
          receiveTimeout="00:00:10">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Network Service account -->  
            <add securityIdentifier="S-1-5-20"/>   
             <!-- Administrators account -->  
            <add securityIdentifier="S-1-5-32-544" />   
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
       <diagnostics performanceCountersEnabled="true" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47fb7-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="47fb7-108">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration>
