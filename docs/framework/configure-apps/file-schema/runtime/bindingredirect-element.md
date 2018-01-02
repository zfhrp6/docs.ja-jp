---
title: "&lt;bindingRedirect&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f8cd497871d8a58504cf790f84cc7e5a1d4e39b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindingredirectgt-element"></a>&lt;bindingRedirect&gt;要素
1 つのアセンブリ バージョンを別のバージョンにリダイレクトします。  
  
 \<configuration>  
\<ランタイム >  
\<assemblyBinding >  
\<dependentAssembly >  
\<bindingRedirect >  
  
## <a name="syntax"></a>構文  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`oldVersion`|必須の属性です。<br /><br /> 初めに要求されていたアセンブリのバージョンを指定します。 アセンブリ バージョン番号の形式が*major.minor.build.revision*です。 このバージョン番号の各部分で有効値は、0 ～ 65535 です。<br /><br /> バージョン範囲は、次の形式でも指定できます。<br /><br /> *n.n.n.n - n.n.n.n*|  
|`newVersion`|必須の属性です。<br /><br /> 形式で要求されていたバージョンの代わりに使用するアセンブリのバージョンを指定します: *n.n.n.n*<br /><br /> この値では `oldVersion` より前のバージョンを指定できます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|なし||  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`dependentAssembly`|各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。 アセンブリごとに 1 つの dependentAssembly 要素を使用します。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 厳密な名前付きアセンブリに対して .NET Framework アプリケーションを構築すると、実行時に新しいバージョンが利用できる場合でも、既定で、アプリケーションの構築時に使用したアセンブリのバージョンが使用されます。 ただし、新しいバージョンのアセンブリで実行するようにもアプリケーションを構成できます。 ランタイムがこれらのファイルを使用して、使用するアセンブリ バージョンを決定する方法の詳細については、「[ランタイム アセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)です。  
  
 複数の `bindingRedirect` 要素を `dependentAssembly` 要素に含めることによって、複数のアセンブリ バージョンをリダイレクトできます。 また、アセンブリの新しいバージョンから古いバージョンにリダイレクトすることもできます。  
  
 アプリケーション構成ファイルで明示的にアセンブリ バインディングをリダイレクトするには、セキュリティ アクセス許可が必要です。 これは、.NET Framework アセンブリおよびサードパーティ製アセンブリに適用されます。 許可を設定して、<xref:System.Security.Permissions.SecurityPermissionFlag>フラグを<xref:System.Security.Permissions.SecurityPermission>です。 詳細については、次を参照してください。[アセンブリ バインディング リダイレクトのセキュリティのアクセス許可](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)です。  
  
## <a name="example"></a>例  
 あるアセンブリ バージョンを別のバージョンにリダイレクトする例を示します。  
  
```xml  
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
  
## <a name="see-also"></a>参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [アセンブリ バージョンのリダイレクト](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
