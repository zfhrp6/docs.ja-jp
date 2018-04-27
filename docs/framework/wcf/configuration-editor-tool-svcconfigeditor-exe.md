---
title: 構成エディター ツール (SvcConfigEditor.exe)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
caps.latest.revision: 45
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1531c68bdbb3b28436d0701536ef274f34513b19
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a><span data-ttu-id="61222-102">構成エディター ツール (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="61222-102">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>
<span data-ttu-id="61222-103">管理者と開発者は、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービス構成エディター (SvcConfigEditor.exe) のグラフィカル ユーザー インターフェイスを使用して、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの構成設定を作成および変更できます。</span><span class="sxs-lookup"><span data-stu-id="61222-103">The [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Configuration Editor (SvcConfigEditor.exe) allows administrators and developers to create and modify configuration settings for [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services using a graphical user interface.</span></span> <span data-ttu-id="61222-104">このツールを使用すると、XML 構成ファイルを直接編集せずに、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のバインディング、動作、サービス、および診断の設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="61222-104">With this tool, you can manage settings for [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bindings, behaviors, services, and diagnostics without having to directly edit XML configuration files.</span></span>  
  
 <span data-ttu-id="61222-105">サービス構成エディターは、C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="61222-105">Service Configuration Editor can be found in the C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin folder.</span></span>  
  
## <a name="the-wcf-configuration-editor"></a><span data-ttu-id="61222-106">WCF 構成エディター</span><span class="sxs-lookup"><span data-stu-id="61222-106">The WCF Configuration Editor</span></span>  
 <span data-ttu-id="61222-107">サービス構成エディターには、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のサービスやクライアントを構成する手順をすべてガイドするウィザードが付属しています。</span><span class="sxs-lookup"><span data-stu-id="61222-107">Service Configuration Editor comes with a wizard that guides you through all the steps in configuring a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service or client.</span></span> <span data-ttu-id="61222-108">エディターで直接編集する代わりにウィザードを使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61222-108">You are strongly advised to use the wizard instead of the editor directly.</span></span>  
  
 <span data-ttu-id="61222-109">標準の System.Configuration スキーマに準拠する構成ファイルが既にいくつかある場合は、ユーザー インターフェイスを使用してバインディング、動作、サービス、および診断の固有の設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="61222-109">If you already have some configuration files that comply with the standard System.Configuration schema, you can manage specific settings for bindings, behavior, services, and diagnostics with the user interface.</span></span> <span data-ttu-id="61222-110">サービス構成エディターを使用すると、既存の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 構成ファイルの設定だけでなく、実行可能ファイル、COM+ サービス、および Web ホスト サービスの設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="61222-110">The Service Configuration Editor enables you to manage the settings for existing [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration files as well as executable files, COM+ services, and Web-hosted services.</span></span> <span data-ttu-id="61222-111">サービス構成エディターで Web ホスト サービスを開くと、上位レベル ノードのサービス固有の構成セクションおよび継承された構成セクションの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="61222-111">When opening a Web-hosted service with Service Configuration Editor, both the service’s own configuration and inherited configurations sections of upper level nodes are shown.</span></span>  
  
 <span data-ttu-id="61222-112">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 構成設定は、構成ファイルの `<system.serviceModel>` セクションにあるため、エディターはこの要素の内容だけを操作し、同じファイル内の他の要素にはアクセスしません。</span><span class="sxs-lookup"><span data-stu-id="61222-112">Because [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration settings are located in the `<system.serviceModel>` section of the configuration file, the editor operates exclusively on the content of this element and does not access other elements in the same file.</span></span> <span data-ttu-id="61222-113">既存の構成ファイルに直接移動したり、サービス、仮想ディレクトリ、または COM+ サービスを含むアセンブリを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="61222-113">You can navigate to existing configuration files directly or you can select an assembly that contains a service, virtual directory, or COM+ service.</span></span> <span data-ttu-id="61222-114">エディターがその特定のサービスの構成ファイルを読み込むと、ユーザーは新しい要素を追加したり、構成ファイルの `<system.serviceModel>` セクションで入れ子になっている既存の要素を編集することができます。</span><span class="sxs-lookup"><span data-stu-id="61222-114">The editor loads the configuration file for that particular service and allows the user to either add new elements or edit existing elements nested in the `<system.serviceModel>` section of the configuration file.</span></span>  
  
 <span data-ttu-id="61222-115">エディターは、IntelliSense をサポートし、スキーマ準拠を強制します。</span><span class="sxs-lookup"><span data-stu-id="61222-115">The editor supports IntelliSense and enforces schema compliance.</span></span> <span data-ttu-id="61222-116">結果として得られる出力は、構成ファイルのスキーマに準拠し、構文的に正しいデータ値を持つことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="61222-116">The resulting output is guaranteed to comply with the schema of the configuration file and to have syntactically correct data values.</span></span> <span data-ttu-id="61222-117">ただし、エディターは構成ファイルのセマンティクスが有効であることは保証しません。</span><span class="sxs-lookup"><span data-stu-id="61222-117">However, the editor does not guarantee that the configuration file is semantically valid.</span></span> <span data-ttu-id="61222-118">つまり、エディターは構成ファイルが関連するサービスで有効に機能することは保証しません。</span><span class="sxs-lookup"><span data-stu-id="61222-118">In other words, the editor does not guarantee that the configuration file can work with the service it configures.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="61222-119">要素を変更すると、エディターは構成ファイルからその構成要素を削除できません。</span><span class="sxs-lookup"><span data-stu-id="61222-119">The editor cannot purge a configuration element from the configuration file once you have modified the element.</span></span> <span data-ttu-id="61222-120">たとえば、エディターを使用してエンドポイント名を空でない文字列に設定して保存すると、構成ファイルは次の内容になります。</span><span class="sxs-lookup"><span data-stu-id="61222-120">For example, if you use the editor to set the endpoint name to a non-empty string and save it, the configuration file has the following content, as shown in the following example.</span></span>  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  <span data-ttu-id="61222-121">そのエンドポイント名を削除するために名前を空の文字列に設定して保存しようとしても、構成ファイルには、`name` 属性が残ります。</span><span class="sxs-lookup"><span data-stu-id="61222-121">If you attempt to remove the name by setting it to an empty string and save the file, the configuration file still contains the `name` attribute, as shown in the following example.</span></span>  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  <span data-ttu-id="61222-122">属性を削除するには、別のテキスト エディターを使用して要素を手動で編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61222-122">To purge the attribute, you must manually edit the element using another text editor.</span></span>  
>   
>  <span data-ttu-id="61222-123">特に、`issueToken` エンドポイント動作の `clientCredential` 要素を使用する場合は、この問題に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61222-123">You should be especially careful with this issue when you use the `issueToken` element of the `clientCredential` Endpoint behavior.</span></span> <span data-ttu-id="61222-124">具体的には、`address` サブ要素の `localIssuer` 属性を空の文字列にしないようにします。</span><span class="sxs-lookup"><span data-stu-id="61222-124">Specifically, the `address` attribute of its `localIssuer` sub-element must not be an empty string.</span></span> <span data-ttu-id="61222-125">構成エディターを使用して既に `address` 属性を変更している場合にその属性を完全に削除したい場合は、構成エディター以外のツールを使用して削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61222-125">If you have modified the `address` attribute using the Configuration Editor and want to remove it completely, you should do so using a tool other than the Editor.</span></span> <span data-ttu-id="61222-126">そうでない場合、属性は空の文字列を含むことになるため、アプリケーションは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="61222-126">Otherwise, the attribute contains an empty string and your application throws an exception.</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="61222-127">構成エディターの使用</span><span class="sxs-lookup"><span data-stu-id="61222-127">Using the Configuration Editor</span></span>  
 <span data-ttu-id="61222-128">サービス構成エディターは、次の Windows SDK のインストール場所にあります。</span><span class="sxs-lookup"><span data-stu-id="61222-128">The Service Configuration Editor can be found at the following Windows SDK installation location:</span></span>  
  
 <span data-ttu-id="61222-129">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="61222-129">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span></span>  
  
 <span data-ttu-id="61222-130">サービス構成エディターを起動すると、後に行うこともできます、**ファイル/オープン**メニューのサービスまたは管理するアセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="61222-130">After you launch the Service Configuration Editor, you can use the **File/Open** menu to browse for the service or assembly you want to manage.</span></span> <span data-ttu-id="61222-131">構成ファイルを直接開き、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] /COM+ サービスを参照し、Web ホスト サービスの構成設定を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="61222-131">You can open configuration files directly, browse for [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] /COM+ services, and open configuration files for Web-hosted services.</span></span>  
  
 <span data-ttu-id="61222-132">サービス構成エディターのユーザー インターフェイスは、次の領域に分割されています。</span><span class="sxs-lookup"><span data-stu-id="61222-132">The Service Configuration Editor's user interface is divided into the following areas:</span></span>  
  
-   <span data-ttu-id="61222-133">ツリー ビュー ペイン: 左側に構成要素をツリー構造で表示します。</span><span class="sxs-lookup"><span data-stu-id="61222-133">Tree View Pane, which displays configuration elements in a tree structure on the left.</span></span> <span data-ttu-id="61222-134">ノードを右クリックと、ツリーで操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="61222-134">You can perform operations in the tree by right-clicking the nodes.</span></span>  
  
-   <span data-ttu-id="61222-135">作業ウィンドウ: ウィンドウの左下に現在の要素の一般的なタスクを表示します。</span><span class="sxs-lookup"><span data-stu-id="61222-135">Task Pane, which displays common tasks for current elements on the lower-left of the window</span></span>  
  
-   <span data-ttu-id="61222-136">詳細ペイン: ツリー ビューで選択された構成ノードの詳細設定を右側に表示します。</span><span class="sxs-lookup"><span data-stu-id="61222-136">Detail Pane, which displays detailed settings of the configuration node selected in the Tree View on the right.</span></span>  
  
### <a name="opening-a-configuration-file"></a><span data-ttu-id="61222-137">構成ファイルを開く</span><span class="sxs-lookup"><span data-stu-id="61222-137">Opening a Configuration File</span></span>  
  
1.  <span data-ttu-id="61222-138">移動する、コマンド ウィンドウを使用してサービス構成エディターを起動、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]インストール場所、および入力`SvcConfigEditor.exe`です。</span><span class="sxs-lookup"><span data-stu-id="61222-138">Start Service Configuration Editor by using a command window to navigate to your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] installation location, and then type `SvcConfigEditor.exe`.</span></span>  
  
2.  <span data-ttu-id="61222-139">**ファイル**メニューの **開く**を管理するファイルの種類をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-139">From the **File** menu, select **Open** and click the type of file you want to manage.</span></span>  
  
3.  <span data-ttu-id="61222-140">**開く** ダイアログ ボックスで、管理し、ダブルクリックする特定のファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="61222-140">In the **Open** dialog box, navigate to the specific file you want to manage and double-click it.</span></span>  
  
 <span data-ttu-id="61222-141">ビューアーは、構成のマージ パスを自動的にたどり、マージされた構成のビューを生成します。</span><span class="sxs-lookup"><span data-stu-id="61222-141">The viewer automatically follows the configuration merge path and creates a view of the merged configuration.</span></span> <span data-ttu-id="61222-142">たとえば、ホストなしのサービスの実際の構成は、Machine.config と App.config の組み合わせです。変更があれば、SvcConfigEditor のアクティブ ファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="61222-142">For example, the actual configuration of a non-hosted service is a combination of Machine.config and App.config. Any changes are applied to the active file in the SvcConfigEditor.</span></span> <span data-ttu-id="61222-143">構成マージ パスの特定ファイルを編集する場合は、直接開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="61222-143">If you want to edit a specific file in the configuration merge path, you should open it directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61222-144">構成ファイルが構成エディター以外で変更されている場合、構成エディターは、現在開いている構成ファイルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="61222-144">Configuration Editor reloads the currently opened configuration file when the latter has been modified outside the Editor.</span></span> <span data-ttu-id="61222-145">再読み込みが発生すると、エディター内で永続的に保存されていないすべての変更が失われます。</span><span class="sxs-lookup"><span data-stu-id="61222-145">When this happens, all the changes that are not durably saved inside the Editor are lost.</span></span> <span data-ttu-id="61222-146">再読み込みが連続して発生する場合は、構成ファイルに定期的にアクセスするサービス (バックグラウンドで実行するウイルス対策ソフトウェアなど) が原因と考えられます。</span><span class="sxs-lookup"><span data-stu-id="61222-146">If reloading happens consistently, the most likely cause is a service that constantly accesses the configuration file, for example, an antivirus software running in the background.</span></span> <span data-ttu-id="61222-147">この問題を解決するには、ファイルが開いているときに、構成エディターがそのファイルにアクセスできる唯一のプロセスであることを保証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61222-147">To resolve this, ensure that Configuration Editor is the only process that can access the file when it is opened.</span></span>  
  
### <a name="services"></a><span data-ttu-id="61222-148">サービス</span><span class="sxs-lookup"><span data-stu-id="61222-148">Services</span></span>  
 <span data-ttu-id="61222-149">**Services**ノードでは、すべての構成ファイルに現在割り当てられているサービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61222-149">The **Services** node displays all of the services currently assigned in the configuration file.</span></span> <span data-ttu-id="61222-150">サブ要素に、ツリー内の各サブ ノードが対応して、<`services`> 構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="61222-150">Each sub-node in the tree corresponds to a sub-element of the <`services`> element in the configuration file.</span></span>  
  
 <span data-ttu-id="61222-151">クリックすると、 **Services**  ノードを表示または実行できますサービスで実行できるタスクの概要ページで、**詳細**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="61222-151">When you click the **Services** node, you can view or perform tasks on the service Summary Page in the **Detail** Pane.</span></span>  
  
#### <a name="creating-a-new-service-configuration"></a><span data-ttu-id="61222-152">新しいサービス構成の作成</span><span class="sxs-lookup"><span data-stu-id="61222-152">Creating a new Service Configuration</span></span>  
 <span data-ttu-id="61222-153">新しいサービス構成は次の方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="61222-153">You can create a new service configuration in the following ways:</span></span>  
  
-   <span data-ttu-id="61222-154">ウィザードを使用して: リンクをクリックして**新しいサービスを作成しています.**</span><span class="sxs-lookup"><span data-stu-id="61222-154">Using a Wizard: Click the link **Create a New Service…**</span></span> <span data-ttu-id="61222-155">作業ウィンドウまたは概要 ページでウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="61222-155">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="61222-156">行えるよう、**ファイル**メニュー]-> [**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="61222-156">You can also do so in the **File** menu -> **Add New Item**.</span></span>  
  
-   <span data-ttu-id="61222-157">手動で作成する: を右クリックすることができます、 **Services**ノードを選択**新しいサービス**です。</span><span class="sxs-lookup"><span data-stu-id="61222-157">Create manually: You can right-click the **Services** node and choose **New Service**.</span></span>  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a><span data-ttu-id="61222-158">新しいサービス エンドポイント構成の作成</span><span class="sxs-lookup"><span data-stu-id="61222-158">Creating a new Service Endpoint Configuration</span></span>  
 <span data-ttu-id="61222-159">新しいサービス エンドポイント構成は次の方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="61222-159">You can create a new service endpoint configuration in the following ways:</span></span>  
  
-   <span data-ttu-id="61222-160">ウィザードによる作成: リンクをクリックして**新しいサービス エンドポイントを作成しています.**</span><span class="sxs-lookup"><span data-stu-id="61222-160">Create using a Wizard: click the link **Create a New Service Endpoint…**</span></span> <span data-ttu-id="61222-161">作業ウィンドウまたは概要 ページでウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="61222-161">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="61222-162">行えるよう、**ファイル**メニュー]-> [**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="61222-162">You can also do so in the **File** menu -> **Add New Item**.</span></span>  
  
-   <span data-ttu-id="61222-163">手動で作成する: を右クリックして、サービスを作成すると、**エンドポイント**ノードを選択"**新しいサービス エンドポイント**"です。</span><span class="sxs-lookup"><span data-stu-id="61222-163">Create manually: Once you created a Service, you can right-click the **Endpoints** node and choose "**New Service Endpoint**".</span></span>  
  
#### <a name="editing-a-service-configuration"></a><span data-ttu-id="61222-164">サービス構成の編集</span><span class="sxs-lookup"><span data-stu-id="61222-164">Editing a Service Configuration</span></span>  
  
1.  <span data-ttu-id="61222-165">クリックして、**サービス**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-165">Click a **Service** node.</span></span>  
  
2.  <span data-ttu-id="61222-166">プロパティ グリッドで設定を編集します。</span><span class="sxs-lookup"><span data-stu-id="61222-166">Edit the settings in the property grids.</span></span>  
  
#### <a name="editing-a-service-endpoint-configuration"></a><span data-ttu-id="61222-167">サービス エンドポイント構成の編集</span><span class="sxs-lookup"><span data-stu-id="61222-167">Editing a Service Endpoint Configuration</span></span>  
  
1.  <span data-ttu-id="61222-168">クリックして、**サービス エンドポイント**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-168">Click a **Service Endpoint** node.</span></span>  
  
2.  <span data-ttu-id="61222-169">プロパティ グリッドで設定を編集します。</span><span class="sxs-lookup"><span data-stu-id="61222-169">Edit the settings in the property grids.</span></span>  
  
#### <a name="adding-a-base-address"></a><span data-ttu-id="61222-170">ベース アドレスの追加</span><span class="sxs-lookup"><span data-stu-id="61222-170">Adding a Base Address</span></span>  
  
1.  <span data-ttu-id="61222-171">クリックして、**ホスト**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-171">Click the **Host** node.</span></span>  
  
2.  <span data-ttu-id="61222-172">クリックして、**新規作成しています.**</span><span class="sxs-lookup"><span data-stu-id="61222-172">Click the **New…**</span></span> <span data-ttu-id="61222-173">ボタンをクリックして、**ベース アドレス**セクションです。</span><span class="sxs-lookup"><span data-stu-id="61222-173">button in the **Base Addresses** section.</span></span>  
  
3.  <span data-ttu-id="61222-174">ダイアログ ボックスにベース アドレスの URI を入力します。</span><span class="sxs-lookup"><span data-stu-id="61222-174">Type in the base address URI in the dialog box.</span></span>  
  
4.  <span data-ttu-id="61222-175">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-175">Click **OK**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61222-176">値を編集することはできません[ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)このツール内です。</span><span class="sxs-lookup"><span data-stu-id="61222-176">You cannot edit the value of [\<baseAddressPrefixFilters>](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) inside this tool.</span></span> <span data-ttu-id="61222-177">この要素を追加または変更するには、テキスト エディターまたは Visual Studio を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61222-177">To add or modify this element, you should use a text editor or Visual Studio.</span></span>  
  
### <a name="client"></a><span data-ttu-id="61222-178">クライアント</span><span class="sxs-lookup"><span data-stu-id="61222-178">Client</span></span>  
 <span data-ttu-id="61222-179">**クライアント**ノードが、構成ファイルのすべてのクライアント エンドポイントを表示します。</span><span class="sxs-lookup"><span data-stu-id="61222-179">The **Client** node displays all of the client endpoints in the configuration file.</span></span> <span data-ttu-id="61222-180">サブ要素に、ツリー内の各サブ ノードが対応して、<`client`> 構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="61222-180">Every sub-node in the tree corresponds to a sub-element of the <`client`> element in the configuration file.</span></span>  
  
 <span data-ttu-id="61222-181">クリックすると、**クライアント**ノードを表示したり、クライアントでタスクを実行する**の概要 ページ**で、**詳細ペイン**です。</span><span class="sxs-lookup"><span data-stu-id="61222-181">When you click the **Client** node, you can view or perform tasks on the client **Summary Page** in the **Detail Pane**.</span></span>  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a><span data-ttu-id="61222-182">新しいクライアント エンドポイント構成の作成</span><span class="sxs-lookup"><span data-stu-id="61222-182">Creating a new Client Endpoint Configuration</span></span>  
 <span data-ttu-id="61222-183">新しいクライアント エンドポイント構成は次の方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="61222-183">You can create a new client endpoint configuration in the following ways:</span></span>  
  
-   <span data-ttu-id="61222-184">ウィザードによる作成: リンクをクリックして**新しいクライアントを作成しています.**</span><span class="sxs-lookup"><span data-stu-id="61222-184">Create by Wizard: Click the link **Create a New Client…**</span></span> <span data-ttu-id="61222-185">**作業ウィンドウ**、ウィンドウの左下にまたは**の概要 ページ**ウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="61222-185">on the **Task Pane** on the lower-left of the window, or **Summary Page** to launch the wizard.</span></span> <span data-ttu-id="61222-186">行えるよう、**ファイル**メニュー]-> [**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="61222-186">You can also do so in the **File** menu -> **Add New Item**.</span></span> <span data-ttu-id="61222-187">クライアント構成を生成するサービス構成の場所の指定を求めるプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61222-187">The wizard prompts you to point to the location of the service configuration, from which the client configuration is generated.</span></span> <span data-ttu-id="61222-188">接続するサービス エンドポイントを選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="61222-188">You can then choose the service endpoint to connect to.</span></span>  
  
-   <span data-ttu-id="61222-189">手動で作成する: を右クリックし、**エンドポイント**ノードの下**クライアント**を選択し、**新規クライアント エンドポイント**です。</span><span class="sxs-lookup"><span data-stu-id="61222-189">Create manually: Right-click the **Endpoints** node under **Client**, and choose **New Client Endpoint**.</span></span>  
  
#### <a name="editing-a-client-endpoint-configuration"></a><span data-ttu-id="61222-190">クライアント エンドポイント構成の編集</span><span class="sxs-lookup"><span data-stu-id="61222-190">Editing a Client Endpoint Configuration</span></span>  
  
1.  <span data-ttu-id="61222-191">クリックして、**クライアント エンドポイント**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-191">Click a **Client Endpoint** node.</span></span>  
  
2.  <span data-ttu-id="61222-192">プロパティ グリッドで設定を編集します。</span><span class="sxs-lookup"><span data-stu-id="61222-192">Edit the settings in the property grids.</span></span>  
  
### <a name="standard-endpoint"></a><span data-ttu-id="61222-193">標準エンドポイント</span><span class="sxs-lookup"><span data-stu-id="61222-193">Standard Endpoint</span></span>  
 <span data-ttu-id="61222-194">標準エンドポイントは、既定値に設定されたアドレス、コントラクト、およびバインディングの 1 つ以上の特性を持つ特殊なエンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="61222-194">Standard endpoints are specialized endpoints that have one or more aspects of the address, contract and binding set to default values.</span></span>  
  
 <span data-ttu-id="61222-195">このような構成設定が格納されている、**標準エンドポイント**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-195">Such configuration settings are stored in the **Standard Endpoint** node.</span></span> <span data-ttu-id="61222-196">**標準エンドポイント**ノードが、構成ファイルのすべての標準エンドポイントの設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="61222-196">The **Standard Endpoint** node displays all of the standard endpoint settings in the configuration file.</span></span> <span data-ttu-id="61222-197">内のサブ要素に対応して、ツリー内の各サブ ノード、`<standardEndpoints>`構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="61222-197">Every sub-node in the tree corresponds to a sub-element in the `<standardEndpoints>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="61222-198">クリックすると、**標準エンドポイント**ノードを表示したり、標準エンドポイントでタスクを実行する**の概要 ページ**で、**詳細ペイン**です。</span><span class="sxs-lookup"><span data-stu-id="61222-198">When you click the **Standard Endpoint** node, you can view or perform tasks on the standard endpoint **Summary Page** in the **Detail Pane**.</span></span>  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a><span data-ttu-id="61222-199">新しい標準エンドポイント構成の作成</span><span class="sxs-lookup"><span data-stu-id="61222-199">Creating a New Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="61222-200">新しい標準エンドポイント構成は、次の方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="61222-200">You can create a new standard endpoint configuration in the following ways:</span></span>  
  
-   <span data-ttu-id="61222-201">右クリックし、**標準エンドポイント**ノード**新しい標準エンドポイント構成しています.**</span><span class="sxs-lookup"><span data-stu-id="61222-201">Right-click the **Standard Endpoint** node and select **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="61222-202">ダイアログ ボックスで、バインドの種類を選択し、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="61222-202">Select the binding type in the dialog box and click **OK**.</span></span>  
  
-   <span data-ttu-id="61222-203">選択、**標準エンドポイント**ノードとクリック**新しい標準エンドポイント構成しています.**</span><span class="sxs-lookup"><span data-stu-id="61222-203">Select the **Standard Endpoint** node and click **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="61222-204">**作業ウィンドウ**ウィンドウの左下にします。</span><span class="sxs-lookup"><span data-stu-id="61222-204">in the **Task Pane** on the lower-left of the window.</span></span>  
  
 <span data-ttu-id="61222-205">**新しい標準エンドポイントを作成する** ダイアログ ボックスが表示され、登録されているすべての標準エンドポイントの種類を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="61222-205">The **Creating a New Standard Endpoint** dialog box displays and lists all registered standard endpoint types.</span></span>  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a><span data-ttu-id="61222-206">標準エンドポイント構成の表示および編集</span><span class="sxs-lookup"><span data-stu-id="61222-206">Viewing and Editing a Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="61222-207">表示および編集する標準エンドポイント構成は、次の方法で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="61222-207">You can open a standard endpoint configuration for viewing and editing in the following ways:</span></span>  
  
-   <span data-ttu-id="61222-208">クリックして展開し、**標準エンドポイント**ノードそれぞれのエンドポイント サブノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-208">Click to expand the **Standard Endpoint** node and click the respective endpoint sub-node.</span></span>  
  
-   <span data-ttu-id="61222-209">クリックして、**標準エンドポイント**ノードの詳細ペインには、それぞれのエンドポイントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-209">Click the **Standard Endpoint** node and click the respective endpoint on the Detail pane.</span></span>  
  
 <span data-ttu-id="61222-210">エンドポイントの属性を右ペインに表示して、編集できます。</span><span class="sxs-lookup"><span data-stu-id="61222-210">Attributes for the endpoint are shown in the right pane for editing.</span></span>  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a><span data-ttu-id="61222-211">標準エンドポイント構成の削除</span><span class="sxs-lookup"><span data-stu-id="61222-211">Deleting a Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="61222-212">標準エンドポイント構成は次の方法で削除できます。</span><span class="sxs-lookup"><span data-stu-id="61222-212">You can delete a standard endpoint configuration in the following ways:</span></span>  
  
-   <span data-ttu-id="61222-213">クリックして展開し、**標準エンドポイント**ノードとそれぞれのエンドポイント サブノードを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-213">Click to expand the **Standard Endpoint** node and right-click the respective endpoint sub-node.</span></span> <span data-ttu-id="61222-214">コンテキスト コマンドを使用して**標準エンドポイント構成の削除**エンドポイントを削除します。</span><span class="sxs-lookup"><span data-stu-id="61222-214">Use the context command **Delete Standard Endpoint Configuration** to delete the endpoint.</span></span>  
  
-   <span data-ttu-id="61222-215">クリックして、**標準エンドポイント**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-215">Click the **Standard Endpoint** node.</span></span> <span data-ttu-id="61222-216">**タスク** ウィンドウで、をクリックして**標準エンドポイント構成の削除**です。</span><span class="sxs-lookup"><span data-stu-id="61222-216">In the **Task** pane, click **Delete Standard Endpoint Configuration**.</span></span>  
  
 <span data-ttu-id="61222-217">標準エンドポイントが使用中の場合は、削除しようとしたときに警告メッセージが表示されます。警告は**「標準エンドポイントは使用されています。削除する場合は、構成の他の部分 (サービス エンドポイントやクライアント エンドポイントなど) からもすべての参照を必ず削除してください。そうしないと、構成が無効になり、次回から開けなくなります。よろしい標準エンドポイントを削除しますか?"**</span><span class="sxs-lookup"><span data-stu-id="61222-217">If the standard endpoint is in used, a warning message is displayed when you attempt to delete it: **The standard endpoint is in use. If you delete it now, please be sure to delete all of its references in other parts of the configuration (for example, in the service endpoint or client endpoint). Otherwise, the configuration will be invalid and cannot be opened next time. Are you sure you want to delete the standard endpoint?"**</span></span>  
  
### <a name="binding"></a><span data-ttu-id="61222-218">バインド</span><span class="sxs-lookup"><span data-stu-id="61222-218">Binding</span></span>  
 <span data-ttu-id="61222-219">バインド構成は、エンドポイントでバインディングを構成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="61222-219">Binding configurations are used to configure bindings on endpoints.</span></span> <span data-ttu-id="61222-220">このような構成設定が格納されている、**バインド**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-220">Such configuration settings are stored in the **Binding** node.</span></span> <span data-ttu-id="61222-221">エンドポイントはバインド構成を名前で参照し、複数のエンドポイントは単一のバインド構成を参照できます。</span><span class="sxs-lookup"><span data-stu-id="61222-221">Endpoints reference binding configurations by name and multiple endpoints can reference a single binding configuration.</span></span>  
  
 <span data-ttu-id="61222-222">**バインド**ノードが、構成ファイルのすべてのバインディング設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="61222-222">The **Bindings** node displays all of the binding settings in the configuration file.</span></span> <span data-ttu-id="61222-223">内のサブ要素に、ツリー内の各サブ ノードが対応して、<`bindings`> 構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="61222-223">Every sub-node in the tree corresponds to a sub-element in the <`bindings`> element in the configuration file.</span></span>  
  
 <span data-ttu-id="61222-224">クリックすると、**バインド**ノードを表示したり、バインドでタスクを実行する**の概要 ページ**で、**詳細ペイン**です。</span><span class="sxs-lookup"><span data-stu-id="61222-224">When you click the **Bindings** node, you can view or perform tasks on the binding **Summary Page** in the **Detail Pane**.</span></span>  
  
#### <a name="creating-a-new-binding-configuration"></a><span data-ttu-id="61222-225">新しいバインド構成の作成</span><span class="sxs-lookup"><span data-stu-id="61222-225">Creating a New Binding Configuration</span></span>  
 <span data-ttu-id="61222-226">新しいバインド構成は次の方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="61222-226">You can create a new binding configuration in the following ways.</span></span>  
  
-   <span data-ttu-id="61222-227">右クリックし、**バインド**ノード**新しいバインド構成**しています.</span><span class="sxs-lookup"><span data-stu-id="61222-227">Right-click the **Bindings** node and select **New Binding Configuration**…</span></span> <span data-ttu-id="61222-228">ダイアログ ボックスで、バインドの種類を選択し、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="61222-228">Select the binding type in the dialog box and click **OK**.</span></span>  
  
-   <span data-ttu-id="61222-229">選択、**バインド**ノードとクリック**新しいバインド構成**しています.</span><span class="sxs-lookup"><span data-stu-id="61222-229">Select the **Bindings** node and click **New Binding Configuration**…</span></span> <span data-ttu-id="61222-230">**作業ウィンドウ**ウィンドウの左下にします。</span><span class="sxs-lookup"><span data-stu-id="61222-230">in the **Task Pane** on the lower-left of the window.</span></span>  
  
-   <span data-ttu-id="61222-231">[サービスまたはクライアントの概要ページ**作成] をクリックして**で、**バインド構成**対応するエンドポイントのバインディング構成を作成するフィールドです。</span><span class="sxs-lookup"><span data-stu-id="61222-231">In the service or client summary page, click **Click to Create** in the **Binding Configuration** field to create a binding configuration for the corresponding endpoint.</span></span>  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a><span data-ttu-id="61222-232">カスタム バインディングへのバインディング要素拡張の追加</span><span class="sxs-lookup"><span data-stu-id="61222-232">Adding Binding Element Extensions to a Custom Binding</span></span>  
  
1.  <span data-ttu-id="61222-233">拡張要素を追加するバインディングを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-233">Select the binding you want to add an extension element to.</span></span>  
  
2.  <span data-ttu-id="61222-234">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-234">Click **Add**.</span></span>  
  
3.  <span data-ttu-id="61222-235">使用できる拡張一覧から、追加するバインディング要素拡張を選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-235">From the list of available extensions, select the binding element extension you want to add.</span></span> <span data-ttu-id="61222-236">複数の項目を選択するには、Ctrl キーを同時に押します。</span><span class="sxs-lookup"><span data-stu-id="61222-236">To select multiple items, press the CTRL key simultaneously.</span></span>  
  
4.  <span data-ttu-id="61222-237">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-237">Click **Add**.</span></span>  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a><span data-ttu-id="61222-238">カスタム バインドの拡張位置の調整</span><span class="sxs-lookup"><span data-stu-id="61222-238">Adjusting the Extension Position in a Custom Binding</span></span>  
 <span data-ttu-id="61222-239">カスタム バインディングは、スタックを形成するバインディング要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="61222-239">A custom binding is a collection of binding elements that form a stack.</span></span> <span data-ttu-id="61222-240">スタックの各バインド要素には、独自の構成設定があります。</span><span class="sxs-lookup"><span data-stu-id="61222-240">Each binding element on the stack has its own configuration settings.</span></span> <span data-ttu-id="61222-241">カスタム バインディング内のバインディング要素拡張の順序は、スタック内のそれらの位置を示します。</span><span class="sxs-lookup"><span data-stu-id="61222-241">The order of the binding element extensions in a custom binding indicates their positions in the stack.</span></span> <span data-ttu-id="61222-242">スタック最上位の要素が最初に適用されます。</span><span class="sxs-lookup"><span data-stu-id="61222-242">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="61222-243">順序を変更するには</span><span class="sxs-lookup"><span data-stu-id="61222-243">To change the ordering:</span></span>  
  
1.  <span data-ttu-id="61222-244">カスタム バインド ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-244">Select the custom binding node.</span></span>  
  
2.  <span data-ttu-id="61222-245">1 つのバインディング拡張要素を選択して、 **Binding Element Extension Position**セクションです。</span><span class="sxs-lookup"><span data-stu-id="61222-245">Select one binding extension element in the **Binding Element Extension Position** section.</span></span>  
  
3.  <span data-ttu-id="61222-246">使用して、**を**または**ダウン**選択した要素の位置を変更するリストの左側にあるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-246">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a><span data-ttu-id="61222-247">カスタム バインディングのバインディング要素拡張の構成の編集</span><span class="sxs-lookup"><span data-stu-id="61222-247">Editing the Configuration of Binding Element Extensions in a Custom Binding</span></span>  
  
1.  <span data-ttu-id="61222-248">ツリー内のバインディング ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-248">Select the binding node in the tree.</span></span>  
  
2.  <span data-ttu-id="61222-249">編集する要素を含むカスタム バインディングを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-249">Select the custom binding that contains the element you want to edit.</span></span>  
  
3.  <span data-ttu-id="61222-250">編集するバインディング要素拡張を選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-250">Select the binding element extension you want to edit.</span></span> <span data-ttu-id="61222-251">要素の設定が、編集場所の右ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="61222-251">The settings of the element appear in the right pane, where they can be edited.</span></span>  
  
### <a name="diagnostics"></a><span data-ttu-id="61222-252">診断</span><span class="sxs-lookup"><span data-stu-id="61222-252">Diagnostics</span></span>  
 <span data-ttu-id="61222-253">**診断**ノードが、構成ファイルのすべての診断設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="61222-253">The **Diagnostics** node displays all of the diagnostic settings in the configuration file.</span></span> <span data-ttu-id="61222-254">診断を使用すると、パフォーマンス カウンターのオンまたはオフ、Windows Management Instrumentation (WMI) の有効または無効、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] トレースの構成、および [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] メッセージ ログの構成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="61222-254">It enables you to turn performance counters on or off, enable or disable Windows Management Instrumentation (WMI), configure [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] tracing, and configure [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] message logging.</span></span> <span data-ttu-id="61222-255">設定、**診断**にノードが対応して、<`system.diagnostics`> セクションと`<diagnostics>`」の「`<system.serviceModel>`構成ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="61222-255">The settings in the **Diagnostics** node correspond to the <`system.diagnostics`> section, and `<diagnostics>` section in `<system.serviceModel>` in the configuration file.</span></span>  
  
 <span data-ttu-id="61222-256">クリックすると、**診断**ノードを表示したり、診断でタスクを実行する**の概要 ページ**で、**詳細ペイン**です。</span><span class="sxs-lookup"><span data-stu-id="61222-256">When you click the **Diagnostics** node, you can view or perform tasks on the diagnostics **Summary Page** in the **Detail Pane**.</span></span>  
  
#### <a name="configuring-performance-counters-and-wmi"></a><span data-ttu-id="61222-257">パフォーマンス カウンターと WMI の構成</span><span class="sxs-lookup"><span data-stu-id="61222-257">Configuring performance counters and WMI</span></span>  
  
1.  <span data-ttu-id="61222-258">クリックして、**診断**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-258">Click the **Diagnostics** node.</span></span>  
  
2.  <span data-ttu-id="61222-259">をクリックして**パフォーマンス カウンターを切り替える**です。</span><span class="sxs-lookup"><span data-stu-id="61222-259">Click **Toggle Performance Counters**.</span></span> <span data-ttu-id="61222-260">パフォーマンス カウンターには、Off (既定)、ServiceOnly、All の 3 つの状態があります。</span><span class="sxs-lookup"><span data-stu-id="61222-260">The performance counter has three states: Off (default), ServiceOnly, and All.</span></span> <span data-ttu-id="61222-261">リンクをクリックすると、これらの 3 つの状態の間で設定が切り替わります。</span><span class="sxs-lookup"><span data-stu-id="61222-261">Clicking the link toggles the setting among these three states.</span></span>  
  
#### <a name="configuring-wmi-provider"></a><span data-ttu-id="61222-262">WMI プロバイダーの構成</span><span class="sxs-lookup"><span data-stu-id="61222-262">Configuring WMI Provider</span></span>  
  
1.  <span data-ttu-id="61222-263">クリックして、**診断**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-263">Click the **Diagnostics** node.</span></span>  
  
2.  <span data-ttu-id="61222-264">WMI プロバイダーを有効にするをクリックして、 **WMI プロバイダーを有効にする**リンクします。</span><span class="sxs-lookup"><span data-stu-id="61222-264">To enable WMI provider, click the **Enable WMI Provider** link.</span></span>  
  
#### <a name="enabling-wcf-tracing"></a><span data-ttu-id="61222-265">WCF トレースの有効化</span><span class="sxs-lookup"><span data-stu-id="61222-265">Enabling WCF Tracing</span></span>  
 <span data-ttu-id="61222-266">標準プロパティを持つ [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] トレース ファイルの作成またはカスタム トレース ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="61222-266">You can create a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] trace file with standard properties or set up a custom trace file.</span></span>  
  
1.  <span data-ttu-id="61222-267">クリックして、**診断**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-267">Click the **Diagnostics** node.</span></span>  
  
2.  <span data-ttu-id="61222-268">をクリックして**トレースを有効にする**です。</span><span class="sxs-lookup"><span data-stu-id="61222-268">Click **Enable Tracing**.</span></span>  
  
3.  <span data-ttu-id="61222-269">クリックして、**トレース レベル**トレース レベルを調整するリンクです。</span><span class="sxs-lookup"><span data-stu-id="61222-269">Click the **Trace Level** link to adjust the trace level.</span></span> <span data-ttu-id="61222-270">トレース レベルは、Off、Critical、Error、Warning、Information、Verbose の 6 つあります。</span><span class="sxs-lookup"><span data-stu-id="61222-270">There are six trace levels: Off, Critical, Error, Warning, Information, and Verbose.</span></span> <span data-ttu-id="61222-271">**アクティビティ トレース**と**アクティビティの伝達**オプションを使用する、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]アクティビティ トレース機能。</span><span class="sxs-lookup"><span data-stu-id="61222-271">The **Activity Tracing** and **Propagate Activity** option enable you to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] activity tracing feature.</span></span>  
  
