---
title: ".NET Framework のバージョンの互換性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 741c2d1c49f44a6a7b299845cdc37cc8425c326b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="version-compatibility-in-the-net-framework"></a><span data-ttu-id="edb2c-102">.NET Framework のバージョンの互換性</span><span class="sxs-lookup"><span data-stu-id="edb2c-102">Version Compatibility in the .NET Framework</span></span>
<span data-ttu-id="edb2c-103">下位互換とは、プラットフォームの特定のバージョンで開発されたアプリが、そのプラットフォームの新しいバージョンでも実行できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="edb2c-103">Backward compatibility means that an app that was developed for a particular version of a platform will run on later versions of that platform.</span></span> <span data-ttu-id="edb2c-104">.NET Framework では、下位互換性が最大限に高められています。.NET Framework のあるバージョンで記述されたソース コードは、.NET Framework の新しいバージョンでコンパイルでき、.NET Framework のあるバージョンで実行されるバイナリは、新しいバージョンの .NET Framework でも同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="edb2c-104">The .NET Framework tries to maximize backward compatibility: Source code written for one version of the .NET Framework should compile on later versions of the .NET Framework, and binaries that run on one version of the .NET Framework should behave identically on later versions of the .NET Framework.</span></span>  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a><span data-ttu-id="edb2c-105">アプリのバージョンの互換性</span><span class="sxs-lookup"><span data-stu-id="edb2c-105">Version compatibility for apps</span></span>  
 <span data-ttu-id="edb2c-106">既定では、アプリは、ビルド対象の .NET Framework のバージョンで実行されます。</span><span class="sxs-lookup"><span data-stu-id="edb2c-106">By default, an app runs on the version of the .NET Framework that it was built for.</span></span> <span data-ttu-id="edb2c-107">そのバージョンが存在せず、アプリの構成ファイルにサポートされるバージョンが定義されていない場合は、.NET Framework 初期化エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="edb2c-107">If that version is not present and the app configuration file does not define supported versions, a .NET Framework initialization error may occur.</span></span> <span data-ttu-id="edb2c-108">この場合、アプリは実行できません。</span><span class="sxs-lookup"><span data-stu-id="edb2c-108">In this case, the attempt to run the app will fail.</span></span>  
  
 <span data-ttu-id="edb2c-109">アプリを実行する特定のバージョンを定義するには、1 つ以上の [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 要素をアプリの構成ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="edb2c-109">To define the specific versions on which your app runs, add one or more [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elements to your app's configuration file.</span></span> <span data-ttu-id="edb2c-110">各 `<supportedRuntime>` 要素は、サポートされるランタイムのバージョンを示します。最初の要素で最も優先度の高いバージョンを、最後の要素で最も優先度の低いバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="edb2c-110">Each `<supportedRuntime>` element lists a supported version of the runtime, with the first specifying the most preferred version and the last specifying the least preferred version.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
```  
  
 <span data-ttu-id="edb2c-111">詳しくは、[.NET Framework 4 または 4.x をサポートするアプリの構成方法](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="edb2c-111">For more information, see [How to: Configure an App to Support .NET Framework 4 or 4.x](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).</span></span>  
  
## <a name="version-compatibility-for-components"></a><span data-ttu-id="edb2c-112">コンポーネントのバージョンの互換性</span><span class="sxs-lookup"><span data-stu-id="edb2c-112">Version compatibility for components</span></span>  
 <span data-ttu-id="edb2c-113">アプリは、それが実行される .NET Framework を制御できますが、コンポーネントは制御できません。</span><span class="sxs-lookup"><span data-stu-id="edb2c-113">An app can control the version of the .NET Framework on which it runs, but a component cannot.</span></span> <span data-ttu-id="edb2c-114">コンポーネントとクラス ライブラリは特定のアプリのコンテキストで読み込まれるので、アプリが実行されるバージョンの .NET Framework で自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="edb2c-114">Components and class libraries are loaded in the context of a particular app, and therefore automatically run on the version of the .NET Framework that the app runs on.</span></span>  
  
 <span data-ttu-id="edb2c-115">この制限のため、互換性の保証は、コンポーネントにとって特に重要です。</span><span class="sxs-lookup"><span data-stu-id="edb2c-115">Because of this restriction, compatibility guarantees are especially important for components.</span></span> <span data-ttu-id="edb2c-116">.NET Framework 4 以降、コンポーネントに <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=fullName> 属性を適用することにより、複数のバージョンで想定されるコンポーネントの互換性の程度を指定できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="edb2c-116">Starting with the .NET Framework 4, you can specify the degree to which a component is expected to remain compatible across multiple versions by applying the <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=fullName> attribute to that component.</span></span> <span data-ttu-id="edb2c-117">ツールは、この属性を使用して、コンポーネントの将来のバージョンでの互換性保証の潜在的な違反を検出できます。</span><span class="sxs-lookup"><span data-stu-id="edb2c-117">Tools can use this attribute to detect potential violations of the compatibility guarantee in future versions of a component.</span></span>  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a><span data-ttu-id="edb2c-118">下位互換性と .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="edb2c-118">Backward compatibility and the .NET Framework 4.5</span></span>  
 <span data-ttu-id="edb2c-119">.NET Framework 4.5 およびそのポイント リリース (4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7) には、以前のバージョンの .NET Framework でビルドされたアプリと下位互換性があります。</span><span class="sxs-lookup"><span data-stu-id="edb2c-119">The .NET Framework 4.5 and its point releases (4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, and 4.7) are backward-compatible with apps that were built with earlier versions of the .NET Framework.</span></span> <span data-ttu-id="edb2c-120">つまり、旧バージョンの .NET Framework でビルドしたアプリとコンポーネントは、.NET Framework 4.5 で変更を行わずに動作します。</span><span class="sxs-lookup"><span data-stu-id="edb2c-120">In other words, apps and components built with previous versions will work without modification on the .NET Framework 4.5.</span></span> <span data-ttu-id="edb2c-121">ただし、既定では、アプリは、開発された共通言語ランタイムのバージョンで動作するため、アプリを .NET Framework 4.5 で実行するには構成ファイルを提供する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="edb2c-121">However, by default, apps run on the version of the common language runtime for which they were developed, so you may have to provide a configuration file to enable your app to run on the .NET Framework 4.5.</span></span> <span data-ttu-id="edb2c-122">詳細については、この記事の前半に記載した「[アプリのバージョンの互換性](#Apps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="edb2c-122">For more information, see the [Version compatibility for apps](#Apps) section earlier in this article.</span></span>  
  
 <span data-ttu-id="edb2c-123">現実的には、この互換性は、.NET Framework のわずかな変更やプログラミング技法の変化によって損なわれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="edb2c-123">In practice, this compatibility can be broken by seemingly inconsequential changes in the .NET Framework and changes in programming techniques.</span></span> <span data-ttu-id="edb2c-124">たとえば、.NET Framework 4.5 でのパフォーマンスの向上によって、旧バージョンでは発生しなかった競合状態が顕在化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="edb2c-124">For example, performance improvements in the .NET Framework 4.5 can expose a race condition that did not occur on earlier versions.</span></span> <span data-ttu-id="edb2c-125">同様に、.NET Framework アセンブリへのハードコーディングされたパスの使用、.NET Framework の特定のバージョンでの等値比較の実行、およびリフレクションの使用によるプライベート フィールドの値の取得は、下位互換性のない動作です。</span><span class="sxs-lookup"><span data-stu-id="edb2c-125">Similarly, using a hard-coded path to .NET Framework assemblies, performing an equality comparison with a particular version of the .NET Framework, and getting the value of a private field by using reflection are not backward-compatible practices.</span></span> <span data-ttu-id="edb2c-126">さらに、各バージョンの .NET Framework には、バグの修正とセキュリティに関連する変更が含まれており、これらが一部のアプリとコンポーネントの互換性に影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="edb2c-126">In addition, each version of the .NET Framework includes bug fixes and security-related changes that can affect the compatibility of some apps and components.</span></span>  
  
 <span data-ttu-id="edb2c-127">アプリまたはコンポーネントが .NET Framework 4.5 (ポイント リリースである [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]、4.5.2、4.6、4.6.1、4.6.2、4.7 を含む) で期待どおりに動作しない場合は、次のチェックリストを参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="edb2c-127">If your app or component does not work as expected on the .NET Framework 4.5 (including its point releases, the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, or 4.7, use the following checklists:</span></span>  
  
-   <span data-ttu-id="edb2c-128">これらのトピックで、アプリに影響する可能性がある変更を確認し、説明されている代替手段を適用します。</span><span class="sxs-lookup"><span data-stu-id="edb2c-128">Check these topics  for any changes that might affect your app and apply the workaround described:</span></span>  
  
    -   [<span data-ttu-id="edb2c-129">.NET framework 4 への移行に関する問題</span><span class="sxs-lookup"><span data-stu-id="edb2c-129">.NET Framework 4 Migration Issues</span></span>](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)  
  
    -   [<span data-ttu-id="edb2c-130">4.5 でのアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="edb2c-130">Application Compatibility in 4.5</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)  
  
    -   [<span data-ttu-id="edb2c-131">4.5.1 でのアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="edb2c-131">Application Compatibility in 4.5.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)  
  
    -   [<span data-ttu-id="edb2c-132">4.5.2 でのアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="edb2c-132">Application Compatibility in 4.5.2</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)  
  
    -   [<span data-ttu-id="edb2c-133">4.6 でのアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="edb2c-133">Application Compatibility in 4.6</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6.md)  
  
    -   [<span data-ttu-id="edb2c-134">4.6.1 でのアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="edb2c-134">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)  
  
    -   [<span data-ttu-id="edb2c-135">4.6.2 でのアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="edb2c-135">Application Compatibility in 4.6.2</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)  

    - [<span data-ttu-id="edb2c-136">4.7 でのアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="edb2c-136">Application Compatibility in 4.7</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
       
-   <span data-ttu-id="edb2c-137">.NET Framework 1.1 アプリがある場合は、次のトピックもレビューしてください。</span><span class="sxs-lookup"><span data-stu-id="edb2c-137">If you have a .NET Framework 1.1 app, also review these topics:</span></span>  
  
    -   [<span data-ttu-id="edb2c-138">.NET Framework 2.0 の互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="edb2c-138">Changes in .NET Framework 2.0</span></span>](http://go.microsoft.com/fwlink/?LinkID=125263)  
  
    -   [<span data-ttu-id="edb2c-139">.NET Framework 3.5 SP1 の変更点</span><span class="sxs-lookup"><span data-stu-id="edb2c-139">Changes in .NET Framework 3.5 SP1</span></span>](http://go.microsoft.com/fwlink/?LinkId=186989)  
  
-   <span data-ttu-id="edb2c-140">.NET Framework 4.5 またはそのポイント リリースで実行するために既存のソース コードを再コンパイルする場合、または [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] をターゲットとするアプリまたはコンポーネントの新しいバージョンを既存のソース コード ベースから開発する場合は、[クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)に関するページで廃止された型とメンバーを確認し、説明されている回避策を適用してください。</span><span class="sxs-lookup"><span data-stu-id="edb2c-140">If you are recompiling existing source code to run on the .NET Framework 4.5 or its point releases, or if you are developing a new version of an app or component that targets the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] from an existing source code base, check [What's Obsolete in the Class Library](../../../docs/framework/whats-new/whats-obsolete.md) for obsolete types and members, and apply the workaround described.</span></span> <span data-ttu-id="edb2c-141">(コンパイル済みのコードは、互換性のために残されている旧式の型とメンバーに対して引き続き実行されます)。</span><span class="sxs-lookup"><span data-stu-id="edb2c-141">(Previously compiled code will continue to run against types and members that have been marked as obsolete.)</span></span>  
  
-   <span data-ttu-id="edb2c-142">アプリが正常に動作しない原因が [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] での変更によるものとわかった場合は、「[ランタイム設定スキーマ](../../../docs/framework/configure-apps/file-schema/runtime/index.md)」を参照して、アプリの構成ファイルのランタイム設定を使用して以前の動作を復元できるかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="edb2c-142">If you determine that a change in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has broken your app, check the [Runtime Settings Schema](../../../docs/framework/configure-apps/file-schema/runtime/index.md) to determine whether you can use a runtime setting in your app's configuration file to restore the previous behavior.</span></span>  
  
-   <span data-ttu-id="edb2c-143">説明されていない問題が発生した場合は、[Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) にバグを報告し、[netfxcf@microsoft.com](mailto:netfxcf@microsoft.com) にバグ番号を連絡してください。</span><span class="sxs-lookup"><span data-stu-id="edb2c-143">If you encounter an issue that is not documented, file a [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) bug and contact [netfxcf@microsoft.com](mailto:netfxcf@microsoft.com) with the bug number.</span></span>  
  
## <a name="compatibility-and-side-by-side-execution"></a><span data-ttu-id="edb2c-144">互換性と side-by-side 実行</span><span class="sxs-lookup"><span data-stu-id="edb2c-144">Compatibility and side-by-side execution</span></span>  
 <span data-ttu-id="edb2c-145">問題の適切な解決策が見つからない場合は、.NET Framework 4.5 (またはそのポイント リリース) は Version 1.1、2.0、3.5 と side-by-side で実行でき、Version 4 に置き換わるインプレース更新であることを思い出してください。</span><span class="sxs-lookup"><span data-stu-id="edb2c-145">If you cannot find a suitable workaround for your issue, remember that the .NET Framework 4.5 (or one of its point releases) runs side by side with versions 1.1, 2.0, and 3.5, and is an in-place update that replaces version 4.</span></span> <span data-ttu-id="edb2c-146">Version 1.1、2.0、3.5 を対象とするアプリでは、適切なバージョンの .NET Framework を対象コンピューターにインストールして、アプリを最良の環境で実行できます。</span><span class="sxs-lookup"><span data-stu-id="edb2c-146">For apps that target versions 1.1, 2.0, and 3.5, you can install the appropriate version of the .NET Framework on the target machine to run the app in its best environment.</span></span> <span data-ttu-id="edb2c-147">side-by-side 実行について詳しくは、[side-by-side 実行](../../../docs/framework/deployment/side-by-side-execution.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="edb2c-147">For more information about side-by-side execution, see [Side-by-Side Execution](../../../docs/framework/deployment/side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb2c-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="edb2c-148">See Also</span></span>  
 <span data-ttu-id="edb2c-149">[新機能](../../../docs/framework/whats-new/index.md) </span><span class="sxs-lookup"><span data-stu-id="edb2c-149">[What's New](../../../docs/framework/whats-new/index.md) </span></span>  
 <span data-ttu-id="edb2c-150">[クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md) </span><span class="sxs-lookup"><span data-stu-id="edb2c-150">[What's Obsolete in the Class Library](../../../docs/framework/whats-new/whats-obsolete.md) </span></span>  
 <span data-ttu-id="edb2c-151">[アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="edb2c-151">[Application Compatibility](../../../docs/framework/migration-guide/application-compatibility.md) </span></span>  
 <span data-ttu-id="edb2c-152">[Microsoft .NET Framework のサポート ライフサイクル ポリシー](http://go.microsoft.com/fwlink/p/?LinkId=248212) </span><span class="sxs-lookup"><span data-stu-id="edb2c-152">[Microsoft .NET Framework Support Lifecycle Policy](http://go.microsoft.com/fwlink/p/?LinkId=248212) </span></span>  
 [<span data-ttu-id="edb2c-153">.NET framework 4 への移行に関する問題</span><span class="sxs-lookup"><span data-stu-id="edb2c-153">.NET Framework 4 Migration Issues</span></span>](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)

