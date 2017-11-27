---
title: "&lt;スタートアップ&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bd2356845c76e81ce2efe87bdf247de293d6115d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltstartupgt-element"></a>&lt;スタートアップ&gt;要素
共通言語ランタイム スタートアップ情報を指定します。  
  
 \<configuration>  
\<スタートアップ >  
  
## <a name="syntax"></a>構文  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|省略可能な属性です。<br /><br /> 有効にするかどうかを指定します、[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)]ランタイムのアクティブ化ポリシーを使用して、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]アクティブ化ポリシー。|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy 属性  
  
|値|説明|  
|-----------|-----------------|  
|`true`|有効にする[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)]ランタイムのアクティブ化ポリシーは、レガシ ランタイムのアクティブ化の手法をバインドする、選択したランタイムの (など、 [CorBindToRuntimeEx 関数](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) の代わりに、構成ファイルから選択した実行時にCLR バージョン 2.0 では、それらを上限です。 したがって、CLR version 4 以降を構成ファイルから選択した場合、.NET Framework の以前のバージョンで作成された混合モード アセンブリは、選択した CLR バージョンを読み込まれます。 CLR バージョン 1.1 または CLR バージョン 2.0 の実質的にインプロセスでサイド バイ サイド機能を無効にする、同じプロセスに読み込みを禁止この値を設定します。|  
|`false`|既定のアクティブ化ポリシーを使用して、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]は後で、レガシ ランタイムに CLR version 1.1 または 2.0 を読み込むプロセス ライセンス認証の手法を許可するとします。 この値を設定すると、以降、.NET Framework 4 でビルドされた場合を除き、.NET Framework 4 に、またはそれ以降の読み込みから混合モードのアセンブリができなくなります。 この値が既定値です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。 ランタイム バージョン 1.1 以降でビルドされたアプリケーションを使用する必要があります、  **\<supportedRuntime >**要素。|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="remarks"></a>コメント  
 **\<SupportedRuntime >** 1.1 以降、ランタイムのバージョンを使用して構築されたすべてのアプリケーションで要素を使用する必要があります。 ランタイムのバージョン 1.0 をサポートするために構築されたアプリケーションを使用する必要があります、  **\<requiredRuntime >**要素。  
  
 Microsoft Internet Explorer でホストされているアプリケーションのスタートアップ コードは無視されます、 **\<スタートアップ >**要素とその子要素です。  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>UseLegacyV2RuntimeActivationPolicy 属性  
 この属性は、アプリケーションなどに、レガシ アクティブ化のパスを使用する場合に便利です、 [CorBindToRuntimeEx 関数](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)、それらのパスを以前のバージョンではなく CLR の version 4 をアクティブ化して、アプリケーションがある場合、またはビルドされた、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]が .NET Framework の以前のバージョンでビルドされた混合モード アセンブリに依存しています。 そのようなシナリオで属性を設定`true`です。  
  
> [!NOTE]
>  属性を設定`true`CLR バージョン 1.1 または CLR バージョン 2.0 のプロセスでサイド バイ サイド機能を効果的に無効化が同じプロセスに読み込みを禁止 (を参照してください[COM 相互運用機能のサイド バイ サイド実行](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32))。  
  
## <a name="example"></a>例  
 次の例では、構成ファイルでランタイムのバージョンを指定する方法を示します。  
  
```xml  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [スタートアップ設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> 使用するランタイム バージョンの指定](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [COM 相互運用機能のサイド バイ サイド実行](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [インプロセスの side-by-side 実行](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
