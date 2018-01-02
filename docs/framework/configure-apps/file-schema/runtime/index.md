---
title: "ランタイム設定スキーマ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
caps.latest.revision: "49"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56346b562489b82800421e91201a76bf7f74e5b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-settings-schema"></a>ランタイム設定スキーマ
ランタイム設定は、.NET Framework を対象とするアプリケーションを構成する共通言語ランタイムによって使用されます。  
  
 [\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
 [\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)  
 [\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)  
 [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)  
 [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
 [\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [\<assemblyBinding>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)  
 [\<dependentAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)  
 [\<assemblyIdentity>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)  
 [\<bindingRedirect>](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)  
 [\<probing>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)  
 [\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)  
 [\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)  
 [\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
 [\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)  
 [\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)  
 [\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)  
 [\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)  
 [\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)  
 [\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)  
 [\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)  
 [\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)  
 [\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)  
 [\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)  
 [\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)  
 [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)  
 [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)  
 [\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)  
 [\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)  
 [\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)  
 [\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)  
 [<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)  
 [<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)  
 [<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)  
 [\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)  
 [\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)  
 [\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)  
 [\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)  
 [\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)  
 [\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)  
 [\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)  
 [\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)  
 [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)  
 [\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)  
 [<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)  
 [\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)  
 [\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|名前付きキャッシュを、メモリ キャッシュの `namedCaches` コレクションに追加します。|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|偽装の実行方法に関係なく、Windows ID が常に非同期ポイント間でフローすることを指定します。|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|<xref:System.AppContext> クラスで使用される、新機能に対するオプトアウト メカニズムを指定するスイッチを 1 つまたは複数定義します。|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|プロセスにおける既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを提供するアセンブリを指定します。|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーの役割を果たす種類を指定します。|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|プロセスのライフサイクルにおいて、プロセスのすべてのアプリケーション ドメインの統計を収集するようにランタイムに指示します。|  
|[\<assemblyBinding>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|[\<assemblyIdentity>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)|アセンブリに関する識別情報が含まれています。|  
|[\<bindingRedirect>](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)|1 つのアセンブリ バージョンを別のバージョンにリダイレクトします。|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|信頼されたアセンブリに対する厳密な名前の検証をバイパスするかどうかを指定します。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|メモリ キャッシュの `namedCaches` コレクションを消去します。|  
|[\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)|ランタイムがアセンブリを検索する場所を指定します。|  
|[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|文字列比較の実行時に、ランタイムがレガシ並べ替え動作を使用するように指定します。|  
|[\<dependentAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。|  
|[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|DEVPATH 環境変数によって指定されたディレクトリで、ランタイムがアセンブリの検索を行うかどうかを指定します。|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] の既定の動作であるバインディング エラーのキャッシュを無効化するかどうかを指定します。|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|スレッドの起動時にスレッド スタック全体をコミットするかどうかを指定します。|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|アプリケーション ドメインの構成設定をランタイム ホストが上書きする既定の動作を無効化するかどうかを指定します。|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|日付と時刻の解析メソッドが、日、月、時間、および午前/午後のみを含む日付の文字列を解析するように調整されたルールのセットを使用するかどうかを決定します。|  
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|暗号化アルゴリズムが連邦情報処理規格 (FIPS: Federal Information Processing Standard) に準拠する必要があるコンピューターの構成要件を強制するかどうかを指定します。|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|共通言語ランタイム イベントで Windows イベント トレーシング (ETW) を有効にするかどうかを指定します。|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|PerfCounter.dll が、.NET Framework バージョン 1.1 のアプリケーションの CategoryOptions レジストリ設定を使用してするかどうかを指定して、カテゴリ別の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを決定します。|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|64 ビット プラットフォームで、合計サイズが 2 GB (ギガバイト) を超える配列を有効にします。|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|ランタイムがガベージ コレクションを並列に実行するかどうかを指定します。|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|共通言語ランタイムがサーバーのガベージ コレクションを実行するかどうかを指定します。|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|ランタイムがコード アクセス セキュリティ (CAS) の発行元ポリシーを使用するかどうかを指定します。|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|ランタイムがアクセス違反およびその他の破損状態例外をキャッチするマネージ コードを許可するかどうかを指定します。|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Windows ID が、現在のスレッドの実行コンテキストのフロー設定に関係なく、非同期ポイント間でフローしないことを指定します。|  
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|リモート ソースからのアセンブリを完全な信頼として読み込むかどうかを指定します。|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> クラスに基づくキャッシュを構成するために使用される要素を定義します。|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|`namedCache` インスタンスの構成設定のコレクションが含まれます。|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|ランタイムがレガシ コード アクセス セキュリティ (CAS) ポリシーを使用するかどうかを指定します。|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|ランタイムが実行時の不適切なプラットフォーム呼び出し宣言を自動的に修正するかどうかを指定します。これにより、マネージ コードとアンマネージ コード間の遷移が遅くなります。|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドで固定量のメモリを使用してハッシュ コードを計算するかどうかを指定します。|  
|[\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|ランタイムが、アプリケーション ドメインの境界間のリモート処理ではなく COM 相互運用を使用することを指定します。|  
|[\<probing>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|アセンブリの読み込み時にランタイムが検索するサブディレクトリを指定します。|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|ランタイムが発行元ポリシーを適用するかどうかを指定します。|  
|[\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|部分名が使用された場合に動的に読み込む必要があるアセンブリの完全名を指定します。|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|サテライト アセンブリのプローブを最適化します。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。|  
|[\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|アセンブリのバインディングとガベージ コレクションの動作に関する情報が含まれています。|  
|[\<shadowCopyTimeStampVerification>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|シャドウ コピーが [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] で導入された既定の起動の動作を使用するか、.NET Framework の以前のバージョンの起動の動作に戻すかどうかを指定します。|  
|[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|.NET Framework の 2 つの異なる実装にある同じアセンブリを 1 つのアプリケーションから参照できるように、既定の動作を無効にすることができます。既定の動作では、アプリケーションの移植性を高めるために、このようなアセンブリは同等のものとして扱われます。|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|既定のメモリ内オブジェクト キャッシュの構成情報を提供します。|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|ランタイムによって、すべての CPU グループにマネージ スレッドを分散するかどうかを指定します。|  
|[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|タスクがハンドルされない例外によって実行中のプロセスを終了するかどうかを指定します。|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|ランタイムで <xref:System.TimeSpan> の値に従来の書式を使用するかどうかを指定します。|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|共通言語ランタイムが Just-In-Time コンパイルの従来の 64 ビット JIT コンパイラを使用するかどうかを決定します。|  
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|ランタイムがアプリケーション ドメインごとに文字列のハッシュ コードを計算するかどうかを指定します。|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|ランタイムが内部的に使用する特定のスレッド作成時に、既定のスタック サイズではなく明示的なスタック サイズを使用することを要求します。|  
  
## <a name="see-also"></a>参照  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [方法: 同時実行ガベージ コレクションを無効にします。](http://msdn.microsoft.com/en-us/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [アセンブリ バージョンのリダイレクト](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