4.  <span data-ttu-id="61222-272">トレース ファイルとオプションを指定するには、トレース リスナー名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-272">Click the trace listener name to specify the trace file and options.</span></span>  
  
#### <a name="enabling-wcf-logging"></a><span data-ttu-id="61222-273">WCF ログの有効化</span><span class="sxs-lookup"><span data-stu-id="61222-273">Enabling WCF Logging</span></span>  
 <span data-ttu-id="61222-274">標準プロパティを持つ [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] トレース ファイルの作成またはカスタム トレース ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="61222-274">You can create a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] trace file with standard properties or set up a custom trace file.</span></span>  
  
1.  <span data-ttu-id="61222-275">クリックして、**診断**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-275">Click the **Diagnostics** node.</span></span>  
  
2.  <span data-ttu-id="61222-276">をクリックして**メッセージのログ記録を有効にする**です。</span><span class="sxs-lookup"><span data-stu-id="61222-276">Click **Enable Message Logging**.</span></span>  
  
3.  <span data-ttu-id="61222-277">クリックして、**ログ レベル**ログ レベルを調整するリンクです。</span><span class="sxs-lookup"><span data-stu-id="61222-277">Click the **Log Level** link to adjust the log level.</span></span> <span data-ttu-id="61222-278">ログ レベルには、無効な形式、サービス、トランスポートの 3 つがあります。</span><span class="sxs-lookup"><span data-stu-id="61222-278">There are three log levels: Malformed, Service, and Transport.</span></span>  
  
