---
title: インプロセスの side-by-side 実行
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee9eb30d6966d8162b29286140c068d854f7911c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397456"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="6e9ad-102">インプロセスの side-by-side 実行</span><span class="sxs-lookup"><span data-stu-id="6e9ad-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="6e9ad-103">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、インプロセスの side-by-side ホスティングを使用して、1 つのプロセスで複数のバージョンの共通言語ランタイム (CLR) を実行できます。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-103">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="6e9ad-104">既定では、マネージ COM コンポーネントは、プロセスに読み込まれている .NET Framework のバージョンに関係なく、コンポーネントがビルドされた .NET Framework のバージョンで実行されます。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="6e9ad-105">背景</span><span class="sxs-lookup"><span data-stu-id="6e9ad-105">Background</span></span>  
 <span data-ttu-id="6e9ad-106">.NET Framework ではマネージ コード アプリケーションに対して常に side-by-side ホスティングが提供されてきましたが、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] より前のバージョンでは、マネージ COM コンポーネントについてはこの機能は提供されませんでした。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="6e9ad-107">以前は、プロセスに読み込まれたマネージ COM コンポーネントは、既に読み込まれているランタイムのバージョン、またはインストールされている .NET Framework の最新バージョンで実行されました。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="6e9ad-108">このバージョンが COM コンポーネントと互換性がない場合、コンポーネントは実行できませんでした。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="6e9ad-109">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] が備える side-by-side ホスティングの新しいアプローチでは、次のことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-109">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
-   <span data-ttu-id="6e9ad-110">.NET Framework の新しいバージョンをインストールしても、既存のアプリケーションに影響はありません。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
-   <span data-ttu-id="6e9ad-111">アプリケーションは、それがビルドされたバージョンの .NET Framework に対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="6e9ad-112">明示的に指示しない限り、新しいバージョンの .NET Framework は使われません。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="6e9ad-113">ただし、新しいバージョンの .NET Framework を使うようにアプリケーションを移行する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="6e9ad-114">ユーザーと開発者への影響</span><span class="sxs-lookup"><span data-stu-id="6e9ad-114">Effects on Users and Developers</span></span>  
  
-   <span data-ttu-id="6e9ad-115">**エンドユーザーとシステム管理者**。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-115">**End users and system administrators**.</span></span> <span data-ttu-id="6e9ad-116">これらのユーザーについては、単独で、またはアプリケーションと共に、ランタイムの新しいバージョンをインストールしても、コンピューターに影響がないことが、これまで以上に確実になっています。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="6e9ad-117">既存のアプリケーションは引き続きこれまでと同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-117">Existing applications will continue to run as they did before.</span></span>  
  
