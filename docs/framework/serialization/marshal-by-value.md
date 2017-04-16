---
title: "値渡しによるマーシャリング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "バイナリ シリアル化, 値渡しによるマーシャリング"
  - "値渡しのマーシャリング オブジェクト"
  - "シリアル化, 値渡しによるマーシャリング"
ms.assetid: ee91e8f0-92e0-4732-8015-d17dee154be1
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 値渡しによるマーシャリング
オブジェクトは、作成されたアプリケーション ドメイン内でのみ有効です。オブジェクトをパラメーターとして渡したり、結果として返したりする処理を試行すると、そのオブジェクトが [MarshalByRefObject](frlrfSystemMarshalByRefObjectClassTopic) から派生しているか、または [Serializable](frlrfSystemSerializableAttributeClassTopic) としてマークされている場合を除いて、その試行は失敗します。**Serializable** としてマークされていると、オブジェクトは自動的にシリアル化され、アプリケーション ドメイン間で転送されます。その後、逆シリアル化され、転送先のアプリケーション ドメインにそのオブジェクトの同一コピーが作成されます。この処理は一般に、値渡しによるマーシャリングと呼ばれます。  
  
 オブジェクトが **MarshalByRefObject** から派生している場合は、そのオブジェクト自体ではなく、オブジェクト参照がアプリケーション ドメイン間で渡されます。**MarshalByRefObject** から派生したオブジェクトを、**Serializable** としてマークすることもできます。このオブジェクトがリモート処理で使用されると、サロゲート セレクター \([SurrogateSelector](frlrfSystemRuntimeSerializationSurrogateSelectorClassTopic)\) によって事前構成された、シリアル化を実行するフォーマッタがシリアル化プロセスを制御し、[MarshalByRefObject](frlrfSystemMarshalByRefObjectClassTopic) から派生したすべてのオブジェクトをプロキシに置き換えます。[SurrogateSelector](frlrfSystemRuntimeSerializationSurrogateSelectorClassTopic) を使用しない場合、シリアル化アーキテクチャは「[シリアル化プロセスの手順](../../../docs/framework/serialization/steps-in-the-serialization-process.md)」で説明されている標準のシリアル化のルールに従います。  
  
## 参照  
 [シリアル化の概念](../../../docs/framework/serialization/serialization-concepts.md)   
 [Remote Objects](http://msdn.microsoft.com/ja-jp/515686e6-0a8d-42f7-8188-73abede57c58)   
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)