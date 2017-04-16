---
title: "&lt;PreferComInsteadOfManagedRemoting&gt; 要素 | Microsoft Docs"
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
  - "<PreferComInsteadOfManagedRemoting> 要素"
  - "PreferComInsteadOfManagedRemoting 要素"
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# &lt;PreferComInsteadOfManagedRemoting&gt; 要素
アプリケーション ドメインの境界を越えるすべての呼び出しについて、リモート処理ではなく COM 相互運用機能をランタイムで使用するかどうかを指定します。  
  
## 構文  
  
```  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> アプリケーション ドメインの境界を越える場合に、リモート処理ではなく COM 相互運用機能をランタイムで使用するかどうかを示します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|ランタイムは、アプリケーション ドメインの境界を越える場合にリモート処理を使用します。  これは、既定の設定です。|  
|`true`|ランタイムは、アプリケーション ドメインの境界を越える場合に COM 相互運用機能を使用します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 `enabled` 属性を `true` に設定した場合、ランタイムの動作は次のようになります。  
  
-   ランタイムは [IManagedObject](../../../../../ocs/framework/unmanaged-api/hosting/imanagedobject-interface.md) インターフェイスをインターフェイスが [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) COM インターフェイスを通じてドメインに入ったとき求めません [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867)。  代わりに、オブジェクトを囲む[ランタイム呼び出し可能ラッパー](../../../../../docs/framework/interop/runtime-callable-wrapper.md) \(RCW: Runtime Callable Wrapper\) を構築します。  
  
-   このドメインで生成された [COM 呼び出し可能ラッパー](../../../../../docs/framework/interop/com-callable-wrapper.md) \(CCW: COM Callable Wrapper\) の [IManagedObject](../../../../../ocs/framework/unmanaged-api/hosting/imanagedobject-interface.md) インターフェイスの `QueryInterface` 呼び出しを受け取った場合、ランタイムは E\_NOINTERFACE を返します。  
  
 この 2 つの動作によって、アプリケーション ドメインの境界を越えるマネージ オブジェクト間での COM インターフェイスを介する呼び出しは、すべてリモート処理ではなく COM と COM 相互運用機能を使用するようになります。  
  
## 使用例  
 次の例は、分離の境界を越える場合に、ランタイムで COM 相互運用機能が使用されるように指定する方法を示しています。  
  
```  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)