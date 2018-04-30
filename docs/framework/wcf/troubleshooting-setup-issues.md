---
title: セットアップに関する問題のトラブルシューティング
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9238c1a1c9092e6806ee941bd7c992071cf98e09
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="troubleshooting-setup-issues"></a><span data-ttu-id="ce775-102">セットアップに関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ce775-102">Troubleshooting Setup Issues</span></span>
<span data-ttu-id="ce775-103">ここでは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] セットアップ問題のトラブルシューティングの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ce775-103">This topic describes how to troubleshoot [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] set up issues.</span></span>  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a><span data-ttu-id="ce775-104">.NET Framework 3.0 の MSI 修復操作の実行では修復されない一部の Windows Communication Foundation レジストリ キー</span><span class="sxs-lookup"><span data-stu-id="ce775-104">Some Windows Communication Foundation Registry Keys are not Repaired by Performing an MSI Repair Operation on the .NET Framework 3.0</span></span>  
 <span data-ttu-id="ce775-105">次のいずれかのレジストリ キーを削除した場合</span><span class="sxs-lookup"><span data-stu-id="ce775-105">If you delete any of the following registry keys:</span></span>  
  
-   <span data-ttu-id="ce775-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="ce775-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span></span>  
  
-   <span data-ttu-id="ce775-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="ce775-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span></span>  
  
-   <span data-ttu-id="ce775-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="ce775-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span></span>  
  
-   <span data-ttu-id="ce775-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="ce775-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span></span>  
  
-   <span data-ttu-id="ce775-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="ce775-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span></span>  
  
 <span data-ttu-id="ce775-111">起動した .NET Framework 3.0 インストーラーを使用して修復を実行する場合、キーが再作成されません、**プログラムの追加/削除**アプレットを**コントロール パネルの **です。</span><span class="sxs-lookup"><span data-stu-id="ce775-111">The keys are not re-created if you run repair by using the .NET Framework 3.0 installer launched from the **Add/Remove Programs** applet in **Control Panel**.</span></span> <span data-ttu-id="ce775-112">これらのキーを正しく再作成するには、.NET Framework 3.0 をアンインストール後、再インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce775-112">To recreate these keys correctly, the user must uninstall and reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a><span data-ttu-id="ce775-113">WMI サービスの破損により .NET Framework 3.0 パッケージのインストール中に Windows Communication Foundation WMI プロバイダーのインストールがブロックされる</span><span class="sxs-lookup"><span data-stu-id="ce775-113">WMI Service Corruption Blocks Installation of the Windows Communication Foundation WMI provider during installation of .NET Framework 3.0 package</span></span>  
 <span data-ttu-id="ce775-114">WMI サービスの破損により、Windows Communication Foundation WMI プロバイダーのインストールがブロックされることがあります。</span><span class="sxs-lookup"><span data-stu-id="ce775-114">WMI Service Corruption may block the installation of the Windows Communication Foundation WMI provider.</span></span> <span data-ttu-id="ce775-115">インストール中、Windows Communication Foundation インストーラーは mofcomp.exe コンポーネントを使用して WCF .mof ファイルを登録できません。</span><span class="sxs-lookup"><span data-stu-id="ce775-115">During installation the Windows Communication Foundation installer is unable to register the WCF .mof file using the mofcomp.exe component.</span></span> <span data-ttu-id="ce775-116">発生する現象を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ce775-116">The following is a list of symptoms:</span></span>  
  
1.  <span data-ttu-id="ce775-117">.NET Framework 3.0 のインストールは正常に完了するのに、WCF WMI プロバイダーが登録されない。</span><span class="sxs-lookup"><span data-stu-id="ce775-117">.NET Framework 3.0 installation completes successfully, but the WCF WMI provider is not registered.</span></span>  
  
2.  <span data-ttu-id="ce775-118">アプリケーション イベント ログに、WCF の WMI プロバイダーの登録、または mofcomp.exe の実行に関する問題を示すエラー イベントが表示される。</span><span class="sxs-lookup"><span data-stu-id="ce775-118">An error event appears in the application event log that references problems registering the WMI provider for WCF, or running mofcomp.exe.</span></span>  
  
