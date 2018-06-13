---
title: '方法 : COM+ サービス モデル構成ツールを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: d26e3b127328a3de4df6bd58fb6015bee045f3c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496241"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="5a2b1-102">方法 : COM+ サービス モデル構成ツールを使用する</span><span class="sxs-lookup"><span data-stu-id="5a2b1-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="5a2b1-103">適切なホスト モードを選択したら、COM+ サービス モデル構成コマンド ライン ツール (ComSvcConfig.exe) を使用して、Web サービスとして公開されるアプリケーション インターフェイスを構成します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a2b1-104">以下の各作業を実行するには、コンピューターの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="5a2b1-105">Windows 7 コンピューターで ComSvcConfig.exe を使用して、最新のサービス モデル バージョン (現在 v4.5) を使用するように Web サービスを構成する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1.  <span data-ttu-id="5a2b1-106">レジストリ キー設定`[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR`DWORD 値 0x00000001 に</span><span class="sxs-lookup"><span data-stu-id="5a2b1-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2.  <span data-ttu-id="5a2b1-107">comsvcconfig.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-107">Run comsvcconfig.exe</span></span>  
  
3.  <span data-ttu-id="5a2b1-108">手順 1. で追加したレジストリ キーを元の値に戻すか、存在しない場合は削除します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a2b1-109">このレジストリ キーを元に戻すことは重要です。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-109">Reverting this registry key is important.</span></span> <span data-ttu-id="5a2b1-110">これは互換性のキーです。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-110">This is a compatibility key.</span></span> <span data-ttu-id="5a2b1-111">この変更を元に戻さないと、コンピューターで実行している他の .NET アプリケーションで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5a2b1-112">ComSvcConfig.exe を使用して Windows 8 コンピューターのダイアログで/install が表示されますを示す"お使いの PC にアプリには、次の Windows の機能が必要があります。 .NET Framework 3.5 (.NET 2.0 と .NET 3.0 を含む".NET Framework 3.5 がインストールされていない場合。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="5a2b1-113">このダイアログは無視してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-113">This dialog may be ignored.</span></span> <span data-ttu-id="5a2b1-114">また、OnlyUseLatestCLR レジストリ キーを DWORD 値 0x00000001 に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="5a2b1-115">COM+ ホスト モードを使用して、Web サービスとして公開されるインターフェイスのセットにインターフェイスを追加するには</span><span class="sxs-lookup"><span data-stu-id="5a2b1-115">To add an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="5a2b1-116">次の例に示すように、`/install` オプションと `/hosting:complus` オプションを使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="5a2b1-117">このコマンドは、Web サービスとして公開されるインターフェイスのセットに (OnlineStore COM+ アプリケーションの) `IFinances` コンポーネントの `ItemOrders.IFinancial` インターフェイスを追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="5a2b1-118">サービスは COM+ ホスト モードを使用するため、アプリケーションを明示的にアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="5a2b1-119">コンポーネントとインターフェイスにはアスタリスク (\*) をワイルドカード文字として使用できますが、選択した機能だけを Web サービスとして公開する場合は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-119">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="5a2b1-120">ワイルドカードを使用すると、このコンポーネントの将来のバージョンを使用して実行したときに、構成構文の決定時には存在しなかったインターフェイスが誤って公開される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="5a2b1-121">/verbose オプションを指定すると、ツールは、エラーだけでなく警告も表示します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="5a2b1-122">公開されたサービスのコントラクトには、`IFinances` インターフェイスのすべてのメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="5a2b1-123">COM+ ホスト モードを使用して、Web サービスとして公開されるインターフェイスのセットにインターフェイスの特定のメソッドだけを追加するには</span><span class="sxs-lookup"><span data-stu-id="5a2b1-123">To add only specific methods from an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="5a2b1-124">次の例に示すように、`/install` オプションと `/hosting:complus` オプション、および必要なメソッドの名前を明示的に指定して、ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="5a2b1-125">このコマンドは、公開されたサービス コントラクトに `Credit` インターフェイスの `Debit` メソッドと `IFinances` メソッドだけを操作として追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="5a2b1-126">インターフェイスのその他のメソッドはすべてコントラクトから除外されるため、Web サービス クライアントから呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="5a2b1-127">Web ホスト モードを使用して、Web サービスとして公開されるインターフェイスのセットにインターフェイスを追加するには</span><span class="sxs-lookup"><span data-stu-id="5a2b1-127">To add an interface to the set of interfaces that are to be exposed as Web services, using the Web hosting mode</span></span>  
  
