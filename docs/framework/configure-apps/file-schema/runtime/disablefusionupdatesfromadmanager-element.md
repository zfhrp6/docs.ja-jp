---
title: '&lt;disableFusionUpdatesFromADManager&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e5e33cd3d250b26f0a83a87c4f7ce438af22e96
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a>&lt;disableFusionUpdatesFromADManager&gt;要素
アプリケーション ドメインの構成設定をランタイム ホストが上書きする既定の動作を無効化するかどうかを指定します。  
  
 \<configuration > 要素  
\<ランタイム > 要素  
\<disableFusionUpdatesFromADManager >  
  
## <a name="syntax"></a>構文  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|必須の属性です。<br /><br /> Fusion の設定を上書きする既定の機能が無効になっているかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|0|Fusion の設定を上書きする機能を無効にしないでください。 これは、以降で、既定の動作、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]です。|  
|1|Fusion の設定を上書きする機能を無効にします。 これは、.NET Framework の以前のバージョンの動作に戻ります。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 以降で、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、既定の動作を許可するのには、<xref:System.AppDomainManager>を使用して構成設定を上書きするオブジェクト、<xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティまたは<xref:System.AppDomainSetup.SetConfigurationBytes%2A>のメソッド、<xref:System.AppDomainSetup>実装に渡されるオブジェクト<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>のサブクラス内のメソッド<xref:System.AppDomainManager>です。 既定のアプリケーション ドメインは、変更する設定は、アプリケーション構成ファイルで指定した設定を上書きします。 渡された構成設定が上書きの他のアプリケーション ドメイン、<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>または<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>メソッドです。  
  
 新しい構成情報を渡すか、null を渡します (`Nothing` Visual Basic で) で渡された構成情報を削除します。  
  
 両方に構成情報を渡さないでください、<xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティおよび<xref:System.AppDomainSetup.SetConfigurationBytes%2A>メソッドです。 両方に構成情報を渡す場合、情報を渡す、<xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティが無視されるため、<xref:System.AppDomainSetup.SetConfigurationBytes%2A>メソッドは、アプリケーション構成ファイルから構成情報をオーバーライドします。 使用する場合、<xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティが null を渡す (`Nothing` Visual Basic で) に、<xref:System.AppDomainSetup.SetConfigurationBytes%2A>への呼び出しで指定された構成バイトを取り除く方法、<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>または<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>メソッドです。  
  
 次の設定を変更する構成情報に加えて、<xref:System.AppDomainSetup>の実装に渡されるオブジェクト、<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>メソッド: <xref:System.AppDomainSetup.ApplicationBase%2A>、 <xref:System.AppDomainSetup.ApplicationName%2A>、 <xref:System.AppDomainSetup.CachePath%2A>、 <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>、 <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>、 <xref:System.AppDomainSetup.DisallowCodeDownload%2A>、 <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>、 <xref:System.AppDomainSetup.DynamicBase%2A>、 <xref:System.AppDomainSetup.LoaderOptimization%2A>、 <xref:System.AppDomainSetup.PrivateBinPath%2A>、 <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>、 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>、および<xref:System.AppDomainSetup.ShadowCopyFiles%2A>です。  
  
 使用する代わりに、`<disableFusionUpdatesFromADManager>`要素、ことができますを無効にする既定の動作または環境変数を設定して、レジストリ設定を作成します。 レジストリで、という名前の DWORD 値を作成する`COMPLUS_disableFusionUpdatesFromADManager``HKCU\Software\Microsoft\.NETFramework`または`HKLM\Software\Microsoft\.NETFramework`、し、値を 1 に設定します。 環境変数を設定、コマンドラインで`COMPLUS_disableFusionUpdatesFromADManager`を 1 にします。  
  
## <a name="example"></a>例  
 次の例を使用して Fusion の設定を上書きする機能を無効にする方法を示しています、`<disableFusionUpdatesFromADManager>`要素。  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
