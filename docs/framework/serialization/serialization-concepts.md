---
title: "シリアル化の概念 | Microsoft Docs"
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
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# シリアル化の概念
シリアル化が必要となる理由について考えてみます。最も重要な理由として、オブジェクトの状態をストレージ メディアに保持し、後の段階で同一コピーを再作成できるようにすることと、アプリケーション ドメイン間でオブジェクトを値渡しで送信することの 2 つが挙げられます。たとえば、シリアル化は ASP.NET でのセッション状態を保存したり、オブジェクトを Windows フォームのクリップボードにコピーしたりするために使用されます。また、リモート処理でオブジェクトを 1 つのアプリケーション ドメインから別のアプリケーション ドメインに値渡しするためにも使用されます。  
  
## このセクションの内容  
 [永続ストレージ](../../../docs/framework/serialization/persistent-storage.md)  
 オブジェクトをシリアル化する必要性について説明します。  
  
 [値渡しによるマーシャリング](../../../docs/framework/serialization/marshal-by-value.md)  
 値渡しによるマーシャリングの処理について説明します。  
  
## 関連項目  
 [バイナリ シリアル化](../../../docs/framework/serialization/binary-serialization.md)  
 共通言語ランタイムに付属しているバイナリ シリアル化機構について説明します。  
  
 [Remote Objects](http://msdn.microsoft.com/ja-jp/515686e6-0a8d-42f7-8188-73abede57c58)  
 .NET Framework でリモート通信に利用できるさまざまな通信方法について説明します。  
  
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)  
 共通言語ランタイムに付属している XML シリアル化および SOAP シリアル化機構について説明します。