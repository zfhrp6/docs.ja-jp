---
title: "シリアル化プロセスの手順 | Microsoft Docs"
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
  - "バイナリ シリアル化, 手順"
  - "シリアル化, 手順"
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# シリアル化プロセスの手順
[フォーマッタ](frlrfSystemRuntimeSerializationFormatterClassTopic)で [Serialize](frlrfSystemRuntimeSerializationFormatterClassSerializeTopic) メソッドが呼び出されると、次の一連の規則に従って、オブジェクトのシリアル化プロセスが実行されます。  
  
-   フォーマッタにサロゲート セレクターが存在するかどうかをチェックします。サロゲート セレクターが存在する場合は、そのサロゲート セレクターが指定された型のオブジェクトを処理できるかどうかをチェックします。そのオブジェクトの型を処理できる場合は、サロゲート セレクターで **ISerializable.GetObjectData** を呼び出します。  
  
-   サロゲート セレクターが存在しないか、またはサロゲート セレクターがそのオブジェクトの型を処理しない場合は、オブジェクトが [Serializable](frlrfSystemSerializableAttributeClassTopic) 属性でマークされているかどうかをチェックします。マークされていない場合は、[SerializationException](frlrfSystemRuntimeSerializationSerializationExceptionClassTopic) をスローします。  
  
-   オブジェクトが適切にマークされている場合は、オブジェクトが [ISerializable](frlrfSystemRuntimeSerializationISerializableClassTopic) インターフェイスを実装しているかどうかをチェックします。実装している場合は、そのオブジェクトで [GetObjectData](frlrfSystemRuntimeSerializationISerializableClassGetObjectDataTopic) を呼び出します。  
  
-   オブジェクトが **ISerializable** を実装していない場合は、既定のシリアル化ポリシーを適用して、[NonSerialized](frlrfSystemNonSerializedAttributeClassTopic) としてマークされていないすべてのフィールドをシリアル化します。  
  
## 参照  
 [バイナリ シリアル化](../../../docs/framework/serialization/binary-serialization.md)   
 [Remote Objects](http://msdn.microsoft.com/ja-jp/515686e6-0a8d-42f7-8188-73abede57c58)   
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)