4.  <span data-ttu-id="61222-279">ログ ファイルとオプションを指定するには、リスナー名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-279">Click the listener name to specify the log file and options.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61222-280">トレースおよびメッセージ ログを有効にして、アプリケーションが閉じられたときに自動的にフラッシュする場合、**自動フラッシュ**オプション。</span><span class="sxs-lookup"><span data-stu-id="61222-280">If you want the trace and message logs to be flushed automatically when your application is closed, enable the **Auto Flush** option.</span></span>  
  
 <span data-ttu-id="61222-281">**診断****概要ページ**診断の構成で最も一般的なタスクを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="61222-281">The **Diagnostics** **Summary Page** enables you to accomplish the most common tasks in configuring diagnostics.</span></span> <span data-ttu-id="61222-282">ただし、リスナーとソースの設定を手動で編集する場合を展開してください、**診断**ノード設定を編集**メッセージ ログ**、**リスナー**と**ソース**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-282">However, if you want to manually edit the Listeners and Sources settings, you must expand the **Diagnostics** node and edit settings in **Message Logging**, **Listeners** and **Sources** node.</span></span>  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a><span data-ttu-id="61222-283">WCF カスタム トレースまたはメッセージ ログの有効化</span><span class="sxs-lookup"><span data-stu-id="61222-283">Enabling WCF Custom Tracing or Message Logging</span></span>  
  
