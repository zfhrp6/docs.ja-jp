---
title: "&lt;qualifyAssembly&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<qualifyAssembly> 要素"
  - "コンテナー タグ, <qualifyAssembly> 要素"
  - "qualifyAssembly 要素"
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;qualifyAssembly&gt; 要素
部分名が使用された場合に動的に読み込む必要があるアセンブリの完全名を指定します。  
  
## 構文  
  
```  
  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`partialName`|必須の属性です。<br /><br /> コード内で使用するアセンブリの部分名を指定します。|  
|`fullName`|必須の属性です。<br /><br /> グローバル アセンブリ キャッシュ内で使用するアセンブリの完全名を指定します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 部分アセンブリ名を使用して <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> メソッドを呼び出すと、共通言語ランタイムはアプリケーション ベース ディレクトリ内でのみアセンブリを検索します。  完全なアセンブリ情報 \(名前、バージョン、公開キー トークン、およびカルチャ\) を指定すると、共通言語ランタイムはグローバル アセンブリ キャッシュ内のアセンブリを捜させますアプリケーション構成ファイルで **\<qualifyAssembly\>** 要素を使用します。  
  
 **fullName** 属性には、アセンブリを識別するための 4 つのフィールド \(名前、バージョン、公開キー トークン、およびカルチャ\) を含める必要があります。  **partialName** 属性は、アセンブリを部分的に参照します。  少なくともアセンブリのテキスト名を指定する必要がありますが \(これが最も一般的です\)、テキスト名だけでなく、バージョン、公開キー トークン、カルチャ、またはこれら 4 つの任意の組み合わせも指定できます。  **partialName** は、呼び出しで指定する名前と一致する必要があります。  たとえば、構成ファイル内の **partialName** 属性として `"math"` を指定した場合に、コード内で呼び出し `Assembly.Load("math, Version=3.3.3.3")` を指定することはできません。  
  
## 使用例  
 `Assembly.Load("math")` を `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` の呼び出しに論理的に変換する例を次に示します。  
  
```  
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
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [NIB: Partial Assembly References](http://msdn.microsoft.com/ja-jp/ec90f07a-398c-4306-9401-0fc5ff9cb59f)