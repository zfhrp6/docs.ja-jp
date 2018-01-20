---
title: "&lt;loadFromRemoteSources&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13b42405a0faf721c46476aadaa0cff8163883c1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a><span data-ttu-id="2d138-102">&lt;loadFromRemoteSources&gt;要素</span><span class="sxs-lookup"><span data-stu-id="2d138-102">&lt;loadFromRemoteSources&gt; Element</span></span>
<span data-ttu-id="2d138-103">リモート ソースからのアセンブリに対して、完全な信頼を付与するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2d138-103">Specifies whether assemblies from remote sources should be granted full trust.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d138-104">場合は、Visual Studio プロジェクトのエラー一覧またはビルド エラーのエラー メッセージのため、このトピックにダイレクトされたを参照してください。[する方法: Visual Studio で Web からアセンブリを使用して](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070)です。</span><span class="sxs-lookup"><span data-stu-id="2d138-104">If you were directed to this topic because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).</span></span>  
  
 <span data-ttu-id="2d138-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2d138-105">\<configuration></span></span>  
<span data-ttu-id="2d138-106">\<runtime></span><span class="sxs-lookup"><span data-stu-id="2d138-106">\<runtime></span></span>  
<span data-ttu-id="2d138-107">\<loadFromRemoteSources></span><span class="sxs-lookup"><span data-stu-id="2d138-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d138-108">構文</span><span class="sxs-lookup"><span data-stu-id="2d138-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d138-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2d138-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2d138-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d138-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d138-111">属性</span><span class="sxs-lookup"><span data-stu-id="2d138-111">Attributes</span></span>  
  
|<span data-ttu-id="2d138-112">属性</span><span class="sxs-lookup"><span data-stu-id="2d138-112">Attribute</span></span>|<span data-ttu-id="2d138-113">説明</span><span class="sxs-lookup"><span data-stu-id="2d138-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2d138-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="2d138-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="2d138-115">リモート ソースから読み込まれたアセンブリに対して、完全な信頼を付与する必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2d138-115">Specifies whether an assembly that is loaded from remote sources should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2d138-116">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="2d138-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="2d138-117">値</span><span class="sxs-lookup"><span data-stu-id="2d138-117">Value</span></span>|<span data-ttu-id="2d138-118">説明</span><span class="sxs-lookup"><span data-stu-id="2d138-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2d138-119">リモート ソースからアプリケーションに完全な信頼を付与しないでください。</span><span class="sxs-lookup"><span data-stu-id="2d138-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="2d138-120">既定値です。</span><span class="sxs-lookup"><span data-stu-id="2d138-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="2d138-121">リモート ソースからアプリケーションへの完全な信頼を付与します。</span><span class="sxs-lookup"><span data-stu-id="2d138-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d138-122">子要素</span><span class="sxs-lookup"><span data-stu-id="2d138-122">Child Elements</span></span>  
 <span data-ttu-id="2d138-123">なし。</span><span class="sxs-lookup"><span data-stu-id="2d138-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d138-124">親要素</span><span class="sxs-lookup"><span data-stu-id="2d138-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2d138-125">要素</span><span class="sxs-lookup"><span data-stu-id="2d138-125">Element</span></span>|<span data-ttu-id="2d138-126">説明</span><span class="sxs-lookup"><span data-stu-id="2d138-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2d138-127">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="2d138-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2d138-128">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="2d138-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d138-129">コメント</span><span class="sxs-lookup"><span data-stu-id="2d138-129">Remarks</span></span>  
 <span data-ttu-id="2d138-130">.NET Framework バージョン 3.5 以前のバージョンで、リモートの場所からアセンブリが読み込まれている場合、アセンブリが実行が読み込まれたゾーンに依存していた許可セットでは部分的に信頼されます。</span><span class="sxs-lookup"><span data-stu-id="2d138-130">In the .NET Framework version 3.5 and earlier versions, if you loaded an assembly from a remote location, the assembly would run partially trusted with a grant set that depended on the zone in which it was loaded.</span></span> <span data-ttu-id="2d138-131">たとえば、web サイトからアセンブリが読み込まれている場合は、インターネット ゾーンに読み込まれましたし、インターネット アクセス許可セットを許可します。</span><span class="sxs-lookup"><span data-stu-id="2d138-131">For example, if you loaded an assembly from a website, it was loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="2d138-132">つまり、プロセスは、インターネットのサンド ボックス内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="2d138-132">In other words, it executed in an Internet sandbox.</span></span> <span data-ttu-id="2d138-133">そのアセンブリを実行しようとする場合、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]と以降のバージョンでは、例外がスローされます; する必要がありますか、明示的にサンド ボックスの作成、アセンブリの (を参照してください[する方法: 実行部分信頼コードをサンド ボックスで](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md))、または完全な信頼で実行します。</span><span class="sxs-lookup"><span data-stu-id="2d138-133">If you try to run that assembly in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later versions, an exception is thrown; you must either explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), or run it in full trust.</span></span>  
  
 <span data-ttu-id="2d138-134">`<loadFromRemoteSources>`で信頼されている、.NET Framework の以前のバージョンで部分的に信頼されたを実行するアセンブリが完全に実行されることを指定した要素により、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="2d138-134">The `<loadFromRemoteSources>` element lets you specify that the assemblies that would have run partially trusted in earlier versions of the .NET Framework are to be run fully trusted in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="2d138-135">既定では、リモート アセンブリに機能しません、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]およびそれ以降。</span><span class="sxs-lookup"><span data-stu-id="2d138-135">By default, remote assemblies do not run in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span> <span data-ttu-id="2d138-136">リモートのアセンブリを実行するか、完全信頼として実行か作成してください、サンド ボックス化された<xref:System.AppDomain>これを実行します。</span><span class="sxs-lookup"><span data-stu-id="2d138-136">To run a remote assembly, you must either run it as fully trusted or create a sandboxed <xref:System.AppDomain> in which to run it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d138-137">[!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]、ローカル ネットワーク共有上のアセンブリは、既定で完全な信頼として実行される; を有効にする必要はありません、`<loadFromRemoteSources>`要素。</span><span class="sxs-lookup"><span data-stu-id="2d138-137">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblies on local network shares are run as full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d138-138">アプリケーションが web サイトからコピーされた場合としてマークされている Windows で web アプリケーションでは、ローカル コンピューター上にある場合でもです。</span><span class="sxs-lookup"><span data-stu-id="2d138-138">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="2d138-139">その指定を変更するには、ファイルのプロパティを変更することで、または使用することができます、`<loadFromRemoteSources>`要素をアセンブリを付与する完全な信頼。</span><span class="sxs-lookup"><span data-stu-id="2d138-139">You can change that designation by changing the file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="2d138-140">代わりに、使用することができます、<xref:System.Reflection.Assembly.UnsafeLoadFrom%2A>オペレーティング システムは、web から読み込まれたものとしてフラグが設定をローカル アセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2d138-140">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>  
  
 <span data-ttu-id="2d138-141">`enabled`はコード アクセス セキュリティ (CAS) が無効になっている場合にのみ、この要素の属性です。</span><span class="sxs-lookup"><span data-stu-id="2d138-141">The `enabled` attribute for this element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="2d138-142">既定では、CAS ポリシーが無効になって、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="2d138-142">By default, CAS policy is disabled in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="2d138-143">設定した場合`enabled`に`true`、リモート アプリケーションには、完全信頼が与えられます。</span><span class="sxs-lookup"><span data-stu-id="2d138-143">If you set `enabled` to `true`, remote applications are granted full trust.</span></span>  
  
 <span data-ttu-id="2d138-144">場合`<loadFromRemoteSources>``enabled`に設定されていない`true`、次の条件下で、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2d138-144">If `<loadFromRemoteSources>``enabled` is not set to `true`, an exception is thrown under the following conditions:</span></span>  
  