1.  <span data-ttu-id="61222-284">クリックして、**診断**ノード、それを展開します。</span><span class="sxs-lookup"><span data-stu-id="61222-284">Click the **Diagnostics** node, and expand it.</span></span>  
  
2.  <span data-ttu-id="61222-285">右クリックし、**リスナー**ノード**新しいリスナー**です。</span><span class="sxs-lookup"><span data-stu-id="61222-285">Right-click the **Listeners** node and select **New Listener**.</span></span>  
  
3.  <span data-ttu-id="61222-286">トレース ファイルの名前を入力、 **InitData**フィールドです。</span><span class="sxs-lookup"><span data-stu-id="61222-286">Type in the trace file name in the **InitData** field.</span></span> <span data-ttu-id="61222-287">パスを参照する [...] ボタンをクリックできます。</span><span class="sxs-lookup"><span data-stu-id="61222-287">You can click the "…" button to browse to a path.</span></span>  
  
4.  <span data-ttu-id="61222-288">クリックすると、 **TypeName**行には、[...] ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61222-288">Clicking the **TypeName** line displays a "…" button.</span></span> <span data-ttu-id="61222-289">このボタンをクリックして、**トレース リスナー型ブラウザー**を既にインストールされている事前構成済みのトレース リスナーを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="61222-289">Click this button to open the **Trace Listener Type Browser**, which you can use to find pre-configured trace listeners that are already installed.</span></span>  
  
