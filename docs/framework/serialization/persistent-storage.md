---
title: "永続ストレージ | Microsoft Docs"
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
  - "バイナリ シリアル化, 永続ストレージ"
  - "永続ストレージ"
  - "シリアル化, 永続ストレージ"
ms.assetid: b112c0dd-93e2-4eef-908d-5963f80bab65
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 永続ストレージ
オブジェクトのフィールドの値をディスクに格納しておき、後でこのデータを取得する必要が生じることはよくあります。これはシリアル化を使用しなくても簡単に実現できますが、シリアル化を使用しない方法は煩雑でエラーの原因となることが多く、オブジェクトの階層を追跡する必要がある場合にはさらに複雑になります。何千ものオブジェクトを含む大規模なビジネス アプリケーションを作成し、それぞれのオブジェクトのフィールドやプロパティをディスクに保存したり、ディスクから復元したりするコードを記述することを想像してみてください。シリアル化は、この目的を実現するための便利なメカニズムを提供します。  
  
 共通言語ランタイムは、オブジェクトがメモリに格納される方法を管理し、[リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)を使用して自動シリアル化のメカニズムを提供します。オブジェクトをシリアル化すると、クラスの名前、アセンブリ、およびそのクラス インスタンスのすべてのデータ メンバーがストレージに書き込まれます。オブジェクトのメンバー変数には、他のインスタンスへの参照が格納されていることがよくあります。クラスをシリアル化するとき、シリアル化エンジンは、既にシリアル化されている参照先オブジェクトを追跡し、同じオブジェクトが複数回シリアル化されないようにします。[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] に用意されているシリアル化アーキテクチャは、オブジェクト グラフおよび循環参照を自動的に正しく処理します。オブジェクト グラフに対する唯一の要件は、シリアル化されたオブジェクトによって参照されるすべてのオブジェクトを、[Serializable](frlrfSystemSerializableAttributeClassTopic) としてもマークすることです。詳細については、「[基本的なシリアル化](../../../docs/framework/serialization/basic-serialization.md)」を参照してください。Serializable としてマークしないと、マークされていないオブジェクトをシリアライザーがシリアル化しようとしたときに例外がスローされます。  
  
 シリアル化されたクラスを逆シリアル化すると、そのクラスが再作成され、すべてのデータ メンバーの値は自動的に復元されます。  
  
## 参照  
 [シリアル化の概念](../../../docs/framework/serialization/serialization-concepts.md)   
 [Remote Objects](http://msdn.microsoft.com/ja-jp/515686e6-0a8d-42f7-8188-73abede57c58)   
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)