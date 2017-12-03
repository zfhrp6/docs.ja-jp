---
title: "ServiceModel 登録ツール (ServiceModelReg.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cfe522817fdc9a2aea23b1c9e8dce3b658d892c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="422f5-102">ServiceModel 登録ツール (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="422f5-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="422f5-103">このコマンド ライン ツールは、単一コンピューター上で WCF および WF コンポーネントの登録を管理するための機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="422f5-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="422f5-104">WCF および WF コンポーネントはインストール時に構成されるため、通常の状況ではこのツールを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="422f5-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="422f5-105">しかし、サービスのアクティブ化に関する問題が発生する場合は、このツールを使用してコンポーネントを登録できます。</span><span class="sxs-lookup"><span data-stu-id="422f5-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="422f5-106">構文</span><span class="sxs-lookup"><span data-stu-id="422f5-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="422f5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="422f5-107">Remarks</span></span>  
 <span data-ttu-id="422f5-108">ツールは次の場所にあります。</span><span class="sxs-lookup"><span data-stu-id="422f5-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="422f5-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="422f5-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="422f5-110">ServiceModel 登録ツールを実行するときに[!INCLUDE[wv](../../../includes/wv-md.md)]、 **Windows の機能の**ダイアログことが反映されない、 **Windows Communication Foundation HTTP Activation** 下のオプション**Microsoft .NET Framework 3.0**がオンになっています。</span><span class="sxs-lookup"><span data-stu-id="422f5-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="422f5-111">**Windows の機能の**ダイアログをクリックしてアクセスできる**開始**、順にクリックして**実行**」と入力し、 **OptionalFeatures**です。</span><span class="sxs-lookup"><span data-stu-id="422f5-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="422f5-112">次の表は、ServiceModelReg.exe で使用できるオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="422f5-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="422f5-113">オプション</span><span class="sxs-lookup"><span data-stu-id="422f5-113">Option</span></span>|<span data-ttu-id="422f5-114">説明</span><span class="sxs-lookup"><span data-stu-id="422f5-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="422f5-115">WCF および WF のすべてのコンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="422f5-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="422f5-116">WCF および WF のすべてのコンポーネントをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="422f5-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="422f5-117">WCF および WF のすべてのコンポーネントを修復します。</span><span class="sxs-lookup"><span data-stu-id="422f5-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="422f5-118">-c で指定された WCF および WF のコンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="422f5-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="422f5-119">-c で指定された WCF および WF のコンポーネントをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="422f5-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="422f5-120">コンポーネントをインストールまたはアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="422f5-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="422f5-121">-httpnamespace – HTTP Namespace 予約</span><span class="sxs-lookup"><span data-stu-id="422f5-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="422f5-122">-tcpportsharing – TCP ポート共有サービス</span><span class="sxs-lookup"><span data-stu-id="422f5-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="422f5-123">-tcpactivation – TCP のアクティブ化サービス (.NET 4 クライアント プロファイルでサポートされていません)</span><span class="sxs-lookup"><span data-stu-id="422f5-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="422f5-124">-namedpipeactivation-名前付きパイプのアクティブ化サービス (.NET 4 クライアント プロファイルでサポートされていません</span><span class="sxs-lookup"><span data-stu-id="422f5-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="422f5-125">(.NET 4 クライアント プロファイルでサポートされていません - msmqactivation – MSMQ アクティブ化サービス</span><span class="sxs-lookup"><span data-stu-id="422f5-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="422f5-126">-etw – ETW イベントの追跡マニフェスト (Windows Vista またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="422f5-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="422f5-127">Quiet モード (エラー ログのみ表示)</span><span class="sxs-lookup"><span data-stu-id="422f5-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="422f5-128">Verbose モード</span><span class="sxs-lookup"><span data-stu-id="422f5-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="422f5-129">著作権やバナー メッセージを表示しません。</span><span class="sxs-lookup"><span data-stu-id="422f5-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="422f5-130">ヘルプ テキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="422f5-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="422f5-131">FileLoadException エラーの修正</span><span class="sxs-lookup"><span data-stu-id="422f5-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="422f5-132">コンピューターに以前のバージョンの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] をインストールしている場合は、ServiceModelReg ツールを実行して新しいインストールを登録するときに、`FileLoadFoundException` エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="422f5-132">If you installed previous versions of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="422f5-133">旧バージョンのインストールから手動でファイルを削除しても、machine.config 設定が元のままである限り、このエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="422f5-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="422f5-134">エラー メッセージは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="422f5-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="422f5-135">System.ServiceModel Version 2.0.0.0 アセンブリが旧 CTP (Customer Technology Preview) リリースによってインストールされていたというエラー メッセージに注目する必要があります。</span><span class="sxs-lookup"><span data-stu-id="422f5-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="422f5-136">最新バージョンの System.ServiceModel アセンブリは、2.0.0.0 ではなく 3.0.0.0 です。</span><span class="sxs-lookup"><span data-stu-id="422f5-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="422f5-137">したがって、旧 CTP リリースの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] がインストールされたままで、完全にはアンインストールされていないコンピューターに正式の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] リリースをインストールすると、この問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="422f5-137">Therefore, this issue is encountered when you want to install the official [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] release on a machine where an early CTP release of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="422f5-138">ServiceModelReg.exe は、旧バージョンのエントリをクリーンアップすることも、新しいバージョンのエントリを登録することもできません。</span><span class="sxs-lookup"><span data-stu-id="422f5-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="422f5-139">唯一の回避策は、machine.config を手動で編集することです。このファイルは次の場所にあります。</span><span class="sxs-lookup"><span data-stu-id="422f5-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="422f5-140">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を 64 ビット コンピューターで実行している場合は、次の場所にある同じファイルも編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="422f5-140">If you are running [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="422f5-141">このファイルを参照する XML ノードを見つけ"'system.servicemodel, Version 2.0.0.0 を ="、および子ノードを削除します。</span><span class="sxs-lookup"><span data-stu-id="422f5-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="422f5-142">ファイルを保存し ServiceModelReg.exe を再実行すると、この問題は解決します。</span><span class="sxs-lookup"><span data-stu-id="422f5-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="422f5-143">例</span><span class="sxs-lookup"><span data-stu-id="422f5-143">Examples</span></span>  
 <span data-ttu-id="422f5-144">次の例に、ServiceModelReg.exe ツールの最も一般的なオプションの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="422f5-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
