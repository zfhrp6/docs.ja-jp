---
title: "&lt;enforceFIPSPolicy&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<enforceFIPSPolicy> 要素"
  - "enforceFIPSPolicy 要素"
  - "連邦情報処理規格 (FIPS: Federal Information Processing Standard)"
  - "FIPS"
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;enforceFIPSPolicy&gt; 要素
暗号アルゴリズムが連邦情報処理規格 \(FIPS: Federal Information Processing Standard\) に準拠することを必要とするコンピューターの構成要件を適用するかどうかを指定します。  
  
## 構文  
  
```  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|enabled|必須の属性です。<br /><br /> 暗号アルゴリズムが FIPS に準拠することを必要とするコンピューターの構成要件の適用を有効にするかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`true`|暗号アルゴリズムが FIPS に準拠することを必要とするようにコンピューターが構成されている場合は、その要件が適用されます。  クラスが FIPS に準拠しないアルゴリズムを実装している場合は、そのコンピューターでの実行時に、そのクラスのコンストラクターまたは `Create` メソッドによって例外がスローされます。  これは、既定の設定です。|  
|`false`|コンピューターの構成に関係なく、アプリケーションで使用される暗号アルゴリズムが FIPS に準拠する必要はありません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 .NET Framework 2.0 以降では、暗号アルゴリズムを実装するクラスの作成はコンピューターの構成によって制御されます。  アルゴリズムが FIPS に準拠することを必要とするようにコンピューターが構成されている場合に、クラスが FIPS に準拠しないアルゴリズムを実装しているときは、そのクラスのインスタンスを作成しようとすると例外がスローされます。  コンストラクターは <xref:System.InvalidOperationException> 例外をスローし、`Create` メソッドは内部に <xref:System.InvalidOperationException> 例外を含む <xref:System.Reflection.TargetInvocationException> 例外をスローします。  
  
 FIPS への準拠を必要とする構成になっているコンピューターでアプリケーションが実行される場合に、アプリケーションで FIPS に準拠しないアルゴリズムが使用されるときは、構成ファイルでこの要素を使用すると、共通言語ランタイム \(CLR: Common Language Runtime\) によって FIPS への準拠が適用されないようにすることができます。  この要素は、[!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)] で導入されました。  
  
## 使用例  
 次の例では、CLR によって FIPS への準拠が適用されないようにする方法を示します。  
  
```  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [暗号モデル](../../../../../docs/standard/security/cryptography-model.md)