-   <span data-ttu-id="5a2b1-128">次の例に示すように、`/install` オプションと `/hosting:was` オプションを使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="5a2b1-129">このコマンドは、Web サービスとして公開されるインターフェイスのセットに (OnlineWarehouse COM+ アプリケーションの) `IStockLevels` コンポーネントの `ItemInventory.Warehouse` インターフェイスを追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="5a2b1-130">サービスは、COM+ 内ではなく、IIS の OnlineWarehouse 仮想ディレクトリ内で Web ホストされるため、アプリケーションは、必要に応じて自動的にアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="5a2b1-131">Web ホスト (インプロセス) 構成を使用するには、コンポーネント サービス管理コンソールを使用して、サーバー アプリケーションではなくライブラリ アプリケーションとして実行されるように COM+ アプリケーションを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="5a2b1-132">サーバー アプリケーションとして構成されたアプリケーションは、標準の Web ホスト モードを使用するため、各要求の処理でプロセス ホップが発生します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="5a2b1-133">`/mex` オプションは、サービスからコントラクト定義を取得するクライアントをサポートするために、アプリケーションのサービス エンドポイントと同じトランスポートを使用する追加の Metadata Exchange (MEX) サービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="5a2b1-134">指定したインターフェイスの Web サービスを削除するには</span><span class="sxs-lookup"><span data-stu-id="5a2b1-134">To remove a Web service for a specified interface</span></span>  
  
-   <span data-ttu-id="5a2b1-135">次の例に示すように、`/uninstall` のオプションを使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="5a2b1-136">このコマンドは、(OnlineStore COM+ アプリケーションから) `IFinances` コンポーネントの `ItemOrders.Financial` インターフェイスを削除します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
### <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="5a2b1-137">現在公開されているインターフェイスを一覧表示するには</span><span class="sxs-lookup"><span data-stu-id="5a2b1-137">To list currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="5a2b1-138">次の例に示すように、`/list` のオプションを使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="5a2b1-139">このコマンドは、ローカル コンピューターに関して、現在公開されているインターフェイス、および対応するアドレスとバインディングの詳細を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="5a2b1-140">現在公開されている特定のインターフェイスを一覧表示するには</span><span class="sxs-lookup"><span data-stu-id="5a2b1-140">To list specific currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="5a2b1-141">次の例に示すように、`/list` のオプションを使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="5a2b1-142">このコマンドは、ローカル コンピューター上の OnlineStore COM+ アプリケーションの現在公開されている COM+ ホスト インターフェイスを、対応するアドレスやバインディングの詳細と共に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="5a2b1-143">ユーティリティで使用できるオプションに関するヘルプを表示するには</span><span class="sxs-lookup"><span data-stu-id="5a2b1-143">To display help on the options that can be used with the utility</span></span>  
  
-   <span data-ttu-id="5a2b1-144">次の例に示すように、/? オプションを</span><span class="sxs-lookup"><span data-stu-id="5a2b1-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="5a2b1-145">使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2b1-145">option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5a2b1-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a2b1-146">See Also</span></span>  
 [<span data-ttu-id="5a2b1-147">COM+ アプリケーションとの統合の概要</span><span class="sxs-lookup"><span data-stu-id="5a2b1-147">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
