---
title: '&lt;codeBase&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3b614546e8ed23cc1a5e169a33fb5878695037ae
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745995"
---
# <a name="ltcodebasegt-element"></a>&lt;codeBase&gt;要素
共通言語ランタイムがアセンブリを検索する場所を指定します。  
  
 \<configuration>  
\<ランタイム >  
\<assemblyBinding>  
\<dependentAssembly >  
\<codeBase >  
  
## <a name="syntax"></a>構文  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`href`|必須の属性です。<br /><br /> ランタイムがアセンブリの指定されたバージョンを検索する場所の URL を指定します。|  
|`version`|必須の属性です。<br /><br /> コードベースを適用するアセンブリのバージョンを指定します。 アセンブリ バージョン番号の形式が*major.minor.build.revision*です。|  
  
## <a name="version-attribute"></a>バージョン属性  
  
|[値]|説明|  
|-----------|-----------------|  
|バージョン番号の各部分の有効な値は、0 ~ 65535 です。|該当なし。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`buildproviders`|カスタム リソース ファイルをコンパイルするためのビルド プロバイダーのコレクションを定義します。 ビルド プロバイダーの数は任意です。|  
|`compilation`|ASP.NET で使用されるすべてのコンパイルの設定を構成します。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`System.web`|ASP.NET 構成セクションのルート要素を指定します。|  
  
## <a name="remarks"></a>コメント  
 ランタイムを使用するため、  **\<codeBase >** 発行者ポリシー ファイルまたはマシン構成ファイルで設定をファイルする必要がありますも、アセンブリ バージョンをリダイレクトします。 アプリケーション構成ファイルは、アセンブリのバージョンをリダイレクトすることがなく、コードベースの設定を持つことができます。 使用するアセンブリ バージョンを決定した後は、ランタイムは、バージョンを決定するファイルのコードベースの設定を適用します。 コードベースが示されていない場合、ランタイムは、通常の方法で、アセンブリをプローブします。  
  
 アセンブリに厳密な名前がある場合、コードベース設定できる任意の場所、ローカル イントラネットまたはインターネット上です。 アセンブリがプライベート アセンブリの場合は、コードベースの設定は、アプリケーションのディレクトリに対する相対パスである必要があります。  
  
 厳密な名前を指定せず、アセンブリのバージョンは無視され、ローダーの最初の外観を使用して\<codebase > 内部\<dependentAssembly >。 別のアセンブリへのバインディングをリダイレクトする、アプリケーション構成ファイルにエントリがある場合、アセンブリのバージョンは、バインド要求と一致しない場合でもはリダイレクトが優先されます。  
  
## <a name="example"></a>例  
 次の例では、ランタイムがアセンブリを検索する場所を指定する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [アセンブリの場所の指定](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