5.  <span data-ttu-id="61222-290">注、**ソース**セクションです。</span><span class="sxs-lookup"><span data-stu-id="61222-290">Note the **Source** section.</span></span> <span data-ttu-id="61222-291">をクリックして**追加**をドロップダウン メニューとダイアログ ボックスが開きこのセクションで、使用できるトレース ソースを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="61222-291">Click **Add** in this section to open a dialog box with a drop-down menu, which lists available tracing sources.</span></span> <span data-ttu-id="61222-292">トレース ソースを選択し、クリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="61222-292">Select a tracing source and click **OK**.</span></span>  
  
6.  <span data-ttu-id="61222-293">メッセージ ログの設定を編集するには、クリックして、**メッセージ ログ**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-293">To edit Message Logging settings, click the **Message Logging** node.</span></span> <span data-ttu-id="61222-294">プロパティ グリッドで設定を編集できます。</span><span class="sxs-lookup"><span data-stu-id="61222-294">You can edit the settings in the property grid.</span></span>  
  
### <a name="advanced"></a><span data-ttu-id="61222-295">詳細設定</span><span class="sxs-lookup"><span data-stu-id="61222-295">Advanced</span></span>  
  
#### <a name="behaviors"></a><span data-ttu-id="61222-296">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="61222-296">Behaviors</span></span>  
 <span data-ttu-id="61222-297">**動作**ノードが、構成ファイルで現在定義されている動作を表示します。</span><span class="sxs-lookup"><span data-stu-id="61222-297">The **Behaviors** node displays the behaviors that are currently defined in the configuration file.</span></span>  
  
 <span data-ttu-id="61222-298">動作構成は、エンドポイントとサービスの動作を構成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="61222-298">Behavior configurations are used to configure behaviors of endpoints and services.</span></span> <span data-ttu-id="61222-299">このような構成設定が格納されている、**詳細**ノードの下**サービスの動作**と**エンドポイント動作**です。</span><span class="sxs-lookup"><span data-stu-id="61222-299">Such configuration settings are stored in the **Advanced** node under **Service Behaviors** and **Endpoint Behaviors**.</span></span> <span data-ttu-id="61222-300">サービス動作はサービスによって使用され、エンドポイント動作はエンドポイントによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="61222-300">Service behaviors are used by services; whereas endpoint behaviors by endpoints.</span></span>  
  
 <span data-ttu-id="61222-301">動作は、スタックを形成する拡張要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="61222-301">Behaviors are a collection of extension elements that for a stack.</span></span> <span data-ttu-id="61222-302">スタック最上位の要素が最初に適用されます。</span><span class="sxs-lookup"><span data-stu-id="61222-302">The element at the top of the stack is applied first.</span></span> <span data-ttu-id="61222-303">各拡張要素は独自の構成を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="61222-303">Each extension element can have its own configuration.</span></span>  
  