-   <span data-ttu-id="6e9ad-118">**アプリケーション開発者**。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-118">**Application developers**.</span></span> <span data-ttu-id="6e9ad-119">Side-by-side ホスティングは、アプリケーション開発者に対する影響はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="6e9ad-120">既定では、アプリケーションはそれがビルドされた .NET Framework のバージョンで常に実行されます。これは変更されていません。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="6e9ad-121">ただし、開発者はこの動作をオーバーライドし、新しいバージョンの .NET Framework で実行するようアプリケーションに指示できます ([シナリオ 2](#scenarios) をご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
-   <span data-ttu-id="6e9ad-122">**ライブラリ開発者とコンシューマー**。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-122">**Library developers and consumers**.</span></span> <span data-ttu-id="6e9ad-123">ライブラリ開発者が直面する互換性の問題は、side-by-side ホスティングでは解決されません。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="6e9ad-124">アプリケーションによって (直接参照または <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> の呼び出しにより) 直接読み込まれるライブラリは、それが読み込まれる <xref:System.AppDomain> のランタイムを引き続き使います。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="6e9ad-125">サポートする .NET Framework のすべてのバージョンについて、ライブラリをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="6e9ad-126">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ランタイムを使ってコンパイルされているアプリケーションに、それより前のランタイムを使ってビルドされたライブラリが含まれる場合は、そのライブラリも [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ランタイムを使います。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-126">If an application is compiled using the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime but includes a library that was built using an earlier runtime, that library will use the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime as well.</span></span> <span data-ttu-id="6e9ad-127">一方、ランタイムを使ってビルドされたアプリケーションに、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] を使ってビルドされたライブラリが含まれる場合は、アプリケーションも [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] を使うように強制する必要があります ([シナリオ 3](#scenarios) をご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-127">However, if you have an application that was built using an earlier runtime and a library that was built using the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], you must force your application to also use the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (see [scenario 3](#scenarios)).</span></span>  
  
-   <span data-ttu-id="6e9ad-128">**マネージ COM コンポーネントの開発者**。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-128">**Managed COM component developers**.</span></span> <span data-ttu-id="6e9ad-129">以前は、マネージ COM コンポーネントはコンピューターにインストールされている最新バージョンのランタイムを使って自動的に実行しました。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="6e9ad-130">現在は、ビルドされたバージョンのランタイムに対して COM コンポーネントを実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="6e9ad-131">次の表で示すように、.NET Framework バージョン 1.1 でビルドされたコンポーネントは、バージョン 4 のコンポーネントとであれば side-by-side で実行できますが、バージョン 2.0、3.0、3.5 のコンポーネントとは、これらのバージョンでは side-by-side ホスティングを使用できないために side-by-side では実行できません。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="6e9ad-132">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="6e9ad-132">.NET Framework version</span></span>|<span data-ttu-id="6e9ad-133">1.1</span><span class="sxs-lookup"><span data-stu-id="6e9ad-133">1.1</span></span>|<span data-ttu-id="6e9ad-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="6e9ad-134">2.0 - 3.5</span></span>|<span data-ttu-id="6e9ad-135">4</span><span class="sxs-lookup"><span data-stu-id="6e9ad-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="6e9ad-136">1.1</span><span class="sxs-lookup"><span data-stu-id="6e9ad-136">1.1</span></span>|<span data-ttu-id="6e9ad-137">利用不可</span><span class="sxs-lookup"><span data-stu-id="6e9ad-137">Not applicable</span></span>|<span data-ttu-id="6e9ad-138">×</span><span class="sxs-lookup"><span data-stu-id="6e9ad-138">No</span></span>|<span data-ttu-id="6e9ad-139">[はい]</span><span class="sxs-lookup"><span data-stu-id="6e9ad-139">Yes</span></span>|  
    |<span data-ttu-id="6e9ad-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="6e9ad-140">2.0 - 3.5</span></span>|<span data-ttu-id="6e9ad-141">×</span><span class="sxs-lookup"><span data-stu-id="6e9ad-141">No</span></span>|<span data-ttu-id="6e9ad-142">利用不可</span><span class="sxs-lookup"><span data-stu-id="6e9ad-142">Not applicable</span></span>|<span data-ttu-id="6e9ad-143">[はい]</span><span class="sxs-lookup"><span data-stu-id="6e9ad-143">Yes</span></span>|  
    |<span data-ttu-id="6e9ad-144">4</span><span class="sxs-lookup"><span data-stu-id="6e9ad-144">4</span></span>|<span data-ttu-id="6e9ad-145">[はい]</span><span class="sxs-lookup"><span data-stu-id="6e9ad-145">Yes</span></span>|<span data-ttu-id="6e9ad-146">[はい]</span><span class="sxs-lookup"><span data-stu-id="6e9ad-146">Yes</span></span>|<span data-ttu-id="6e9ad-147">利用不可</span><span class="sxs-lookup"><span data-stu-id="6e9ad-147">Not applicable</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6e9ad-148">.NET Framework バージョン 3.0 および 3.5 はバージョン 2.0 に対して増分的にビルドされているため、side-by-side で実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="6e9ad-149">これらは、本質的に同じバージョンです。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="6e9ad-150">side-by-side ホスティングの一般的なシナリオ</span><span class="sxs-lookup"><span data-stu-id="6e9ad-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
-   <span data-ttu-id="6e9ad-151">**シナリオ 1:** 以前のバージョンの .NET Framework でビルドされた COM コンポーネントを使うネイティブ アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="6e9ad-152">インストールされている .NET Framework のバージョン: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] および COM コンポーネントによって使われている他のすべての .NET Framework のバージョンの場合。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-152">.NET Framework versions installed: The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="6e9ad-153">対処方法: このシナリオの場合は、何も行いません。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="6e9ad-154">COM コンポーネントは、登録された .NET Framework のバージョンで実行されます。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
-   <span data-ttu-id="6e9ad-155">**シナリオ 2**: [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] でビルドされたマネージ アプリケーションを、できれば [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)] で実行したいが、バージョン 2.0 が存在しない場合は [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] で実行したい場合。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-155">**Scenario 2**: Managed application built with the [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] that you would prefer to run with the [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], but are willing to run on the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="6e9ad-156">インストールされている .NET Framework のバージョン: 以前のバージョンの .NET Framework と [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-156">.NET Framework versions installed: An earlier version of the .NET Framework and the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="6e9ad-157">対処方法: アプリケーション ディレクトリの[アプリケーション構成ファイル](../../../docs/framework/configure-apps/index.md)で、次のように設定された [\<startup> 要素](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)と [\<supportedRuntime> 要素](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)を使います。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-157">What to do: In the [application configuration file](../../../docs/framework/configure-apps/index.md) in the application directory, use the [\<startup> element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="6e9ad-158">**シナリオ 3:** 以前のバージョンの .NET Framework でビルドされた COM コンポーネントを使うネイティブ アプリケーションを、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] で実行したい場合。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="6e9ad-159">インストールされている .NET Framework のバージョン: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-159">.NET Framework versions installed: The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="6e9ad-160">対処方法: アプリケーション ディレクトリのアプリケーション構成ファイルで、`useLegacyV2RuntimeActivationPolicy` 属性と `true` に設定した `<startup>` 要素と、次のように設定された `<supportedRuntime>` 要素を使います。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="6e9ad-161">例</span><span class="sxs-lookup"><span data-stu-id="6e9ad-161">Example</span></span>  
 <span data-ttu-id="6e9ad-162">次の例では、コンポーネントがコンパイルされた .NET Framework のバージョンを使うことでマネージ COM コンポーネントを実行しているアンマネージ COM ホストを示します。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="6e9ad-163">次の例を実行するには、[!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] を使って次のマネージ COM コンポーネントをコンパイルして登録します。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-163">To run the following example, compile and register the following managed COM component using the [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].</span></span> <span data-ttu-id="6e9ad-164">コンポーネントを登録するには、**[プロジェクト]** メニューの **[プロパティ]** をクリックし、**[ビルド]** タブをクリックして、**[COM の相互運用機能に登録]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="6e9ad-165">次のアンマネージ C++ アプリケーションをコンパイルすると、前の例で作成した COM オブジェクトがアクティブ化すされます。</span><span class="sxs-lookup"><span data-stu-id="6e9ad-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
```  
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");   
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e9ad-166">参照</span><span class="sxs-lookup"><span data-stu-id="6e9ad-166">See Also</span></span>  
 [<span data-ttu-id="6e9ad-167">\<startup> 要素</span><span class="sxs-lookup"><span data-stu-id="6e9ad-167">\<startup> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
 [<span data-ttu-id="6e9ad-168">\<<supportedRuntime> 要素</span><span class="sxs-lookup"><span data-stu-id="6e9ad-168">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
