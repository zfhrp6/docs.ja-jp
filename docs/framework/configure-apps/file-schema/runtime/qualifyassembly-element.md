---
title: "&lt;qualifyAssembly&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 521bbccd83f224cc824dae41309715d65472454e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltqualifyassemblygt-element"></a>&lt;qualifyAssembly&gt;要素
部分名が使用された場合に動的に読み込む必要があるアセンブリの完全名を指定します。  
  
 \<configuration>  
\<ランタイム >  
\<assemblyBinding >  
\<qualifyAssembly >  
  
## <a name="syntax"></a>構文  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`partialName`|必須の属性です。<br /><br /> コードに表示されるアセンブリの部分名を指定します。|  
|`fullName`|必須の属性です。<br /><br /> グローバル アセンブリ キャッシュに表示されるアセンブリの完全な名前を指定します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 呼び出す、<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>部分アセンブリ名を使用して、メソッド、共通言語ランタイムによってのみ、アプリケーション ベース ディレクトリ内のアセンブリを探すようにします。 使用して、  **\<qualifyAssembly >** (名前、バージョン、公開キー トークン、およびカルチャ) の完全なアセンブリ情報を提供し、により、共通言語ランタイムを検索するアプリケーション構成ファイル内の要素グローバル アセンブリ キャッシュにアセンブリ。  
  
 **FullName**属性がアセンブリ id の 4 つのフィールドを含める必要があります。 名前、バージョン、公開キー トークン、およびカルチャ。 **それよりも**属性では、アセンブリは参照部分的にする必要があります。 アセンブリのテキストの名前 (最も一般的なケース) を少なくとも指定する必要がありますが、バージョン、公開キー トークン、またはカルチャ (または、4 つが、すべての 4 つの任意の組み合わせ) にも含めることができます。 **それよりも**の呼び出しで指定された名前に一致する必要があります。 たとえば、指定することはできません`"math"`として、**それよりも**構成ファイルと呼び出し属性`Assembly.Load("math, Version=3.3.3.3")`コードにします。  
  
## <a name="example"></a>例  
 次の例は、呼び出しを論理的にオンに`Assembly.Load("math")`に`Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`です。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [NIB: 部分アセンブリ参照](http://msdn.microsoft.com/en-us/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
