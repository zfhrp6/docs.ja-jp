---
title: "&lt;configuration&gt; の &lt;assemblyBinding&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<assemblyBinding> 要素"
  - "assemblyBinding 要素"
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;configuration&gt; の &lt;assemblyBinding&gt; 要素
構成レベルでのアセンブリ バインディング ポリシーを指定します。  
  
## 構文  
  
```  
<assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1">  
</assemblyBinding>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`xmlns`|必須の属性です。<br /><br /> アセンブリのバインディングに必要な XML 名前空間を指定します。  値として、文字列 "urn:schemas\-microsoft\-com:asm.v1" を使用します。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<linkedConfiguration\> 要素](../../../../docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)|インクルードする構成ファイルを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<configuration\> 要素](../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## 解説  
 [\<linkedConfiguration\> 要素](../../../../docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) は、アセンブリ構成設定を複製するのではなく、既知の場所にあるアセンブリ構成ファイルをアプリケーション構成ファイルにインクルードできるようにすることで、コンポーネント アセンブリの管理を簡素化します。  
  
> [!NOTE]
>  Windows side\-by\-side マニフェストを使用するアプリケーションに対しては、`<linkedConfiguration>` 要素がサポートされません。  
  
## 使用例  
 ローカル ハード ディスク上の構成ファイルをインクルードする方法を、次のコード例に示します。  
  
```  
<configuration>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>  
   </assemblyBinding>  
</configuration>  
```  
  
## 参照  
 [構成ファイル スキーマ](../../../../docs/framework/configure-apps/file-schema/index.md)