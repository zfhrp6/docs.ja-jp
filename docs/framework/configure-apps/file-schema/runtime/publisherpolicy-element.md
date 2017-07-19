---
title: "&lt;publisherPolicy&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<publisherPolicy> 要素"
  - "コンテナー タグ, <publisherPolicy> 要素"
  - "publisherPolicy 要素"
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# &lt;publisherPolicy&gt; 要素
ランタイムが発行者ポリシーを適用するかどうかを指定します。  
  
## 構文  
  
```  
  
<publisherPolicy apply="yes|no"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`apply`|発行者ポリシーを適用するかどうかを指定します。|  
  
## apply 属性  
  
|値|説明|  
|-------|--------|  
|`yes`|発行者ポリシーを適用します。  これは、既定の設定です。|  
|`no`|発行者ポリシーを適用しません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 コンポーネントの販売元は、アセンブリの新しいバージョンをリリースするときに、以前のバージョンを使用していたアプリケーションが新しいバージョンを使用するように、発行者ポリシーを含めることができます。  指定するには、特定のアセンブリの発行者ポリシーを適用するかどうか **\<dependentAssembly\>** 要素に **\<publisherPolicy\>** 要素を含めます。  
  
 **apply** 属性の既定の設定は **yes** です。  **apply** 属性を **no** に設定すると、アセンブリに対して既に設定されていたすべての **yes** がオーバーライドされます。  
  
 アクセス許可はアプリケーションに明示的にアプリケーション構成ファイルの [\<publisherPolicy apply\= "いいえ」\/\>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) 要素を使用して発行者ポリシーを無視する必要があります。  アクセス許可は、[SecurityPermission クラス](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic)の [BindingRedirects](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic) フラグを設定することによって付与されます。  詳細については、「[アセンブリ バインディング リダイレクトのセキュリティ アクセス許可](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)」を参照してください。  
  
## 使用例  
 アセンブリ `myAssembly` の発行者ポリシーを無効にする例を示します。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [アセンブリ バージョンのリダイレクト](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)