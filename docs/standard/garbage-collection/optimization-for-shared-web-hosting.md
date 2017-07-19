---
title: "Optimization for Shared Web Hosting | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "garbage collection, Web hosting"
  - "garbage collection, optimizing"
  - "garbage collection, shared Web hosting"
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Optimization for Shared Web Hosting
複数の小さい Web サイトをホストすることで共有されるサーバーを管理する場合は、.NET Framework ディレクトリにある Aspnet.config ファイルの `runtime` ノードに次の `gcTrimCommitOnLowMemory` の設定を追加することで、パフォーマンスを最適化し、サイトの容量を増やすことができます。  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  この設定が推奨されるのは、共有 Web ホストのシナリオだけです。  
  
 ガベージ コレクターは将来の割り当てのためにメモリを保持しているので、コミットされる領域は、厳密に必要な量より多くなる場合があります。  この領域を減らして、システム メモリに高負荷がかかるときに備えることができます。  このコミットされる領域を少なくすると、パフォーマンスが向上し、より多くのサイトをホストできるようになります。  
  
 `gcTrimCommitOnLowMemory` の設定を有効にすると、ガベージ コレクターは、システム メモリの負荷を評価し、負荷が 90% に達するとトリミング モードに移行します。  その後、負荷が 85% 以下に低下するまで、トリミング モードを維持します。  
  
 状況によっては、ガベージ コレクターは `gcTrimCommitOnLowMemory` の設定が現在のアプリケーションに対して効果がないと判断して、設定を無視する場合があります。  
  
## 例  
 次の XML フラグメントは、`gcTrimCommitOnLowMemory` の設定を有効にする方法を示しています。  省略記号は、`runtime` ノードでの他の設定を示します。  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## 参照  
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)