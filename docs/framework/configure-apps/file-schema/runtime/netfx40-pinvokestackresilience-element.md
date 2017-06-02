---
title: "&lt;NetFx40_PInvokeStackResilience&gt; 要素 | Microsoft Docs"
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
  - "<NetFx40_PInvokeStackResilience> 要素"
  - "NetFx40_PInvokeStackResilience 要素"
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;NetFx40_PInvokeStackResilience&gt; 要素
ランタイムが、マネージ コードとアンマネージ コードの間の切り替えを低速にしてでも、実行時に不適切なプラットフォーム呼び出し宣言を自動的に修正するかどうかを指定します。  
  
## 構文  
  
```  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムが、32 ビット プラットフォームで実行時に不適切なプラットフォーム呼び出し宣言を検出し、スタックを自動的に修正するかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`0`|ランタイムは、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] で導入された、より高速な相互運用マーシャリング アーキテクチャを使用します。このアーキテクチャは、不適切なプラットフォーム呼び出し宣言を検出および修正しません。  これは、既定の設定です。|  
|`1`|ランタイムは、不適切なプラットフォーム呼び出し宣言を検出および修正する、より低速な切り替えを使用します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## 解説  
 この要素を使用すると、より高速な相互運用マーシャリングを、不適切なプラットフォーム呼び出し宣言に対するランタイム回復と交換できます。  
  
 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 以降では、効率化された相互運用マーシャリング アーキテクチャによって、マネージ コードからアンマネージ コードへの切り替えのパフォーマンスが大幅に向上します。  旧バージョンの .NET Framework では、マーシャリング レイヤーは 32 ビット プラットフォームで不適切なプラットフォーム呼び出し宣言を検出し、スタックを自動的に修正しました。  新しいマーシャリング アーキテクチャでは、この手順が排除されます。  その結果、切り替えは非常に高速ですが、不適切なプラットフォーム呼び出し宣言によってプログラム エラーが発生することがあります。  
  
 開発中に不適切な宣言を簡単に検出するために、Visual Studio デバッグ機能が強化されました。  [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) マネージ デバッグ アシスタント \(MDA\) は、アプリケーションにデバッガーがアタッチされて稼働しているときに、不適切なプラットフォーム呼び出し宣言を通知します。  
  
 再コンパイルできず、不適切なプラットフォーム呼び出し宣言のあるコンポーネントをアプリケーションが使用する状況に対処するために、`NetFx40_PInvokeStackResilience` 要素を使用できます。  `enabled="1"` を指定してこの要素をアプリケーション構成ファイルに追加すると、切り替えは遅くなりますが、旧バージョンの .NET Framework の動作との互換モードを選択することができます。  旧バージョンの .NET Framework に対してコンパイルされたアセンブリでは、この互換モードが自動的に選択されるため、この要素は不要です。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## 使用例  
 マネージ コードとアンマネージ コードの間の切り替えは低速になりますが、アプリケーションの不適切なプラットフォーム呼び出し宣言に対する回復を強化する方法を次の例に示します。  
  
```  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)