##### <a name="creating-a-new-behavior-configuration"></a><span data-ttu-id="61222-304">新しい動作構成の作成</span><span class="sxs-lookup"><span data-stu-id="61222-304">Creating a new Behavior Configuration</span></span>  
 <span data-ttu-id="61222-305">新しい動作構成は次の 2 つの方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="61222-305">You can create a new behavior configuration in two ways.</span></span>  
  
-   <span data-ttu-id="61222-306">動作ノードの 1 つを右クリックし ["**新しい動作構成]**</span><span class="sxs-lookup"><span data-stu-id="61222-306">Right-click one of the behavior nodes and select "**New Behavior Configuration…**</span></span>  
  
-   <span data-ttu-id="61222-307">動作ノードのいずれかを選択し、クリックして、**新しい動作構成**しています.</span><span class="sxs-lookup"><span data-stu-id="61222-307">Select one of the behavior nodes and click the **New Behavior Configuration**…</span></span> <span data-ttu-id="61222-308">**作業ウィンドウ**ウィンドウの左下にします。</span><span class="sxs-lookup"><span data-stu-id="61222-308">in the **Task Pane** on the lower-left of the window.</span></span>  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a><span data-ttu-id="61222-309">動作への動作要素拡張の追加</span><span class="sxs-lookup"><span data-stu-id="61222-309">Adding Behavior Element Extensions to a Behavior</span></span>  
  
1.  <span data-ttu-id="61222-310">動作ノードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-310">Select one of the behavior nodes.</span></span>  
  
2.  <span data-ttu-id="61222-311">編集する動作を選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-311">Select the behavior you want edit.</span></span>  
  
3.  <span data-ttu-id="61222-312">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-312">Click **Add**.</span></span>  
  
4.  <span data-ttu-id="61222-313">使用できる拡張一覧から、追加する動作要素拡張を選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-313">From the list of available extensions, select the behavior element extension you want to add.</span></span>  
  
5.  <span data-ttu-id="61222-314">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-314">Click **Add**.</span></span>  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a><span data-ttu-id="61222-315">動作の拡張位置の調整</span><span class="sxs-lookup"><span data-stu-id="61222-315">Adjusting the Extension Position in a Behavior</span></span>  
 <span data-ttu-id="61222-316">動作は、スタックを形成する要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="61222-316">Behaviors are collections of elements that form a stack.</span></span> <span data-ttu-id="61222-317">スタックの各要素には、独自の構成があります。</span><span class="sxs-lookup"><span data-stu-id="61222-317">Each element on the stack has its own configuration.</span></span> <span data-ttu-id="61222-318">動作内の動作要素拡張の順序は、スタック内のそれらの位置を示します。</span><span class="sxs-lookup"><span data-stu-id="61222-318">The order of the behavior element extensions in a behavior indicates their positions in the stack.</span></span> <span data-ttu-id="61222-319">スタック最上位の要素が最初に適用されます。</span><span class="sxs-lookup"><span data-stu-id="61222-319">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="61222-320">順序を変更するには</span><span class="sxs-lookup"><span data-stu-id="61222-320">To change the ordering:</span></span>  
  
1.  <span data-ttu-id="61222-321">動作ノードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-321">Select one of the behavior nodes.</span></span>  
  
2.  <span data-ttu-id="61222-322">編集する動作を選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-322">Select the behavior you want edit.</span></span>  
  
3.  <span data-ttu-id="61222-323">動作拡張要素を選択して、**動作要素拡張の位置**セクションです。</span><span class="sxs-lookup"><span data-stu-id="61222-323">Select a behavior extension element in the **Behavior Element Extension Position** section.</span></span>  
  
4.  <span data-ttu-id="61222-324">使用して、**を**または**ダウン**選択した要素の位置を変更するリストの左側にあるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-324">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a><span data-ttu-id="61222-325">動作要素拡張の構成の編集</span><span class="sxs-lookup"><span data-stu-id="61222-325">Editing the Configuration of Behavior Element Extensions</span></span>  
  
1.  <span data-ttu-id="61222-326">ツリー内の動作ノードの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-326">Select one of the behavior nodes in the tree.</span></span>  
  
2.  <span data-ttu-id="61222-327">編集する要素を含む動作を選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-327">Select the behavior that contains the element you want to edit.</span></span>  
  
3.  <span data-ttu-id="61222-328">編集する動作要素拡張を選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-328">Select the behavior element extension you want to edit.</span></span> <span data-ttu-id="61222-329">要素の設定が、編集場所の右ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="61222-329">The settings of the element appear in the right pane where they can be edited.</span></span>  
  
#### <a name="protocolmapping"></a><span data-ttu-id="61222-330">ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="61222-330">ProtocolMapping</span></span>  
 <span data-ttu-id="61222-331">このセクションでは、プロトコル アドレス スキームと可能なバインドの間に定義されているマッピングを介して、http、tcp、MSMQ、net.pipe などのさまざまなプロトコルに対する既定のバインドの種類を設定できます。</span><span class="sxs-lookup"><span data-stu-id="61222-331">This section allows you to set default binding types for different protocols such as http, tcp, MSMQ or net.pipe through defined mapping between protocol address schemes and the possible bindings.</span></span> <span data-ttu-id="61222-332">他のプロトコルへの新しいマッピングを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="61222-332">You can also add new mappings to other protocols.</span></span>  
  
#### <a name="extensions"></a><span data-ttu-id="61222-333">拡張機能</span><span class="sxs-lookup"><span data-stu-id="61222-333">Extensions</span></span>  
 <span data-ttu-id="61222-334">新しいバインディング拡張、バインディング要素拡張、標準エンドポイント拡張、および動作拡張を登録して、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 構成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="61222-334">New binding extensions, binding element extensions, standard endpoint extensions and behavior extensions can be registered for use in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration.</span></span> <span data-ttu-id="61222-335">拡張は、名前と種類のペアです。</span><span class="sxs-lookup"><span data-stu-id="61222-335">Extensions are name/type pairs.</span></span> <span data-ttu-id="61222-336">名前は構成の拡張の名前を定義し、種類は拡張を実装します。</span><span class="sxs-lookup"><span data-stu-id="61222-336">The name defines the name of the extension in configuration, whereas the type implements the extension.</span></span> <span data-ttu-id="61222-337">拡張には次の 4 種類があります。</span><span class="sxs-lookup"><span data-stu-id="61222-337">There are four types of extensions:</span></span>  
  
-   <span data-ttu-id="61222-338">バインディング拡張は、バインディングの種類全体を定義します。</span><span class="sxs-lookup"><span data-stu-id="61222-338">Binding extensions define an entire binding type.</span></span> <span data-ttu-id="61222-339">例 : `basicHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="61222-339">Example: `basicHttpBinding`.</span></span>  
  
-   <span data-ttu-id="61222-340">バインディング要素拡張は、バインディングの要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="61222-340">Binding element extensions define an element of a binding.</span></span> <span data-ttu-id="61222-341">例 : `textMessageEncoding`。</span><span class="sxs-lookup"><span data-stu-id="61222-341">Example: `textMessageEncoding`.</span></span>  
  
-   <span data-ttu-id="61222-342">標準エンドポイント拡張は、標準エンドポイント全体を定義します。</span><span class="sxs-lookup"><span data-stu-id="61222-342">Standard endpoint extensions define an entire standard endpoint.</span></span> <span data-ttu-id="61222-343">例 : `discoveryEndpoint`。</span><span class="sxs-lookup"><span data-stu-id="61222-343">Example: `discoveryEndpoint`.</span></span>  
  
-   <span data-ttu-id="61222-344">動作要素拡張は、動作の要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="61222-344">Behavior element extensions define an element of a behavior.</span></span> <span data-ttu-id="61222-345">例 : `clientVia`。</span><span class="sxs-lookup"><span data-stu-id="61222-345">Example: `clientVia`.</span></span>  
  
 <span data-ttu-id="61222-346">構成に登録されている拡張は、同じ種類の他のすべての [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] コンポーネントと同じように使用できます。</span><span class="sxs-lookup"><span data-stu-id="61222-346">Extensions that have been registered in configuration can be used like any other [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] component of the same type.</span></span>  
  
##### <a name="adding-a-new-extension"></a><span data-ttu-id="61222-347">新しい機能の追加</span><span class="sxs-lookup"><span data-stu-id="61222-347">Adding a new extension</span></span>  
 <span data-ttu-id="61222-348">詳細設定ノード内の拡張ノードの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-348">Select one of the extension nodes in the advanced nodes:</span></span>  
  
1.  <span data-ttu-id="61222-349">**[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-349">Click **New**.</span></span>  
  
2.  <span data-ttu-id="61222-350">名前と種類を入力します。</span><span class="sxs-lookup"><span data-stu-id="61222-350">Enter a name and type.</span></span>  
  
3.  <span data-ttu-id="61222-351">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61222-351">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="61222-352">拡張は、エディターの適切な場所に表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="61222-352">The extension now appears in the appropriate place in the Editor.</span></span> <span data-ttu-id="61222-353">たとえば、動作要素拡張を追加すると、使用できる拡張一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="61222-353">For example, if you add a behavior element extension, it appears in the list of available extensions.</span></span>  
  
#### <a name="hosting-environment"></a><span data-ttu-id="61222-354">ホスト環境</span><span class="sxs-lookup"><span data-stu-id="61222-354">Hosting Environment</span></span>  
 <span data-ttu-id="61222-355">ここでは、環境をホストするサービスのインスタンス化設定を定義できます。</span><span class="sxs-lookup"><span data-stu-id="61222-355">This section allows you to define instantiation settings for the service hosting environment.</span></span>  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a><span data-ttu-id="61222-356">ウィザードによる構成ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="61222-356">Creating a Configuration File Using the Wizard</span></span>  
 <span data-ttu-id="61222-357">新しい構成ファイルを作成する 1 つの方法として、新しいサービス要素ウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="61222-357">One way to create a new configuration file is to use the New Service Element Wizard.</span></span> <span data-ttu-id="61222-358">ウィザードは、インストールされたサービスの種類および [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] と互換性のある、COM+、Web ホストの仮想ディレクトリなどの他の要素をコンピューター上で見つけると、それらを読み込んで、構成の作成を効率よく行います。</span><span class="sxs-lookup"><span data-stu-id="61222-358">The wizard finds the installed service types and other elements compatible with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] on the computer, including COM+ and Web-hosted virtual directories, and loads them to make creating the configuration much more streamlined.</span></span>  
  
#### <a name="creating-a-configuration-file"></a><span data-ttu-id="61222-359">構成ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="61222-359">Creating a Configuration File</span></span>  
  
1.  <span data-ttu-id="61222-360">移動する、コマンド ウィンドウを使用してサービス構成エディターを起動、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]インストール場所、および入力`SvcConfigEditor.exe`です。</span><span class="sxs-lookup"><span data-stu-id="61222-360">Start Service Configuration Editor by using a command window to navigate to your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] installation location, and then type `SvcConfigEditor.exe`.</span></span>  
  
2.  <span data-ttu-id="61222-361">**ファイル**メニューの **開く** をクリック**実行可能ファイル**、 **COM + サービス**、または**web ホスト サービス**を作成する構成ファイルの種類に応じて、します。</span><span class="sxs-lookup"><span data-stu-id="61222-361">From the **File** menu, select **Open** and click **Executable**, **COM+ Service**, or **WebHosted Service**, depending on the type of configuration file you want to create.</span></span>  
  
3.  <span data-ttu-id="61222-362">**開く** ダイアログ ボックスで、構成ファイルを作成し、ダブルクリックする特定のファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="61222-362">In the **Open** dialog box, navigate to the specific file you want to create a configuration file for and double-click it.</span></span>  
  
4.  <span data-ttu-id="61222-363">**ファイル** メニューのをポイント**新しい項目の追加** をクリック**サービス**です。</span><span class="sxs-lookup"><span data-stu-id="61222-363">In the **File** menu, point to **Add New Item** and click **Service**.</span></span> <span data-ttu-id="61222-364">新しいサービス要素ウィザードが開きます。</span><span class="sxs-lookup"><span data-stu-id="61222-364">The New Service Element Wizard opens.</span></span>  
  
5.  <span data-ttu-id="61222-365">ウィザードの手順に従って新しいサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="61222-365">Follow the steps in the wizard to create the new service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61222-366">ウィザードによって生成される構成ファイルから NetPeerTcpBinding を使用する場合は、手動でバインディング構成要素を追加し、その `mode` 要素の `security` 属性を "None" に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61222-366">If you want to use the NetPeerTcpBinding from the configuration file generated by the Wizard, you have to manually add a binding configuration element and modify the `mode` attribute of its `security` element to "None".</span></span>  
  
## <a name="configuring-com"></a><span data-ttu-id="61222-367">COM+ の構成</span><span class="sxs-lookup"><span data-stu-id="61222-367">Configuring COM+</span></span>  
 <span data-ttu-id="61222-368">サービス構成エディターによって、既存の COM+ アプリケーションに新しい構成ファイルを作成したり、既存の COM+ 構成を編集することができます。</span><span class="sxs-lookup"><span data-stu-id="61222-368">The Service Configuration Editor enables you to create a new configuration file for an existing COM+ application, or edit an existing COM+ configuration.</span></span> <span data-ttu-id="61222-369">**COM コントラクト**ノードは表示されているときに、<`comContract`> セクションは構成ファイルに存在します。</span><span class="sxs-lookup"><span data-stu-id="61222-369">The **COM Contract** node is only visible when the <`comContract`> section exists in the configuration file.</span></span>  
  
### <a name="creating-a-new-com-configuration"></a><span data-ttu-id="61222-370">新しい COM+ 構成の作成</span><span class="sxs-lookup"><span data-stu-id="61222-370">Creating a New COM+ Configuration</span></span>  
 <span data-ttu-id="61222-371">新しい COM+ 構成を作成する前に、COM+ アプリケーションがコンポーネント サービスにインストールされて、グローバル アセンブリ キャッシュ (GAC) に登録されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="61222-371">Before creating a new COM+ configuration, make sure that your COM+ application is installed in Component Services, and registered in the Global Assembly Cache (GAC).</span></span>  
  
1.  <span data-ttu-id="61222-372">選択**ファイル**メニュー]-> [**統合** -> **COM + アプリケーションです。**</span><span class="sxs-lookup"><span data-stu-id="61222-372">Select **File** menu -> **Integrate** -> **COM+ Application.**</span></span> <span data-ttu-id="61222-373">この操作は、現在開いているファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="61222-373">This operation closes the current opened file.</span></span> <span data-ttu-id="61222-374">現在のファイルに保存されていないデータがあれば、[保存] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61222-374">If there is unsaved data in the current file, a Save dialog appears.</span></span> <span data-ttu-id="61222-375">**COM + 統合ウィザード**が起動されます。</span><span class="sxs-lookup"><span data-stu-id="61222-375">The **COM+ Integration Wizard** is then launched.</span></span>  
  
2.  <span data-ttu-id="61222-376">最初のページで、ツリーから COM+ アプリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-376">In the first page, select the COM+ application from the tree.</span></span> <span data-ttu-id="61222-377">ツリーで COM+ アプリケーションが見つからない場合は、COM+ アプリケーションがコンポーネント サービスにインストールされて、グローバル アセンブリ キャッシュ (GAC) に登録されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="61222-377">If you cannot find your COM+ application in the tree, verify that it is installed in the Component Services and registered in the Global Assembly Cache (GAC).</span></span>  
  
3.  <span data-ttu-id="61222-378">次のページで、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスとして公開するメソッドを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-378">In the next page, select which method(s) you want to expose as [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="61222-379">既定では、COM+ アプリケーションでサポートされるすべてのメソッドが表示され、選択されます。</span><span class="sxs-lookup"><span data-stu-id="61222-379">All the supported methods in the COM+ application are displayed and selected by default.</span></span>  
  
4.  <span data-ttu-id="61222-380">ホスト メソッドを選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-380">Choose a hosting method.</span></span>  
  
5.  <span data-ttu-id="61222-381">ウィザードの手順に従って他の設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="61222-381">Configure other settings according to the guides in the wizard.</span></span>  
  
6.  <span data-ttu-id="61222-382">サービス構成エディターは、バックグラウンドで ComSvcConfig.exe を利用して、構成ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="61222-382">Service Configuration Editor utilizes ComSvcConfig.exe in the background to generate configuration file.</span></span> <span data-ttu-id="61222-383">これが完了すると、概要を表示してウィザードを終了できます。</span><span class="sxs-lookup"><span data-stu-id="61222-383">After this is completed, you can view a summary and exit the wizard.</span></span> <span data-ttu-id="61222-384">構成を直接編集できるように、生成された構成ファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="61222-384">The generated configuration file is opened so that you can edit it directly.</span></span>  
  
### <a name="editing-an-existing-com-configuration"></a><span data-ttu-id="61222-385">既存の COM+ 構成の編集</span><span class="sxs-lookup"><span data-stu-id="61222-385">Editing an Existing COM+ Configuration</span></span>  
  
1.  <span data-ttu-id="61222-386">選択**ファイル**メニュー]-> [**開く** -> **COM + サービス**しています.</span><span class="sxs-lookup"><span data-stu-id="61222-386">Select **File** menu -> **Open** -> **COM+ Service**…</span></span>  
  
2.  <span data-ttu-id="61222-387">編集する COM+ サービスを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="61222-387">Select the COM+ Service you want to edit from the list.</span></span>  
  
3.  <span data-ttu-id="61222-388">構成設定を編集し、 **COM コントラクト**ノード。</span><span class="sxs-lookup"><span data-stu-id="61222-388">Edit configuration settings in the **COM Contracts** node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="61222-389">COM コントラクトを含む構成ファイルを直接開いて編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="61222-389">You can also directly open and edit a configuration file that contains COM contracts.</span></span>  
  
## <a name="security"></a><span data-ttu-id="61222-390">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="61222-390">Security</span></span>  
 <span data-ttu-id="61222-391">構成エディターによって生成されるサービス構成ファイルは、セキュリティによる保護が保証されていません。</span><span class="sxs-lookup"><span data-stu-id="61222-391">A service configuration file generated by the Configuration Editor is not guaranteed to be secure.</span></span> <span data-ttu-id="61222-392">参照してください、[セキュリティ](../../../docs/framework/wcf/feature-details/security.md)ドキュメントを保護する方法を調べるには、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services です。</span><span class="sxs-lookup"><span data-stu-id="61222-392">Please refer to the [Security](../../../docs/framework/wcf/feature-details/security.md) documentation to find out how to secure your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services.</span></span>  
  
 <span data-ttu-id="61222-393">また、構成エディターを使用して読み書きできるのは、有効な [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 構成要素だけです。</span><span class="sxs-lookup"><span data-stu-id="61222-393">In addition, the Configuration Editor can only be used to read and write valid [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration elements.</span></span> <span data-ttu-id="61222-394">ツールは、スキーマに準拠するユーザー定義の要素を無視します。</span><span class="sxs-lookup"><span data-stu-id="61222-394">The tool ignores schema-compliant, user-defined elements.</span></span> <span data-ttu-id="61222-395">また、これらの要素を構成ファイルから削除したり、既知の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 要素に対する影響を究明することはありません。</span><span class="sxs-lookup"><span data-stu-id="61222-395">It also does not attempt remove these elements from the configuration file or determine their effects on the known [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] elements.</span></span> <span data-ttu-id="61222-396">これらの要素がアプリケーションやシステムに脅威を与えるかどうかを究明するのはユーザーの責任です。</span><span class="sxs-lookup"><span data-stu-id="61222-396">It is the user’s responsibility to determine whether these elements pose a threat to the application or the system.</span></span>