-   <span data-ttu-id="2d138-145">現在のドメインのサンド ボックス化動作の動作とは異なります、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="2d138-145">The sandboxing behavior of the current domain is different from its behavior in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span> <span data-ttu-id="2d138-146">これには、無効になり、CAS ポリシーとセキュリティで保護されたしないで現在のドメインが必要です。</span><span class="sxs-lookup"><span data-stu-id="2d138-146">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>  
  
-   <span data-ttu-id="2d138-147">読み込まれるアセンブリではない、`MyComputer`ゾーンです。</span><span class="sxs-lookup"><span data-stu-id="2d138-147">The assembly being loaded is not from the `MyComputer` zone.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d138-148">取得することがあります、 <xref:System.IO.FileLoadException> Windows Virtual PC アプリケーションで、ホスト コンピュータ上のリンク フォルダーからファイルをロードしようとするとします。</span><span class="sxs-lookup"><span data-stu-id="2d138-148">You may get a <xref:System.IO.FileLoadException> in a Windows Virtual PC application when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="2d138-149">このエラーは、経由でリンクされているフォルダーからファイルをロードしようとしたときにも発生する可能性があります[リモート デスクトップ サービス](http://go.microsoft.com/fwlink/?LinkId=182775)(ターミナル サービス)。</span><span class="sxs-lookup"><span data-stu-id="2d138-149">This error may also occur when you try to load a file from a folder linked over [Remote Desktop Services](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="2d138-150">例外を避けるためには、次のように設定します。`enabled`に`true`です。</span><span class="sxs-lookup"><span data-stu-id="2d138-150">To avoid the exception, set `enabled` to `true`.</span></span>  
  
 <span data-ttu-id="2d138-151">設定、`<loadFromRemoteSources>`要素を`true`により、この例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="2d138-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="2d138-152">これにより、ことをせず、サンド ボックスに、共通言語ランタイムのセキュリティを読み込まれたアセンブリを指定して、として実行を許可することができます完全な信頼。</span><span class="sxs-lookup"><span data-stu-id="2d138-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute as full trust.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2d138-153">アセンブリが完全信頼で実行する必要がありますされない場合は、この構成要素を設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="2d138-153">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="2d138-154">代わりに、作成、セキュリティで保護された<xref:System.AppDomain>アセンブリの読み込み先となります。</span><span class="sxs-lookup"><span data-stu-id="2d138-154">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2d138-155">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="2d138-155">Configuration File</span></span>  
 <span data-ttu-id="2d138-156">この要素は、通常は、アプリケーション構成ファイルで使用しますが、コンテキストに応じてその他の構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d138-156">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="2d138-157">詳細については、記事を参照してください。[詳細暗黙的な使用の CAS ポリシー: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET セキュリティ ブログ。</span><span class="sxs-lookup"><span data-stu-id="2d138-157">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d138-158">例</span><span class="sxs-lookup"><span data-stu-id="2d138-158">Example</span></span>  
 <span data-ttu-id="2d138-159">次の例では、リモート ソースからアプリケーションに完全な信頼を付与する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2d138-159">The following example shows how to grant full trust to applications from remote sources.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d138-160">参照</span><span class="sxs-lookup"><span data-stu-id="2d138-160">See Also</span></span>  
 [<span data-ttu-id="2d138-161">CAS ポリシーの複数の暗黙的な用途: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="2d138-161">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [<span data-ttu-id="2d138-162">方法 : サンドボックスで部分信頼コードを実行する</span><span class="sxs-lookup"><span data-stu-id="2d138-162">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [<span data-ttu-id="2d138-163">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="2d138-163">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="2d138-164">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="2d138-164">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
