---
title: "&lt;Directives&gt; 要素 (.NET ネイティブ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;Directives&gt; 要素 (.NET ネイティブ)
[!INCLUDE[net_native](../../../includes/net-native-md.md)]のすべてのランタイム ディレクティブ ファイルのルート要素です。  
  
 **\<Directives xmlns\="http:\/\/schemas.microsoft.com\/netfx\/2013\/01\/metadata"\>**  
  
## 構文  
  
```xml  
  
        <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## 属性  
  
|属性|説明|  
|--------|--------|  
|`xmlns`|XML 名前空間。  値は常に **"http:\/\/schemas.microsoft.com\/netfx\/2013\/01\/metadata"** です。|  
  
## 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<Application\>](../../../docs/framework/net-native/application-element-net-native.md)|リフレクションで使用可能なメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。|  
|[\<Library\>](../../../docs/framework/net-native/library-element-net-native.md)|実行時にメタデータを必要とする子型と型のメンバーを持つアセンブリを定義します。|  
  
## 解説  
 各ランタイム ディレクティブ ファイルには、`<Directives>` 要素を 1 つのみ含めることができます。  
  
 `<Directives>` 要素には、0 または 1 個の [\<Application\>](../../../docs/framework/net-native/application-element-net-native.md) 要素と、0 個以上の [\<Library\>](../../../docs/framework/net-native/library-element-net-native.md) 要素を含めることができます。  
  
## 参照  
 [ランタイム ディレクティブ \(rd.xml\) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)