3.  <span data-ttu-id="ce775-119">ユーザーの %temp% ディレクトリの dd_wcf_retCA\* という名前のセットアップ ログ ファイルに、WCF WMI プロバイダーの登録に失敗したことが示される。</span><span class="sxs-lookup"><span data-stu-id="ce775-119">The setup log file named dd_wcf_retCA\* in the user's %temp% directory contains references to failure to register the WCF WMI provider.</span></span>  
  
4.  <span data-ttu-id="ce775-120">イベント ログまたはセットアップ トレース ログ ファイルに、次の例外のいずれかが記録される。</span><span class="sxs-lookup"><span data-stu-id="ce775-120">An exception such as one the following may be listed in the event log or setup trace log file:</span></span>  
  
     <span data-ttu-id="ce775-121">ServiceModelReg [11:09:59:046]: System.ApplicationException : "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" で E:\WINDOWS\system32\wbem\mofcomp.exe を実行している間に予期しない結果 3 が発生しました</span><span class="sxs-lookup"><span data-stu-id="ce775-121">ServiceModelReg [11:09:59:046]: System.ApplicationException: Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"</span></span>  
  
     <span data-ttu-id="ce775-122">または</span><span class="sxs-lookup"><span data-stu-id="ce775-122">or:</span></span>  
  
     <span data-ttu-id="ce775-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException : 'System.Management.ManagementPath' の型初期化子が例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="ce775-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: The type initializer for 'System.Management.ManagementPath' threw an exception.</span></span> <span data-ttu-id="ce775-124">---> System.Runtime.InteropServices.COMException (0x80040154) : CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} を含むコンポーネントの COM クラス ファクトリを取得中に、次のエラーが発生しました: 80040154。</span><span class="sxs-lookup"><span data-stu-id="ce775-124">---> System.Runtime.InteropServices.COMException (0x80040154): Retrieving the COM class factory for component with CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} failed due to the following error: 80040154.</span></span>  
  
     <span data-ttu-id="ce775-125">または</span><span class="sxs-lookup"><span data-stu-id="ce775-125">or:</span></span>  
  
     <span data-ttu-id="ce775-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException : ファイルまたはアセンブリ 'C:\WINDOWS\system32\wbem\mofcomp.exe'、またはその依存関係の 1 つが読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="ce775-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Could not load file or assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' or one of its dependencies.</span></span> <span data-ttu-id="ce775-127">指定されたファイルが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="ce775-127">The system cannot find the file specified.</span></span>  
  
     <span data-ttu-id="ce775-128">ファイル名 : C:\WINDOWS\system32\wbem\mofcomp.exe</span><span class="sxs-lookup"><span data-stu-id="ce775-128">File name: 'C:\WINDOWS\system32\wbem\mofcomp.exe</span></span>  
  
 <span data-ttu-id="ce775-129">上で説明した問題を解決するためには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce775-129">The following steps must be followed to resolve the problem described previously.</span></span>  
  
