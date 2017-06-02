---
title: "&lt;runtime&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<runtime> 要素"
  - "コンテナー タグ, <runtime> 要素"
  - "runtime 要素"
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
caps.latest.revision: 70
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 62
---
# &lt;runtime&gt; 要素
アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。  
  
## 構文  
  
```  
<runtime>  
</runtime>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<alwaysFlowImpersonationPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|偽装の実行方法に関係なく、Windows ID が常に非同期ポイント間をフローするように指定します。|  
|[\<appDomainManagerAssembly\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|プロセスの既定のアプリケーション ドメインにアプリケーション ドメイン マネージャーを提供するアセンブリを指定します。|  
|[\<appDomainManagerType\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーとして機能する型を指定します。|  
|[\<appDomainResourceMonitoring\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|プロセスの有効期間中、プロセス内のすべてのアプリケーション ドメインに関する統計情報を収集するようにランタイムに指示します。|  
|[\<assemblyBinding\>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|[\<bypassTrustedAppStrongNames\>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|完全に信頼されているアセンブリの厳密な名前の検証をバイパスするかどうかを指定します。|  
|[\<CompatSortNLSVersion\>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|文字列比較の実行時に、ランタイムがレガシ並べ替え動作を使用するように指定します。|  
|[\<developmentMode\>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|DEVPATH 環境変数で指定されたディレクトリでランタイムがアセンブリを検索するかどうかを指定します。|  
|[\<disableCachingBindingFailures\>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|.NET Framework Version 2.0 の既定の動作であるバインディング エラーのキャッシュを無効にするかどうかを指定します。|  
|[\<disableCommitThreadStack\>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|スレッドの起動時にスレッド スタック全体をコミットするかどうかを指定します。|  
|[\<disableFusionUpdatesFromADManager\>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|アプリケーション ドメインの構成設定をランタイム ホストがオーバーライドできるという既定の動作を、無効にするかどうかを指定します。|  
|[\<enforceFIPSPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|暗号アルゴリズムが連邦情報処理規格 \(FIPS: Federal Information Processing Standard\) に準拠することを必要とするコンピューターの構成要件を適用するかどうかを指定します。|  
|[\<etwEnable\>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|共通言語ランタイム イベントで Windows イベント トレーシング \(ETW\) を有効にするかどうかを指定します。|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads\>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|PerfCounter.dll がカテゴリ固有の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを判断するために .NET Framework Version 1.1 アプリケーションの CategoryOptions レジストリ設定を使用するかどうかを指定します。|  
|[\<gcAllowVeryLargeObjects\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|64 ビット プラットフォームで、合計サイズが 2 GB \(ギガバイト\) を超える配列を有効にします。|  
|[\<gcConcurrent\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|共通言語ランタイムがガベージ コレクションを並列に実行するかどうかを指定します。|  
|[\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。|  
|[\<gcServer\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|共通言語ランタイムがサーバーのガベージ コレクションを実行するかどうかを指定します。|  
|[\<generatePublisherEvidence\>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|ランタイムがコード アクセス セキュリティ \(CAS: Code Access Security\) 発行者ポリシーを使用するかどうかを指定します。|  
|[\<legacyCorruptedStateExceptionsPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|ランタイムでアクセス違反やその他の破損状態の例外をマネージ コードがキャッチできるかどうかを指定します。|  
|[\<legacyImpersonationPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|現在のスレッドの実行コンテキストのフロー設定に関係なく、Windows ID が非同期ポイント間をフローしないように指定します。|  
|[\<loadfromRemoteSources\>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|リモート ソースからのアセンブリを完全信頼アセンブリとして読み込むかどうかを指定します。|  
|[\<NetFx40\_LegacySecurityPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|ランタイムがレガシ コード アクセス セキュリティ \(CAS: Code Access Security\) ポリシーを使用するかどうかを指定します。|  
|[\<NetFx40\_PInvokeStackResilience\>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|ランタイムが、マネージ コードとアンマネージ コードの間の切り替えを低速にしてでも、実行時に不適切なプラットフォーム呼び出し宣言を自動的に修正するかどうかを指定します。|  
|[\<NetFx45\_CultureAwareComparerGetHashCode\_LongStrings\>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|<xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName> のメソッドのハッシュ コードを計算するためにランタイムが固定メモリを使用するかどうかを指定します。|  
|[\<PreferComInsteadOfRemoting\>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|ランタイムでアプリケーション ドメインの境界を越えたリモート処理ではなく COM 相互運用機能が使用されることを指定します。|  
|[\<relativeBindForResources\>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|サテライト アセンブリのプローブを最適化します。|  
|[\<shadowCopyVerifyByTimeStamp\>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|シャドウ コピーの動作を、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] で導入された既定の起動動作にするか、旧バージョンの .NET Framework の起動動作に戻すかを指定します。|  
|[\<supportPortability\>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|.NET Framework の 2 つの異なる実装にある同じアセンブリを 1 つのアプリケーションから参照できるように、既定の動作を無効にすることができます。既定の動作では、アプリケーションの移植性を高めるために、このようなアセンブリは同等のものとして扱われます。|  
|[\<system.runtime.caching\>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|既定のメモリ内オブジェクト キャッシュの構成情報を提供します。|  
|[\<Thread\_UseAllCpuGroups\>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|ランタイムによって、すべての CPU グループにマネージ スレッドを分散するかどうかを指定します。|  
|[\<ThrowUnobservedTaskExceptions\>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|未処理の例外を実行中のプロセスを停止する必要があるかどうかを指定します。|  
|[\<TimeSpan\_LegacyFormatMode\>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|ランタイムで <xref:System.TimeSpan> 値に書式設定のレガシ動作を使用するかどうかを指定します。|  
|[\<UseRandomizedStringHashAlgorithm\>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|ランタイムがアプリケーション ドメインごとに文字列のハッシュ コードを計算するかどうかを指定します。|  
|[\<UseSmallInternalThreadStacks\>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|ランタイムで内部的に使用する特定のスレッドを作成するときに、既定のスタック サイズではなく明示的なスタック サイズを使用することを要求します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## 解説  
 .NET Framework Version 2.0 では、アプリケーション ドメイン内の非同期ポイント間で偽装 ID がフローします。  .NET Framework Version 2.0 では、machine.config ファイルまたはアプリケーションの構成ファイルでランタイム要素を適切に構成することで、非同期ポイント間の偽装のフローを有効または無効にできます。  ASP.NET の場合、偽装のフローは Windows \<\>Folder\\Microsoft.NET\\Framework\\vx.x.xxxx のディレクトリにある aspnet.config ファイルで構成できます。  
  
 既定では、ASP.NET は、aspnet.config ファイルに次の構成設定が使用されて偽装フローが無効になります。  
  
```  
configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 ASP.NET で偽装のフローを可能にする場合は、次の構成設定を明示的に使用する必要があります。  
  
```  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
 詳細については、「[\<legacyImpersonationPolicy\> 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)」および「[\<alwaysFlowImpersonationPolicy\> 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)」を参照してください。  
  
## 使用例  
 あるアセンブリ バージョンを別のバージョンにリダイレクトする例を示します。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
             <bindingRedirect oldVersion="1.0.0.0"  
                              newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [アセンブリ バージョンのリダイレクト](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)   
 [How to: Disable Concurrent Garbage Collection](http://msdn.microsoft.com/ja-jp/ba2c6c67-5778-497c-9fac-5f793b5500c7)