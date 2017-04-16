---
title: "選択的シリアル化 | Microsoft Docs"
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
  - "バイナリ シリアル化, 選択的シリアル化"
  - "シリアル化, 選択的シリアル化"
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 選択的シリアル化
クラスには、シリアル化できないフィールドが含まれていることがよくあります。たとえば、クラスのメンバー変数の 1 つにスレッド ID が格納されているとします。クラスを逆シリアル化すると、クラスのシリアル化時に格納された ID を持つスレッドが実行されなくなることがあります。この場合、ID 値をシリアル化しても意味はありません。メンバー変数に [NonSerialized](frlrfSystemNonSerializedAttributeClassTopic) 属性を使用してマークすることで、メンバー変数がシリアル化されないようにすることができます。以下に例を示します。  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```  
  
 機密データを含むオブジェクトは、可能であれば、シリアル化できないようにしてください。オブジェクトをシリアル化する必要がある場合は、機密データを格納する特定のフィールドに **NonSerialized** 属性を適用します。これらのフィールドをシリアル化の対象から除外しない場合は、フィールドに格納されているデータがシリアル化の許可を持つ任意のコードに公開されることに注意する必要があります。安全なシリアル化コードの記述方法の詳細については、「[セキュリティとシリアル化](../../../docs/framework/misc/security-and-serialization.md)」を参照してください。  
  
## 参照  
 [バイナリ シリアル化](../../../docs/framework/serialization/binary-serialization.md)   
 [Remote Objects](http://msdn.microsoft.com/ja-jp/515686e6-0a8d-42f7-8188-73abede57c58)   
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [セキュリティとシリアル化](../../../docs/framework/misc/security-and-serialization.md)