1.  <span data-ttu-id="ce775-130">実行[WMI 診断ユーティリティ、バージョン 2.0](http://go.microsoft.com/fwlink/?LinkId=94685) WMI サービスを修復します。</span><span class="sxs-lookup"><span data-stu-id="ce775-130">Run [the WMI Diagnosis Utility, version 2.0](http://go.microsoft.com/fwlink/?LinkId=94685) to repair the WMI service.</span></span> <span data-ttu-id="ce775-131">詳細については、このツールを使用して、次を参照してください。、 [WMI 診断ユーティリティ](http://go.microsoft.com/fwlink/?LinkId=94686)トピックです。</span><span class="sxs-lookup"><span data-stu-id="ce775-131">For more information about using this tool, see the [WMI Diagnosis Utility](http://go.microsoft.com/fwlink/?LinkId=94686) topic.</span></span>  
  
 <span data-ttu-id="ce775-132">使用して .NET Framework 3.0 のインストールを修復、**プログラムの追加/削除**内にあるアプレット**コントロール パネル**、または .NET Framework 3.0 のアンインストール/再インストールします。</span><span class="sxs-lookup"><span data-stu-id="ce775-132">Repair the .NET Framework 3.0 installation by using the **Add/Remove Programs** applet located in **Control Panel**, or uninstall/reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a><span data-ttu-id="ce775-133">.NET Framework 3.5 のインストール後に .NET Framework 3.0 を修復すると、.NET Framework 3.5 によって導入された machine.config 内の構成要素が削除される</span><span class="sxs-lookup"><span data-stu-id="ce775-133">Repairing .NET Framework 3.0 after .NET Framework 3.5 Installation Removes Configuration Elements Introduced by .NET Framework 3.5 in machine.config</span></span>  
 <span data-ttu-id="ce775-134">[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] をインストールした後に .NET Framework 3.0 を修復すると、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] によって導入された machine.config 内の構成要素が削除されます。</span><span class="sxs-lookup"><span data-stu-id="ce775-134">If you do a repair of .NET Framework 3.0 after you installed [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], configuration elements introduced by [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] in machine.config are removed.</span></span> <span data-ttu-id="ce775-135">ただし、web.config は元の状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="ce775-135">However, the web.config remains intact.</span></span> <span data-ttu-id="ce775-136">修復の回避策は[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]ARP、または使用を使用してその後、[ワークフロー サービス登録ツール (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md)で、`/c`スイッチします。</span><span class="sxs-lookup"><span data-stu-id="ce775-136">The workaround is to repair [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] after this via ARP, or use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch.</span></span>  
  
 <span data-ttu-id="ce775-137">[ワークフロー サービス登録ツール (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\framework\v3.5\ または %windir%\Microsoft.NET\framework64\v3.5\ にあります</span><span class="sxs-lookup"><span data-stu-id="ce775-137">[WorkFlow Service Registration Tool (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\\</span></span>  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a><span data-ttu-id="ce775-138">.NET Framework 3.5 のインストール後に WCF/WF Webhost に対して IIS を適切に構成する</span><span class="sxs-lookup"><span data-stu-id="ce775-138">Configure IIS Properly for WCF/WF Webhost after Installing .NET Framework 3.5</span></span>  
 <span data-ttu-id="ce775-139">[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] のインストールでは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に関連する追加の IIS 構成設定の構成に失敗すると、インストール ログにエラーが記録され、インストールが続行されます。</span><span class="sxs-lookup"><span data-stu-id="ce775-139">When [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation fails to configure additional [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-related IIS configuration settings, it logs an error in the installation log and continues.</span></span> <span data-ttu-id="ce775-140">WorkflowServices アプリケーションを実行しようとしても、必要な構成設定がないため、実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="ce775-140">Any attempt to run WorkflowServices applications will fail, since the required configuration settings are missing.</span></span> <span data-ttu-id="ce775-141">たとえば、xoml やルール サービスの読み込みに失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ce775-141">For example, loading xoml or rules service can fail.</span></span>  
  
 <span data-ttu-id="ce775-142">回避策を使用して、この問題、[ワークフロー サービス登録ツール (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md)で、`/c`正しく、マシンでスクリプト マップを IIS を構成するスイッチです。</span><span class="sxs-lookup"><span data-stu-id="ce775-142">To workaround this problem, use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch to properly configure IIS script maps on the machine.</span></span> <span data-ttu-id="ce775-143">[ワークフロー サービス登録ツール (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\framework\v3.5\ または %windir%\Microsoft.NET\framework64\v3.5\ にあります</span><span class="sxs-lookup"><span data-stu-id="ce775-143">[WorkFlow Service Registration Tool (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\\</span></span>  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a><span data-ttu-id="ce775-144">アセンブリ 'System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' から型 'System.ServiceModel.Activation.HttpModule' を読み込むことができない</span><span class="sxs-lookup"><span data-stu-id="ce775-144">Could not load type ‘System.ServiceModel.Activation.HttpModule’ from assembly ‘System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089’</span></span>  
 <span data-ttu-id="ce775-145">このエラーが発生[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]がインストールされているし、 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] HTTP アクティブ化が有効にします。</span><span class="sxs-lookup"><span data-stu-id="ce775-145">This error occurs if [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] is installed and then [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)][!INCLUDE[indigo2](../../../includes/indigo2-md.md)] HTTP Activation is enabled.</span></span> <span data-ttu-id="ce775-146">この問題を解決するには、[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] コマンド プロンプト内から次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ce775-146">To resolve the issue run the following command-line from inside the [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] Command Prompt:</span></span>  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce775-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce775-147">See Also</span></span>  
 [<span data-ttu-id="ce775-148">セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="ce775-148">Set-Up Instructions</span></span>](../../../docs/framework/wcf/samples/set-up-instructions.md)
